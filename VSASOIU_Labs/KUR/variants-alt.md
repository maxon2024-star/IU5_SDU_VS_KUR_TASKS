Ниже представлен список вариантов для курсовой работы. Каждый вариант содержит вычислительную задачу, рекомендации по ISA, предложение для кастомной инструкции и формат входных/выходных данных.

---

### Математические вычисления (1–20)
1. Сумма арифметической прогрессии | Алгоритм: Цикл сложения с шагом | ISA: 16-bit, ADD, JUMP | Custom: MAC | Input: N, Start, Step | Output: Sum
2. Вычисление факториала N | Алгоритм: Последовательное умножение | ISA: 32-bit, MUL, SUB | Custom: FAST_MUL | Input: N | Output: N!
3. Числа Фибоначчи до N-го элемента | Алгоритм: Рекуррентное сложение в массив | ISA: 16-bit, ADD, STORE | Custom: SWAP_REG | Input: N | Output: Array
4. НОД двух чисел (Евклид) | Алгоритм: Вычитание до равенства | ISA: 16-bit, SUB, CMP | Custom: MOD_FAST | Input: A, B | Output: GCD
5. Бинарное возведение в степень | Алгоритм: Сдвиги и умножения | ISA: 32-bit, MUL, AND | Custom: SQ_ACC | Input: Base, Exp | Output: Res
6. Полином методом Горнера | Алгоритм: Последовательное умножение+сложение | ISA: 16-bit, MUL, ADD | Custom: MAC | Input: Coeffs, X | Output: P(X)
7. Поиск максимума в массиве | Алгоритм: Линейный проход с сравнением | ISA: 16-bit, LOAD, CMP | Custom: MAX_ACC | Input: Array, Len | Output: Max
8. Сортировка пузырьком | Алгоритм: Вложенные циклы с обменом | ISA: 16-bit, SWAP, JUMP | Custom: CMP_SWAP | Input: Array | Output: Sorted Array
9. Среднее арифметическое массива | Алгоритм: Суммирование и деление | ISA: 16-bit, ADD, DIV | Custom: DIV_SHIFT | Input: Array, Len | Output: Mean
10. Подсчет четных/нечетных | Алгоритм: Проверка младшего бита | ISA: 16-bit, AND, BRANCH | Custom: COUNT_BITS | Input: Array | Output: Counts
11. Квадратный корень (Ньютон) | Алгоритм: Итерационное уточнение | ISA: 32-bit, MUL, SUB | Custom: SQRT_ITER | Input: Val | Output: Sqrt
12. Транспонирование матрицы NxN | Алгоритм: Перестановка индексов | ISA: 16-bit, LOAD, STORE | Custom: BLOCK_XFER | Input: Matrix | Output: Transposed
13. Умножение матриц 4x4 | Алгоритм: Тройной цикл с накоплением | ISA: 16-bit, MAC, LOOP | Custom: DOT_PROD | Input: MatA, MatB | Output: MatC
14. СЛАУ методом Гаусса (3x3) | Алгоритм: Прямой ход и обратная подстановка | ISA: 32-bit, DIV, SUB | Custom: PIVOT_SWAP | Input: Matrix, Vector | Output: Solution
15. Определитель 3x3 | Алгоритм: Правило Саррюса | ISA: 32-bit, MUL, ADD | Custom: DET_3X3 | Input: Matrix | Output: Det
16. Поиск подстроки (наивный) | Алгоритм: Сдвиг и посимвольное сравнение | ISA: 8-bit, LOAD, CMP | Custom: STR_CMP | Input: Str, Pat | Output: Index
17. Перевод между системами счисления | Алгоритм: Деление с остатком | ISA: 16-bit, DIV, MOD | Custom: BASE_CONV | Input: Num, BaseIn, BaseOut | Output: String
18. Биномиальный коэффициент C(n,k) | Алгоритм: Формула через факториалы | ISA: 16-bit, MUL, DIV | Custom: COMB_FAST | Input: n, k | Output: C
19. Сумма главной диагонали | Алгоритм: Инкремент по двум индексам | ISA: 16-bit, ADD, INDEX | Custom: DIAG_SUM | Input: Matrix | Output: Sum
20. Проверка числа на простоту | Алгоритм: Деление до √N | ISA: 16-bit, DIV, CMP | Custom: PRIM_TEST | Input: N | Output: Boolean

### Цифровая обработка сигналов (21–40)
21. Скользящее среднее (окно 8) | Алгоритм: Сумма буфера и сдвиг | ISA: 16-bit, ADD, SHIFT | Custom: MOV_AVG | Input: Signal | Output: Filtered
22. FIR-фильтр НЧ (4 тапа) | Алгоритм: Свёртка с коэффициентами | ISA: 16-bit, MAC, LOAD | Custom: MAC_ACC | Input: Coeffs, Signal | Output: Filtered
23. Энергия сигнала | Алгоритм: Сумма квадратов отсчётов | ISA: 32-bit, MUL, ADD | Custom: SQ_ACC | Input: Samples | Output: Energy
24. Детектор нуля | Алгоритм: Сравнение знака соседних отсчётов | ISA: 16-bit, CMP, XOR | Custom: ZERO_CROSS | Input: Signal | Output: Count
25. Амплитудная модуляция (AM) | Алгоритм: Перемножение несущей и огибающей | ISA: 16-bit, MUL, ADD | Custom: AM_MIX | Input: Carrier, Mod | Output: AM_Signal
26. DFT 8-point (упрощ.) | Алгоритм: Матричное умножение на экспоненты | ISA: 32-bit, MAC, TRIG | Custom: DFT_BUTTER | Input: Real/Imag | Output: Spectrum
27. Автокорреляция | Алгоритм: Сдвиг и скалярное произведение | ISA: 32-bit, MUL, ADD | Custom: AUTO_CORR | Input: Signal, Lag | Output: Corr
28. Экспоненциальный фильтр (IIR) | Алгоритм: Рекуррентное сглаживание | ISA: 16-bit, MAC, SHIFT | Custom: IIR_STEP | Input: Alpha, Signal | Output: Filtered
29. Отношение сигнал/шум (SNR) | Алгоритм: Логарифмирование отношения мощностей | ISA: 32-bit, DIV, LOG2 | Custom: LOG2_FAST | Input: Signal, Noise | Output: SNR_dB
30. Пиковый детектор | Алгоритм: Сравнение с окном и запоминание | ISA: 16-bit, CMP, STORE | Custom: PEAK_DET | Input: Signal | Output: Peak_Array
31. Компенсация DC-смещения | Алгоритм: Вычитание среднего значения | ISA: 16-bit, SUB, AVG | Custom: SUB_DC | Input: Signal | Output: AC_Signal
32. RMS значение | Алгоритм: Среднеквадратичное вычисление | ISA: 32-bit, MUL, ADD, SQRT | Custom: RMS_ACC | Input: Samples | Output: RMS
33. Синтез синусоиды (табличный) | Алгоритм: Фазовый накопитель и выборка | ISA: 16-bit, ADD, LOAD | Custom: LFO_PHASE | Input: Freq, Phase | Output: Wave
34. Дифференциал сигнала | Алгоритм: Разность соседних отсчётов | ISA: 16-bit, SUB, STORE | Custom: DIFF_CALC | Input: Signal | Output: Derivative
35. Линейная интерполяция (2x) | Алгоритм: Вставка среднего значения | ISA: 16-bit, ADD, SHIFT | Custom: LIN_INTERP | Input: Signal | Output: Upsampled
36. Децимация (2x) | Алгоритм: Прореживание с антиалиасингом | ISA: 16-bit, LOAD, STORE | Custom: DECIM_FILTER | Input: Signal | Output: Downsampled
37. Кросс-корреляция | Алгоритм: Сдвиг двух сигналов и умножение | ISA: 32-bit, MAC, CMP | Custom: CROSS_CORR | Input: SigA, SigB | Output: Corr
38. Компрессор динамического диапазона | Алгоритм: Нелинейное преобразование амплитуды | ISA: 16-bit, CMP, MUL | Custom: DYN_COMP | Input: Audio | Output: Compressed
39. Спектр через алгоритм Гёрцеля | Алгоритм: Рекуррентный фильтр для одной частоты | ISA: 32-bit, MAC, TRIG | Custom: GOERTZEL | Input: Signal, Freq | Output: Magnitude
40. Выравнивание гистограммы (1D) | Алгоритм: Накопление и масштабирование | ISA: 16-bit, LOAD, STORE, ADD | Custom: HIST_EQ | Input: Data | Output: Equalized

### Обработка изображений и графики (41–60)
41. Инверсия цвета (grayscale) | Алгоритм: Вычитание из максимума | ISA: 8-bit, XOR, STORE | Custom: NOT_ACC | Input: Image | Output: Inverted
42. Бинаризация по порогу | Алгоритм: Сравнение с константой | ISA: 8-bit, CMP, STORE | Custom: THRESH_FAST | Input: Image, Thresh | Output: Binary
43. Увеличение яркости с насыщением | Алгоритм: Сложение с clamp | ISA: 8-bit, ADD, SAT | Custom: ADD_SAT | Input: Image, Offset | Output: Bright
44. Гистограмма изображения | Алгоритм: Подсчёт частот яркостей | ISA: 8-bit, LOAD, ADD | Custom: BIN_COUNT | Input: Image | Output: Hist[256]
45. Размытие 3x3 | Алгоритм: Сумма соседей и деление | ISA: 16-bit, ADD, SHIFT | Custom: BLUR_3X3 | Input: Image | Output: Blurred
46. Границы (Собель 3x3) | Алгоритм: Свёртка с ядрами Gx, Gy | ISA: 16-bit, MUL, ADD | Custom: SOBEL_3X3 | Input: Image | Output: Edges
47. Поворот на 90° | Алгоритм: Транспонирование + реверс строк | ISA: 8-bit, LOAD, STORE | Custom: ROT90_FAST | Input: Image | Output: Rotated
48. Масштабирование 2x (nearest) | Алгоритм: Дублирование пикселей | ISA: 8-bit, LOAD, STORE | Custom: DUP_2X | Input: Image | Output: Scaled
49. Альфа-блендинг | Алгоритм: Взвешенная сумма двух кадров | ISA: 16-bit, MUL, ADD | Custom: ALPHA_BLEND | Input: ImgA, ImgB, Alpha | Output: Blended
50. Средний цвет ROI | Алгоритм: Сумма и деление по области | ISA: 8-bit, ADD, DIV | Custom: AVG_COLOR | Input: ROI | Output: AvgRGB
51. Замена цвета по маске | Алгоритм: Условная запись | ISA: 8-bit, CMP, STORE | Custom: COLOR_MASK | Input: Image, Mask, NewColor | Output: Modified
52. Даунсемплинг 2x (среднее 2x2) | Алгоритм: Блочное усреднение | ISA: 16-bit, ADD, SHIFT | Custom: AVG_2X2 | Input: Image | Output: Downscaled
53. Контраст изображения | Алгоритм: Разность max и min | ISA: 8-bit, CMP, STORE | Custom: RANGE_CALC | Input: Image | Output: Contrast
54. Шахматный паттерн | Алгоритм: Проверка чётности координат | ISA: 8-bit, XOR, STORE | Custom: CHECKER_GEN | Input: Size | Output: Pattern
55. Сжатие RLE | Алгоритм: Группировка одинаковых байтов | ISA: 16-bit, CMP, STORE | Custom: RLE_PACK | Input: Image | Output: RLE_Data
56. Декодирование RLE | Алгоритм: Распаковка счётчиков | ISA: 16-bit, LOAD, STORE | Custom: RLE_UNPACK | Input: RLE_Data | Output: Image
57. Градиент направления | Алгоритм: Вычисление угла по Dx, Dy | ISA: 16-bit, MUL, ATAN2 | Custom: GRAD_ANGLE | Input: Dx, Dy | Output: Angle
58. Пороговая сегментация по цвету | Алгоритм: Фильтрация по диапазону RGB | ISA: 16-bit, CMP, MASK | Custom: COLOR_THRESH | Input: RGB, Range | Output: Mask
59. Инверсия битов пикселя | Алгоритм: Побитовый реверс | ISA: 8-bit, REV, STORE | Custom: BIT_REV8 | Input: Image | Output: BitRev
60. RGB -> Grayscale | Алгоритм: Взвешенная сумма каналов | ISA: 16-bit, MAC, SHIFT | Custom: RGB2GRAY | Input: RGB_Image | Output: Gray

### Криптография и защита данных (61–80)
61. CRC-8 для блока | Алгоритм: Полиномиальное деление XOR | ISA: 8-bit, XOR, SHIFT | Custom: CRC8_STEP | Input: Data, Len | Output: CRC
62. XOR-шифр с ключом | Алгоритм: Побитовое сложение по модулю 2 | ISA: 8-bit, XOR, LOAD | Custom: XOR_KEY | Input: Data, Key | Output: Cipher
63. Контрольная сумма (Checksum) | Алгоритм: Накопление суммы байтов | ISA: 16-bit, ADD, STORE | Custom: CHKSUM_ACC | Input: Data | Output: Sum
64. Генератор PRNG (LCG) | Алгоритм: Линейный конгруэнтный метод | ISA: 32-bit, MUL, ADD | Custom: LCG_STEP | Input: Seed | Output: Stream
65. S-Box подстановка | Алгоритм: Табличная замена байта | ISA: 8-bit, LOAD, STORE | Custom: SBOX_LKUP | Input: Byte | Output: SubByte
66. Простой хеш (добавление+сдвиг) | Алгоритм: Rolling hash | ISA: 32-bit, ADD, SHIFT | Custom: ROL_HASH | Input: String | Output: Hash
67. Реверс битов в байте | Алгоритм: Зеркальное отражение | ISA: 8-bit, REV, STORE | Custom: BIT_REV | Input: Data | Output: RevData
68. Проверка чётности (Parity) | Алгоритм: XOR всех битов | ISA: 8-bit, XOR, COUNT | Custom: PARITY_FAST | Input: Data | Output: Parity
69. Стеганография LSB | Алгоритм: Замена младших битов | ISA: 8-bit, AND, OR | Custom: LSB_HIDE | Input: Msg, Cover | Output: Stego
70. Извлечение LSB | Алгоритм: Маскирование и сборка | ISA: 8-bit, AND, STORE | Custom: LSB_EXTRACT | Input: Stego | Output: Msg
71. Adler-32 (упрощ.) | Алгоритм: Два аккумулятора и модуль | ISA: 32-bit, ADD, MOD | Custom: ADLER_STEP | Input: Data | Output: Checksum
72. Шифр Цезаря | Алгоритм: Сдвиг с зацикливанием алфавита | ISA: 8-bit, ADD, CMP | Custom: CAESAR_SHIFT | Input: Text, Shift | Output: Cipher
73. Таблица CRC16 | Алгоритм: Предвычисление остатков | ISA: 16-bit, XOR, SHIFT | Custom: CRC16_TAB | Input: Poly | Output: Table
74. Проверка Luhn | Алгоритм: Удвоение чётных цифр и сумма | ISA: 16-bit, MUL, ADD | Custom: LUHN_CHECK | Input: Number | Output: Valid
75. Простой MAC | Алгоритм: XOR с ключом и накопление | ISA: 32-bit, XOR, MAC | Custom: HMAC_STEP | Input: Msg, Key | Output: MAC
76. Моноалфавитный шифр | Алгоритм: Подстановка по ключевой карте | ISA: 8-bit, LKUP, STORE | Custom: SUB_CIPHER | Input: Text, KeyMap | Output: Cipher
77. Хеш FNV-1a | Алгоритм: XOR + умножение на константу | ISA: 32-bit, XOR, MUL | Custom: FNV_STEP | Input: Data | Output: Hash
78. Обфускация (XOR+Rotate) | Алгоритм: Побитовые операции с ключом | ISA: 16-bit, XOR, ROR | Custom: OBFUSCATE | Input: Data, Key | Output: Obfuscated
79. Fletcher-16 | Алгоритм: Двойная сумма с модулем | ISA: 16-bit, ADD, MOD | Custom: FLETCHER | Input: Data | Output: Check
80. Простой KDF | Алгоритм: Хеширование пароля с солью | ISA: 32-bit, ADD, XOR | Custom: KDF_SIMPLE | Input: Password | Output: Key

### Управление и робототехника (81–100)
81. ПИД-регулятор | Алгоритм: Пропорциональная+интегральная+дифференциальная составляющая | ISA: 32-bit, MUL, ADD | Custom: PID_STEP | Input: Err, Kp, Ki, Kd | Output: Ctrl
82. ШИМ генератор | Алгоритм: Сравнение счётчика с duty | ISA: 16-bit, CMP, TOGGLE | Custom: PWM_GEN | Input: Duty, Period | Output: PWM_State
83. Детектор фронта | Алгоритм: Задержка и XOR | ISA: 8-bit, XOR, DELAY | Custom: EDGE_DET | Input: Signal | Output: Edges
84. Дебаунсер кнопки | Алгоритм: Подсчёт стабильных тактов | ISA: 8-bit, CMP, COUNT | Custom: DEBOUNCE | Input: Raw_Btn | Output: Stable_Btn
85. Шаговый двигатель | Алгоритм: Циклическая смена фаз | ISA: 16-bit, STORE, JUMP | Custom: STEP_SEQ | Input: Dir, Steps | Output: Coil_State
86. Термостат с гистерезисом | Алгоритм: Сравнение с верхним/нижним порогом | ISA: 16-bit, CMP, STORE | Custom: HYST_CTRL | Input: Temp, Set, Hyst | Output: Heater
87. Трекинг энкодера | Алгоритм: Учёт направления и импульсов | ISA: 32-bit, ADD, CMP | Custom: ENC_TRACK | Input: A, B, Dir | Output: Pos
88. Маппинг ШИМ -> угол | Алгоритм: Линейное преобразование диапазона | ISA: 16-bit, MUL, SHIFT | Custom: SERVO_MAP | Input: Angle | Output: PulseWidth
89. Детектор превышения с задержкой | Алгоритм: Таймер срабатывания | ISA: 16-bit, CMP, TIMER | Custom: THR_DELAY | Input: Val, Thresh | Output: Alert
90. Автопилот по компасу | Алгоритм: Вычисление ошибки курса | ISA: 16-bit, SUB, CMP | Custom: HDG_ERR | Input: Target, Current | Output: Turn
91. Таймерное реле | Алгоритм: Счётчики включения/выключения | ISA: 16-bit, ADD, CMP | Custom: RELAY_TMR | Input: OnTime, OffTime | Output: Relay
92. Скорость по датчику | Алгоритм: Деление пути на время | ISA: 32-bit, DIV, STORE | Custom: SPEED_CALC | Input: Dist, Time | Output: Vel
93. Фильтр Калмана (1D) | Алгоритм: Предсказание и коррекция | ISA: 32-bit, MAC, ADD | Custom: KALMAN_1D | Input: Meas, Cov | Output: Est
94. Управление светом по Lux | Алгоритм: Маппинг освещённости в яркость | ISA: 16-bit, CMP, MUL | Custom: LUX_DIM | Input: Sensor, Target | Output: Brightness
95. Детектор движения (2 датчика) | Алгоритм: Логическое И/ИЛИ состояний | ISA: 8-bit, XOR, AND | Custom: MOT_DET | Input: PIR1, PIR2 | Output: Motion
96. Time-to-Impact | Алгоритм: Отношение расстояния к скорости | ISA: 32-bit, DIV, SUB | Custom: TTI_CALC | Input: Dist, Vel | Output: Time
97. Вентилятор по температуре | Алгоритм: ПИД или табличный маппинг | ISA: 16-bit, CMP, MAP | Custom: TEMP_FAN | Input: Temp | Output: FanDuty
98. Контроллер уровня жидкости | Алгоритм: Управление насосом по датчикам | ISA: 16-bit, CMP, STORE | Custom: LVL_CTRL | Input: Sensor, Min, Max | Output: Pump
99. Курс по GPS (упрощ.) | Алгоритм: Вычисление азимута | ISA: 32-bit, ATAN2, DIV | Custom: GPS_BRNG | Input: Lat1, Lon1, Lat2, Lon2 | Output: Bearing
100. Клапан по давлению | Алгоритм: Пропорциональное управление | ISA: 16-bit, CMP, PWM | Custom: PRESS_VALVE | Input: Pressure, Set | Output: ValvePos

### Сжатие и кодирование данных (101–120)
101. Хаффман (4 символа) | Алгоритм: Табличная упаковка | ISA: 8-bit, CMP, STORE | Custom: HUFF_PACK | Input: Data | Output: Bitstream
102. Декодирование Хаффмана | Алгоритм: Обход дерева по битам | ISA: 8-bit, LKUP, LOAD | Custom: HUFF_UNPACK | Input: Bitstream | Output: Data
103. Дельта-кодирование | Алгоритм: Вычисление разности | ISA: 16-bit, SUB, STORE | Custom: DELTA_ENC | Input: Array | Output: Deltas
104. Восстановление дельты | Алгоритм: Накопительное сложение | ISA: 16-bit, ADD, STORE | Custom: DELTA_DEC | Input: Deltas | Output: Array
105. Код Gray (Bin->Gray) | Алгоритм: Сдвиг и XOR | ISA: 8-bit, XOR, SHIFT | Custom: BIN2GRAY | Input: Bin | Output: Gray
106. Код Gray (Gray->Bin) | Алгоритм: Обратное преобразование | ISA: 8-bit, XOR, STORE | Custom: GRAY2BIN | Input: Gray | Output: Bin
107. RLE строк | Алгоритм: Сжатие последовательностей | ISA: 8-bit, CMP, STORE | Custom: RLE_STR | Input: String | Output: RLE
108. Манчестерское кодирование | Алгоритм: Преобразование битов в переходы | ISA: 8-bit, XOR, STORE | Custom: MANCH_ENC | Input: Bitstream | Output: Manchester
109. Декодирование Манчестера | Алгоритм: Восстановление битов по переходам | ISA: 8-bit, XOR, CMP | Custom: MANCH_DEC | Input: Manchester | Output: Bitstream
110. Base64 (3->4) | Алгоритм: Сдвиги и маскирование | ISA: 8-bit, SHIFT, OR | Custom: B64_ENC | Input: 3Bytes | Output: 4Chars
111. Base64 декодирование | Алгоритм: Обратная сборка байтов | ISA: 8-bit, SHIFT, AND | Custom: B64_DEC | Input: 4Chars | Output: 3Bytes
112. Fletcher-16 | Алгоритм: Двойный аккумулятор | ISA: 16-bit, ADD, MOD | Custom: FLETCHER16 | Input: Data | Output: Check
113. XOR-сжатие | Алгоритм: Удаление повторяющихся блоков | ISA: 8-bit, XOR, STORE | Custom: XOR_COMP | Input: Data, Key | Output: Compressed
114. LZ77 упрощ. | Алгоритм: Поиск совпадений в окне | ISA: 16-bit, CMP, STORE | Custom: LZ_MATCH | Input: Data, Dict | Output: Offset, Len
115. RLE с флагом | Алгоритм: Компрессия с маркером повтора | ISA: 8-bit, CMP, STORE | Custom: RLE_FLAG | Input: Data | Output: RLE_Data
116. Декодирование RLE с флагом | Алгоритм: Распаковка по маркерам | ISA: 8-bit, LOAD, STORE | Custom: RLE_UNFLAG | Input: RLE_Data | Output: Data
117. Удаление нулей | Алгоритм: Пропуск нулевых байтов | ISA: 8-bit, CMP, STORE | Custom: ZERO_SKIP | Input: Data | Output: Sparse
118. Восстановление нулей | Алгоритм: Заполнение по карте позиций | ISA: 8-bit, LOAD, STORE | Custom: ZERO_FILL | Input: Sparse | Output: Data
119. Кодирование 4B5B | Алгоритм: Табличная замена 4->5 бит | ISA: 8-bit, LKUP, STORE | Custom: 4B5B_ENC | Input: 4Bits | Output: 5Bits
120. Декодирование 4B5B | Алгоритм: Обратная таблица | ISA: 8-bit, LKUP, STORE | Custom: 4B5B_DEC | Input: 5Bits | Output: 4Bits

### Графы и сетевые алгоритмы (121–140)
121. BFS в лабиринте | Алгоритм: Поиск в ширину по сетке | ISA: 16-bit, LOAD, QUEUE | Custom: BFS_STEP | Input: Grid | Output: Path
122. Связные компоненты (DFS) | Алгоритм: Обход в глубину | ISA: 16-bit, VISIT, STORE | Custom: DFS_COUNT | Input: AdjMat | Output: Count
123. Степень вершины | Алгоритм: Сумма строки матрицы смежности | ISA: 16-bit, ADD, LOAD | Custom: DEG_CALC | Input: AdjMat, V | Output: Degree
124. Минимальное остовное дерево (Kruskal) | Алгоритм: Сортировка рёбер и объединение | ISA: 16-bit, SORT, UNION | Custom: MST_EDGE | Input: Edges | Output: Tree
125. Кратчайший путь (Dijkstra) | Алгоритм: Жадный выбор минимума | ISA: 32-bit, ADD, MIN | Custom: DIJK_STEP | Input: Weights, Src | Output: Dist
126. Проверка на ацикличность | Алгоритм: Обнаружение обратных рёбер | ISA: 16-bit, DFS, BACK | Custom: CYC_DETECT | Input: AdjMat | Output: IsCyclic
127. Центральность вершины | Алгоритм: Сумма кратчайших путей | ISA: 32-bit, ADD, DIV | Custom: CENT_CALC | Input: Graph, V | Output: Central
128. Топологическая сортировка | Алгоритм: Подсчёт входных степеней | ISA: 16-bit, INDEG, STACK | Custom: TOPO_SORT | Input: DAG | Output: Order
129. Поиск мостов | Алгоритм: DFS с tin/low | ISA: 16-bit, DFS, LOW | Custom: BRIDGE_DET | Input: Graph | Output: Bridges
130. Плотность графа | Алгоритм: 2E/(V*(V-1)) | ISA: 32-bit, DIV, MUL | Custom: DENSITY | Input: E, V | Output: Density
131. Проверка двудольности | Алгоритм: Раскраска в 2 цвета | ISA: 16-bit, COLOR, BFS | Custom: BIPART_CHK | Input: Graph | Output: IsBipart
132. Число Эйлера | Алгоритм: V-E+F | ISA: 16-bit, ADD, SUB | Custom: EULER_NUM | Input: V, E, F | Output: Chi
133. Эйлеров путь | Алгоритм: Алгоритм Иерхольцера | ISA: 16-bit, DEG, STACK | Custom: EULER_PATH | Input: Graph | Output: Path
134. Радиус графа | Алгоритм: Минимум эксцентриситетов | ISA: 32-bit, MIN, MAX | Custom: GRAPH_RAD | Input: DistMat | Output: Radius
135. Максимальный поток (Ford-Fulkerson) | Алгоритм: Поиск увеличивающих путей | ISA: 32-bit, ADD, MIN | Custom: FLOW_STEP | Input: CapMat, S, T | Output: MaxFlow
136. Диаметр графа | Алгоритм: Максимум эксцентриситетов | ISA: 32-bit, MAX, BFS | Custom: GRAPH_DIAM | Input: DistMat | Output: Diameter
137. Изоморфизм малых графов | Алгоритм: Перебор перестановок | ISA: 16-bit, CMP, PERM | Custom: ISO_CHECK | Input: G1, G2 | Output: IsIso
138. Хроматическое число | Алгоритм: Жадная раскраска | ISA: 16-bit, COLOR, BACK | Custom: CHROM_NUM | Input: Graph | Output: Chi
139. Кликa размера K | Алгоритм: Бэктрекинг | ISA: 16-bit, CMP, BACK | Custom: CLIQUE_DET | Input: Graph, K | Output: Clique
140. Лапласиан графа | Алгоритм: D - A | ISA: 32-bit, SUB, STORE | Custom: LAPLACIAN | Input: AdjMat | Output: LapMat

### Моделирование и физика (141–160)
141. Свободное падение | Алгоритм: Интегрирование ускорения | ISA: 32-bit, MUL, ADD | Custom: GRAV_STEP | Input: T, G | Output: H, V
142. Теплопроводность 1D | Алгоритм: Разностная схема | ISA: 32-bit, ADD, MUL | Custom: HEAT_DIFF | Input: Temp, Alpha | Output: NewTemp
143. Маятник (Эйлер) | Алгоритм: Дифференциальное уравнение | ISA: 32-bit, SIN, MUL | Custom: PEND_STEP | Input: Theta, L | Output: NewTheta
144. Траектория снаряда | Алгоритм: Параметрические уравнения | ISA: 32-bit, MUL, ADD | Custom: PROJ_TRAJ | Input: V0, Angle | Output: X, Y
145. Логистическое уравнение | Алгоритм: Моделирование популяции | ISA: 32-bit, MUL, SUB | Custom: LOGIST_STEP | Input: P, K, R | Output: NewP
146. Сила трения | Алгоритм: F = μN | ISA: 32-bit, MUL, SIGN | Custom: FRIC_CALC | Input: Mass, Mu | Output: Fric
147. Упругое соударение | Алгоритм: Законы сохранения импульса/энергии | ISA: 32-bit, ADD, SUB | Custom: ELAST_COLL | Input: M1, V1, M2, V2 | Output: V1', V2'
148. Работа силы | Алгоритм: W = F·d | ISA: 32-bit, MUL, ADD | Custom: WORK_CALC | Input: F, Dx | Output: W
149. Радиоактивный распад | Алгоритм: N(t) = N0·e^(-λt) | ISA: 32-bit, DIV, MUL | Custom: DECAY_STEP | Input: N0, T, Half | Output: N
150. Идеальный газ | Алгоритм: PV = nRT | ISA: 32-bit, MUL, DIV | Custom: IDEAL_GAS | Input: N, T, V | Output: P
151. Маятник с затуханием | Алгоритм: Добавление члена скорости | ISA: 32-bit, MUL, SUB | Custom: DAMP_PEND | Input: Theta, B | Output: NewTheta
152. Кинетическая энергия | Алгоритм: E = mv²/2 | ISA: 32-bit, MUL, SHIFT | Custom: KE_CALC | Input: M, V | Output: KE
153. Гармонические колебания | Алгоритм: x(t) = A·sin(ωt) | ISA: 32-bit, MUL, SIN | Custom: HARM_OSC | Input: T, W | Output: X
154. Момент силы | Алгоритм: τ = r × F | ISA: 32-bit, MUL, CROSS | Custom: TORQUE_CALC | Input: R, F | Output: Tau
155. Диффузия 1D | Алгоритм: Уравнение Фика | ISA: 32-bit, ADD, SUB | Custom: DIFF_1D | Input: C, D | Output: NewC
156. Мощность цепи | Алгоритм: P = VI = I²R | ISA: 32-bit, MUL, DIV | Custom: POWER_CALC | Input: V, I, R | Output: P
157. RC-фильтр | Алгоритм: Дифференциальное уравнение | ISA: 32-bit, MUL, ADD | Custom: RC_STEP | Input: Vin, R, C | Output: Vout
158. Центр масс | Алгоритм: Σmi·xi / Σmi | ISA: 32-bit, MUL, ADD, DIV | Custom: COM_CALC | Input: M, X | Output: Xcom
159. Бросок мяча с отскоком | Алгоритм: Отскок с коэффициентом восстановления | ISA: 32-bit, MUL, CMP | Custom: BOUNCE_SIM | Input: H, V, E | Output: H_new
160. Индуктивность соленоида | Алгоритм: L = μ₀N²A/l | ISA: 32-bit, MUL, DIV | Custom: INDUCT_CALC | Input: N, A, L | Output: L

### Биоинформатика и строки (161–180)
161. Подсчёт нуклеотидов | Алгоритм: Скан строки ДНК | ISA: 8-bit, CMP, ADD | Custom: NT_COUNT | Input: DNA_Str | Output: A,C,G,T
162. Поиск мотива ДНК | Алгоритм: Сдвиг окна и сравнение | ISA: 8-bit, CMP, SHIFT | Custom: MOTIF_FIND | Input: DNA, Motif | Output: Index
163. Трансляция ДНК->AA | Алгоритм: Таблица кодонов | ISA: 8-bit, LKUP, STORE | Custom: DNA2AA | Input: Codon | Output: AA
164. GC-содержание | Алгоритм: Отношение G+C к длине | ISA: 8-bit, ADD, DIV | Custom: GC_CONTENT | Input: DNA | Output: Percent
165. Палиндром | Алгоритм: Сравнение с реверсом | ISA: 8-bit, CMP, STORE | Custom: PAL_CHK | Input: Str | Output: IsPal
166. Подсчёт слов | Алгоритм: Детекция пробелов | ISA: 8-bit, CMP, ADD | Custom: WORD_COUNT | Input: Text | Output: Count
167. Удаление дубликатов символов | Алгоритм: Множество встреченных | ISA: 8-bit, CMP, STORE | Custom: DEDUP_STR | Input: Str | Output: Unique
168. Расстояние Левенштейна | Алгоритм: Динамическое программирование | ISA: 16-bit, MIN, ADD | Custom: LEV_DIST | Input: Str1, Str2 | Output: Dist
169. Реверс строки | Алгоритм: Обмен с краёв к центру | ISA: 8-bit, SWAP, STORE | Custom: STR_REV | Input: Str | Output: RevStr
170. Подсчёт символа | Алгоритм: Линейный скан | ISA: 8-bit, CMP, ADD | Custom: CHAR_CNT | Input: Str, Ch | Output: Count
171. Смена регистра | Алгоритм: Битовая маска или таблица | ISA: 8-bit, CMP, XOR | Custom: CASE_CONV | Input: Text | Output: NewText
172. Анаграмма | Алгоритм: Сортировка и сравнение | ISA: 8-bit, SORT, CMP | Custom: ANA_CHK | Input: Str1, Str2 | Output: IsAna
173. Энтропия Шеннона | Алгоритм: -Σp·log2(p) | ISA: 32-bit, LOG, MUL | Custom: ENTROPY | Input: Freqs | Output: H
174. Самая длинная повторяющаяся подстрока | Алгоритм: Суффиксный перебор | ISA: 8-bit, CMP, STORE | Custom: LONG_REP | Input: Str | Output: Len
175. Base32 кодирование | Алгоритм: Группировка по 5 бит | ISA: 8-bit, SHIFT, OR | Custom: B32_ENC | Input: Data | Output: Base32
176. Base32 декодирование | Алгоритм: Обратная сборка | ISA: 8-bit, SHIFT, AND | Custom: B32_DEC | Input: Base32 | Output: Data
177. LCS (длина) | Алгоритм: DP таблица | ISA: 16-bit, MAX, CMP | Custom: LCS_LEN | Input: Str1, Str2 | Output: Len
178. Уникальные символы | Алгоритм: Битовая карта | ISA: 8-bit, SET, ADD | Custom: UNIQ_CNT | Input: Str | Output: Count
179. Сбалансированность скобок | Алгоритм: Счётчик открывающих/закрывающих | ISA: 8-bit, PUSH, POP | Custom: BAL_CHK | Input: Expr | Output: IsBal
180. ISBN-10 контрольная сумма | Алгоритм: Взвешенная сумма mod 11 | ISA: 16-bit, MUL, ADD, MOD | Custom: ISBN_CHK | Input: Digits | Output: Check

### Встроенные системы и протоколы (181–200)
181. UART приёмник (8N1) | Алгоритм: Стробирование битов по таймеру | ISA: 8-bit, SHIFT, COUNT | Custom: UART_RX | Input: BitStream | Output: Byte
182. UART передатчик | Алгоритм: Формирование старт/стоп битов | ISA: 8-bit, STORE, SHIFT | Custom: UART_TX | Input: Byte | Output: BitStream
183. I2C адрес (7-bit) | Алгоритм: Выделение адреса и RW-бита | ISA: 8-bit, SHIFT, STORE | Custom: I2C_ADDR | Input: Frame | Output: Addr, RW
184. CRC для CAN | Алгоритм: Полином 15 бит | ISA: 16-bit, XOR, SHIFT | Custom: CAN_CRC | Input: Data | Output: CRC
185. Парсинг JSON ключа | Алгоритм: Поиск строки до двоеточия | ISA: 8-bit, CMP, STORE | Custom: KEY_PARSE | Input: Str, Key | Output: Value
186. DTMF декодер | Алгоритм: Сопоставление пар частот | ISA: 16-bit, CMP, LKUP | Custom: DTMF_DEC | Input: FreqPair | Output: Digit
187. SPI Master (TX) | Алгоритм: Сдвиг MOSI по SCK | ISA: 8-bit, SHIFT, STORE | Custom: SPI_TX | Input: Byte | Output: MOSI
188. SPI Slave (RX) | Алгоритм: Сборка MISO в регистр | ISA: 8-bit, SHIFT, STORE | Custom: SPI_RX | Input: MISO | Output: Byte
189. Manchester II (IR) | Алгоритм: Анализ длительности импульса | ISA: 8-bit, CMP, STORE | Custom: IR_DEC | Input: PulseWidth | Output: Bit
190. Генерация пакета (Header+CRC) | Алгоритм: Сборка фрейма | ISA: 16-bit, STORE, XOR | Custom: PKT_GEN | Input: Payload | Output: Frame
191. Валидация пакета | Алгоритм: Проверка заголовка и CRC | ISA: 16-bit, CMP, XOR | Custom: PKT_VAL | Input: Frame | Output: Valid
192. PWM -> ADC | Алгоритм: Маппинг ширины в значение | ISA: 16-bit, MUL, DIV | Custom: PWM2ADC | Input: Duty, Period | Output: Value
193. Triangle Wave генератор | Алгоритм: Линейный счёт вверх/вниз | ISA: 16-bit, ADD, CMP | Custom: TRI_GEN | Input: Amp, Freq | Output: Wave
194. Таймер обратного отсчёта | Алгоритм: Декремент до нуля | ISA: 16-bit, SUB, CMP | Custom: TIMER_CNT | Input: Start | Output: Expire
195. BCD -> Binary | Алгоритм: Умножение десятков и сложение | ISA: 8-bit, MUL, ADD | Custom: BCD2BIN | Input: BCD | Output: Bin
196. Binary -> BCD | Алгоритм: Деление на 10 | ISA: 8-bit, DIV, STORE | Custom: BIN2BCD | Input: Bin | Output: BCD
197. Парсинг командной строки | Алгоритм: Разделение по пробелам | ISA: 8-bit, CMP, STORE | Custom: CMD_PARSE | Input: Str | Output: Cmd, Args
198. Генерация бита чётности UART | Алгоритм: XOR всех битов данных | ISA: 8-bit, XOR, STORE | Custom: PARITY_GEN | Input: Byte | Output: ParityBit
199. 7-сегментный декодер | Алгоритм: Таблица соответствия цифр | ISA: 8-bit, LKUP, STORE | Custom: 7SEG_ENC | Input: Digit | Output: Segments
200. State Machine протокола | Алгоритм: Переходы по событиям | ISA: 16-bit, JMP, STORE | Custom: PROTO_SM | Input: Event | Output: State, Action

---
