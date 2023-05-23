# Регулярные выражения

## Краткое описание
Регулярные выражения представляют эффективный и гибкий метод по обработке больших текстов, позволяя в то же время существенно уменьшить объемы кода по сравнению с использованием стандартных операций со строками.       
Основная функциональность регулярных выражений в .NET сосредоточена в пространстве имен System.Text.RegularExpressions. А центральным классом при работе с регулярными выражениями является класс Regex. Например, у нас есть некоторый текст и нам надо найти в нем все словоформы какого-нибудь слова. С классом Regex это сделать очень просто:
    
    using System.Text.RegularExpressions;

    string s = "Бык тупогуб, тупогубенький бычок, у быка губа бела была тупа";
    Regex regex = new Regex(@"туп(\w*)");
    MatchCollection matches = regex.Matches(s);
    if (matches.Count > 0)
    {
        foreach (Match match in matches)
            Console.WriteLine(match.Value);
    }
    else
    {
        Console.WriteLine("Совпадений не найдено");
    }

## Параметры конструкторов RegexOptions
Класс Regex имеет ряд конструкторов, позволяющих выполнить начальную инициализацию объекта. Две версии конструкторов в качестве одного из параметров принимают перечисление RegexOptions. Некоторые из значений, принимаемых данным перечислением:
1. Compiled: при установке этого значения регулярное выражение компилируется в сборку, что обеспечивает более быстрое выполнение
2. CultureInvariant: при установке этого значения будут игнорироваться региональные различия
3. IgnoreCase: при установке этого значения будет игнорироваться регистр
4. IgnorePatternWhitespace: удаляет из строки пробелы и разрешает комментарии, начинающиеся со знака #
5. Multiline: указывает, что текст надо рассматривать в многострочном режиме. При таком режиме символы "^" и "$" совпадают, соответственно, с началом и концом любой строки, а не с началом и концом всего текста
6. RightToLeft: приписывает читать строку справа налево
7. Singleline: при данном режиме символ "." соответствует любому символу, в том числе последовательности "\n", которая осуществляет переход на следующую строку

Несколько параметров можно установить с помощью символа "|"

    Regex regex = new Regex(@"туп(\w*)", RegexOptions.Compiled | RegexOptions.IgnoreCase);

## Синтаксис регулярных выражений
- ^: соответствие должно начинаться в начале строки (например, выражение @"^пр\w*" соответствует слову "привет" в строке "привет мир")
- $: конец строки (например, выражение @"\w*ир$" соответствует слову "мир" в строке "привет мир", так как часть "ир" находится в самом конце)
- .: знак точки определяет любой одиночный символ (например, выражение "м.р" соответствует слову "мир" или "мор")
- *: предыдущий символ повторяется 0 и более раз
- +: предыдущий символ повторяется 1 и более раз
- ?: предыдущий символ повторяется 0 или 1 раз
- \s: соответствует любому пробельному символу
- \S: соответствует любому символу, не являющемуся пробелом
- \w: соответствует любому алфавитно-цифровому символу
- \W: соответствует любому не алфавитно-цифровому символу
- \d: соответствует любой десятичной цифре
- \D : соответствует любому символу, не являющемуся десятичной цифрой

## Пример использования Regex
### Проверка на соответствие строки формату

    using System.Text.RegularExpressions;

    string pattern = @"^(?("")(""[^""]+?""@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))" +
                    @"(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-\w]*[0-9a-z]*\.)+[a-z0-9]{2,17}))$";
    var data = new string[]
    {
        "tom@gmail.com",
        "+12345678999",
        "bob@yahoo.com",
        "+13435465566",
        "sam@yandex.ru",
        "+43743989393"
    };

    Console.WriteLine("Email List");
    for(int i = 0; i < data.Length; i++)
    {
        if (Regex.IsMatch(data[i], pattern, RegexOptions.IgnoreCase))
        {
            Console.WriteLine(data[i]);
        }
    }

### Метод Replace
Класс Regex имеет метод Replace, который позволяет заменить строку, соответствующую регулярному выражению, другой строкой:

    string text = "Мама  мыла  раму. ";
    string pattern = @"\s+";
    string target = " ";
    Regex regex = new Regex(pattern);
    string result = regex.Replace(text, target);
    Console.WriteLine(result);

# Ссылки на источники
[Регулярные выражения](https://metanit.com/sharp/tutorial/7.4.php)