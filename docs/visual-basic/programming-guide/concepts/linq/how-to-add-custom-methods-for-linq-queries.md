---
title: 'Instrukcje: Dodawanie metod niestandardowych do kwerend LINQ (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: a58ced83a01e41be707f2483cabe9c8e867e2c1a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829177"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a>Instrukcje: Dodawanie metod niestandardowych do kwerend LINQ (Visual Basic)
Można rozszerzyć zbiór metod, które służy do zapytań LINQ, dodając metody rozszerzenia umożliwiające <xref:System.Collections.Generic.IEnumerable%601> interfejsu. Na przykład oprócz standardowych średnia lub maksymalna operacje, możesz utworzyć niestandardowe metody agregacji do obliczenia pojedynczej wartości z sekwencji wartości. Można również utworzyć metodę, która działa jako filtr niestandardowy lub przekształcenia danych określonego dla sekwencji wartości i zwraca nową sekwencję. Przykłady takich metod <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, i <xref:System.Linq.Enumerable.Reverse%2A>.  
  
 Po rozszerzeniu <xref:System.Collections.Generic.IEnumerable%601> interfejsu swoje niestandardowe metody można zastosować do kolekcji wyliczenia. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="adding-an-aggregate-method"></a>Dodawanie metody agregacji  
 Metoda agregacji oblicza pojedynczej wartości z zestawu wartości. LINQ zapewnia kilka metod agregacji, takich jak <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Max%2A>. Metoda agregacji można utworzyć, dodając metodę rozszerzenia, aby <xref:System.Collections.Generic.IEnumerable%601> interfejsu.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć metodę rozszerzenia o nazwie `Median` można obliczyć mediany sekwencji liczb typu `double`.  
  
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
  
 Chcesz wywołać tę metodę rozszerzenia dla dowolnej kolekcji wyliczalny tak samo jak inne metody agregacji z <xref:System.Collections.Generic.IEnumerable%601> interfejsu.  
  
> [!NOTE]
>  W języku Visual Basic, możesz użyć wywołania metody lub nieprawidłowa składnia standardowej kwerendy `Aggregate` lub `Group By` klauzuli. Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md) i [grupy przez klauzulę](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 Poniższy przykład kodu pokazuje sposób użycia `Median` metodę dla tablicy typu `double`.  
  
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
  

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Przeciążenie to metoda agregacji do akceptowania różnych typów  
 Metoda agregacji można przeciążać tak, aby go akceptuje sekwencje różnych typów. Jest standardowego podejścia do tworzenia przeciążenia dla każdego typu. Innym rozwiązaniem jest tworzenie przeciążenia, które będą typu ogólnego i przekonwertować go do określonego typu za pomocą delegata. Można także połączyć oba podejścia.  
  
#### <a name="to-create-an-overload-for-each-type"></a>Aby utworzyć przeciążenia dla każdego typu  
 Można utworzyć określonego przeciążenia dla każdego typu, które mają być obsługiwane. Poniższy przykład kodu pokazuje przeciążenie `Median` metodę `integer` typu.  
  
```vb  
' Integer overload  
  
<Extension()>   
Function Median(ByVal source As IEnumerable(Of Integer)) As Double  
    Return Aggregate num In source Select CDbl(num) Into med = Median()  
End Function  
```  
 Teraz można wywołać `Median` przeciążenia dla obu `integer` i `double` typów, jak pokazano w poniższym kodzie:  
  
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
  
 
#### <a name="to-create-a-generic-overload"></a>Aby utworzyć przeciążenie ogólne  
 Można również utworzyć przeciążenie, które akceptuje sekwencji ogólnych obiektów. Tego przeciążenia przyjmuje jako parametr delegata i używa go w celu konwersji sekwencji obiektów typu ogólnego dla określonego typu.  
  
 Poniższy kod pokazuje przeciążenie `Median` metody, która przyjmuje <xref:System.Func%602> delegować jako parametr. Ten delegat przyjmuje obiekt ogólny typ T i zwraca obiekt typu `double`.  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 Teraz można wywołać `Median` metodę sekwencji obiektów dowolnego typu. Jeśli typ nie ma swój własny przeciążenia metody, należy przekazać parametr delegata. W języku Visual Basic, w tym celu można użyć wyrażenia lambda. Ponadto jeśli używasz `Aggregate` lub `Group By` klauzuli zamiast wywołania metody które można przekazać dowolna wartość lub wyrażenie, który znajduje się w zakresie tej klauzuli.  
  
 Poniższy przykład kodu pokazuje sposób wywoływania `Median` Metoda tablicy liczb całkowitych i tablicę ciągów. Dla ciągów mediana dla długości ciągów w tablicy jest obliczana. W przykładzie pokazano sposób przekazywania <xref:System.Func%602> parametru, aby delegować `Median` metody dla każdego przypadku.  
  
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
## <a name="adding-a-method-that-returns-a-collection"></a>Dodawanie metody, które zwraca kolekcję  
 Możesz rozszerzyć <xref:System.Collections.Generic.IEnumerable%601> interfejs za pomocą metody niestandardowe zapytanie, która zwraca sekwencję wartości. W tym przypadku metoda musi zwracać kolekcję typu <xref:System.Collections.Generic.IEnumerable%601>. Takie metody może służyć do zastosowania przekształcenia danych lub filtrów do sekvence hodnot.  
  
 Poniższy przykład pokazuje, jak utworzyć metodę rozszerzenia o nazwie `AlternateElements` zwracającego każdy inny element w kolekcji, począwszy od pierwszego elementu.  
  
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
 Chcesz wywołać tę metodę rozszerzenia dla dowolnego wyliczalny kolekcji, tak samo, jak możesz wywołać innych metod z <xref:System.Collections.Generic.IEnumerable%601> interfejsu, jak pokazano w poniższym kodzie:  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic.IEnumerable%601>
- [Metody rozszerzeń](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
