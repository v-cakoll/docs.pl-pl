---
title: Kolekcje (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: a560155b936aef7a4a346d39eaed75e0a85c1a73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169886"
---
# <a name="collections-c"></a>Kolekcje (C#)

W przypadku wielu aplikacji chcesz tworzyć grupy powiązanych obiektów i zarządzać nimi. Istnieją dwa sposoby grupowania obiektów: przez tworzenie tablic obiektów i tworzenie kolekcji obiektów.

Tablice są najbardziej przydatne do tworzenia i pracy ze stałą liczbą silnie typizonych obiektów. Aby uzyskać informacje o tablicach, zobacz [Tablice](../arrays/index.md).

Kolekcje zapewniają bardziej elastyczny sposób pracy z grupami obiektów. W przeciwieństwie do tablic, grupa obiektów, z których pracujesz, może dynamicznie rosnąć i zmniejszać się wraz ze zmianą potrzeb aplikacji. W przypadku niektórych kolekcji można przypisać klucz do dowolnego obiektu, który można umieścić w kolekcji, dzięki czemu można szybko pobrać obiekt przy użyciu klucza.

Kolekcja jest klasą, więc należy zadeklarować wystąpienie klasy, zanim będzie można dodać elementy do tej kolekcji.

Jeśli kolekcja zawiera elementy tylko jednego typu danych, można użyć <xref:System.Collections.Generic?displayProperty=nameWithType> jednej z klas w przestrzeni nazw. Kolekcja ogólna wymusza bezpieczeństwo typów, dzięki czemu nie można dodać do niej żadnego innego typu danych. Podczas pobierania elementu z kolekcji ogólnej, nie trzeba określić jego typ danych lub przekonwertować go.

> [!NOTE]
> Przykłady w tym temacie obejmują [przy użyciu](../../language-reference/keywords/using-directive.md) `System.Collections.Generic` dyrektyw `System.Linq` dla i przestrzeni nazw.

 **W tym temacie**

- [Korzystanie z prostej kolekcji](#BKMK_SimpleCollection)

- [Rodzaje kolekcji](#BKMK_KindsOfCollections)

  - [Klasy System.Collections.Generic](#BKMK_Generic)

  - [Klasy System.Collections.Concurrent](#BKMK_Concurrent)

  - [Klasy System.Collections](#BKMK_Collections)

- [Implementowanie kolekcji par klucz/wartość](#BKMK_KeyValuePairs)

- [Korzystanie z LINQ w celu uzyskania dostępu do kolekcji](#BKMK_LINQ)

- [Sortowanie kolekcji](#BKMK_Sorting)

- [Definiowanie kolekcji niestandardowej](#BKMK_CustomCollection)

- [Iteratory](#BKMK_Iterators)

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a>Korzystanie z prostej kolekcji

Przykłady w tej sekcji użyć <xref:System.Collections.Generic.List%601> klasy ogólnej, która umożliwia pracę z silnie typizowana lista obiektów.

Poniższy przykład tworzy listę ciągów, a następnie iteruje za pomocą ciągów przy użyciu [foreach](../../language-reference/keywords/foreach-in.md) instrukcji.

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

Jeśli zawartość kolekcji są znane z wyprzedzeniem, można użyć *inicjatora kolekcji* do zainicjowania kolekcji. Aby uzyskać więcej informacji, zobacz [Inicjatory obiektów i kolekcji](../classes-and-structs/object-and-collection-initializers.md).

Poniższy przykład jest taki sam jak w poprzednim przykładzie, z wyjątkiem inicjatorkolekcji jest używany do dodawania elementów do kolekcji.

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

Można użyć [for](../../language-reference/keywords/for.md) instrukcji zamiast `foreach` instrukcji do iterate za pośrednictwem kolekcji. Można to osiągnąć, uzyskując dostęp do elementów kolekcji przez pozycję indeksu. Indeks elementów zaczyna się od 0 i kończy się na liczbę elementów minus 1.

Poniższy przykład itetensje za pośrednictwem `for` elementów `foreach`kolekcji przy użyciu zamiast .

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

Poniższy przykład usuwa elementy z listy ogólnej. Zamiast `foreach` instrukcji, [do](../../language-reference/keywords/for.md) instrukcji, że iteruje w kolejności malejącej jest używany. Jest tak, <xref:System.Collections.Generic.List%601.RemoveAt%2A> ponieważ metoda powoduje, że elementy po usunięty element mają niższą wartość indeksu.

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

Dla typu elementów w <xref:System.Collections.Generic.List%601>programie , można również zdefiniować własną klasę. W poniższym przykładzie `Galaxy` klasy, która <xref:System.Collections.Generic.List%601> jest używana przez jest zdefiniowana w kodzie.

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

Wiele wspólnych kolekcji są dostarczane przez .NET Framework. Każdy typ kolekcji jest przeznaczony do określonego celu.

Niektóre wspólne klasy kolekcji są opisane w tej sekcji:

- <xref:System.Collections.Generic>, klasy

- <xref:System.Collections.Concurrent>, klasy

- <xref:System.Collections>, klasy

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a>Klasy System.Collections.Generic

Kolekcję rodzajową można utworzyć przy użyciu <xref:System.Collections.Generic> jednej z klas w obszarze nazw. Kolekcja rodzajowa jest przydatna, gdy każdy element w kolekcji ma ten sam typ danych. Kolekcja ogólna wymusza silne wpisywanie, zezwalając tylko żądany typ danych, które mają być dodane.

W poniższej tabeli wymieniono niektóre <xref:System.Collections.Generic?displayProperty=nameWithType> często używane klasy obszaru nazw:

|Klasa|Opis|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|Reprezentuje kolekcję par klucz/wartość, które są zorganizowane na podstawie klucza.|
|<xref:System.Collections.Generic.List%601>|Reprezentuje listę obiektów, do których można uzyskać dostęp za pomocą indeksu. Udostępnia metody wyszukiwania, sortowania i modyfikowania list.|
|<xref:System.Collections.Generic.Queue%601>|Reprezentuje pierwszy w, pierwszy out (FIFO) kolekcji obiektów.|
|<xref:System.Collections.Generic.SortedList%602>|Reprezentuje kolekcję par klucz/wartość, które są sortowane według <xref:System.Collections.Generic.IComparer%601> klucza na podstawie skojarzonej implementacji.|
|<xref:System.Collections.Generic.Stack%601>|Reprezentuje ostatniw, first out (LIFO) kolekcji obiektów.|

Aby uzyskać dodatkowe informacje, zobacz [Często używane typy kolekcji](../../../standard/collections/commonly-used-collection-types.md), [wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)i <xref:System.Collections.Generic>.

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a>Klasy System.Collections.Concurrent

W .NET Framework 4 lub nowsze <xref:System.Collections.Concurrent> kolekcje w przestrzeni nazw zapewniają wydajne operacje bezpieczne dla wątków dostępu do elementów kolekcji z wielu wątków.

Klasy w <xref:System.Collections.Concurrent> przestrzeni nazw powinny być używane zamiast <xref:System.Collections.Generic?displayProperty=nameWithType> odpowiednich <xref:System.Collections?displayProperty=nameWithType> typów w przestrzeni nazw i zawsze, gdy wiele wątków uzyskuje dostęp do kolekcji jednocześnie. Aby uzyskać więcej informacji, zobacz <xref:System.Collections.Concurrent> [Kolekcje bezpieczne dla wątków](../../../standard/collections/thread-safe/index.md) i .

Niektóre klasy zawarte <xref:System.Collections.Concurrent> w <xref:System.Collections.Concurrent.BlockingCollection%601>przestrzeni <xref:System.Collections.Concurrent.ConcurrentDictionary%602> <xref:System.Collections.Concurrent.ConcurrentQueue%601>nazw <xref:System.Collections.Concurrent.ConcurrentStack%601>to , , i .

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a>Klasy System.Collections

Klasy w <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw nie przechowują elementów jako specjalnie `Object`wpisanych obiektów, ale jako obiekty typu .

Jeśli to możliwe, należy użyć kolekcji <xref:System.Collections.Generic?displayProperty=nameWithType> ogólnych <xref:System.Collections.Concurrent> w obszarze nazw lub obszaru `System.Collections` nazw zamiast starszych typów w obszarze nazw.

W poniższej tabeli wymieniono niektóre `System.Collections` z często używanych klas w obszarze nazw:

|Klasa|Opis|
|---|---|
|<xref:System.Collections.ArrayList>|Reprezentuje tablicę obiektów, których rozmiar jest dynamicznie zwiększany zgodnie z wymaganiami.|
|<xref:System.Collections.Hashtable>|Reprezentuje kolekcję par klucz/wartość, które są zorganizowane na podstawie kodu skrótu klucza.|
|<xref:System.Collections.Queue>|Reprezentuje pierwszy w, pierwszy out (FIFO) kolekcji obiektów.|
|<xref:System.Collections.Stack>|Reprezentuje ostatniw, first out (LIFO) kolekcji obiektów.|

Obszar <xref:System.Collections.Specialized> nazw zawiera wyspecjalizowane i silnie typizowane klasy kolekcji, takie jak kolekcje tylko do ciągów i słowniki połączonelisty i hybrydowe.

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementowanie kolekcji par klucz/wartość

Kolekcja <xref:System.Collections.Generic.Dictionary%602> ogólna umożliwia dostęp do elementów w kolekcji przy użyciu klucza każdego elementu. Każdy dodatek do słownika składa się z wartości i skojarzonego z nim klucza. Pobieranie wartości przy użyciu jego klucza `Dictionary` jest szybki, ponieważ klasa jest implementowana jako tabela mieszania.

Poniższy przykład tworzy `Dictionary` kolekcję i iteruje za `foreach` pośrednictwem słownika przy użyciu instrukcji.

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

Zamiast tego użyj inicjatora kolekcji do tworzenia `Dictionary` kolekcji, można zastąpić `BuildDictionary` i `AddToDictionary` metody z następującą metodą.

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

W poniższym <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> przykładzie użyto `Dictionary` metody i <xref:System.Collections.Generic.Dictionary%602.Item%2A> właściwości, aby szybko znaleźć element według klucza. Właściwość `Item` umożliwia dostęp do elementu `elements` w kolekcji `elements[symbol]` przy użyciu w języku C#.

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

W poniższym <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> przykładzie zamiast tego używa metody szybko znaleźć element według klucza.

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

## <a name="using-linq-to-access-a-collection"></a>Korzystanie z LINQ w celu uzyskania dostępu do kolekcji

LINQ (Language-Integrated Query) może służyć do uzyskiwania dostępu do kolekcji. Zapytania LINQ zapewniają możliwości filtrowania, porządkowania i grupowania. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do LINQ w języku C#](linq/index.md).

Poniższy przykład uruchamia kwerendę LINQ `List`względem ogólnego . Kwerenda LINQ zwraca inną kolekcję, która zawiera wyniki.

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

W poniższym przykładzie przedstawiono procedurę sortowania kolekcji. Przykład sortuje wystąpienia `Car` klasy, które są <xref:System.Collections.Generic.List%601>przechowywane w pliku . Klasa `Car` implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> metoda została zaimplementowana.

Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metody sprawia, że pojedyncze porównanie, który jest używany do sortowania. Kod napisany przez `CompareTo` użytkownika w metodzie zwraca wartość dla każdego porównania bieżącego obiektu z innym obiektem. Zwracana wartość jest mniejsza niż zero, jeśli bieżący obiekt jest mniejszy niż inny obiekt, większy niż zero, jeśli bieżący obiekt jest większy niż inny obiekt, a zero, jeśli są równe. Dzięki temu można zdefiniować w kodzie kryteria dla większej niż, mniejszej niż i równej.

W `ListCars` metodzie `cars.Sort()` instrukcja sortuje listę. To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje, `CompareTo` że metoda ma być `Car` wywoływana `List`automatycznie dla obiektów w .

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

Kolekcję można zdefiniować, <xref:System.Collections.Generic.IEnumerable%601> implementując lub <xref:System.Collections.IEnumerable> interfejsu.

Mimo że można zdefiniować kolekcję niestandardową, zwykle lepiej jest zamiast tego używać kolekcji, które są zawarte w .NET Framework, które są opisane w [kinds of collections](#BKMK_KindsOfCollections) wcześniej w tym temacie.

W poniższym przykładzie zdefiniowano `AllColors`klasę kolekcji niestandardowej o nazwie . Ta klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który <xref:System.Collections.IEnumerable.GetEnumerator%2A> wymaga, aby zaimplementowana metoda.

Metoda `GetEnumerator` zwraca wystąpienie `ColorEnumerator` klasy. `ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> interfejs, który wymaga, aby <xref:System.Collections.IEnumerator.Current%2A> zaimplementowano właściwość, <xref:System.Collections.IEnumerator.MoveNext%2A> metodę i <xref:System.Collections.IEnumerator.Reset%2A> metodę.

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

*Iterator* służy do wykonywania niestandardowej iteracji za pomocą kolekcji. Iterator może być metodą `get` lub akcesorem. Iterator używa [yield return](../../language-reference/keywords/yield.md) instrukcji do zwrócenia każdego elementu kolekcji po jednym naraz.

Wywołanie iterator przy użyciu [foreach](../../language-reference/keywords/foreach-in.md) instrukcji. Każda iteracja `foreach` pętli wywołuje iterator. Po `yield return` osiągnięciu instrukcji w iteratorze zwracane jest wyrażenie, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołanie wywołania sterująca.

Aby uzyskać więcej informacji, zobacz [Iterytory (C#)](./iterators.md).

W poniższym przykładzie użyto metody iteratorem. Metoda iterator ma `yield return` instrukcję, która znajduje się wewnątrz [for](../../language-reference/keywords/for.md) pętli. W `ListEvenNumbers` metodzie każda iteracja `foreach` treści instrukcji tworzy wywołanie metody iterator, która `yield return` przechodzi do następnej instrukcji.

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
- [Koncepcje programowania (C#)](./index.md)
- [Option Strict — Instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [LINQ do obiektów (C#)](./linq/linq-to-objects.md)
- [Równoległe LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)
- [Kolekcje i struktury danych](../../../standard/collections/index.md)
- [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)
- [Porównywanie i sortowanie w kolekcjach](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [Kiedy należy używać kolekcji ogólnych](../../../standard/collections/when-to-use-generic-collections.md)
