# miem-c-to-pseudocode-prompt
1. Открываем @chatsgpts_bot, @neyroseti_Gptbot, gemini.google.com или любой другой гпт
2. Пишем боту:
   ```
   Запомни этот код:
   Код на си
   ```
   ```
   Преобразуй код, который ты запомнил, написанный на языке C в псевдокод со следующим синтаксисом:
   Инициализация переменных, массивов, матриц должна отсутствовать. Присваение им изначальных значений так же не требуется, если это не прописано в отдельной строке.
   Обращение к элементу массива записывается так же, как и в C, с помощью квадратных скобок([]).
   Указатели (& и * перед переменной) игнорируются.
   Точка с запятой в конце операций не используется.
   Вложенность логических элементов соблюдается посредством табуляции, как в Python.
   Комментарии игнорируются.
   Импорт модулей не записывается. Объявление переменных с помощью "#define" не записывается, однако они считаются объявленными ранее и могут использоваться в коде.
   Все функции кроме main объявляются такой структурой:
   
   Алг «Функция x»
   Ввод: y
   Вывод: z
   Нач
   
   Кон
   
   Где x - название функции в фиурных кавычках («»), y - перечисленные через запятую ожидаемые названия параметров, z - название возвращаемой переменной. Между "Нач" и "Кон" должно быть тело функции.
   
   Функция main объявляется аналогично другим, но без строк "Ввод" и "Вывод", а также вместо "Алг «Функция x»" пишется "Алг «x»"
   
   Операция присвоения значения переменной записывается как ":=".
   Во всех логических выражениях знак ">=" заменяется на "≥", "<=" на "≤", "&&" на "и", "||" на "или", "!" на "не", "==" на "=".
   Все сокращенные записи присваения (+=, -=, *=, %=, /=, ++, --) расписываются полностью (с учетом знака присваения :=). В случае с присваением вида x++, x--, ++x, --x, где x - переменная, использованным внутри других выражений, оно выносится в раскрытом виде за пределы выражения, где оно использовано, в случае ++x или --x до этого выражения, а в случае x++ или x-- сразу после этого выражения.
   Во всех строках двойные кавычки ("") заменяются на фигурные кавычки («»)
   Во всех строках сочетание "\n" не записывается.
   Условная конструкция if (без else) заменяется следующей:
   
   если x то
   
   всё
   
   Где x - условие, а перед "всё" записываются действия, если условие истино.
   
   Условная конструкция if-else заменяется следующей:
   
   если x то
   
   иначе
   
   всё
   
   Где x - условие, перед "иначе" записываются действия, если условие истино, а перед "всё" записываются действия, если условие ложно.
   
   Важно: в двух конструкциях выше после x должно быть именно слово "то", а "всё" должно обязательно присутствовать.
   Использование тернарного оператора "? :" заменяется конструкцией, эквивалентной условной if-else, приведенной выше.
   
   Цикл "for" заменяется следующей конструкцией:
   
   цикл от i:=x до y шаг z
   
   кц
   
   Где i - название итератора, x - начальное значение итератора, y - значение, которое включительно может достигать итератор, z - значение, на которое увеличивается итератор после каждой итерации. Перед "кц" должно быть тело цикла. Если z равен 1, то " шаг z" в этой конструкции можно не писать.
   Если в круглых скобках цикла for помимо итератора объявляются другие переменные, то их объявление должно быть в отдельных строках сразу перед этим циклом.
   
   Циклы следующего вида:
   
   do {
   x
   } while (y)
   
   где x - действия из тела цикла, а y - условие цикла, должны заменяться следующей конструкцией:
   
   цикл
   x
   до y
   кц
   
   где x - логическое выражение из условия цикла. В данном случае между словами "цикл" и "до" должно быть тело цикла.
   
   Циклы следующего вида:
   
   while (y) {
   x
   }
   
   где x - действия из тела цикла, а y - условие цикла, должны заменяться следующей конструкцией:
   
   
   цикл-пока x
   
   кц
   
   где x - логическое выражение из условия цикла. Перед "кц" должно быть тело цикла.
   
   Важно учитывать типы циклов while в исходном коде и верно их заменять.
   
   Оператор "break" заменяется на "выход".
   
   Оператор "return" заменяется на "вернуть" во всех функциях кроме main. Внутри функции main в псевдокоде оператор "return" заменяется на "выход".
   
   Использование функций "abs(x)" и "fabs(x)", где x - аргумент, заменятся на "|x|".
   
   Функция "scanf()" заменяется во всех местах на "ввод()" с сохранением всех аргументов, кроме первого, но без символов указателей (& и *).
   Функция "printf()" заменяется во всех местах на "вывод()" с сохранением всех аргументов, но без символов указателей (& и *).
   ```
   ```
   В полученном коде удали все строки, содержащие буквально только "вывод(«»)" или "вывод(« »)" или "вывод()". Также удали из всех аргументов функций "вывод()" пустые строки "« »". Перед "Кон" убери слово "выход".
   ```
3. Полученный кодд требует ревью, в т.ч удаления остатков инициализации переменных
4. **Бонус:** VBA макрос для подчеркивания всех нужных слов в ворде. Разработчик -> Макросы -> + и вставляем:
   ```
   Sub UnderlinePseudocode()
   Dim wordsToUnderline() As String
   Dim word As Variant
   wordsToUnderline = Split("Функция,Алг,Вход,Выход,Нач,цикл,цикл-пока,пока,от,до,шаг,если,не,и,или,то,иначе,всё,кц,Кон", ",")
   For Each word In wordsToUnderline
       With Selection.Range.Find
       .MatchWholeWord = True
    With .Replacement
    .ClearFormatting
    .Font.underline = True
    End With
    .Execute FindText:=word, ReplaceWith:=word, _
    Format:=True, Replace:=wdReplaceAll
   End With
   Next word
   End Sub
   ```
   Выделяем весь псевдокод и выполняем макрос
