---
title: 'Porady: dodawanie metod niestandardowych do kwerend LINQ (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c94973bf9eae0feb2f7690dcc10e839b6b7c060c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="f3f71-102">Porady: dodawanie metod niestandardowych do kwerend LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3f71-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>
<span data-ttu-id="f3f71-103">Można rozszerzyć zestaw metod, których można używać do kwerend LINQ przez dodanie metody rozszerzenia umożliwiające <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f3f71-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="f3f71-104">Na przykład oprócz standardowych średniej lub maksymalna operacji, można tworzyć niestandardowe metody agregacji do obliczenia wartości jednego z sekwencji wartości.</span><span class="sxs-lookup"><span data-stu-id="f3f71-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="f3f71-105">Można również utworzyć metodę, która działa jako filtr niestandardowy lub przekształcania określonych danych sekwencji wartości i zwraca nową sekwencję.</span><span class="sxs-lookup"><span data-stu-id="f3f71-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="f3f71-106">Przykłady takich metod <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, i <xref:System.Linq.Enumerable.Reverse%2A>.</span><span class="sxs-lookup"><span data-stu-id="f3f71-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>  
  
 <span data-ttu-id="f3f71-107">Po rozszerzeniu <xref:System.Collections.Generic.IEnumerable%601> interfejsu, niestandardowe metody można zastosować do żadnej kolekcji wyliczalny.</span><span class="sxs-lookup"><span data-stu-id="f3f71-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="f3f71-108">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="f3f71-108">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="adding-an-aggregate-method"></a><span data-ttu-id="f3f71-109">Dodawanie metody agregacji</span><span class="sxs-lookup"><span data-stu-id="f3f71-109">Adding an Aggregate Method</span></span>  
 <span data-ttu-id="f3f71-110">Metoda agregacji oblicza pojedynczą wartość z zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="f3f71-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="f3f71-111">LINQ udostępnia kilka metod agregacji, w tym <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="f3f71-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="f3f71-112">Łączny metodę można utworzyć przez dodanie metody rozszerzenia do <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f3f71-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="f3f71-113">W poniższym przykładzie przedstawiono sposób tworzenia metodę rozszerzenia o nazwie `Median` można obliczyć mediany sekwencji liczb typu `double`.</span><span class="sxs-lookup"><span data-stu-id="f3f71-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>  
  
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
  
 <span data-ttu-id="f3f71-114">Wywołanie tej metody rozszerzenia dla dowolnej kolekcji wyliczalny w taki sam sposób wywołania innych metod agregacji z <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f3f71-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3f71-115">W języku Visual Basic, możesz użyć wywołania metody lub składnia kwerendy standardowe `Aggregate` lub `Group By` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="f3f71-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="f3f71-116">Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md) i [grupy przez klauzuli](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f3f71-116">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="f3f71-117">Poniższy przykładowy kod przedstawia sposób użycia `Median` metodę dla tablicy typu `double`.</span><span class="sxs-lookup"><span data-stu-id="f3f71-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>  
  
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
  

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="f3f71-118">Przeładowanie metody agregacji do akceptowania różnych typów</span><span class="sxs-lookup"><span data-stu-id="f3f71-118">Overloading an Aggregate Method to Accept Various Types</span></span>  
 <span data-ttu-id="f3f71-119">Można przeciążać metodę agregacji, tak, aby akceptowane sekwencji różnych typów.</span><span class="sxs-lookup"><span data-stu-id="f3f71-119">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="f3f71-120">Standardowa podejście jest tworzenie przeciążenia dla każdego typu.</span><span class="sxs-lookup"><span data-stu-id="f3f71-120">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="f3f71-121">Innym rozwiązaniem jest tworzenie przeciążenia, które otrzymuje typu ogólnego i przekonwertować go do określonego typu za pomocą delegata.</span><span class="sxs-lookup"><span data-stu-id="f3f71-121">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="f3f71-122">Można także połączyć obu podejść.</span><span class="sxs-lookup"><span data-stu-id="f3f71-122">You can also combine both approaches.</span></span>  
  
#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="f3f71-123">Aby utworzyć przeciążenia dla każdego typu</span><span class="sxs-lookup"><span data-stu-id="f3f71-123">To create an overload for each type</span></span>  
 <span data-ttu-id="f3f71-124">Można utworzyć określonego przeciążenia dla poszczególnych typów, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f3f71-124">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="f3f71-125">Poniższy przykład kodu pokazuje przeciążenia `Median` metodę `integer` typu.</span><span class="sxs-lookup"><span data-stu-id="f3f71-125">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>  
  
```vb  
' Integer overload  
  
<Extension()>   
Function Median(ByVal source As IEnumerable(Of Integer)) As Double  
    Return Aggregate num In source Select CDbl(num) Into med = Median()  
End Function  
```  
 <span data-ttu-id="f3f71-126">Można teraz wywołać `Median` przeciążenia dla obu `integer` i `double` typy, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f3f71-126">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>  
  
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
  
 
#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="f3f71-127">Aby utworzyć ogólnego przeciążenia</span><span class="sxs-lookup"><span data-stu-id="f3f71-127">To create a generic overload</span></span>  
 <span data-ttu-id="f3f71-128">Można również utworzyć przeciążenia, które akceptuje sekwencji ogólnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="f3f71-128">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="f3f71-129">To przeciążenie delegata jako parametr przyjmuje i używa go do konwersji sekwencji obiektów typu ogólnego określonego typu.</span><span class="sxs-lookup"><span data-stu-id="f3f71-129">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>  
  
 <span data-ttu-id="f3f71-130">Poniższy kod przedstawia przeciążenia `Median` metody pobierającej <xref:System.Func%602> delegata jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f3f71-130">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="f3f71-131">Ten delegat przyjmuje ogólnego typu T obiektu i zwraca obiekt typu `double`.</span><span class="sxs-lookup"><span data-stu-id="f3f71-131">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 <span data-ttu-id="f3f71-132">Można teraz wywołać `Median` metody sekwencji obiekty dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="f3f71-132">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="f3f71-133">Jeśli typ nie ma własną przeciążenie metody, należy przekazać parametr delegata.</span><span class="sxs-lookup"><span data-stu-id="f3f71-133">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="f3f71-134">W języku Visual Basic w tym celu można użyć wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="f3f71-134">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="f3f71-135">Ponadto jeśli używasz `Aggregate` lub `Group By` klauzuli zamiast wywołania metody, można przekazać dowolna wartość lub wyrażenie, które znajduje się w zakresie tej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="f3f71-135">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>  
  
 <span data-ttu-id="f3f71-136">Poniższy przykład kodu pokazuje sposób wywoływania `Median` Metoda tablicy liczb całkowitych i Tablica ciągów.</span><span class="sxs-lookup"><span data-stu-id="f3f71-136">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="f3f71-137">Ciągi jest obliczana mediana dla długości ciągów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="f3f71-137">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="f3f71-138">W przykładzie pokazano sposób przekazywania <xref:System.Func%602> przekazać parametr `Median` metody dla każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="f3f71-138">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>  
  
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
## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="f3f71-139">Dodawanie metody, która zwraca kolekcję</span><span class="sxs-lookup"><span data-stu-id="f3f71-139">Adding a Method That Returns a Collection</span></span>  
 <span data-ttu-id="f3f71-140">Można rozszerzyć <xref:System.Collections.Generic.IEnumerable%601> interfejsu za pomocą metody niestandardowe zapytanie zwracające sekwencję wartości.</span><span class="sxs-lookup"><span data-stu-id="f3f71-140">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="f3f71-141">W tym przypadku metoda musi zwracać kolekcję typu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="f3f71-141">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="f3f71-142">Tych metod można zastosować filtry lub danych transformacje z wartości sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f3f71-142">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>  
  
 <span data-ttu-id="f3f71-143">Poniższy przykład przedstawia sposób tworzenia metodę rozszerzenia o nazwie `AlternateElements` zwracającą każdego innego elementu w kolekcji, rozpoczynając od pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="f3f71-143">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>  
  
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
 <span data-ttu-id="f3f71-144">Można wywołać tej metody rozszerzenia dla dowolnej kolekcji wyliczalny tak samo, jak możesz wywołać innych metod z <xref:System.Collections.Generic.IEnumerable%601> interfejsu, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f3f71-144">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3f71-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3f71-145">See Also</span></span>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="f3f71-146">Metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="f3f71-146">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
