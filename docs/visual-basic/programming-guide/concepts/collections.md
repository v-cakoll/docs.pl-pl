---
title: Kolekcje
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: d27761ba7a955d1dc8843ad168a82a9c9c27a6f6
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202446"
---
# <a name="collections-visual-basic"></a>Kolekcje (Visual Basic)

W przypadku wielu aplikacji, należy utworzyć grupy powiązanych obiektów i zarządzać nimi. Istnieją dwa sposoby grupowania obiektów: przez tworzenie tablic obiektów i tworzenie kolekcji obiektów.

Tablice są najbardziej przydatne do tworzenia i pracy ze stałą liczbą obiektów silnie wpisanych. Aby uzyskać informacje na temat tablic, zobacz [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).

Kolekcje zapewniają bardziej elastyczny sposób pracy z grupami obiektów. W przeciwieństwie do tablic, Grupa obiektów, z którymi pracujesz, może być zwiększana i zmniejszana dynamicznie w miarę potrzeby zmiany aplikacji. W przypadku niektórych kolekcji można przypisać klucz do dowolnego obiektu, który został umieszczony w kolekcji, dzięki czemu można szybko pobrać obiekt przy użyciu klucza.

Kolekcja jest klasą, więc należy zadeklarować wystąpienie klasy, aby można było dodać elementy do tej kolekcji.

Jeśli kolekcja zawiera elementy tylko jednego typu danych, można użyć jednej z klas w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw. Ogólna kolekcja wymusza bezpieczeństwo typu, tak aby nie można było dodać do niego żadnego innego typu danych. Po pobraniu elementu z kolekcji ogólnej nie trzeba określać jego typu danych ani go przekonwertować.

> [!NOTE]
> Przykłady w tym temacie zawierają instrukcje [Importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla `System.Collections.Generic` i `System.Linq` przestrzeni nazw.

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a>Korzystanie z prostej kolekcji

W przykładach w tej sekcji użyto klasy generycznej <xref:System.Collections.Generic.List%601> , która pozwala na współpracę z silnie wpisaną listą obiektów.

Poniższy przykład tworzy listę ciągów, a następnie wykonuje iterację przez ciągi przy użyciu [for each... Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) — instrukcja.

```vb
' Create a list of strings.
Dim salmons As New List(Of String)
salmons.Add("chinook")
salmons.Add("coho")
salmons.Add("pink")
salmons.Add("sockeye")

' Iterate through the list.
For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook coho pink sockeye
```

Jeśli zawartość kolekcji jest znana z wyprzedzeniem, można użyć *inicjatora kolekcji* w celu zainicjowania kolekcji. Aby uzyskać więcej informacji, zobacz [Inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

Poniższy przykład jest taki sam jak w poprzednim przykładzie, z wyjątkiem tego, że inicjator kolekcji jest używany do dodawania elementów do kolekcji.

```vb
' Create a list of strings by using a
' collection initializer.
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook coho pink sockeye
```

Możesz użyć [dla... Następna](../../../visual-basic/language-reference/statements/for-next-statement.md) Instrukcja zamiast instrukcji, `For Each` Aby wykonać iterację w kolekcji. Można to osiągnąć, uzyskując dostęp do elementów kolekcji według pozycji indeksu. Indeks elementów zaczyna się od 0 i kończą się na liczbie elementów pomniejszonej o 1.

Poniższy przykład wykonuje iterację elementów kolekcji przy użyciu `For…Next` zamiast `For Each` .

```vb
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For index = 0 To salmons.Count - 1
    Console.Write(salmons(index) & " ")
Next
'Output: chinook coho pink sockeye
```

Poniższy przykład usuwa element z kolekcji przez określenie obiektu do usunięcia.

```vb
' Create a list of strings by using a
' collection initializer.
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

' Remove an element in the list by specifying
' the object.
salmons.Remove("coho")

For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook pink sockeye
```

Poniższy przykład usuwa elementy z listy ogólnej. Zamiast `For Each` instrukcji, [dla... ](../../../visual-basic/language-reference/statements/for-next-statement.md)Używana jest następna instrukcja, która wykonuje iterację w kolejności malejącej. Wynika to z faktu, że <xref:System.Collections.Generic.List%601.RemoveAt%2A> Metoda powoduje, że elementy po usuniętym elemencie mają niższą wartość indeksu.

```vb
Dim numbers As New List(Of Integer) From
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}

' Remove odd numbers.
For index As Integer = numbers.Count - 1 To 0 Step -1
    If numbers(index) Mod 2 = 1 Then
        ' Remove the element by specifying
        ' the zero-based index in the list.
        numbers.RemoveAt(index)
    End If
Next

' Iterate through the list.
' A lambda expression is placed in the ForEach method
' of the List(T) object.
numbers.ForEach(
    Sub(number) Console.Write(number & " "))
' Output: 0 2 4 6 8
```

Dla typu elementów w <xref:System.Collections.Generic.List%601> , można również zdefiniować własną klasę. W poniższym przykładzie `Galaxy` Klasa, która jest używana przez program, <xref:System.Collections.Generic.List%601> jest zdefiniowana w kodzie.

```vb
Private Sub IterateThroughList()
    Dim theGalaxies As New List(Of Galaxy) From
        {
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}
        }

    For Each theGalaxy In theGalaxies
        With theGalaxy
            Console.WriteLine(.Name & "  " & .MegaLightYears)
        End With
    Next

    ' Output:
    '  Tadpole  400
    '  Pinwheel  25
    '  Milky Way  0
    '  Andromeda  3
End Sub

Public Class Galaxy
    Public Property Name As String
    Public Property MegaLightYears As Integer
End Class
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a>Rodzaje kolekcji

.NET Framework udostępnia wiele popularnych kolekcji. Każdy typ kolekcji jest przeznaczony do określonego celu.

Niektóre popularne klasy kolekcji zostały opisane w tej sekcji:

- <xref:System.Collections.Generic>, klasy

- <xref:System.Collections.Concurrent>, klasy

- <xref:System.Collections>, klasy

- `Collection`Klasa Visual Basic

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

Aby uzyskać dodatkowe informacje, zobacz [często używane typy kolekcji](../../../standard/collections/commonly-used-collection-types.md), [wybór klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)i <xref:System.Collections.Generic?displayProperty=nameWithType> .

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

<a name="BKMK_VisualBasic"></a>

### <a name="visual-basic-collection-class"></a>Klasa kolekcji Visual Basic

Można użyć klasy Visual Basic, <xref:Microsoft.VisualBasic.Collection> Aby uzyskać dostęp do elementu kolekcji przy użyciu indeksu liczbowego lub `String` klucza. Można dodawać elementy do obiektu kolekcji z lub bez określenia klucza. W przypadku dodania elementu bez klucza należy użyć jego indeksu liczbowego, aby uzyskać do niego dostęp.

Klasa Visual Basic `Collection` przechowuje wszystkie jej elementy jako typ `Object` , więc można dodać element dowolnego typu danych. Nie ma zabezpieczeń przed dodawaniem nieprawidłowych typów danych.

W przypadku używania klasy Visual Basic `Collection` pierwszy element w kolekcji ma indeks 1. Różni się to od klas kolekcji .NET Framework, dla których indeks początkowy to 0.

Jeśli to możliwe, należy używać kolekcji ogólnych w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw lub <xref:System.Collections.Concurrent> przestrzeni nazw zamiast `Collection` klasy Visual Basic.

Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Collection>.

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementowanie kolekcji par klucz/wartość

<xref:System.Collections.Generic.Dictionary%602>Kolekcja ogólna umożliwia dostęp do elementów w kolekcji za pomocą klucza każdego elementu. Każde dodanie do słownika składa się z wartości i skojarzonego z nim klucza. Pobieranie wartości przy użyciu jej klucza jest szybkie, ponieważ `Dictionary` Klasa jest zaimplementowana jako tablica skrótów.

Poniższy przykład tworzy `Dictionary` kolekcję i wykonuje iterację w słowniku przy użyciu `For Each` instrukcji.

```vb
Private Sub IterateThroughDictionary()
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    For Each kvp As KeyValuePair(Of String, Element) In elements
        Dim theElement As Element = kvp.Value

        Console.WriteLine("key: " & kvp.Key)
        With theElement
            Console.WriteLine("values: " & .Symbol & " " &
                .Name & " " & .AtomicNumber)
        End With
    Next
End Sub

Private Function BuildDictionary() As Dictionary(Of String, Element)
    Dim elements As New Dictionary(Of String, Element)

    AddToDictionary(elements, "K", "Potassium", 19)
    AddToDictionary(elements, "Ca", "Calcium", 20)
    AddToDictionary(elements, "Sc", "Scandium", 21)
    AddToDictionary(elements, "Ti", "Titanium", 22)

    Return elements
End Function

Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)
    Dim theElement As New Element

    theElement.Symbol = symbol
    theElement.Name = name
    theElement.AtomicNumber = atomicNumber

    elements.Add(Key:=theElement.Symbol, value:=theElement)
End Sub

Public Class Element
    Public Property Symbol As String
    Public Property Name As String
    Public Property AtomicNumber As Integer
End Class
```

Aby zamiast tego użyć inicjatora kolekcji do skompilowania `Dictionary` kolekcji, można zamienić `BuildDictionary` `AddToDictionary` metody i przy użyciu następującej metody.

```vb
Private Function BuildDictionary2() As Dictionary(Of String, Element)
    Return New Dictionary(Of String, Element) From
        {
            {"K", New Element With
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},
            {"Ca", New Element With
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},
            {"Sc", New Element With
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},
            {"Ti", New Element With
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}
        }
End Function
```

W poniższym przykładzie zastosowano <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metodę i <xref:System.Collections.Generic.Dictionary%602.Item%2A> Właściwość, `Dictionary` Aby szybko znaleźć element według klucza. `Item`Właściwość umożliwia dostęp do elementu w `elements` kolekcji przy użyciu `elements(symbol)` kodu w Visual Basic.

```vb
Private Sub FindInDictionary(ByVal symbol As String)
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    If elements.ContainsKey(symbol) = False Then
        Console.WriteLine(symbol & " not found")
    Else
        Dim theElement = elements(symbol)
        Console.WriteLine("found: " & theElement.Name)
    End If
End Sub
```

Poniższy przykład używa <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody szybkie znajdowanie elementu według klucza.

```vb
Private Sub FindInDictionary2(ByVal symbol As String)
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    Dim theElement As Element = Nothing
    If elements.TryGetValue(symbol, theElement) = False Then
        Console.WriteLine(symbol & " not found")
    Else
        Console.WriteLine("found: " & theElement.Name)
    End If
End Sub
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a>Używanie LINQ do uzyskiwania dostępu do kolekcji

LINQ (zapytanie zintegrowane z językiem) może służyć do uzyskiwania dostępu do kolekcji. Zapytania LINQ zapewniają możliwości filtrowania, porządkowania i grupowania. Aby uzyskać więcej informacji, zobacz [wprowadzenie z LINQ w Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).

Poniższy przykład wykonuje zapytanie LINQ względem ogólnego `List` . Zapytanie LINQ zwraca inną kolekcję, która zawiera wyniki.

```vb
Private Sub ShowLINQ()
    Dim elements As List(Of Element) = BuildList()

    ' LINQ Query.
    Dim subset = From theElement In elements
                  Where theElement.AtomicNumber < 22
                  Order By theElement.Name

    For Each theElement In subset
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)
    Next

    ' Output:
    '  Calcium 20
    '  Potassium 19
    '  Scandium 21
End Sub

Private Function BuildList() As List(Of Element)
    Return New List(Of Element) From
        {
            {New Element With
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},
            {New Element With
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},
            {New Element With
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},
            {New Element With
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}
        }
End Function

Public Class Element
    Public Property Symbol As String
    Public Property Name As String
    Public Property AtomicNumber As Integer
End Class
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a>Sortowanie kolekcji

Poniższy przykład ilustruje procedurę sortowania kolekcji. Przykład sortuje wystąpienia `Car` klasy, które są przechowywane w <xref:System.Collections.Generic.List%601> . `Car`Klasa implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> Metoda została zaimplementowana.

Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metody wykonuje pojedyncze porównanie, które jest używane do sortowania. Kod pisany przez użytkownika w `CompareTo` metodzie zwraca wartość dla każdego porównania bieżącego obiektu z innym obiektem. Zwracana wartość jest mniejsza niż zero, jeśli bieżący obiekt jest mniejszy niż inny obiekt, większy niż zero, jeśli bieżący obiekt jest większy niż inny obiekt, i zero, jeśli są równe. Dzięki temu można zdefiniować w kodzie kryteria dla wartości większej niż, mniejszej niż i równej.

W `ListCars` metodzie `cars.Sort()` instrukcja sortuje listę. To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje `CompareTo` automatyczne wywoływanie metody dla `Car` obiektów w obiekcie `List` .

```vb
Public Sub ListCars()

    ' Create some new cars.
    Dim cars As New List(Of Car) From
    {
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}
    }

    ' Sort the cars by color alphabetically, and then by speed
    ' in descending order.
    cars.Sort()

    ' View all of the cars.
    For Each thisCar As Car In cars
        Console.Write(thisCar.Color.PadRight(5) & " ")
        Console.Write(thisCar.Speed.ToString & " ")
        Console.Write(thisCar.Name)
        Console.WriteLine()
    Next

    ' Output:
    '  blue  50 car4
    '  blue  30 car5
    '  blue  20 car1
    '  green 50 car7
    '  green 10 car3
    '  red   60 car6
    '  red   50 car2
End Sub

Public Class Car
    Implements IComparable(Of Car)

    Public Property Name As String
    Public Property Speed As Integer
    Public Property Color As String

    Public Function CompareTo(ByVal other As Car) As Integer _
        Implements System.IComparable(Of Car).CompareTo
        ' A call to this method makes a single comparison that is
        ' used for sorting.

        ' Determine the relative order of the objects being compared.
        ' Sort by color alphabetically, and then by speed in
        ' descending order.

        ' Compare the colors.
        Dim compare As Integer
        compare = String.Compare(Me.Color, other.Color, True)

        ' If the colors are the same, compare the speeds.
        If compare = 0 Then
            compare = Me.Speed.CompareTo(other.Speed)

            ' Use descending order for speed.
            compare = -compare
        End If

        Return compare
    End Function
End Class
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a>Definiowanie kolekcji niestandardowej

Kolekcję można zdefiniować przez implementację <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerable> interfejsu lub. Aby uzyskać dodatkowe informacje, zobacz [Wyliczanie kolekcji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).

Chociaż można zdefiniować kolekcję niestandardową, zazwyczaj lepiej jest używać kolekcji, które znajdują się w .NET Framework, które są opisane w [typach kolekcji](#kinds-of-collections) wcześniej w tym temacie.

W poniższym przykładzie zdefiniowano klasę kolekcji niestandardowej o nazwie `AllColors` . Ta klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> Metoda została zaimplementowana.

`GetEnumerator`Metoda zwraca wystąpienie `ColorEnumerator` klasy. `ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> interfejs, który wymaga <xref:System.Collections.IEnumerator.Current%2A> <xref:System.Collections.IEnumerator.MoveNext%2A> zaimplementowania właściwości, metody i <xref:System.Collections.IEnumerator.Reset%2A> metody.

```vb
Public Sub ListColors()
    Dim colors As New AllColors()

    For Each theColor As Color In colors
        Console.Write(theColor.Name & " ")
    Next
    Console.WriteLine()
    ' Output: red blue green
End Sub

' Collection class.
Public Class AllColors
    Implements System.Collections.IEnumerable

    Private _colors() As Color =
    {
        New Color With {.Name = "red"},
        New Color With {.Name = "blue"},
        New Color With {.Name = "green"}
    }

    Public Function GetEnumerator() As System.Collections.IEnumerator _
        Implements System.Collections.IEnumerable.GetEnumerator

        Return New ColorEnumerator(_colors)

        ' Instead of creating a custom enumerator, you could
        ' use the GetEnumerator of the array.
        'Return _colors.GetEnumerator
    End Function

    ' Custom enumerator.
    Private Class ColorEnumerator
        Implements System.Collections.IEnumerator

        Private _colors() As Color
        Private _position As Integer = -1

        Public Sub New(ByVal colors() As Color)
            _colors = colors
        End Sub

        Public ReadOnly Property Current() As Object _
            Implements System.Collections.IEnumerator.Current
            Get
                Return _colors(_position)
            End Get
        End Property

        Public Function MoveNext() As Boolean _
            Implements System.Collections.IEnumerator.MoveNext
            _position += 1
            Return (_position < _colors.Length)
        End Function

        Public Sub Reset() Implements System.Collections.IEnumerator.Reset
            _position = -1
        End Sub
    End Class
End Class

' Element class.
Public Class Color
    Public Property Name As String
End Class
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a>Iteratory

*Iterator* jest używany do wykonywania niestandardowej iteracji w kolekcji. Iterator może być metodą lub `get` akcesorem. Iterator używa instrukcji [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) do zwrócenia każdego elementu kolekcji pojedynczo.

Należy wywołać iterator przy użyciu [for each... Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) — instrukcja. Każda iteracja `For Each` pętli wywołuje iterator. Po `Yield` osiągnięciu instrukcji w iteratorze zwracane jest wyrażenie, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu iteratora.

Aby uzyskać więcej informacji, zobacz [Iteratory (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).

W poniższym przykładzie zastosowano metodę iteratora. Metoda iteratora zawiera `Yield` instrukcję, która znajduje się wewnątrz elementu [... Następna](../../../visual-basic/language-reference/statements/for-next-statement.md) pętla. W `ListEvenNumbers` metodzie każda iteracja `For Each` treści instrukcji tworzy wywołanie metody iteratora, która przechodzi do następnej `Yield` instrukcji.

```vb
Public Sub ListEvenNumbers()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    Console.WriteLine()
    ' Output: 6 8 10 12 14 16 18
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As IEnumerable(Of Integer)

' Yield even numbers in the range.
    For number = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="see-also"></a>Zobacz także

- [Inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Koncepcje programowania (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)
- [Option Strict — Instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [Równoległe LINQ (PLINQ)](../../../standard/parallel-programming/introduction-to-plinq.md)
- [Kolekcje i struktury danych](../../../standard/collections/index.md)
- [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)
- [Porównania i sortowania w kolekcjach](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [Kiedy należy używać kolekcji ogólnych](../../../standard/collections/when-to-use-generic-collections.md)
