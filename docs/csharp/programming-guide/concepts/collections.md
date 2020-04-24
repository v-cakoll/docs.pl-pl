---
title: Kolekcje (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: d2996648690fc03b5f1d6a90e0be96155c5a24ed
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645467"
---
# <a name="collections-c"></a>Kolekcje (C#)

W przypadku wielu aplikacji należy utworzyć grupy powiązanych obiektów i zarządzać nimi. Istnieją dwa sposoby grupowania obiektów: przez tworzenie tablic obiektów i tworzenie kolekcji obiektów.

Tablice są najbardziej przydatne do tworzenia i pracy ze stałą liczbą silnie typizowanych obiektów. Aby uzyskać informacje o tablicach, zobacz [Tablice](../arrays/index.md).

Kolekcje zapewniają bardziej elastyczny sposób pracy z grupami obiektów. W przeciwieństwie do tablic, grupa obiektów, z którymi pracujesz, może dynamicznie rosnąć i zmniejszać się wraz ze zmianą potrzeb aplikacji. W przypadku niektórych kolekcji można przypisać klucz do dowolnego obiektu, który można umieścić w kolekcji, dzięki czemu można szybko pobrać obiekt przy użyciu klucza.

Kolekcja jest klasą, więc należy zadeklarować wystąpienie klasy, zanim będzie można dodać elementy do tej kolekcji.

Jeśli kolekcja zawiera elementy tylko jednego typu danych, można użyć <xref:System.Collections.Generic?displayProperty=nameWithType> jednej z klas w obszarze nazw. Kolekcja ogólna wymusza bezpieczeństwo typu, dzięki czemu nie można dodawać do niej żadnego innego typu danych. Podczas pobierania elementu z kolekcji ogólnej, nie trzeba określać jego typ danych lub przekonwertować go.

> [!NOTE]
> Przykłady w tym temacie obejmują [przy](../../language-reference/keywords/using-directive.md) użyciu `System.Collections.Generic` `System.Linq` dyrektyw dla i obszarów nazw.

 **W tym temacie**

- [Korzystanie z prostej kolekcji](#BKMK_SimpleCollection)

- [Rodzaje kolekcji](#BKMK_KindsOfCollections)

  - [System.Collections.Generic Klasy](#BKMK_Generic)

  - [System.Collections.Równoczesnych klas](#BKMK_Concurrent)

  - [Klasy System.Collections](#BKMK_Collections)

- [Implementowanie kolekcji par kluczy/wartości](#BKMK_KeyValuePairs)

- [Korzystanie z linq w celu uzyskania dostępu do kolekcji](#BKMK_LINQ)

- [Sortowanie kolekcji](#BKMK_Sorting)

- [Definiowanie kolekcji niestandardowej](#BKMK_CustomCollection)

- [Iteratory](#BKMK_Iterators)

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a>Korzystanie z prostej kolekcji

Przykłady w tej sekcji <xref:System.Collections.Generic.List%601> używają klasy ogólnej, która umożliwia pracę z silnie typizowanymi listami obiektów.

Poniższy przykład tworzy listę ciągów, a następnie iteruje za pośrednictwem ciągów przy użyciu [foreach](../../language-reference/keywords/foreach-in.md) instrukcji.

```csharp
// Create a list of strings.
var salmons = new List<string>();
salmons.Add("chinook");
salmons.Add("coho");
salmons.Add("pink");
salmons.Add("sockeye");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

Jeśli zawartość kolekcji są znane z wyprzedzeniem, można użyć *inicjatora kolekcji,* aby zainicjować kolekcję. Aby uzyskać więcej informacji, zobacz [Inicjatory obiektów i kolekcji](../classes-and-structs/object-and-collection-initializers.md).

Poniższy przykład jest taki sam jak w poprzednim przykładzie, z wyjątkiem inicjatora kolekcji jest używany do dodawania elementów do kolekcji.

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

Instrukcji [for](../../language-reference/keywords/for.md) zamiast `foreach` instrukcji do iteracji za pośrednictwem kolekcji. Można to osiągnąć, uzyskując dostęp do elementów kolekcji przez położenie indeksu. Indeks elementów rozpoczyna się od 0 i kończy się na liczbie elementów minus 1.

Poniższy przykład iteruje za pośrednictwem elementów kolekcji przy użyciu `for` zamiast . `foreach`

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

for (var index = 0; index < salmons.Count; index++)
{
    Console.Write(salmons[index] + " ");
}
// Output: chinook coho pink sockeye
```

Poniższy przykład usuwa element z kolekcji, określając obiekt do usunięcia.

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Remove an element from the list by specifying
// the object.
salmons.Remove("coho");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook pink sockeye
```

Poniższy przykład usuwa elementy z listy rodzajowej. Zamiast `foreach` instrukcji [for, for](../../language-reference/keywords/for.md) instrukcji, która iteruje w porządku malejącym jest używany. Jest tak, <xref:System.Collections.Generic.List%601.RemoveAt%2A> ponieważ metoda powoduje, że elementy po usunięty element mają niższą wartość indeksu.

```csharp
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };

// Remove odd numbers.
for (var index = numbers.Count - 1; index >= 0; index--)
{
    if (numbers[index] % 2 == 1)
    {
        // Remove the element by specifying
        // the zero-based index in the list.
        numbers.RemoveAt(index);
    }
}

// Iterate through the list.
// A lambda expression is placed in the ForEach method
// of the List(T) object.
numbers.ForEach(
    number => Console.Write(number + " "));
// Output: 0 2 4 6 8
```

Dla typu elementów <xref:System.Collections.Generic.List%601>w programie można również zdefiniować własną klasę. W poniższym przykładzie `Galaxy` klasa, która <xref:System.Collections.Generic.List%601> jest używana przez jest zdefiniowana w kodzie.

```csharp
private static void IterateThroughList()
{
    var theGalaxies = new List<Galaxy>
        {
            new Galaxy() { Name="Tadpole", MegaLightYears=400},
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},
            new Galaxy() { Name="Milky Way", MegaLightYears=0},
            new Galaxy() { Name="Andromeda", MegaLightYears=3}
        };

    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);
    }

    // Output:
    //  Tadpole  400
    //  Pinwheel  25
    //  Milky Way  0
    //  Andromeda  3
}

public class Galaxy
{
    public string Name { get; set; }
    public int MegaLightYears { get; set; }
}
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a>Rodzaje kolekcji

Wiele typowych kolekcji są dostarczane przez .NET Framework. Każdy rodzaj kolekcji jest przeznaczony do określonego celu.

Niektóre typowe klasy kolekcji są opisane w tej sekcji:

- <xref:System.Collections.Generic>, klasy

- <xref:System.Collections.Concurrent>, klasy

- <xref:System.Collections>, klasy

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a>System.Collections.Generic Klasy

Kolekcję rodzajową można utworzyć przy użyciu <xref:System.Collections.Generic> jednej z klas w obszarze nazw. Kolekcja ogólna jest przydatna, gdy każdy element w kolekcji ma ten sam typ danych. Kolekcja ogólna wymusza silne wpisywanie, zezwalając na dodawać tylko żądany typ danych.

W poniższej tabeli wymieniono niektóre <xref:System.Collections.Generic?displayProperty=nameWithType> z często używanych klas obszaru nazw:

|Klasa|Opis|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|Reprezentuje kolekcję par klucz/wartość, które są zorganizowane na podstawie klucza.|
|<xref:System.Collections.Generic.List%601>|Reprezentuje listę obiektów, które są dostępne przez indeks. Udostępnia metody wyszukiwania, sortowania i modyfikowania list.|
|<xref:System.Collections.Generic.Queue%601>|Reprezentuje pierwszy w, pierwszy na zewnątrz (FIFO) kolekcja obiektów.|
|<xref:System.Collections.Generic.SortedList%602>|Reprezentuje kolekcję par klucz/wartość, które są sortowane według <xref:System.Collections.Generic.IComparer%601> klucza na podstawie skojarzonej implementacji.|
|<xref:System.Collections.Generic.Stack%601>|Reprezentuje ostatnią w, pierwszy na zewnątrz (LIFO) kolekcji obiektów.|

Aby uzyskać dodatkowe informacje, zobacz [Typy często używanych kolekcji](../../../standard/collections/commonly-used-collection-types.md), [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)i <xref:System.Collections.Generic>.

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a>System.Collections.Równoczesnych klas

W programie .NET Framework 4 lub nowszym kolekcje w obszarze <xref:System.Collections.Concurrent> nazw zapewniają wydajne operacje bezpieczne dla wątków, aby uzyskać dostęp do elementów kolekcji z wielu wątków.

Klasy w <xref:System.Collections.Concurrent> obszarze nazw powinny być używane zamiast odpowiednich <xref:System.Collections.Generic?displayProperty=nameWithType> <xref:System.Collections?displayProperty=nameWithType> typów w i przestrzenie nazw, gdy wiele wątków uzyskuje dostęp do kolekcji jednocześnie. Aby uzyskać więcej informacji, zobacz <xref:System.Collections.Concurrent> [Kolekcje bezpieczne dla wątków](../../../standard/collections/thread-safe/index.md) i .

Niektóre klasy zawarte <xref:System.Collections.Concurrent> w obszarze <xref:System.Collections.Concurrent.BlockingCollection%601> <xref:System.Collections.Concurrent.ConcurrentDictionary%602>nazw <xref:System.Collections.Concurrent.ConcurrentQueue%601>to <xref:System.Collections.Concurrent.ConcurrentStack%601>, , i .

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a>Klasy System.Collections

Klasy w <xref:System.Collections?displayProperty=nameWithType> obszarze nazw nie przechowują elementów jako obiektów specjalnie `Object`wpisywanych, ale jako obiekty typu .

Jeśli to możliwe, należy użyć kolekcji <xref:System.Collections.Generic?displayProperty=nameWithType> ogólnych w <xref:System.Collections.Concurrent> obszarze nazw lub obszaru nazw `System.Collections` zamiast starszych typów w obszarze nazw.

W poniższej tabeli wymieniono niektóre `System.Collections` z często używanych klas w obszarze nazw:

|Klasa|Opis|
|---|---|
|<xref:System.Collections.ArrayList>|Reprezentuje tablicę obiektów, których rozmiar jest dynamicznie zwiększany zgodnie z wymaganiami.|
|<xref:System.Collections.Hashtable>|Reprezentuje kolekcję par klucz/wartość, które są zorganizowane na podstawie kodu skrótu klucza.|
|<xref:System.Collections.Queue>|Reprezentuje pierwszy w, pierwszy na zewnątrz (FIFO) kolekcja obiektów.|
|<xref:System.Collections.Stack>|Reprezentuje ostatnią w, pierwszy na zewnątrz (LIFO) kolekcji obiektów.|

Obszar <xref:System.Collections.Specialized> nazw zawiera wyspecjalizowane i silnie typizowane klasy kolekcji, takie jak kolekcje tylko do ciągu i połączone listy i słowniki hybrydowe.

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementowanie kolekcji par kluczy/wartości

Kolekcja <xref:System.Collections.Generic.Dictionary%602> ogólna umożliwia dostęp do elementów w kolekcji przy użyciu klucza każdego elementu. Każdy dodatek do słownika składa się z wartości i skojarzonego z nim klucza. Pobieranie wartości przy użyciu jego klucz `Dictionary` jest szybki, ponieważ klasa jest implementowana jako tabela mieszania.

Poniższy przykład `Dictionary` tworzy kolekcję i iteruje za `foreach` pośrednictwem słownika przy użyciu instrukcji.

```csharp
private static void IterateThruDictionary()
{
    Dictionary<string, Element> elements = BuildDictionary();

    foreach (KeyValuePair<string, Element> kvp in elements)
    {
        Element theElement = kvp.Value;

        Console.WriteLine("key: " + kvp.Key);
        Console.WriteLine("values: " + theElement.Symbol + " " +
            theElement.Name + " " + theElement.AtomicNumber);
    }
}

private static Dictionary<string, Element> BuildDictionary()
{
    var elements = new Dictionary<string, Element>();

    AddToDictionary(elements, "K", "Potassium", 19);
    AddToDictionary(elements, "Ca", "Calcium", 20);
    AddToDictionary(elements, "Sc", "Scandium", 21);
    AddToDictionary(elements, "Ti", "Titanium", 22);

    return elements;
}

private static void AddToDictionary(Dictionary<string, Element> elements,
    string symbol, string name, int atomicNumber)
{
    Element theElement = new Element();

    theElement.Symbol = symbol;
    theElement.Name = name;
    theElement.AtomicNumber = atomicNumber;

    elements.Add(key: theElement.Symbol, value: theElement);
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

Zamiast tego zamiast tego użyj inicjatora kolekcji do tworzenia `Dictionary` kolekcji, można zastąpić `BuildDictionary` i `AddToDictionary` metody z następującą metodą.

```csharp
private static Dictionary<string, Element> BuildDictionary2()
{
    return new Dictionary<string, Element>
    {
        {"K",
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        {"Ca",
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        {"Sc",
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        {"Ti",
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}
```

W poniższym przykładzie <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> użyto metody i <xref:System.Collections.Generic.Dictionary%602.Item%2A> `Dictionary` właściwości, aby szybko znaleźć element według klucza. Właściwość `Item` umożliwia dostęp do elementu `elements` w kolekcji przy użyciu `elements[symbol]` w języku C#.

```csharp
private static void FindInDictionary(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    if (elements.ContainsKey(symbol) == false)
    {
        Console.WriteLine(symbol + " not found");
    }
    else
    {
        Element theElement = elements[symbol];
        Console.WriteLine("found: " + theElement.Name);
    }
}
```

W poniższym <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> przykładzie zamiast tego używa metody szybko znaleźć element po kluczu.

```csharp
private static void FindInDictionary2(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    Element theElement = null;
    if (elements.TryGetValue(symbol, out theElement) == false)
        Console.WriteLine(symbol + " not found");
    else
        Console.WriteLine("found: " + theElement.Name);
}
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a>Korzystanie z linq w celu uzyskania dostępu do kolekcji

LINQ (Zapytanie zintegrowane z językiem) może służyć do uzyskiwania dostępu do kolekcji. Zapytania LINQ zapewniają możliwości filtrowania, zamawiania i grupowania. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do LINQ w języku C#](linq/index.md).

W poniższym przykładzie uruchamia kwerendę LINQ względem ogólnego `List`. Kwerenda LINQ zwraca inną kolekcję, która zawiera wyniki.

```csharp
private static void ShowLINQ()
{
    List<Element> elements = BuildList();

    // LINQ Query.
    var subset = from theElement in elements
                 where theElement.AtomicNumber < 22
                 orderby theElement.Name
                 select theElement;

    foreach (Element theElement in subset)
    {
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);
    }

    // Output:
    //  Calcium 20
    //  Potassium 19
    //  Scandium 21
}

private static List<Element> BuildList()
{
    return new List<Element>
    {
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a>Sortowanie kolekcji

Poniższy przykład ilustruje procedurę sortowania kolekcji. Przykład sortuje wystąpienia `Car` klasy, które są <xref:System.Collections.Generic.List%601>przechowywane w . Klasa `Car` implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> metoda została zaimplementowana.

Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metody sprawia, że pojedyncze porównanie, który jest używany do sortowania. Kod napisany przez użytkownika `CompareTo` w metodzie zwraca wartość dla każdego porównania bieżącego obiektu z innym obiektem. Zwracana wartość jest mniejsza niż zero, jeśli bieżący obiekt jest mniejszy niż inny obiekt, większa od zera, jeśli bieżący obiekt jest większa od innego obiektu, i zero, jeśli są równe. Dzięki temu można zdefiniować w kodzie kryteria dla większych niż, mniej niż i równe.

W `ListCars` metodzie `cars.Sort()` instrukcji sortuje listę. To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje, `CompareTo` że metoda ma być `Car` wywoływana `List`automatycznie dla obiektów w .

```csharp
private static void ListCars()
{
    var cars = new List<Car>
    {
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},
        { new Car() { Name = "car2", Color = "red", Speed = 50}},
        { new Car() { Name = "car3", Color = "green", Speed = 10}},
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},
        { new Car() { Name = "car6", Color = "red", Speed = 60}},
        { new Car() { Name = "car7", Color = "green", Speed = 50}}
    };

    // Sort the cars by color alphabetically, and then by speed
    // in descending order.
    cars.Sort();

    // View all of the cars.
    foreach (Car thisCar in cars)
    {
        Console.Write(thisCar.Color.PadRight(5) + " ");
        Console.Write(thisCar.Speed.ToString() + " ");
        Console.Write(thisCar.Name);
        Console.WriteLine();
    }

    // Output:
    //  blue  50 car4
    //  blue  30 car5
    //  blue  20 car1
    //  green 50 car7
    //  green 10 car3
    //  red   60 car6
    //  red   50 car2
}

public class Car : IComparable<Car>
{
    public string Name { get; set; }
    public int Speed { get; set; }
    public string Color { get; set; }

    public int CompareTo(Car other)
    {
        // A call to this method makes a single comparison that is
        // used for sorting.

        // Determine the relative order of the objects being compared.
        // Sort by color alphabetically, and then by speed in
        // descending order.

        // Compare the colors.
        int compare;
        compare = String.Compare(this.Color, other.Color, true);

        // If the colors are the same, compare the speeds.
        if (compare == 0)
        {
            compare = this.Speed.CompareTo(other.Speed);

            // Use descending order for speed.
            compare = -compare;
        }

        return compare;
    }
}
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a>Definiowanie kolekcji niestandardowej

Kolekcję można zdefiniować, <xref:System.Collections.Generic.IEnumerable%601> implementując lub <xref:System.Collections.IEnumerable> interfejs.

Chociaż można zdefiniować kolekcji niestandardowej, zwykle lepiej jest zamiast tego użyć kolekcji, które są zawarte w .NET Framework, które są opisane w [Rodzaje kolekcji](#BKMK_KindsOfCollections) wcześniej w tym temacie.

Poniższy przykład definiuje niestandardową `AllColors`klasę kolekcji o nazwie . Ta klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który <xref:System.Collections.IEnumerable.GetEnumerator%2A> wymaga, aby metoda została zaimplementowana.

Metoda `GetEnumerator` zwraca wystąpienie `ColorEnumerator` klasy. `ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> interfejs, który wymaga, <xref:System.Collections.IEnumerator.Current%2A> <xref:System.Collections.IEnumerator.MoveNext%2A> aby zaimplementowano właściwość, metodę i <xref:System.Collections.IEnumerator.Reset%2A> metodę.

```csharp
private static void ListColors()
{
    var colors = new AllColors();

    foreach (Color theColor in colors)
    {
        Console.Write(theColor.Name + " ");
    }
    Console.WriteLine();
    // Output: red blue green
}

// Collection class.
public class AllColors : System.Collections.IEnumerable
{
    Color[] _colors =
    {
        new Color() { Name = "red" },
        new Color() { Name = "blue" },
        new Color() { Name = "green" }
    };

    public System.Collections.IEnumerator GetEnumerator()
    {
        return new ColorEnumerator(_colors);

        // Instead of creating a custom enumerator, you could
        // use the GetEnumerator of the array.
        //return _colors.GetEnumerator();
    }

    // Custom enumerator.
    private class ColorEnumerator : System.Collections.IEnumerator
    {
        private Color[] _colors;
        private int _position = -1;

        public ColorEnumerator(Color[] colors)
        {
            _colors = colors;
        }

        object System.Collections.IEnumerator.Current
        {
            get
            {
                return _colors[_position];
            }
        }

        bool System.Collections.IEnumerator.MoveNext()
        {
            _position++;
            return (_position < _colors.Length);
        }

        void System.Collections.IEnumerator.Reset()
        {
            _position = -1;
        }
    }
}

// Element class.
public class Color
{
    public string Name { get; set; }
}
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a>Iteratory

*Iterator* jest używany do wykonywania iteracji niestandardowej nad kolekcją. Iterator może być metodą `get` lub akcesorem. Iterator używa [yield return](../../language-reference/keywords/yield.md) instrukcji, aby zwrócić każdy element kolekcji po jednym naraz.

Wywołać iterator przy użyciu [foreach](../../language-reference/keywords/foreach-in.md) instrukcji. Każda iteracja `foreach` pętli wywołuje iteratora. Po `yield return` osiągnięciu instrukcji w iteratorze zwracane jest wyrażenie, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest ponownie uruchamiane z tej lokalizacji przy następnym wywołanie iteratora.

Aby uzyskać więcej informacji, zobacz [Iteratory (C#)](./iterators.md).

W poniższym przykładzie użyto metody iteratora. Metoda iteratora `yield return` ma instrukcję, która znajduje się wewnątrz [for](../../language-reference/keywords/for.md) pętli. W `ListEvenNumbers` metodzie każda iteracja `foreach` treści instrukcji tworzy wywołanie metody iteratora, `yield return` która przechodzi do następnej instrukcji.

```csharp
private static void ListEvenNumbers()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    Console.WriteLine();
    // Output: 6 8 10 12 14 16 18
}

private static IEnumerable<int> EvenSequence(
    int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (var number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="see-also"></a>Zobacz też

- [Inicjatory obiektów i kolekcji](../classes-and-structs/object-and-collection-initializers.md)
- [Pojęcia programistyczne (C#)](./index.md)
- [Option Strict — Instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [LINQ do obiektów (C#)](./linq/linq-to-objects.md)
- [Równoległe LINQ (PLINQ)](../../../standard/parallel-programming/introduction-to-plinq.md)
- [Kolekcje i struktury danych](../../../standard/collections/index.md)
- [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)
- [Porównania i sortowanie w kolekcjach](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [Kiedy używać kolekcji ogólnych](../../../standard/collections/when-to-use-generic-collections.md)
