---
title: Kolekcje (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: 60519de1f580bf1cfa4aa067d4a999b20ea8d54d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45685793"
---
# <a name="collections-visual-basic"></a>Kolekcje (Visual Basic)
W przypadku wielu aplikacji, dla których chcesz utworzyć grupy i zarządzać nimi powiązanych obiektów. Istnieją dwa sposoby grupowania obiektów: poprzez tworzenie tablic obiektów oraz poprzez tworzenie kolekcji obiektów.  
  
 Tablice są najbardziej przydatne do tworzenia i pracy ze stałą liczbą jednoznacznie silnych obiektów. Aby uzyskać informacje na temat tablic, zobacz [tablic](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Kolekcje zapewniają bardziej elastyczny sposób pracy z grupami obiektów. W odróżnieniu od tablic grupa obiektów, którymi pracujesz można zwiększyć lub zmniejszyć dynamicznie, potrzeb zmiany aplikacji. W niektórych kolekcjach można przypisać klawisz do dowolnych obiektów umieszczonych do kolekcji, tak aby pozwala na szybkie pobranie obiektu przy użyciu klucza.  
  
 Kolekcja jest klasą, więc należy zadeklarować wystąpienia klasy, aby można było dodać elementy do tej kolekcji.  
  
 Jeśli kolekcja zawiera elementy tylko jednego typu danych, możesz użyć jednej z klas w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw. Ogólna kolekcja wymusza typ bezpieczeństwa tak, aby żaden typ danych można dodać do niego. Po pobraniu elementu z kolekcji generycznej, nie trzeba określać jego typu danych, ani go konwertować.  
  
> [!NOTE]
>  W przykładach w tym temacie zawierają [Importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrukcji dla `System.Collections.Generic` i `System.Linq` przestrzeni nazw.  
  
 **W tym temacie**  
  
-   [Za pomocą prostej kolekcji](#BKMK_SimpleCollection)  
  
-   [Rodzaje kolekcji](#BKMK_KindsOfCollections)  
  
    -   [System.Collections.Generic Classes](#BKMK_Generic)  
  
    -   [Klasy System.Collections.Concurrent](#BKMK_Concurrent)  
  
    -   [Klasy System.Collections](#BKMK_Collections)  
  
    -   [Klasa kolekcji Visual Basic](#BKMK_VisualBasic)  
  
-   [Implementowanie kolekcji par klucz/wartość](#BKMK_KeyValuePairs)  
  
-   [Za pomocą LINQ do dostępu do kolekcji](#BKMK_LINQ)  
  
-   [Sortowanie kolekcji](#BKMK_Sorting)  
  
-   [Definiowanie kolekcji niestandardowej](#BKMK_CustomCollection)  
  
-   [Iteratory](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>Za pomocą prostej kolekcji  
 W przykładach w tej sekcji użyto ogólnego <xref:System.Collections.Generic.List%601> klasy, która umożliwia pracę z silnie typizowanej listy obiektów.  
  
 Poniższy przykład tworzy listę ciągów i następnie iterację przez ciągi przy użyciu [For Each... Następny](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrukcji.  
  
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
  
 Jeśli zawartość kolekcji jest znana z wyprzedzeniem, można użyć *inicjatora kolekcji* do zainicjowania dla kolekcji. Aby uzyskać więcej informacji, zobacz [inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
 Poniższy przykład jest taka sama, jak w poprzednim przykładzie, z wyjątkiem inicjatora kolekcji jest używana do dodawania elementów do kolekcji.  
  
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
  
 Możesz użyć [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) instrukcji zamiast `For Each` instrukcję do iterowania po kolekcji. Osiągniesz to uzyskując dostęp do elementów kolekcji przez pozycję indeksu. Indeks elementów zaczyna się od 0 i kończy się liczbą elementów pomniejszoną o 1.  
  
 Poniższy przykład wykonuje iterację przez elementy kolekcji za pomocą `For…Next` zamiast `For Each`.  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 Poniższy przykład usuwa element z kolekcji określając obiekt do usunięcia.  
  
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
  
 Poniższy przykład usuwa elementy z listy ogólnej. Zamiast `For Each` instrukcji [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) używana jest instrukcja, która dokonuje iteracji w kolejności malejącej. Jest to spowodowane <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda powoduje, że elementy po usuniętym elemencie muszą mieć niższą wartość indeksu.  
  
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
  
 Aby uzyskać typ elementów w <xref:System.Collections.Generic.List%601>, można również definiować własne klasy. W poniższym przykładzie `Galaxy` klasę, która jest używana przez <xref:System.Collections.Generic.List%601> jest zdefiniowana w kodzie.  
  
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
 Wiele typowych kolekcji jest dostarczanych przez program .NET Framework. Każdy typu kolekcji jest przeznaczony do określonego celu.  
  
 W tej sekcji opisano niektóre typowe klasy kolekcji:  
  
-   <xref:System.Collections.Generic> Klasy  
  
-   <xref:System.Collections.Concurrent> Klasy  
  
-   <xref:System.Collections> Klasy  
  
-   Visual Basic `Collection` klasy  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a>System.Collections.Generic Classes  

 Możesz utworzyć ogólną kolekcję używając jednej z klas w <xref:System.Collections.Generic> przestrzeni nazw. Ogólna kolekcja jest przydatna w przypadku, gdy każdy element w kolekcji ma ten sam typ danych. Ogólna kolekcja wymusza silne wpisywanie, zezwalając tylko na żądane dane typu ma zostać dodana.  
  
 W poniższej tabeli wymieniono niektóre z najczęściej używanych klas <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw:  
  
|Class|Opis|  
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|Przedstawia kolekcję par klucz wartość, które są zorganizowane na podstawie klucza.|  
|<xref:System.Collections.Generic.List%601>|Reprezentuje listę obiektów, które mogą być udostępniane przez indeks. Udostępnia metody do wyszukiwania, sortowania i modyfikowania list.|  
|<xref:System.Collections.Generic.Queue%601>|Reprezentuje pierwszy na wejściu, pierwszy FIFO kolekcji obiektów.|  
|<xref:System.Collections.Generic.SortedList%602>|Przedstawia kolekcję par klucz wartość, które są sortowane według klucza, w oparciu o związaną <xref:System.Collections.Generic.IComparer%601> implementacji.|  
|<xref:System.Collections.Generic.Stack%601>|Reprezentuje ostatni na wejściu, pierwszy LIFO kolekcji obiektów.|  
  
 Aby uzyskać więcej informacji, zobacz [powszechnie używane typy kolekcji](../../../standard/collections/commonly-used-collection-types.md), [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md), i <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a>System.Collections.Concurrent Classes   
 W .NET Framework 4 lub nowszej, kolekcje w programie <xref:System.Collections.Concurrent> przestrzeni nazw zapewniają efektywne działania wątków do uzyskiwania dostępu do elementów kolekcji z wielu wątków.  
  
 Klasy w <xref:System.Collections.Concurrent> przestrzeni nazw powinny być używane zamiast odpowiednich typów w <xref:System.Collections.Generic?displayProperty=nameWithType> i <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw w każdym przypadku, gdy wiele wątków jednocześnie uzyskują kolekcji. Aby uzyskać więcej informacji, zobacz [kolekcje obsługujące wielowątkowość](../../../standard/collections/thread-safe/index.md) i <xref:System.Collections.Concurrent>.  
  
 Niektóre klasy uwzględnione w <xref:System.Collections.Concurrent> nazw są <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, i <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a>Klasy System.Collections    
 Klasy w <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw nie przechowują elementów jako specjalnie typowanych obiektów, ale jako obiekty typu `Object`.  
  
 Jeśli to możliwe, należy używać ogólnych kolekcji w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw lub <xref:System.Collections.Concurrent> przestrzeni nazw, zamiast typów odziedziczonych w `System.Collections` przestrzeni nazw.  
  
 W poniższej tabeli wymieniono niektóre z najczęściej używanych klas w `System.Collections` przestrzeni nazw:  
  
|Class|Opis|  
|---|---|  
|<xref:System.Collections.ArrayList>|Reprezentuje tablicę obiektów, których rozmiar jest dynamicznie zwiększany w miarę wymagane.|  
|<xref:System.Collections.Hashtable>|Przedstawia kolekcję par klucz wartość, które są zorganizowane na podstawie kodu skrótu klucza.|  
|<xref:System.Collections.Queue>|Reprezentuje pierwszy na wejściu, pierwszy FIFO kolekcji obiektów.|  
|<xref:System.Collections.Stack>|Reprezentuje ostatni na wejściu, pierwszy LIFO kolekcji obiektów.|  
  
 <xref:System.Collections.Specialized> Przestrzeń nazw zawiera specjalistyczne i silnie typizowanych klas kolekcji, takich jak kolekcje wyłącznie ciągów i listy powiązane i słowniki hybrydowe.  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a>Klasa kolekcji Visual Basic  
 Visual Basic można użyć <xref:Microsoft.VisualBasic.Collection> klasy dostęp do elementu kolekcji, korzystając albo z indeksu numerycznego lub a `String` klucza. Można dodać elementy do obiektu kolekcji z lub bez określenia klucza. Jeśli dodajesz element bez klucza, należy użyć jego indeksu liczbowego do niego dostęp.  
  
 Visual Basic `Collection` klasa przechowuje wszystkie elementy jako typ `Object`, więc można dodać element każdego typu danych. Nie ma zabezpieczenia nieprawidłowych typów danych dodawane.  
  
 Jeśli używasz języka Visual Basic `Collection` klasy, pierwszy element kolekcji posiada indeks 1. To różni się od klas kolekcji .NET Framework, dla których indeks początkowy to 0.  
  
 Jeśli to możliwe, należy używać ogólnych kolekcji w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw lub <xref:System.Collections.Concurrent> przestrzeni nazw, a nie Visual Basic `Collection` klasy.  
  
 Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Collection>.  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementowanie kolekcji par klucz/wartość   
 <xref:System.Collections.Generic.Dictionary%602> Kolekcji ogólnej umożliwia dostęp do elementów w kolekcji za pomocą klucza każdego elementu. Każdy dodatkem do słownika składa się z wartości i skojarzonego z nim klucza. Pobieranie wartości przy użyciu własnego klucza jest szybkie ponieważ `Dictionary` klasy jest implementowany jako tabelę mieszania.  
  
 Poniższy przykład tworzy `Dictionary` kolekcji i wykonuje iteracje przez słownik za pomocą `For Each` instrukcji.  
  
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
  
 Zamiast tego za pomocą inicjatora kolekcji tworzyć `Dictionary` kolekcji, można zastąpić `BuildDictionary` i `AddToDictionary` metody przy użyciu następującej metody.  
  
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
  
 W poniższym przykładzie użyto <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metody i <xref:System.Collections.Generic.Dictionary%602.Item%2A> właściwość `Dictionary` szybko znaleźć element według klucza. `Item` Właściwość pozwala na dostęp do elementu w `elements` kolekcji przy użyciu `elements(symbol)` kodu w języku Visual Basic.  
  
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
  
 W poniższym przykładzie zamiast użyto <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda szybko znaleźć element według klucza.  
  
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
##  <a name="using-linq-to-access-a-collection"></a>Za pomocą LINQ do dostępu do kolekcji  
 LINQ (Language-Integrated Query) może służyć do dostępu do kolekcji. Zapytania LINQ zapewniają filtrowanie, porządkowanie i możliwości grupowania. Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
 Poniższy przykład wykonuje zapytanie LINQ na ogólnej `List`. Zapytanie LINQ zwraca inną kolekcję, która zawiera wyniki.  
  
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
 Poniżej przedstawiono przykładową procedurę sortowania zbioru. Przykład sortuje wystąpienia `Car` klasy, które są przechowywane w <xref:System.Collections.Generic.List%601>. `Car` Klasy implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> metoda zaimplementowana.  
  
 Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metody tworzy pojedyncze porównanie, który jest używane do sortowania. Kod napisany przez użytkownika w `CompareTo` metoda zwraca wartość dla każdego porównania bieżącego obiektu z innego obiektu. Wartość zwracana jest mniejsza niż zero, jeżeli bieżący obiekt jest mniejszy niż inny obiekt, większa niż zero, jeśli bieżący obiekt jest większy niż inny obiekt i zero czy są równe. Umożliwia to definiowanie w kodzie kryteriów dla większych niż, mniejsze więc równa.  
  
 W `ListCars` metody `cars.Sort()` instrukcji sortuje listy. To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje, że `CompareTo` metoda zostaje wywołana automatycznie dla `Car` obiekty w `List`.  
  
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
 Można zdefiniować kolekcję implementując <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.IEnumerable> interfejsu. Aby uzyskać więcej informacji, zobacz [wyliczania kolekcji](https://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).  
  
 Chociaż można zdefiniować kolekcję niestandardową, to zazwyczaj lepiej jest użyć zamiast tego kolekcje, które znajdują się w .NET Framework, które są opisane w [rodzaje kolekcji](#kinds-of-collections) we wcześniejszej części tego tematu.  
  
 W poniższym przykładzie zdefiniowano klasę kolekcji niestandardowej o nazwie `AllColors`. Ta klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda zaimplementowana.  
  
 `GetEnumerator` Metoda zwraca wystąpienie `ColorEnumerator` klasy. `ColorEnumerator` implementuje <xref:System.Collections.IEnumerator> interfejs, który wymaga, aby <xref:System.Collections.IEnumerator.Current%2A> właściwości <xref:System.Collections.IEnumerator.MoveNext%2A> metody i <xref:System.Collections.IEnumerator.Reset%2A> metoda zaimplementowana.  
  
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
##  <a name="iterators"></a>Iteratory  
 *Iteratora* służy do wykonywania niestandardowych iteracji przez kolekcję. Iteracją może być metodą lub `get` metody dostępu. Używa iteratora [uzyskanie](../../../visual-basic/language-reference/statements/yield-statement.md) instrukcja zwraca każdy element kolekcji naraz.  
  
 Wywołujesz iterację używając [For Each... Następny](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrukcji. Każda iteracja `For Each` pętli wywołuje iteratora. Gdy `Yield` osiągnięciu instrukcji w iteratorze, wyrażenie jest zwracane, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji w przy następnym wywołaniu iteratora.  
  
 Aby uzyskać więcej informacji, zobacz [Iteratory (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).  
  
 Poniższy przykład wykorzystuje metodę iteratora. Metoda iteratora ma `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli. W `ListEvenNumbers` metody, każda iteracja `For Each` treść instrukcji tworzy wywołanie metody iteracyjnej, która przechodzi do następnej `Yield` instrukcji.  
  
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
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
- [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
- [Równoległe LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)  
- [Kolekcje i struktury danych](../../../standard/collections/index.md)  
- [Tworzenie kolekcji i manipulowanie nimi](https://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
- [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)  
- [Porównywanie i sortowanie w ramach kolekcji](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
- [Kiedy należy używać kolekcji ogólnych](../../../standard/collections/when-to-use-generic-collections.md)
