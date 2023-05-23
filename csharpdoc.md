# Стандарт документирования C#
## Основные правила документирования кода
1. Помните! Код чаще читается, чем пишется, поэтому не экономьте на понятности и чистоте кода ради скорости набора.
2. Не используйте малопонятные префиксы или суффиксы (например, венгерскую нотацию), современные языки и средства разработки позволяют контролировать типы данных на этапе разработки и сборки.
3. Не используйте подчеркивание для отделения слов внутри идентификаторов, это удлиняет идентификаторы и затрудняет чтение. Вместо этого используйте стиль именования Кемел или Паскаль.
4. Старайтесь не использовать сокращения лишний раз, помните о тех, кто читает код.
5. Старайтесь делать имена идентификаторов как можно короче (но не в ущерб читабельности). Помните, что современные языки позволяют формировать имя из пространств имен и типов. Главное, чтобы смысл идентификатора был понятен в используемом контексте. Например, количество элементов коллекции лучше назвать Count, а не CountOfElementsInMyCollection.
6. Когда придумываете название для нового, общедоступного (public) класса, пространства имен или интерфейса, старайтесь не использовать имена, потенциально или явно конфликтующие со стандартными идентификаторами.
7. Предпочтительно использовать имена, которые ясно и четко описывают предназначение и/или смысл сущности.
8. Старайтесь не использовать для разных сущностей имена, отличающиеся только регистром букв. Разрабатываемые вами компоненты могут быть использованы из языков, не различающих регистр, и некоторые методы (или даже весь компонент) окажутся недоступными.
9. Старайтесь использовать имена с простым написанием. Их легче читать и набирать. Избегайте (в разумных пределах) использования слов с двойными буквами, сложным чередованием согласных. Прежде, чем остановиться в выборе имени, убедитесь, что оно легко пишется и однозначно воспринимается на слух. Если оно с трудом читается, и вы ошибаетесь при его наборе, возможно, стоит выбрать другое.

### Стили использования регистра букв
- Паскаль – указание этого стиля оформления идентификатора обозначает, что первая буква заглавная и все последующие первые буквы слов тоже заглавные. Например, BackColor, LastModified, DateTime.
- Кэмел – указание этого стиля обозначает, что первая буква строчная, а остальные первые буквы слов заглавные. Например, borderColor, accessTime, templateName.

### Рекомендации по сокращениям
1. Не используйте аббревиатуры или неполные слова в идентификаторах, если только они не являются общепринятыми. Например, пишите GetWindow, а не GetWin.
2. Не используйте акронимы, если они не общеприняты в области информационных технологий.
3. Широко распространенные акронимы используйте для замены длинных фраз. Например, UI вместо User Interface или Olap вместо On-line Analytical Processing.
4. Если имеется идентификатор длиной менее трех букв, являющийся сокращением, то его записывают заглавными буквами, например System.IO, System.Web.UI. Имена длиннее двух букв записывайте в стиле Паскаль или Кэмел, например Guid, Xml, xmlDocument.

        using System.IO;
        using System.Web.UI;

        public class Math
        {
            public const PI = ...;
            public const E  = ...;
        }

### Рекомендации по выбору слов
Не рекомендуется использовать следующие слова в качестве именований идентификаторов:        

![name](https://github.com/Mikibirev/oop/assets/93863789/a49fe615-d220-473f-92a4-dd80118725b0)

### Рекомендации по именованию классов и структур
1. Используйте существительное (одно или несколько прилагательных и существительное) для имени класса.
2. Используйте стиль Паскаль для регистра букв.
3. Не используйте специальных префиксов, поясняющих, что это класс. Например, FileStream, а не CFileStream.
4. В подходящих случаях используйте составные слова для производных классов, где вторая часть слова поясняет базовый класс. К примеру, ApplicationException – вполне подходящее название для класса, унаследованного от Exception, поскольку ApplicationException является наследником класса Exception. Не стоит, однако злоупотреблять этим методом, пользуйтесь им разумно. К примеру, Button – вполне подходящее название для класса, производного от Control. Общее правило может быть, например, таким: «Если производный класс незначительно меняет свойства, поведение или внешний вид базового, используйте составные слова. Если класс значительно расширяет или меняет поведение базового, используйте новое существительное, отражающее суть производного класса». LinkLabel незначительно меняет внешний вид и поведение Label и, соответственно, использует составное имя.
5. Используйте составное имя, когда класс принадлежит некоторой специфичной категории, например FileStream, StringCollection, IntegrityException. Это относится к классам, которые являются потоками (Stream), коллекциями (Collection, Queue, Stack), ассоциативными контейнерами (Dictionary), исключениями (Exception).
6. Для классов-наследников, реализующих интерфейс IDictionary рекомендуется использовать тройное имя в виде <ТипКлюча>To<ТипЗначения>Dictionary. Вместо Dictionary можно использовать слово Map. Если это очевидно, можно опускать название значения. Примеры: StringToStringDictionary, StringToIntegerMap или KeywordMap. Переменным такого типа рекомендуется давать более конкретное семантическое название, например userToPasswordMap (user --> password), nameServiceDictionary (name --> service).
7. Для базового класса, предназначенного не для прямого использования, а для наследования, следует использовать суффикс Base. Например, CollectionBase. Такие классы также стоит делать абстрактными.

        public class FileStream {}
        public class Button {}
        public class String {}
        public class StringCollection {}

### Рекомендации по именованию полей класса
1. Непубличные поля (private, protected и protected internal) именуются в стиле Кэмел и начинаются с префикса _.
2. Публичные поля именуются в соответствии с правилами именования свойств.
3. Одна декларация должна содержать не более одного поля и должна располагаться на одной строке.

        class A
        {
            // Так нельзя:
            int _var1, _var2; 

            // Так тоже:
            int _var1, 
                _var2; 

            // Надо так:
            int _var1;
            int _var2;
            ...

4. Публичные поля должны в обязательном порядке документироваться XML-комментариями. Желательно снабжать XML-комментариями и непубличные поля.
5. Обращаясь к публичным полям старайтесь избегать их передачи по ссылке, т.к. велика вероятность того, что в следующих версиях приложения эти поля могут стать свойствами.

### Рекомендации по именованию методов
1. Используйте глаголы или комбинацию глагола и существительных и прилагательных для имен методов.
2. Используйте стиль Паскаль для регистра букв (вне зависимости от области видимости метода).

        private int RemoveAll() {}
        public void GetCharArray() {}
        internal static Invoke() {}

## Основы оформления документирующих комментариев
### XML-документация
Вы создаете документацию для кода, указывая ее в специальных полях комментариев, обозначаемых тройными косыми чертами. Поля комментария включают XML-элементы, которые описывают блок кода, следующий за комментариями:

    /// <summary>
    ///  This class performs an important function.
    /// </summary>
    public class MyClass {}

Все публичные поля и методы необходимо снабжать XML-комментариями. Приватные снабжать желательно.

### Пример комментариев XML

    namespace MyNamespace
    {
        /// <summary>
        /// Enter description here for class X.
        /// </summary>
        public unsafe class MyClass
        {
            /// <summary>
            /// Enter description here for the first constructor.
            /// </summary>
            public MyClass() { }

            /// <summary>
            /// Enter description here for the second constructor.
            /// </summary>
            /// <param name="i">Describe parameter.</param>
            public MyClass(int i) { }

            /// <summary>
            /// Enter description here for field message.
            /// </summary>
            public string? message;

            /// <summary>
            /// Enter description for constant PI.
            /// </summary>
            public const double PI = 3.14;

            /// <summary>
            /// Enter description for method func.
            /// </summary>
            /// <returns>Describe return value.</returns>
            public int func() { return 1; }

            /// <summary>
            /// Enter description for method someMethod.
            /// </summary>
            /// <param name="str">Describe parameter.</param>
            /// <param name="num">Describe parameter.</param>
            /// <param name="ptr">Describe parameter.</param>
            /// <returns>Describe return value.</returns>
            public int someMethod(string str, ref int nm, void* ptr) { return 1; }

            /// <summary>
            /// Enter description for method anotherMethod.
            /// </summary>
            /// <param name="array1">Describe parameter.</param>
            /// <param name="array">Describe parameter.</param>
            /// <returns>Describe return value.</returns>
            public int anotherMethod(short[] array1, int[,] array) { return 0; }

            /// <summary>
            /// Enter description for operator.
            /// </summary>
            /// <param name="first">Describe parameter.</param>
            /// <param name="second">Describe parameter.</param>
            /// <returns>Describe return value.</returns>
            public static MyClass operator +(MyClass first, MyClass second) { return first; }

            /// <summary>
            /// Enter description for property.
            /// </summary>
            public int prop { get { return 1; } set { } }

            /// <summary>
            /// Enter description for event.
            /// </summary>
            public event Del? OnHappened;

            /// <summary>
            /// Enter description for index.
            /// </summary>
            /// <param name="str">Describe parameter.</param>
            /// <returns></returns>
            public int this[string s] { get { return 1; } }

            /// <summary>
            /// Enter description for class Nested.
            /// </summary>
            public class Nested { }

            /// <summary>
            /// Enter description for delegate.
            /// </summary>
            /// <param name="i">Describe parameter.</param>
            public delegate void Del(int i);

            /// <summary>
            /// Enter description for operator.
            /// </summary>
            /// <param name="myParameter">Describe parameter.</param>
            /// <returns>Describe return value.</returns>
            public static explicit operator int(MyClass myParameter) { return 1; }
        }
    }

### Поддержка и создание XML-документации в Visual Studio
Visual Studio предоставляет возможность автоматического добавления XML-документации.

#### Порядок создания схемы XML
1. Откройте XML-файл в Visual Studio.
2. В строке меню выберите XML>Создать схему.
Документ XML-схемы будет создан и открыт для каждого пространства имен в XML-файле. Каждая схема открывается, как и любой временный файл. Схемы можно сохранять на диск, добавлять в проект или удалять.

# Ссылки на источники
[Соглашения по оформлению кода команды RSDN](http://rsdn.org/article/mag/200401/codestyle.XML)
[Комментарии XML-документации](https://learn.microsoft.com/ru-ru/dotnet/csharp/language-reference/xmldoc/)
[Создание схемы XML из XML-документа](https://learn.microsoft.com/ru-ru/visualstudio/xml-tools/how-to-create-an-xml-schema-from-an-xml-document?view=vs-2022)
