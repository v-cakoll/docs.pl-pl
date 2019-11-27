---
title: 'Porady: dodawanie metod niestandardowych do kwerend LINQ'
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 3004a9c9c7abeffd9993b848ad765e7ae2dc8876
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353372"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="31e05-102">Instrukcje: dodawanie metod niestandardowych dla zapytań LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31e05-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>

<span data-ttu-id="31e05-103">Można rozszerzać zestaw metod, których można użyć dla zapytań LINQ przez dodanie metod rozszerzających do interfejsu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="31e05-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="31e05-104">Na przykład oprócz standardowej średniej lub maksymalnej operacji można utworzyć niestandardową metodę agregującą, aby obliczyć pojedynczą wartość z sekwencji wartości.</span><span class="sxs-lookup"><span data-stu-id="31e05-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="31e05-105">Możesz również utworzyć metodę, która działa jako filtr niestandardowy lub Przekształć dane dla sekwencji wartości i zwraca nową sekwencję.</span><span class="sxs-lookup"><span data-stu-id="31e05-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="31e05-106">Przykładami takich metod są <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>i <xref:System.Linq.Enumerable.Reverse%2A>.</span><span class="sxs-lookup"><span data-stu-id="31e05-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="31e05-107">Rozszerzając interfejs <xref:System.Collections.Generic.IEnumerable%601>, można zastosować własne metody do dowolnej wyliczalnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="31e05-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="31e05-108">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="31e05-108">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="31e05-109">Dodawanie metody agregującej</span><span class="sxs-lookup"><span data-stu-id="31e05-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="31e05-110">Metoda agregująca oblicza pojedynczą wartość z zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="31e05-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="31e05-111">LINQ zawiera kilka metod agregujących, w tym <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>i <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="31e05-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="31e05-112">Można utworzyć własną metodę agregującą, dodając metodę rozszerzenia do interfejsu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="31e05-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="31e05-113">Poniższy przykład kodu pokazuje, jak utworzyć metodę rozszerzenia o nazwie `Median`, aby obliczyć medianę dla sekwencji liczb typu `double`.</span><span class="sxs-lookup"><span data-stu-id="31e05-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

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

<span data-ttu-id="31e05-114">Ta metoda rozszerzenia jest wywoływana dla każdej wyliczalnej kolekcji w taki sam sposób, w jaki wywołujemy inne metody agregacji z interfejsu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="31e05-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

> [!NOTE]
> <span data-ttu-id="31e05-115">W Visual Basic można użyć wywołania metody lub standardowej składni zapytania dla klauzuli `Aggregate` lub `Group By`.</span><span class="sxs-lookup"><span data-stu-id="31e05-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="31e05-116">Aby uzyskać więcej informacji, zobacz [klauzula agregująca](../../../../visual-basic/language-reference/queries/aggregate-clause.md) i [klauzula GROUP by](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="31e05-116">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>

<span data-ttu-id="31e05-117">Poniższy przykład kodu pokazuje, jak używać metody `Median` dla tablicy typu `double`.</span><span class="sxs-lookup"><span data-stu-id="31e05-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="31e05-118">Przeciążanie metody agregującej w celu zaakceptowania różnych typów</span><span class="sxs-lookup"><span data-stu-id="31e05-118">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="31e05-119">Można przeciążyć metodę agregacji, aby akceptować sekwencje różnych typów.</span><span class="sxs-lookup"><span data-stu-id="31e05-119">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="31e05-120">Standardowe podejście polega na utworzeniu przeciążenia dla każdego typu.</span><span class="sxs-lookup"><span data-stu-id="31e05-120">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="31e05-121">Innym rozwiązaniem jest utworzenie przeciążenia, które będzie miało typ ogólny i przekonwertować go na określony typ za pomocą delegata.</span><span class="sxs-lookup"><span data-stu-id="31e05-121">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="31e05-122">Można również połączyć oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="31e05-122">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="31e05-123">Aby utworzyć Przeciążenie dla każdego typu</span><span class="sxs-lookup"><span data-stu-id="31e05-123">To create an overload for each type</span></span>

<span data-ttu-id="31e05-124">Można utworzyć określone Przeciążenie dla każdego typu, który ma być obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="31e05-124">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="31e05-125">Poniższy przykład kodu przedstawia Przeciążenie metody `Median` dla typu `integer`.</span><span class="sxs-lookup"><span data-stu-id="31e05-125">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```vb
' Integer overload

<Extension()>
Function Median(ByVal source As IEnumerable(Of Integer)) As Double
    Return Aggregate num In source Select CDbl(num) Into med = Median()
End Function
```

<span data-ttu-id="31e05-126">Teraz można wywoływać przeciążenia `Median` dla typów `integer` i `double`, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="31e05-126">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

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

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="31e05-127">Aby utworzyć Przeciążenie ogólne</span><span class="sxs-lookup"><span data-stu-id="31e05-127">To create a generic overload</span></span>

<span data-ttu-id="31e05-128">Można również utworzyć Przeciążenie, które akceptuje sekwencję obiektów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="31e05-128">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="31e05-129">To przeciążenie przyjmuje delegat jako parametr i używa go do konwersji sekwencji obiektów typu ogólnego do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="31e05-129">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="31e05-130">Poniższy kod przedstawia Przeciążenie metody `Median`, która przyjmuje <xref:System.Func%602> delegat jako parametr.</span><span class="sxs-lookup"><span data-stu-id="31e05-130">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="31e05-131">Ten delegat pobiera obiekt typu ogólnego T i zwraca obiekt typu `double`.</span><span class="sxs-lookup"><span data-stu-id="31e05-131">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```vb
' Generic overload.

<Extension()>
Function Median(Of T)(ByVal source As IEnumerable(Of T),
                      ByVal selector As Func(Of T, Double)) As Double
    Return Aggregate num In source Select selector(num) Into med = Median()
End Function
```

<span data-ttu-id="31e05-132">Teraz można wywołać metodę `Median` dla sekwencji obiektów dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="31e05-132">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="31e05-133">Jeśli typ nie ma własnego przeciążenia metody, należy przekazać parametr delegata.</span><span class="sxs-lookup"><span data-stu-id="31e05-133">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="31e05-134">W Visual Basic można użyć wyrażenia lambda do tego celu.</span><span class="sxs-lookup"><span data-stu-id="31e05-134">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="31e05-135">Ponadto, jeśli używasz klauzuli `Aggregate` lub `Group By` zamiast wywołania metody, można przekazać dowolną wartość lub wyrażenie, które znajduje się w zakresie tej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="31e05-135">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="31e05-136">Poniższy przykładowy kod pokazuje, jak wywołać metodę `Median` dla tablicy liczb całkowitych i tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="31e05-136">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="31e05-137">Dla ciągów, mediany dla długości ciągów w tablicy jest obliczany.</span><span class="sxs-lookup"><span data-stu-id="31e05-137">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="31e05-138">W przykładzie pokazano, jak przekazać parametr delegata <xref:System.Func%602> do metody `Median` dla każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="31e05-138">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

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

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="31e05-139">Dodawanie metody zwracającej kolekcję</span><span class="sxs-lookup"><span data-stu-id="31e05-139">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="31e05-140">Interfejs <xref:System.Collections.Generic.IEnumerable%601> można zwiększyć przy użyciu niestandardowej metody zapytania, która zwraca sekwencję wartości.</span><span class="sxs-lookup"><span data-stu-id="31e05-140">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="31e05-141">W takim przypadku metoda musi zwracać kolekcję typu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="31e05-141">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="31e05-142">Takie metody mogą służyć do zastosowania filtrów lub transformacji danych do sekwencji wartości.</span><span class="sxs-lookup"><span data-stu-id="31e05-142">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="31e05-143">Poniższy przykład pokazuje, jak utworzyć metodę rozszerzenia o nazwie `AlternateElements`, która zwraca każdy inny element w kolekcji, rozpoczynając od pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="31e05-143">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

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

<span data-ttu-id="31e05-144">Można wywołać tę metodę rozszerzenia dla każdej wyliczalnej kolekcji tak samo jak w przypadku wywołania innych metod z interfejsu <xref:System.Collections.Generic.IEnumerable%601>, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="31e05-144">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="31e05-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31e05-145">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="31e05-146">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="31e05-146">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
