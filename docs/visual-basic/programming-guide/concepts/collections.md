---
title: Kolekcje (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: get-started-article
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aac9ed655982ff4618e0bdb7fd2af16aaa546719
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="collections-visual-basic"></a>Kolekcje (Visual Basic)
Dla wielu aplikacji, dla których chcesz Utwórz i Zarządzaj grupami powiązanych obiektów. Istnieją dwa sposoby do obiektów grup: tworzenie tablic obiektów oraz tworzenie kolekcji obiektów.  
  
 Tablice są najbardziej przydatne do tworzenia i Praca z stała liczba silnie typizowanych obiektów. Aby uzyskać informacje dotyczące tablic, zobacz [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Kolekcje umożliwiają bardziej elastyczne do pracy z grupy obiektów. W przeciwieństwie do tablic grupy obiektów, którymi współpracujesz można zwiększyć lub zmniejszyć dynamicznie, musi mieć zmiany aplikacji. Niektóre zbiory klucza można przypisać do wszystkich obiektów, które można umieścić w kolekcji, tak, aby szybko można pobrać obiektu przy użyciu klucza.  
  
 Kolekcja jest klasa, więc należy zadeklarować wystąpienia klasy, aby można było dodać elementy do tej kolekcji.  
  
 Jeśli kolekcja zawiera elementy tylko jednego typu danych, możesz użyć jednej z klas w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw. Ogólnej kolekcji wymusza zabezpieczenie typów, dzięki czemu można dodać do niego inny typ danych. Podczas pobierania elementu z kolekcji uniwersalnej, nie trzeba określić jego typu danych albo przekonwertować go.  
  
> [!NOTE]
>  Przykłady w tym temacie, można dołączyć [importów](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrukcje dla `System.Collections.Generic` i `System.Linq` przestrzeni nazw.  
  
 **W tym temacie**  
  
-   [Przy użyciu prostych kolekcji](#BKMK_SimpleCollection)  
  
-   [Typy kolekcji](#BKMK_KindsOfCollections)  
  
    -   [System.Collections.Generic — klasy](#BKMK_Generic)  
  
    -   [Klasy System.Collections.Concurrent](#BKMK_Concurrent)  
  
    -   [System.Collections — klasy](#BKMK_Collections)  
  
    -   [Klasa kolekcji Visual Basic](#BKMK_VisualBasic)  
  
-   [Implementowanie kolekcję par klucz/wartość](#BKMK_KeyValuePairs)  
  
-   [Otwieranie kolekcji za pomocą LINQ](#BKMK_LINQ)  
  
-   [Sortowanie kolekcji](#BKMK_Sorting)  
  
-   [Definiowanie kolekcji niestandardowej](#BKMK_CustomCollection)  
  
-   [Iteratory](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>Przy użyciu prostych kolekcji  
 Przykłady w tej sekcji używać ogólnych <xref:System.Collections.Generic.List%601> klasy, która umożliwia pracę z silnie typizowaną listę obiektów.  
  
 Poniższy przykład tworzy listę ciągów i następnie iteruje ciągi za pomocą [For Each... Następny](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrukcji.  
  
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
  
 Jeśli zawartość kolekcji są znane z wyprzedzeniem, możesz użyć *inicjatora kolekcji* do zainicjowania dla kolekcji. Aby uzyskać więcej informacji, zobacz [inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
 Poniższy przykład jest taki sam, jak poprzedni przykład, z wyjątkiem inicjatora kolekcji służy do dodawania elementów do kolekcji.  
  
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
  
 Można użyć [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) instrukcji zamiast `For Each` instrukcji do iterowania po kolekcji. Można to zrobić, należy podczas uzyskiwania dostępu do elementów kolekcji przez indeks. Indeks elementów rozpoczyna się od 0 i kończy się liczbę element pomniejszonej o 1.  
  
 Poniższy przykład iterację elementów kolekcji za pomocą `For…Next` zamiast `For Each`.  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 Poniższy przykład umożliwia usunięcie elementu z kolekcji, określając obiekt do usunięcia.  
  
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
  
 Poniższy przykład umożliwia usunięcie elementów z listy ogólnej. Zamiast `For Each` instrukcji [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) używana jest instrukcja, która wykonuje iterację w kolejności malejącej. Jest to spowodowane <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda powoduje elementów po usunięty element ma niższą wartość indeksu.  
  
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
  
 Dla typu elementów w <xref:System.Collections.Generic.List%601>, możesz również definiować własne klasy. W poniższym przykładzie `Galaxy` klasy, która jest używana przez <xref:System.Collections.Generic.List%601> jest zdefiniowany w kodzie.  
  
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
## <a name="kinds-of-collections"></a>Typy kolekcji   
 Wielu typowych kolekcji są dostarczane przez program .NET Framework. Każdy typ kolekcji jest przeznaczony dla określonego celu.  
  
 W tej sekcji opisano niektóre typowe klasy kolekcji:  
  
-   <xref:System.Collections.Generic>klasy  
  
-   <xref:System.Collections.Concurrent>klasy  
  
-   <xref:System.Collections>klasy  
  
-   Visual Basic `Collection` — klasa  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a>System.Collections.Generic — klasy  

 Można utworzyć kolekcję ogólną za pomocą jednej z klas w <xref:System.Collections.Generic> przestrzeni nazw. Ogólnej kolekcji jest przydatne, gdy każdy element w kolekcji ma ten sam typ danych. Wymusza ogólnej kolekcji silne wpisywanie, zezwalając tylko żądanych danych typu do dodania.  
  
 W poniższej tabeli przedstawiono niektóre często używane klasy <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw:  
  
|Class|Opis|  
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|Reprezentuje kolekcję pary klucz wartość, które są zorganizowane według klucza.|  
|<xref:System.Collections.Generic.List%601>|Reprezentuje listę obiektów, które mogą być udostępniane przez indeks. Udostępnia metody do wyszukiwania, sortowania i modyfikowania list.|  
|<xref:System.Collections.Generic.Queue%601>|Reprezentuje pierwszy w pierwszym FIFO kolekcji obiektów.|  
|<xref:System.Collections.Generic.SortedList%602>|Reprezentuje kolekcję par klucz/wartość, które są sortowane według klucza opartego na skojarzonym <xref:System.Collections.Generic.IComparer%601> implementacji.|  
|<xref:System.Collections.Generic.Stack%601>|Reprezentuje ostatni w pierwszym LIFO kolekcji obiektów.|  
  
 Aby uzyskać dodatkowe informacje, zobacz [często używane typy kolekcji](../../../standard/collections/commonly-used-collection-types.md), [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md), i <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a>Klasy System.Collections.Concurrent   
 W programie .NET Framework 4 lub nowszego, kolekcje w <xref:System.Collections.Concurrent> przestrzeni nazw zapewniają wydajność operacji wątkowo do uzyskiwania dostępu do kolekcji elementów, wiele wątków.  
  
 Klasy w <xref:System.Collections.Concurrent> przestrzeń nazw powinna być używana zamiast odpowiednie typy w <xref:System.Collections.Generic?displayProperty=nameWithType> i <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw w każdym przypadku, gdy wiele wątków jednocześnie uzyskują kolekcji. Aby uzyskać więcej informacji, zobacz [kolekcje obsługujące wielowątkowość](../../../standard/collections/thread-safe/index.md) i <xref:System.Collections.Concurrent>.  
  
 Niektóre klasy uwzględnione w <xref:System.Collections.Concurrent> przestrzeni nazw są <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, i <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a>System.Collections — klasy    
 Klasy w <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw nie należy przechowywać elementów, w szczególności obiektów określonego typu, ale jako obiekty typu `Object`.  
  
 Jeśli to możliwe, należy użyć kolekcje ogólne w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw lub <xref:System.Collections.Concurrent> przestrzeni nazw zamiast starsze typy w `System.Collections` przestrzeni nazw.  
  
 W poniższej tabeli przedstawiono niektóre często używane klasy w `System.Collections` przestrzeni nazw:  
  
|Class|Opis|  
|---|---|  
|<xref:System.Collections.ArrayList>|Reprezentuje tablicę obiektów, którego rozmiar jest dynamicznie zwiększony jako wymagane.|  
|<xref:System.Collections.Hashtable>|Reprezentuje kolekcję pary klucz wartość, które są podzielone na podstawie kodu skrótu klucza.|  
|<xref:System.Collections.Queue>|Reprezentuje pierwszy w pierwszym FIFO kolekcji obiektów.|  
|<xref:System.Collections.Stack>|Reprezentuje ostatni w pierwszym LIFO kolekcji obiektów.|  
  
 <xref:System.Collections.Specialized> Przestrzeń nazw zawiera klasy specjalistyczne i jednoznacznie kolekcji, takie jak kolekcji tylko do ciągów i słowników połączone listy i hybrydowych.  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a>Klasa kolekcji Visual Basic  
 Korzystając z języka Visual Basic <xref:Microsoft.VisualBasic.Collection> klasa do dostępu do elementu przy użyciu liczbowym indeksem kolekcji lub a `String` klucza. Elementy można dodać do obiektu kolekcji lub bez określenia klucza. Jeśli dodasz do elementu bez klucza, należy użyć jego indeksu liczbowego dostępu do niego.  
  
 Visual Basic `Collection` klasy wszystkie jego elementy są przechowywane jako typ `Object`, dzięki czemu można dodać elementu każdego typu danych. Nie ma żadnych zabezpieczenie przed typy danych nieodpowiednie dodawany.  
  
 Jeśli używasz programu Visual Basic `Collection` klasy, pierwszy element w kolekcji ma indeks równy 1. To różni się od klasy kolekcji .NET Framework, dla których początkowy indeks jest 0.  
  
 Jeśli to możliwe, należy użyć kolekcje ogólne w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw lub <xref:System.Collections.Concurrent> przestrzeni nazw zamiast Visual Basic `Collection` klasy.  
  
 Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Collection>.  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementowanie kolekcję par klucz/wartość   
 <xref:System.Collections.Generic.Dictionary%602> Kolekcji ogólnych umożliwia dostęp do elementów w kolekcji przy użyciu klucza każdego elementu. Każda dodatkowa do słownika składa się z wartością i skojarzonego z nim klucza. Pobieranie wartości przy użyciu swojego klucza jest szybkie, ponieważ `Dictionary` klasy jest zaimplementowany jako tablicy skrótów.  
  
 Poniższy przykład tworzy `Dictionary` kolekcji i iteruje po słowniku przy użyciu `For Each` instrukcji.  
  
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
  
 Aby zamiast tego użyj inicjatora kolekcji, aby utworzyć `Dictionary` kolekcji, można zastąpić `BuildDictionary` i `AddToDictionary` metody przy użyciu następującej metody.  
  
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
  
 W poniższym przykładzie użyto <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> — metoda i <xref:System.Collections.Generic.Dictionary%602.Item%2A> właściwość `Dictionary` można szybko znaleźć elementu według klucza. `Item` Właściwość umożliwia dostęp do elementu w `elements` kolekcji przy użyciu `elements(symbol)` kodu w języku Visual Basic.  
  
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
  
 W poniższym przykładzie zamiast niego użyto <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody szybko znaleźć elementu według klucza.  
  
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
##  <a name="using-linq-to-access-a-collection"></a>Otwieranie kolekcji za pomocą LINQ  
 LINQ (zapytania język Language-Integrated) można uzyskać dostępu do kolekcji. Zapytania LINQ zapewniają filtrowanie, kolejność i grupowanie możliwości. Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
 W poniższym przykładzie uruchamiane zapytania LINQ względem ogólnego `List`. Zapytania LINQ zwraca innej kolekcji z wynikami.  
  
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
 Poniższy przykład przedstawia procedurę sortowanie kolekcji. Przykład sortuje wystąpienia `Car` klasy, które są przechowywane w <xref:System.Collections.Generic.List%601>. `Car` Klasa implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> metoda zaimplementowana.  
  
 Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metoda pozwala jednym porównanie, które jest używane do sortowania. Napisany przez użytkownika kod `CompareTo` metoda zwraca wartość dla każdego porównania bieżący obiekt z innym obiektem. Wartość zwracana jest mniejsza niż zero, jeśli bieżący obiekt jest mniejsza od drugiego obiektu, większa niż zero, jeśli bieżący obiekt jest większy niż drugi obiekt i zero czy są równe. Dzięki temu można zdefiniować w kodzie kryteria większa niż poniżej, a równa.  
  
 W `ListCars` metody `cars.Sort()` instrukcji sortuje listę. To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje, że `CompareTo` wywoływanej automatycznie dla metody `Car` obiekty w `List`.  
  
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
 Należy zdefiniować kolekcję zaimplementowanie <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.IEnumerable> interfejsu. Aby uzyskać dodatkowe informacje, zobacz [wyliczanie kolekcji](http://msdn.microsoft.com/en-us/71807ea7-9180-48a6-916f-35a5251d477f).  
  
 Mimo że można zdefiniować niestandardowej kolekcji, jest zazwyczaj lepiej jest użyć kolekcje, które znajdują się w programie .NET Framework, które zostały opisane w [rodzaje kolekcji](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) wcześniej w tym temacie.  
  
 W poniższym przykładzie zdefiniowano klasę kolekcji niestandardowej o nazwie `AllColors`. Ta klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda zaimplementowana.  
  
 `GetEnumerator` Metoda zwraca wystąpienie klasy `ColorEnumerator` klasy. `ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> interfejs, który wymaga, aby <xref:System.Collections.IEnumerator.Current%2A> właściwość <xref:System.Collections.IEnumerator.MoveNext%2A> metody i <xref:System.Collections.IEnumerator.Reset%2A> metoda zaimplementowana.  
  
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
 *Iterator* służy do przeprowadzania niestandardowej iteracji w kolekcji. Iterator może być metodą lub `get` dostępu. Używa iteratora [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrukcji, aby zwracany był każdy element kolekcji jednym naraz.  
  
 Należy wywołać przy użyciu iteratora [For Each... Następny](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrukcji. Każdej iteracji `For Each` pętli wywołuje iteratora. Gdy `Yield` iteratora osiągnie instrukcję, wyrażenie jest zwracany i są przechowywane w bieżącej lokalizacji w kodzie. Wykonanie jest ponownie z tej lokalizacji iteratora jest wywoływana przy następnym uruchomieniu.  
  
 Aby uzyskać więcej informacji, zobacz [Iteratory (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).  
  
 W poniższym przykładzie użyto metody iteracyjnej. Iterator — metoda ma `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli. W `ListEvenNumbers` metoda, każdej iteracji `For Each` treść instrukcji tworzy wywołanie do metody iteracyjne, który przechodzi do następnego `Yield` instrukcji.  
  
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
 [Inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Koncepcje programowania (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)  
 [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [LINQ do obiektów (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [Równoległe LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [Kolekcje i struktury danych](../../../standard/collections/index.md)  
 [Tworzenie i operowanie nimi kolekcje](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069)  
 [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)  
 [Porównywanie i sortowanie w kolekcjach](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [Kiedy należy używać kolekcji ogólnych](../../../standard/collections/when-to-use-generic-collections.md)
