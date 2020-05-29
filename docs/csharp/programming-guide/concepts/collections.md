---
title: Kolekcje (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 30aa3e34f362f34fc601f90ee61613acd6e4bc68
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201134"
---
# <a name="collections-c"></a>Kolekcje (C#)

W przypadku wielu aplikacji, należy utworzyć grupy powiązanych obiektów i zarządzać nimi. Istnieją dwa sposoby grupowania obiektów: przez tworzenie tablic obiektów i tworzenie kolekcji obiektów.

Tablice są najbardziej przydatne do tworzenia i pracy ze stałą liczbą obiektów silnie wpisanych. Aby uzyskać informacje na temat tablic, zobacz [tablice](../arrays/index.md).

Kolekcje zapewniają bardziej elastyczny sposób pracy z grupami obiektów. W przeciwieństwie do tablic, Grupa obiektów, z którymi pracujesz, może być zwiększana i zmniejszana dynamicznie w miarę potrzeby zmiany aplikacji. W przypadku niektórych kolekcji można przypisać klucz do dowolnego obiektu, który został umieszczony w kolekcji, dzięki czemu można szybko pobrać obiekt przy użyciu klucza.

Kolekcja jest klasą, więc należy zadeklarować wystąpienie klasy, aby można było dodać elementy do tej kolekcji.

Jeśli kolekcja zawiera elementy tylko jednego typu danych, można użyć jednej z klas w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw. Ogólna kolekcja wymusza bezpieczeństwo typu, tak aby nie można było dodać do niego żadnego innego typu danych. Po pobraniu elementu z kolekcji ogólnej nie trzeba określać jego typu danych ani go przekonwertować.

> [!NOTE]
> Aby zapoznać się z przykładami w tym temacie, należy uwzględnić dyrektywy [using](../../language-reference/keywords/using-directive.md) dla `System.Collections.Generic` `System.Linq` przestrzeni nazw i.

 **W tym temacie**

- [Korzystanie z prostej kolekcji](#BKMK_SimpleCollection)

- [Rodzaje kolekcji](#BKMK_KindsOfCollections)

  - [Klasy System. Collections. Generic](#BKMK_Generic)

  - [Klasy System. Collections. współbieżne](#BKMK_Concurrent)

  - [Klasy System. Collections](#BKMK_Collections)

- [Implementowanie kolekcji par klucz/wartość](#BKMK_KeyValuePairs)

- [Używanie LINQ do uzyskiwania dostępu do kolekcji](#BKMK_LINQ)

- [Sortowanie kolekcji](#BKMK_Sorting)

- [Definiowanie kolekcji niestandardowej](#BKMK_CustomCollection)

- [Iteratory](#BKMK_Iterators)

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a>Korzystanie z prostej kolekcji

W przykładach w tej sekcji użyto klasy generycznej <xref:System.Collections.Generic.List%601> , która pozwala na współpracę z silnie wpisaną listą obiektów.

Poniższy przykład tworzy listę ciągów, a następnie iteruje przez ciągi przy użyciu instrukcji [foreach](../../language-reference/keywords/foreach-in.md) .

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

Jeśli zawartość kolekcji jest znana z wyprzedzeniem, można użyć *inicjatora kolekcji* w celu zainicjowania kolekcji. Aby uzyskać więcej informacji, zobacz [Inicjatory obiektów i kolekcji](../classes-and-structs/object-and-collection-initializers.md).

Poniższy przykład jest taki sam jak w poprzednim przykładzie, z wyjątkiem tego, że inicjator kolekcji jest używany do dodawania elementów do kolekcji.

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

Można użyć instrukcji [for](../../language-reference/keywords/for.md) zamiast `foreach` instrukcji, aby wykonać iterację w kolekcji. Można to osiągnąć, uzyskując dostęp do elementów kolekcji według pozycji indeksu. Indeks elementów zaczyna się od 0 i kończą się na liczbie elementów pomniejszonej o 1.

Poniższy przykład wykonuje iterację elementów kolekcji przy użyciu `for` zamiast `foreach` .

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

Poniższy przykład usuwa element z kolekcji przez określenie obiektu do usunięcia.

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

Poniższy przykład usuwa elementy z listy ogólnej. Zamiast `foreach` instrukcji, instrukcja [for](../../language-reference/keywords/for.md) , która wykonuje iterację w kolejności malejącej, jest używana. Wynika to z faktu, że <xref:System.Collections.Generic.List%601.RemoveAt%2A> Metoda powoduje, że elementy po usuniętym elemencie mają niższą wartość indeksu.

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

Dla typu elementów w <xref:System.Collections.Generic.List%601> , można również zdefiniować własną klasę. W poniższym przykładzie `Galaxy` Klasa, która jest używana przez program, <xref:System.Collections.Generic.List%601> jest zdefiniowana w kodzie.

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

.NET Framework udostępnia wiele popularnych kolekcji. Każdy typ kolekcji jest przeznaczony do określonego celu.

Niektóre popularne klasy kolekcji zostały opisane w tej sekcji:

- <xref:System.Collections.Generic>, klasy

- <xref:System.Collections.Concurrent>, klasy

- <xref:System.Collections>, klasy

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a>Klasy System. Collections. Generic

Można utworzyć ogólną kolekcję przy użyciu jednej z klas w <xref:System.Collections.Generic> przestrzeni nazw. Kolekcja ogólna jest przydatna, gdy każdy element w kolekcji ma ten sam typ danych. Ogólna kolekcja wymusza silne wpisywanie przez umożliwienie dodania tylko żądanego typu danych.

W poniższej tabeli wymieniono niektóre często używane klasy <xref:System.Collections.Generic?displayProperty=nameWithType> obszaru nazw:

|Klasa|Opis|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|Reprezentuje kolekcję par klucz/wartość, które są zorganizowane na podstawie klucza.|
|<xref:System.Collections.Generic.List%601>|Reprezentuje listę obiektów, do których można uzyskać dostęp za pomocą indeksu. Zapewnia metody wyszukiwania, sortowania i modyfikowania list.|
|<xref:System.Collections.Generic.Queue%601>|Przedstawia kolekcję obiektów First In, First Out (FIFO).|
|<xref:System.Collections.Generic.SortedList%602>|Reprezentuje kolekcję par klucz/wartość, które są posortowane według klucza w oparciu o skojarzoną <xref:System.Collections.Generic.IComparer%601> implementację.|
|<xref:System.Collections.Generic.Stack%601>|Przedstawia kolekcję obiektów w ostatniej pierwszej, wychodzącej (LIFO).|

Aby uzyskać dodatkowe informacje, zobacz [często używane typy kolekcji](../../../standard/collections/commonly-used-collection-types.md), [wybór klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)i <xref:System.Collections.Generic> .

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a>Klasy System. Collections. współbieżne

W .NET Framework 4 lub nowszej kolekcje w <xref:System.Collections.Concurrent> przestrzeni nazw zapewniają wydajne, bezpieczne dla wątków operacje umożliwiające dostęp do elementów kolekcji z wielu wątków.

Klasy w <xref:System.Collections.Concurrent> przestrzeni nazw powinny być używane zamiast odpowiednich typów w <xref:System.Collections.Generic?displayProperty=nameWithType> <xref:System.Collections?displayProperty=nameWithType> przestrzeniach nazw i za każdym razem, gdy wiele wątków uzyskuje dostęp do kolekcji współbieżnie. Aby uzyskać więcej informacji, zobacz [kolekcje bezpieczne dla wątków](../../../standard/collections/thread-safe/index.md) i <xref:System.Collections.Concurrent> .

Niektóre klasy zawarte w <xref:System.Collections.Concurrent> przestrzeni nazw to <xref:System.Collections.Concurrent.BlockingCollection%601> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602> , <xref:System.Collections.Concurrent.ConcurrentQueue%601> , i <xref:System.Collections.Concurrent.ConcurrentStack%601> .

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a>Klasy System. Collections

Klasy w <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw nie przechowują elementów jako obiektów o określonych typach, ale jako obiektów typu `Object` .

Jeśli to możliwe, należy używać kolekcji ogólnych w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw lub <xref:System.Collections.Concurrent> przestrzeni nazw zamiast starszych typów w `System.Collections` przestrzeni nazw.

W poniższej tabeli przedstawiono niektóre z najczęściej używanych klas w `System.Collections` przestrzeni nazw:

|Klasa|Opis|
|---|---|
|<xref:System.Collections.ArrayList>|Reprezentuje tablicę obiektów, których rozmiar jest dynamicznie zwiększany w miarę potrzeb.|
|<xref:System.Collections.Hashtable>|Reprezentuje kolekcję par klucz/wartość, które są zorganizowane na podstawie kodu skrótu klucza.|
|<xref:System.Collections.Queue>|Przedstawia kolekcję obiektów First In, First Out (FIFO).|
|<xref:System.Collections.Stack>|Przedstawia kolekcję obiektów w ostatniej pierwszej, wychodzącej (LIFO).|

<xref:System.Collections.Specialized>Przestrzeń nazw udostępnia wyspecjalizowane i silnie typy kolekcji klas, takich jak kolekcje tylko do ciągów i powiązane z listą oraz słowniki hybrydowe.

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementowanie kolekcji par klucz/wartość

<xref:System.Collections.Generic.Dictionary%602>Kolekcja ogólna umożliwia dostęp do elementów w kolekcji za pomocą klucza każdego elementu. Każde dodanie do słownika składa się z wartości i skojarzonego z nim klucza. Pobieranie wartości przy użyciu jej klucza jest szybkie, ponieważ `Dictionary` Klasa jest zaimplementowana jako tablica skrótów.

Poniższy przykład tworzy `Dictionary` kolekcję i wykonuje iterację w słowniku przy użyciu `foreach` instrukcji.

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

Aby zamiast tego użyć inicjatora kolekcji do skompilowania `Dictionary` kolekcji, można zamienić `BuildDictionary` `AddToDictionary` metody i przy użyciu następującej metody.

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

W poniższym przykładzie zastosowano <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metodę i <xref:System.Collections.Generic.Dictionary%602.Item%2A> Właściwość, `Dictionary` Aby szybko znaleźć element według klucza. `Item`Właściwość umożliwia dostęp do elementu w `elements` kolekcji przy użyciu `elements[symbol]` języka C#.

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

Poniższy przykład używa <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody szybkie znajdowanie elementu według klucza.

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

## <a name="using-linq-to-access-a-collection"></a>Używanie LINQ do uzyskiwania dostępu do kolekcji

LINQ (zapytanie zintegrowane z językiem) może służyć do uzyskiwania dostępu do kolekcji. Zapytania LINQ zapewniają możliwości filtrowania, porządkowania i grupowania. Aby uzyskać więcej informacji, zobacz [wprowadzenie z LINQ w języku C#](linq/index.md).

Poniższy przykład wykonuje zapytanie LINQ względem ogólnego `List` . Zapytanie LINQ zwraca inną kolekcję, która zawiera wyniki.

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

Poniższy przykład ilustruje procedurę sortowania kolekcji. Przykład sortuje wystąpienia `Car` klasy, które są przechowywane w <xref:System.Collections.Generic.List%601> . `Car`Klasa implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> Metoda została zaimplementowana.

Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metody wykonuje pojedyncze porównanie, które jest używane do sortowania. Kod pisany przez użytkownika w `CompareTo` metodzie zwraca wartość dla każdego porównania bieżącego obiektu z innym obiektem. Zwracana wartość jest mniejsza niż zero, jeśli bieżący obiekt jest mniejszy niż inny obiekt, większy niż zero, jeśli bieżący obiekt jest większy niż inny obiekt, i zero, jeśli są równe. Dzięki temu można zdefiniować w kodzie kryteria dla wartości większej niż, mniejszej niż i równej.

W `ListCars` metodzie `cars.Sort()` instrukcja sortuje listę. To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje `CompareTo` automatyczne wywoływanie metody dla `Car` obiektów w obiekcie `List` .

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

Kolekcję można zdefiniować przez implementację <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerable> interfejsu lub.

Chociaż można zdefiniować kolekcję niestandardową, zazwyczaj lepiej jest używać kolekcji, które znajdują się w .NET Framework, które są opisane w [typach kolekcji](#BKMK_KindsOfCollections) wcześniej w tym temacie.

W poniższym przykładzie zdefiniowano klasę kolekcji niestandardowej o nazwie `AllColors` . Ta klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> Metoda została zaimplementowana.

`GetEnumerator`Metoda zwraca wystąpienie `ColorEnumerator` klasy. `ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> interfejs, który wymaga <xref:System.Collections.IEnumerator.Current%2A> <xref:System.Collections.IEnumerator.MoveNext%2A> zaimplementowania właściwości, metody i <xref:System.Collections.IEnumerator.Reset%2A> metody.

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

*Iterator* jest używany do wykonywania niestandardowej iteracji w kolekcji. Iterator może być metodą lub `get` akcesorem. Iterator używa instrukcji [yield return](../../language-reference/keywords/yield.md) , aby zwrócić każdy element kolekcji pojedynczo.

Należy wywołać iterator przy użyciu instrukcji [foreach](../../language-reference/keywords/foreach-in.md) . Każda iteracja `foreach` pętli wywołuje iterator. Po `yield return` osiągnięciu instrukcji w iteratorze zwracane jest wyrażenie, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu iteratora.

Aby uzyskać więcej informacji, zobacz [Iteratory (C#)](./iterators.md).

W poniższym przykładzie zastosowano metodę iteratora. Metoda iteratora zawiera `yield return` instrukcję, która znajduje się wewnątrz pętli [for](../../language-reference/keywords/for.md) . W `ListEvenNumbers` metodzie każda iteracja `foreach` treści instrukcji tworzy wywołanie metody iteratora, która przechodzi do następnej `yield return` instrukcji.

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

## <a name="see-also"></a>Zobacz także

- [Inicjatory obiektów i kolekcji](../classes-and-structs/object-and-collection-initializers.md)
- [Koncepcje programowania (C#)](./index.md)
- [Option Strict — Instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [LINQ to Objects (C#)](./linq/linq-to-objects.md)
- [Równoległe LINQ (PLINQ)](../../../standard/parallel-programming/introduction-to-plinq.md)
- [Kolekcje i struktury danych](../../../standard/collections/index.md)
- [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)
- [Porównania i sortowania w kolekcjach](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [Kiedy należy używać kolekcji ogólnych](../../../standard/collections/when-to-use-generic-collections.md)
