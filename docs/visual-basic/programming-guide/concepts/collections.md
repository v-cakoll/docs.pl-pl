---
title: Kolekcje
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: ba16d04e781bcf69356b1f603d92e104816a0860
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400828"
---
# <a name="collections-visual-basic"></a>Kolekcje (Visual Basic)

W przypadku wielu aplikacji należy utworzyć grupy powiązanych obiektów i zarządzać nimi. Istnieją dwa sposoby grupowania obiektów: przez tworzenie tablic obiektów i tworzenie kolekcji obiektów.

Tablice są najbardziej przydatne do tworzenia i pracy ze stałą liczbą silnie typizowanych obiektów. Aby uzyskać informacje o tablicach, zobacz [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).

Kolekcje zapewniają bardziej elastyczny sposób pracy z grupami obiektów. W przeciwieństwie do tablic, grupa obiektów, z którymi pracujesz, może dynamicznie rosnąć i zmniejszać się wraz ze zmianą potrzeb aplikacji. W przypadku niektórych kolekcji można przypisać klucz do dowolnego obiektu, który można umieścić w kolekcji, dzięki czemu można szybko pobrać obiekt przy użyciu klucza.

Kolekcja jest klasą, więc należy zadeklarować wystąpienie klasy, zanim będzie można dodać elementy do tej kolekcji.

Jeśli kolekcja zawiera elementy tylko jednego typu danych, można użyć <xref:System.Collections.Generic?displayProperty=nameWithType> jednej z klas w obszarze nazw. Kolekcja ogólna wymusza bezpieczeństwo typu, dzięki czemu nie można dodawać do niej żadnego innego typu danych. Podczas pobierania elementu z kolekcji ogólnej, nie trzeba określać jego typ danych lub przekonwertować go.

> [!NOTE]
> W przykładach w tym temacie dołącz [imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrukcji dla `System.Collections.Generic` i `System.Linq` obszarów nazw.

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a>Korzystanie z prostej kolekcji

Przykłady w tej sekcji <xref:System.Collections.Generic.List%601> używają klasy ogólnej, która umożliwia pracę z silnie typizowanymi listami obiektów.

Poniższy przykład tworzy listę ciągów, a następnie iteruje za pośrednictwem ciągów przy użyciu [For Each... Następna](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrukcja.

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

Jeśli zawartość kolekcji są znane z wyprzedzeniem, można użyć *inicjatora kolekcji,* aby zainicjować kolekcję. Aby uzyskać więcej informacji, zobacz [Inicjalizatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

Poniższy przykład jest taki sam jak w poprzednim przykładzie, z wyjątkiem inicjatora kolekcji jest używany do dodawania elementów do kolekcji.

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

Można użyć [For... Następna](../../../visual-basic/language-reference/statements/for-next-statement.md) instrukcja `For Each` zamiast instrukcji do iteracji za pośrednictwem kolekcji. Można to osiągnąć, uzyskując dostęp do elementów kolekcji przez położenie indeksu. Indeks elementów rozpoczyna się od 0 i kończy się na liczbie elementów minus 1.

Poniższy przykład iteruje za pośrednictwem elementów kolekcji przy użyciu `For…Next` zamiast . `For Each`

```vb
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For index = 0 To salmons.Count - 1
    Console.Write(salmons(index) & " ")
Next
'Output: chinook coho pink sockeye
```

Poniższy przykład usuwa element z kolekcji, określając obiekt do usunięcia.

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

Poniższy przykład usuwa elementy z listy rodzajowej. Zamiast oświadczenia, `For Each` [For... Następna](../../../visual-basic/language-reference/statements/for-next-statement.md) instrukcja, która iteruje w kolejności malejącej jest używany. Jest tak, <xref:System.Collections.Generic.List%601.RemoveAt%2A> ponieważ metoda powoduje, że elementy po usunięty element mają niższą wartość indeksu.

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

Dla typu elementów <xref:System.Collections.Generic.List%601>w programie można również zdefiniować własną klasę. W poniższym przykładzie `Galaxy` klasa, która <xref:System.Collections.Generic.List%601> jest używana przez jest zdefiniowana w kodzie.

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

Wiele typowych kolekcji są dostarczane przez .NET Framework. Każdy rodzaj kolekcji jest przeznaczony do określonego celu.

Niektóre typowe klasy kolekcji są opisane w tej sekcji:

- <xref:System.Collections.Generic>, klasy

- <xref:System.Collections.Concurrent>, klasy

- <xref:System.Collections>, klasy

- Klasa `Collection` Visual Basic

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

Aby uzyskać dodatkowe informacje, zobacz [Typy często używanych kolekcji](../../../standard/collections/commonly-used-collection-types.md), [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)i <xref:System.Collections.Generic?displayProperty=nameWithType>.

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

<a name="BKMK_VisualBasic"></a>

### <a name="visual-basic-collection-class"></a>Klasa kolekcji Visual Basic

Klasy Visual Basic <xref:Microsoft.VisualBasic.Collection> można użyć, aby uzyskać dostęp do elementu kolekcji przy użyciu indeksu numerycznego lub klucza. `String` Elementy można dodawać do obiektu kolekcji z lub bez określania klucza. Jeśli dodasz element bez klucza, należy użyć jego indeksu numerycznego, aby uzyskać do niego dostęp.

Klasa Visual `Collection` Basic przechowuje wszystkie `Object`jej elementy jako typ, dzięki czemu można dodać element dowolnego typu danych. Nie ma żadnego zabezpieczenia przed dodaniem nieodpowiednich typów danych.

Podczas korzystania z `Collection` klasy Visual Basic, pierwszy element w kolekcji ma indeks 1. Różni się to od klas kolekcji .NET Framework, dla których indeks początkowy wynosi 0.

Jeśli to możliwe, należy użyć kolekcji <xref:System.Collections.Generic?displayProperty=nameWithType> ogólnych w <xref:System.Collections.Concurrent> obszarze nazw lub przestrzeni `Collection` nazw zamiast klasy Visual Basic.

Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Collection>.

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementowanie kolekcji par kluczy/wartości

Kolekcja <xref:System.Collections.Generic.Dictionary%602> ogólna umożliwia dostęp do elementów w kolekcji przy użyciu klucza każdego elementu. Każdy dodatek do słownika składa się z wartości i skojarzonego z nim klucza. Pobieranie wartości przy użyciu jego klucz `Dictionary` jest szybki, ponieważ klasa jest implementowana jako tabela mieszania.

Poniższy przykład `Dictionary` tworzy kolekcję i iteruje za `For Each` pośrednictwem słownika przy użyciu instrukcji.

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

Zamiast tego zamiast tego użyj inicjatora kolekcji do tworzenia `Dictionary` kolekcji, można zastąpić `BuildDictionary` i `AddToDictionary` metody z następującą metodą.

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

W poniższym przykładzie <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> użyto metody i <xref:System.Collections.Generic.Dictionary%602.Item%2A> `Dictionary` właściwości, aby szybko znaleźć element według klucza. Właściwość `Item` umożliwia dostęp do elementu `elements` w kolekcji przy użyciu `elements(symbol)` kodu w języku Visual Basic.

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

W poniższym <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> przykładzie zamiast tego używa metody szybko znaleźć element po kluczu.

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

## <a name="using-linq-to-access-a-collection"></a>Korzystanie z linq w celu uzyskania dostępu do kolekcji

LINQ (Zapytanie zintegrowane z językiem) może służyć do uzyskiwania dostępu do kolekcji. Zapytania LINQ zapewniają możliwości filtrowania, zamawiania i grupowania. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do linq w języku Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).

W poniższym przykładzie uruchamia kwerendę LINQ względem ogólnego `List`. Kwerenda LINQ zwraca inną kolekcję, która zawiera wyniki.

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

Poniższy przykład ilustruje procedurę sortowania kolekcji. Przykład sortuje wystąpienia `Car` klasy, które są <xref:System.Collections.Generic.List%601>przechowywane w . Klasa `Car` implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> metoda została zaimplementowana.

Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metody sprawia, że pojedyncze porównanie, który jest używany do sortowania. Kod napisany przez użytkownika `CompareTo` w metodzie zwraca wartość dla każdego porównania bieżącego obiektu z innym obiektem. Zwracana wartość jest mniejsza niż zero, jeśli bieżący obiekt jest mniejszy niż inny obiekt, większa od zera, jeśli bieżący obiekt jest większa od innego obiektu, i zero, jeśli są równe. Dzięki temu można zdefiniować w kodzie kryteria dla większych niż, mniej niż i równe.

W `ListCars` metodzie `cars.Sort()` instrukcji sortuje listę. To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje, `CompareTo` że metoda ma być `Car` wywoływana `List`automatycznie dla obiektów w .

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

Kolekcję można zdefiniować, <xref:System.Collections.Generic.IEnumerable%601> implementując lub <xref:System.Collections.IEnumerable> interfejs. Aby uzyskać dodatkowe informacje, zobacz [Wyliczanie kolekcji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).

Chociaż można zdefiniować kolekcji niestandardowej, zwykle lepiej jest zamiast tego użyć kolekcji, które są zawarte w .NET Framework, które są opisane w [Rodzaje kolekcji](#kinds-of-collections) wcześniej w tym temacie.

Poniższy przykład definiuje niestandardową `AllColors`klasę kolekcji o nazwie . Ta klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który <xref:System.Collections.IEnumerable.GetEnumerator%2A> wymaga, aby metoda została zaimplementowana.

Metoda `GetEnumerator` zwraca wystąpienie `ColorEnumerator` klasy. `ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> interfejs, który wymaga, <xref:System.Collections.IEnumerator.Current%2A> <xref:System.Collections.IEnumerator.MoveNext%2A> aby zaimplementowano właściwość, metodę i <xref:System.Collections.IEnumerator.Reset%2A> metodę.

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

*Iterator* jest używany do wykonywania iteracji niestandardowej nad kolekcją. Iterator może być metodą `get` lub akcesorem. Iterator używa [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrukcji do zwrócenia każdego elementu kolekcji po jednym naraz.

Wywołać iterator przy użyciu [For Each... Następna](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrukcja. Każda iteracja `For Each` pętli wywołuje iteratora. Po `Yield` osiągnięciu instrukcji w iteratorze zwracane jest wyrażenie, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest ponownie uruchamiane z tej lokalizacji przy następnym wywołanie iteratora.

Aby uzyskać więcej informacji, zobacz [Iteratory (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).

W poniższym przykładzie użyto metody iteratora. Metoda iteratora `Yield` ma instrukcję, która znajduje się wewnątrz [For... Następna](../../../visual-basic/language-reference/statements/for-next-statement.md) pętla. W `ListEvenNumbers` metodzie każda iteracja `For Each` treści instrukcji tworzy wywołanie metody iteratora, `Yield` która przechodzi do następnej instrukcji.

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

## <a name="see-also"></a>Zobacz też

- [Inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Pojęcia programistyczne (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)
- [Option Strict — Instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [LINQ do obiektów (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [Równoległe LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)
- [Kolekcje i struktury danych](../../../standard/collections/index.md)
- [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)
- [Porównywanie i sortowanie w kolekcjach](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [Kiedy należy używać kolekcji ogólnych](../../../standard/collections/when-to-use-generic-collections.md)
