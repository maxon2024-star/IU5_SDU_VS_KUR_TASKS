# Лабораторная работа №3: Проектирование управляющего автомата (УА) на жесткой логике

## 1. Введение и теоретическая база

В предыдущих работах мы создали структурный базис операционного автомата (ОА) и интегрировали его с АЛУ. Но сейчас наш Datapath "глупый" — мы вынуждены вручную задавать сигналы `we`, `alu_ctrl` и адреса регистров прямо из тестбенча. В реальном чипе эту работу выполняет Управляющий автомат (Control Unit).

**Цель работы:** Реализация конечного автомата (FSM) для управления трактом данных.

**Теоретическая база:** Модуль 1, Лекции 9-10 (ЦА Мура/Мили). Как и прежде, разработка ведется исключительно в симуляторе (ModelSim, Icarus Verilog или Vivado), что позволяет не упираться в аппаратные лимиты ПЛИС и больше внимания уделить архитектурным решениям.

Управляющий автомат считывает код операции (OpCode) и проходит через классический машинный цикл:


**Выборка (Fetch) -> Декодирование (Decode) -> Выполнение (Execute)**. В этой лабораторной работе мы реализуем "жесткую логику" (Hardwired Control), где каждое состояние жестко закодировано в архитектуре конечного автомата (Finite State Machine).

---

## 2. Генерация индивидуального варианта (Google Colab)

Скопируйте скрипт в Google Colab, введите свои данные и узнайте, какой тип автомата и какие инструкции вам предстоит реализовать.

```python
import hashlib

def generate_lab3_variant(year, group, variant):
    seed_string = f"{year}-{group}-{variant}-lab3"
    hash_int = int(hashlib.md5(seed_string.encode()).hexdigest(), 16)
    
    # Тип автомата
    fsm_types = ["Автомат Мура (Moore FSM)", "Автомат Мили (Mealy FSM)"]
    fsm = fsm_types[hash_int % len(fsm_types)]
    
    # Разрядность кода операции (OpCode)
    opcode_widths = [3, 4, 5]
    op_width = opcode_widths[(hash_int // 10) % len(opcode_widths)]
    
    # Набор обязательных инструкций (3-4 базовые инструкции)
    instruction_sets = [
        ["ADD (Сложение)", "SUB (Вычитание)", "MOV (Копирование регистра)"],
        ["ADD (Сложение)", "AND (Логическое И)", "LDI (Загрузка константы)"],
        ["SUB (Вычитание)", "OR (Логическое ИЛИ)", "MOV (Копирование регистра)"],
        ["ADD (Сложение)", "SUB (Вычитание)", "AND (Логическое И)", "XOR (Искл. ИЛИ)"]
    ]
    instr_set = instruction_sets[(hash_int // 100) % len(instruction_sets)]
    
    print("="*60)
    print(f"ТЕХНИЧЕСКОЕ ЗАДАНИЕ (Control Unit): Группа {group}, Вариант {variant}")
    print("="*60)
    print(f"1. Архитектура FSM:            {fsm}")
    print(f"2. Разрядность OpCode:         {op_width} бит")
    print("3. Обязательный набор команд: ")
    for i, instr in enumerate(instr_set, 1):
        print(f"   {i}. {instr}")
    print("="*60)
    print("Примечание: Инструкции должны корректно переключать состояния FSM!")

# === ВВЕДИТЕ СВОИ ДАННЫЕ СЮДА ===
generate_lab3_variant(year=2026, group="ИУ5-41Б", variant=15)

```

---

## 3. Описание задания и базовые примеры кода

Вам необходимо спроектировать "мозг" процессора.

**Пошаговые задачи:**

1. Спроектировать FSM (машину состояний Мура или Мили), реализующую базовый цикл: Выборка $\rightarrow$ Декодирование $\rightarrow$ Выполнение.


2. Закодировать 3-4 базовые инструкции (например, ADD, SUB, MOV), выданные вам в варианте.


3. Симуляция: подача "машинного кода" на вход УА и проверка правильности выставления управляющих сигналов для ОА.



### Структурная схема (Control Unit)

```text
              +-----------------------------------+
              |          Control Unit (FSM)       |
              |                                   |
    clk ----->|                                   |-----> we_rf (Разрешение записи в RF)
    rst ----->|                                   |-----> alu_ctrl (Код операции для АЛУ)
              |                                   |
 opcode ----->|          State Register           |-----> (Другие мультиплексоры Datapath)
              |  (Fetch -> Decode -> Execute)     |
              |                                   |
              +-----------------------------------+

```

### 3.1 Шаблон Управляющего автомата (`control_unit.v`)

В Verilog конечные автоматы обычно описываются тремя блоками (или двумя, если объединить логику). Ниже приведен пример для **Автомата Мура**.

```verilog
module control_unit #(
    parameter OPCODE_WIDTH = 4
)(
    input  wire                    clk,
    input  wire                    rst,
    input  wire [OPCODE_WIDTH-1:0] opcode,  // Код операции (машинный код)
    
    // Управляющие сигналы для ОА (Datapath)
    output reg                     we_rf,   // Запись в регистр
    output reg  [2:0]              alu_ctrl // Управление АЛУ
);

    // Кодировка состояний FSM (State Encoding)
    localparam STATE_FETCH   = 2'd0;
    localparam STATE_DECODE  = 2'd1;
    localparam STATE_EXECUTE = 2'd2;

    // Коды инструкций (OpCodes) - Настройте под свой вариант!
    localparam OP_ADD = 4'b0001;
    localparam OP_SUB = 4'b0010;
    localparam OP_MOV = 4'b0011;

    reg [1:0] current_state, next_state;

    // 1. Блок памяти FSM (Синхронный переход состояний)
    always @(posedge clk) begin
        if (rst) current_state <= STATE_FETCH;
        else     current_state <= next_state;
    end

    // 2. Логика переходов (Комбинаторная)
    always @(*) begin
        // Значение по умолчанию
        next_state = current_state; 
        
        case (current_state)
            STATE_FETCH: begin
                // В реальном процессоре здесь мы бы читали инструкцию из памяти
                next_state = STATE_DECODE;
            end
            STATE_DECODE: begin
                // Анализируем OpCode
                next_state = STATE_EXECUTE; 
            end
            STATE_EXECUTE: begin
                // Инструкция выполнена, возвращаемся за следующей
                next_state = STATE_FETCH;
            end
            default: next_state = STATE_FETCH;
        endcase
    end

    // 3. Выходная логика (Для автомата Мура выходы зависят ТОЛЬКО от состояния)
    always @(*) begin
        // Инициализация выходов нулями (защита от Latch)
        we_rf = 1'b0;
        alu_ctrl = 3'b000;

        case (current_state)
            STATE_EXECUTE: begin
                // Выставляем сигналы в зависимости от того, какую инструкцию декодировали
                case (opcode)
                    OP_ADD: begin
                        we_rf = 1'b1;       // Разрешаем записать результат
                        alu_ctrl = 3'b000;  // Код сложения для АЛУ (из Лабы 2)
                    end
                    OP_SUB: begin
                        we_rf = 1'b1;
                        alu_ctrl = 3'b001;
                    end
                    OP_MOV: begin
                        // Например, MOV реализуется пробросом операнда А через АЛУ
                        we_rf = 1'b1;
                        alu_ctrl = 3'b100; // Условный код "PASS_A" в вашем АЛУ
                    end
                endcase
            end
            // В состояниях FETCH и DECODE мы не пишем в регистры
        endcase
    end

endmodule

```

### 3.2 Базовый тестбенч (`cu_tb.v`)

В этой лабораторной мы имитируем подачу машинного кода на вход.

```verilog
`timescale 1ns / 1ps

module cu_tb;

    parameter OPCODE_WIDTH = 4;

    reg clk;
    reg rst;
    reg [OPCODE_WIDTH-1:0] opcode;
    
    wire we_rf;
    wire [2:0] alu_ctrl;

    // Инстанцирование CU
    control_unit #(.OPCODE_WIDTH(OPCODE_WIDTH)) dut (
        .clk(clk),
        .rst(rst),
        .opcode(opcode),
        .we_rf(we_rf),
        .alu_ctrl(alu_ctrl)
    );

    always #5 clk = ~clk; // Период 10 нс

    initial begin
        $dumpfile("cu_waves.vcd");
        $dumpvars(0, cu_tb);

        clk = 0; rst = 1; opcode = 0;
        #15 rst = 0;

        // Эмулируем подачу инструкции ADD
        // FSM находится в состоянии FETCH -> DECODE -> EXECUTE
        opcode = 4'b0001; 
        #30; // Ждем 3 такта (Fetch, Decode, Execute)
        
        // Эмулируем подачу инструкции SUB
        opcode = 4'b0010;
        #30; 

        // Проверьте по диаграммам, что we_rf поднимается только в состоянии EXECUTE!

        #50 $finish;
    end
endmodule

```

---

## 4. Критерии приемки и контрольные вопросы

### Рекомендуемая структура проекта

```text
lab3_fsm/
├── src/
│   └── control_unit.v       # Исходный код автомата
├── tb/
│   └── cu_tb.v              # Тестбенч
├── sim/                     
└── README.md                

```

**Запуск в Icarus Verilog:** 1. `iverilog -o sim/cu.vvp src/control_unit.v tb/cu_tb.v`
2. `vvp sim/cu.vvp`
3. `gtkwave cu_waves.vcd`

### Критерии успешной сдачи

* **Синтаксис и Latch-free код:** В коде отсутствуют нежелательные защелки (Latches). Переменные в блоках `always @(*)` инициализируются значениями по умолчанию.
* **Машинный цикл:** Временные диаграммы четко показывают переход автомата по стадиям: `Fetch -> Decode -> Execute`.


* **Корректные сигналы:** При подаче "машинного кода" (OpCode) автомат правильно формирует управляющие сигналы (`we`, `alu_ctrl`) для заявленных в варианте 3-4 базовых инструкций.


* **Соответствие варианту:** Строго реализован автомат Мура или Мили в зависимости от технического задания.

### Контрольные вопросы к защите

1. В чем принципиальное отличие конечного автомата Мура от автомата Мили? Как это выражается в коде на Verilog?
2. Почему запись результата в регистровый файл (`we_rf = 1`) активируется только на стадии `Execute`, а не `Decode`? Что произойдет, если поднять флаг записи раньше времени?
3. Что такое OpCode (Код операции)? Какая часть процессора отвечает за его расшифровку?
4. Как избежать возникновения непреднамеренных Latch (защелок) при описании комбинаторной части конечного автомата?
5. На данный момент мы подаем `opcode` вручную из тестбенча. Откуда в реальном процессоре управляющий автомат берет эти данные во время фазы `Fetch`?