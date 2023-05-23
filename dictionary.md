# Коллекция Dictionary
### Описание Dictionary
Еще один распространенный тип коллекции представляют словари. Словарь хранит объекты, которые представляют пару ключ-значение. Класс словаря Dictionary<K, V> типизируется двумя типами: параметр K представляет тип ключей, а параметр V предоставляет тип значений.

### Создание и инициализация Dictionary
Создание пустого словаря:

    Dictionary<int, string> people = new Dictionary<int, string>();
    
При определении словаря его сразу же можно инициализировать значениями:

    var people = new Dictionary<int, string>()
    {
        { 5, "Tom"},
        { 3, "Sam"},
        { 11, "Bob"}
    };

Также мы можем применять другой способ инициализации:

    var people = new Dictionary<int, string>()
    {
        [5] = "Tom",
        [6] = "Sam",
        [7] = "Bob"
    };  
    
Стоит отметить, что каждый элемент в словаре представляет структуру KeyValuePair<TKey, TValue>, где параметр TKey представляет тип ключа, а параметр TValue - тип значений элементов. Эта структура предоставляет свойства Key и Value, с помощью которых можно получить соответственно ключ и значение элемента в словаре. И одна из версий конструктора Dictionary позволяет инициализировать словарь коллекцией объектов KeyValuePair:

    var mike = new KeyValuePair<int, string>(56, "Mike"); 
    var employees = new List<KeyValuePair<int, string>>() { mike};
    var people = new Dictionary<int, string>(employees);
    
### Методы и свойства Dictionary

- void Add(K key, V value): добавляет новый элемент в словарь
- void Clear(): очищает словарь
- bool ContainsKey(K key): проверяет наличие элемента с определенным ключом и возвращает true при его наличии в словаре
- bool ContainsValue(V value): проверяет наличие элемента с определенным значением и возвращает true при его наличии в словаре
- bool Remove(K key): удаляет по ключу элемент из словаря
- Другая версия этого метода позволяет получить удленный элемент в выходной параметр: bool Remove(K key, out V value)
- bool TryGetValue(K key, out V value): получает из словаря элемент по ключу key. При успешном получении передает значение элемента в выходной параметр value и возвращает true
- bool TryAdd(K key, V value): добавляет в словарь элемент с ключом key и значением value. При успешном добавлении возвращает true
- Count возвращает количество элементов в словаре.

### Применение методов Dictionary

    // условная телефонная книга
    var phoneBook = new Dictionary<string, string>();

    // добавляем элемент: ключ - номер телефона, значение - имя абонента
    phoneBook.Add("+123456", "Tom");
    // альтернативное добавление
    // phoneBook["+123456"] = "Tom";

    // Проверка наличия
    var phoneExists1 = phoneBook.ContainsKey("+123456");    // true
    Console.WriteLine($"+123456: {phoneExists1}");
    var phoneExists2 = phoneBook.ContainsKey("+567456");    // false
    Console.WriteLine($"+567456: {phoneExists2}");
    var abonentExists1 = phoneBook.ContainsValue("Tom");      // true
    Console.WriteLine($"Tom: {abonentExists1}");
    var abonentExists2 = phoneBook.ContainsValue("Bob");      // false
    Console.WriteLine($"Bob: {abonentExists2}");

    // удаление элемента
    phoneBook.Remove("+123456");

    // проверяем количество элементов после удаления
    Console.WriteLine($"Count: {phoneBook.Count}"); // Count: 0

# Ссылки на источники
[Коллекция Dictionary<K, V>](https://metanit.com/sharp/tutorial/4.9.php)
