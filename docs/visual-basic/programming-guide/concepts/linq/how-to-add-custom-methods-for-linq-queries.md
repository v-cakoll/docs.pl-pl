---
title: 'Porady: dodawanie metod niestandardowych do kwerend LINQ (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 6fa212ff05547e8edd3964a6e1c9f76c11cdbe08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a>Porady: dodawanie metod niestandardowych do kwerend LINQ (Visual Basic)
Można rozszerzyć zestaw metod, których można używać do kwerend LINQ przez dodanie metody rozszerzenia umożliwiające <xref:System.Collections.Generic.IEnumerable%601> interfejsu. Na przykład oprócz standardowych średniej lub maksymalna operacji, można tworzyć niestandardowe metody agregacji do obliczenia wartości jednego z sekwencji wartości. Można również utworzyć metodę, która działa jako filtr niestandardowy lub przekształcania określonych danych sekwencji wartości i zwraca nową sekwencję. Przykłady takich metod <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, i <xref:System.Linq.Enumerable.Reverse%2A>.  
  
 Po rozszerzeniu <xref:System.Collections.Generic.IEnumerable%601> interfejsu, niestandardowe metody można zastosować do żadnej kolekcji wyliczalny. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="adding-an-aggregate-method"></a>Dodawanie metody agregacji  
 Metoda agregacji oblicza pojedynczą wartość z zestawu wartości. LINQ udostępnia kilka metod agregacji, w tym <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Max%2A>. Łączny metodę można utworzyć przez dodanie metody rozszerzenia do <xref:System.Collections.Generic.IEnumerable%601> interfejsu.  
  
 W poniższym przykładzie przedstawiono sposób tworzenia metodę rozszerzenia o nazwie `Median` można obliczyć mediany sekwencji liczb typu `double`.  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module LINQExtension  
  
    ' Extension method for the IEnumerable(of T) interface.   
    ' The method accepts only values of the Double type.  
    <Extension()>   
    Function Median(ByVal source As IEnumerable(Of Double)) As Double  
        If source.Count = 0 Then  
            Throw New InvalidOperationException("Cannot compute median for an empty set.")  
        End If  
  
        Dim sortedSource = From number In source   
                           Order By number  
  
        Dim itemIndex = sortedSource.Count \ 2  
  
        If sortedSource.Count Mod 2 = 0 Then  
            ' Even number of items in list.  
            Return (sortedSource(itemIndex) + sortedSource(itemIndex - 1)) / 2  
        Else  
            ' Odd number of items in list.  
            Return sortedSource(itemIndex)  
        End If  
    End Function  
End Module  
```  
  
 Wywołanie tej metody rozszerzenia dla dowolnej kolekcji wyliczalny w taki sam sposób wywołania innych metod agregacji z <xref:System.Collections.Generic.IEnumerable%601> interfejsu.  
  
> [!NOTE]
>  W języku Visual Basic, możesz użyć wywołania metody lub składnia kwerendy standardowe `Aggregate` lub `Group By` klauzuli. Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md) i [grupy przez klauzuli](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 Poniższy przykładowy kod przedstawia sposób użycia `Median` metodę dla tablicy typu `double`.  
  
```vb  
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}  
  
Dim query1 = Aggregate num In numbers1 Into Median()  
  
Console.WriteLine("Double: Median = " & query1)  
```  
  
```vb  
' This code produces the following output:  
'  
' Double: Median = 4.85  
```  
  

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Przeładowanie metody agregacji do akceptowania różnych typów  
 Można przeciążać metodę agregacji, tak, aby akceptowane sekwencji różnych typów. Standardowa podejście jest tworzenie przeciążenia dla każdego typu. Innym rozwiązaniem jest tworzenie przeciążenia, które otrzymuje typu ogólnego i przekonwertować go do określonego typu za pomocą delegata. Można także połączyć obu podejść.  
  
#### <a name="to-create-an-overload-for-each-type"></a>Aby utworzyć przeciążenia dla każdego typu  
 Można utworzyć określonego przeciążenia dla poszczególnych typów, które mają być obsługiwane. Poniższy przykład kodu pokazuje przeciążenia `Median` metodę `integer` typu.  
  
```vb  
' Integer overload  
  
<Extension()>   
Function Median(ByVal source As IEnumerable(Of Integer)) As Double  
    Return Aggregate num In source Select CDbl(num) Into med = Median()  
End Function  
```  
 Można teraz wywołać `Median` przeciążenia dla obu `integer` i `double` typy, jak pokazano w poniższym kodzie:  
  
```vb  
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}  
  
Dim query1 = Aggregate num In numbers1 Into Median()  
  
Console.WriteLine("Double: Median = " & query1)  
```  
  
```vb  
Dim numbers2() As Integer = {1, 2, 3, 4, 5}  
  
Dim query2 = Aggregate num In numbers2 Into Median()  
  
Console.WriteLine("Integer: Median = " & query2)  
```  
  
```vb  
' This code produces the following output:  
'  
' Double: Median = 4.85  
' Integer: Median = 3  
```  
  
 
#### <a name="to-create-a-generic-overload"></a>Aby utworzyć ogólnego przeciążenia  
 Można również utworzyć przeciążenia, które akceptuje sekwencji ogólnych obiektów. To przeciążenie delegata jako parametr przyjmuje i używa go do konwersji sekwencji obiektów typu ogólnego określonego typu.  
  
 Poniższy kod przedstawia przeciążenia `Median` metody pobierającej <xref:System.Func%602> delegata jako parametr. Ten delegat przyjmuje ogólnego typu T obiektu i zwraca obiekt typu `double`.  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 Można teraz wywołać `Median` metody sekwencji obiekty dowolnego typu. Jeśli typ nie ma własną przeciążenie metody, należy przekazać parametr delegata. W języku Visual Basic w tym celu można użyć wyrażenia lambda. Ponadto jeśli używasz `Aggregate` lub `Group By` klauzuli zamiast wywołania metody, można przekazać dowolna wartość lub wyrażenie, które znajduje się w zakresie tej klauzuli.  
  
 Poniższy przykład kodu pokazuje sposób wywoływania `Median` Metoda tablicy liczb całkowitych i Tablica ciągów. Ciągi jest obliczana mediana dla długości ciągów w tablicy. W przykładzie pokazano sposób przekazywania <xref:System.Func%602> przekazać parametr `Median` metody dla każdego przypadku.  
  
```vb  
Dim numbers3() As Integer = {1, 2, 3, 4, 5}  
  
' You can use num as a parameter for the Median method   
' so that the compiler will implicitly convert its value to double.  
' If there is no implicit conversion, the compiler will  
' display an error message.  
  
Dim query3 = Aggregate num In numbers3 Into Median(num)  
  
Console.WriteLine("Integer: Median = " & query3)  
  
Dim numbers4() As String = {"one", "two", "three", "four", "five"}  
  
' With the generic overload, you can also use numeric properties of objects.  
  
Dim query4 = Aggregate str In numbers4 Into Median(str.Length)  
  
Console.WriteLine("String: Median = " & query4)  
  
' This code produces the following output:  
'  
' Integer: Median = 3  
' String: Median = 4  
```  
## <a name="adding-a-method-that-returns-a-collection"></a>Dodawanie metody, która zwraca kolekcję  
 Można rozszerzyć <xref:System.Collections.Generic.IEnumerable%601> interfejsu za pomocą metody niestandardowe zapytanie zwracające sekwencję wartości. W tym przypadku metoda musi zwracać kolekcję typu <xref:System.Collections.Generic.IEnumerable%601>. Tych metod można zastosować filtry lub danych transformacje z wartości sekwencji.  
  
 Poniższy przykład przedstawia sposób tworzenia metodę rozszerzenia o nazwie `AlternateElements` zwracającą każdego innego elementu w kolekcji, rozpoczynając od pierwszego elementu.  
  
```vb  
' Extension method for the IEnumerable(of T) interface.   
' The method returns every other element of a sequence.  
  
<Extension()>   
Function AlternateElements(Of T)(  
    ByVal source As IEnumerable(Of T)  
    ) As IEnumerable(Of T)  
  
    Dim list As New List(Of T)  
    Dim i = 0  
    For Each element In source  
        If (i Mod 2 = 0) Then  
            list.Add(element)  
        End If  
        i = i + 1  
    Next  
    Return list  
End Function  
```  
 Można wywołać tej metody rozszerzenia dla dowolnej kolekcji wyliczalny tak samo, jak możesz wywołać innych metod z <xref:System.Collections.Generic.IEnumerable%601> interfejsu, jak pokazano w poniższym kodzie:  
  
```vb  
Dim strings() As String = {"a", "b", "c", "d", "e"}  
  
Dim query = strings.AlternateElements()  
  
For Each element In query  
    Console.WriteLine(element)  
Next  
  
' This code produces the following output:  
'  
' a  
' c  
' e  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Metody rozszerzeń](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
