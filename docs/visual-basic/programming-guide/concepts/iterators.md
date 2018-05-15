---
title: Iteratory (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: ecc48ad5bbddc82457a8d6cc8e60ee419fb593fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iterators-visual-basic"></a><span data-ttu-id="4791a-102">Iteratory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4791a-102">Iterators (Visual Basic)</span></span>
<span data-ttu-id="4791a-103">*Iterator* może służyć do kroków opisanych w kolekcji, takie jak listy i stałych.</span><span class="sxs-lookup"><span data-stu-id="4791a-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>  
  
 <span data-ttu-id="4791a-104">Metody iterator lub `get` akcesor wykonuje niestandardowych iteracji w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4791a-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="4791a-105">Iterator — metoda korzysta z [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrukcji, aby zwracany był każdy element jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="4791a-105">An iterator method uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="4791a-106">Gdy `Yield` osiągnięciu instrukcji zapamiętanych bieżącej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4791a-106">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="4791a-107">Wykonanie jest uruchamiany ponownie z tej lokalizacji w następnym razem, gdy zostanie wywołana funkcja iteratora.</span><span class="sxs-lookup"><span data-stu-id="4791a-107">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="4791a-108">Korzystać z iteratora z kodu klienta za pomocą [For Each... Następny](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrukcji, lub za pomocą zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="4791a-108">You consume an iterator from client code by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>  
  
 <span data-ttu-id="4791a-109">W poniższym przykładzie pierwszej iteracji `For Each` pętli powoduje wykonanie kontynuować w `SomeNumbers` metody iteracyjnej do pierwszego `Yield` osiągnięciu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4791a-109">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="4791a-110">Tą iterację zwraca wartość 3 i są przechowywane w bieżącej lokalizacji w metodzie iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="4791a-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="4791a-111">Przy następnej iteracji pętli, wykonywanie w metodzie iteracyjnej będzie kontynuowane z, w którym ją przerwał pracę, ponownie zatrzymywanie po osiągnięciu `Yield` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4791a-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="4791a-112">Tą iterację zwraca wartość 5, a bieżącą lokalizację w metodzie iteracyjnej ponownie zostanie zachowane.</span><span class="sxs-lookup"><span data-stu-id="4791a-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="4791a-113">Pętla działanie jest kończone po osiągnięciu na końcu metody iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="4791a-113">The loop completes when the end of the iterator method is reached.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In SomeNumbers()  
        Console.Write(number & " ")  
    Next  
    ' Output: 3 5 8  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function SomeNumbers() As System.Collections.IEnumerable  
    Yield 3  
    Yield 5  
    Yield 8  
End Function  
```  
  
 <span data-ttu-id="4791a-114">Zwracany typ metody iterator lub `get` dostępu może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="4791a-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="4791a-115">Można użyć `Exit Function` lub `Return` instrukcji, aby zakończyć iterację.</span><span class="sxs-lookup"><span data-stu-id="4791a-115">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="4791a-116">Funkcja iteratora języka Visual Basic lub `get` deklaracja dostępu zawiera [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="4791a-116">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
 <span data-ttu-id="4791a-117">Iteratory zostały wprowadzone w języku Visual Basic w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="4791a-117">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="4791a-118">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="4791a-118">**In this topic**</span></span>  
  
-   [<span data-ttu-id="4791a-119">Prostego iteratora</span><span class="sxs-lookup"><span data-stu-id="4791a-119">Simple Iterator</span></span>](#BKMK_SimpleIterator)  
  
-   [<span data-ttu-id="4791a-120">Tworzenie klasy kolekcji</span><span class="sxs-lookup"><span data-stu-id="4791a-120">Creating a Collection Class</span></span>](#BKMK_CollectionClass)  
  
-   [<span data-ttu-id="4791a-121">Bloki try</span><span class="sxs-lookup"><span data-stu-id="4791a-121">Try Blocks</span></span>](#BKMK_TryBlocks)  
  
-   [<span data-ttu-id="4791a-122">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="4791a-122">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)  
  
-   [<span data-ttu-id="4791a-123">Przy użyciu Iteratory z listą ogólnych</span><span class="sxs-lookup"><span data-stu-id="4791a-123">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)  
  
-   [<span data-ttu-id="4791a-124">Informacje o składni</span><span class="sxs-lookup"><span data-stu-id="4791a-124">Syntax Information</span></span>](#BKMK_SyntaxInformation)  
  
-   [<span data-ttu-id="4791a-125">Implementacja techniczna</span><span class="sxs-lookup"><span data-stu-id="4791a-125">Technical Implementation</span></span>](#BKMK_Technical)  
  
-   [<span data-ttu-id="4791a-126">Użyj Iteratory</span><span class="sxs-lookup"><span data-stu-id="4791a-126">Use of Iterators</span></span>](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  <span data-ttu-id="4791a-127">Wszystkie przykłady w tym temacie, z wyjątkiem przykład prostego iteratora, obejmują [importów](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrukcje dla `System.Collections` i `System.Collections.Generic` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4791a-127">For all examples in the topic except the Simple Iterator example, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>  
  
##  <a name="BKMK_SimpleIterator"></a> <span data-ttu-id="4791a-128">Prostego iteratora</span><span class="sxs-lookup"><span data-stu-id="4791a-128">Simple Iterator</span></span>  
 <span data-ttu-id="4791a-129">W poniższym przykładzie przedstawiono jeden `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="4791a-129">The following example has a single `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="4791a-130">W `Main`, każdej iteracji `For Each` treść instrukcji tworzy wywołanie funkcji iteracyjnej, który przechodzi do następnego `Yield` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4791a-130">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    ' Output: 6 8 10 12 14 16 18  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As System.Collections.Generic.IEnumerable(Of Integer)  
  
    ' Yield even numbers in the range.  
    For number As Integer = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
##  <a name="BKMK_CollectionClass"></a> <span data-ttu-id="4791a-131">Tworzenie klasy kolekcji</span><span class="sxs-lookup"><span data-stu-id="4791a-131">Creating a Collection Class</span></span>  
 <span data-ttu-id="4791a-132">W poniższym przykładzie `DaysOfTheWeek` klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4791a-132">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="4791a-133">Kompilator niejawnie wywołuje `GetEnumerator` metody, która zwraca <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="4791a-133">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>  
  
 <span data-ttu-id="4791a-134">`GetEnumerator` Metoda zwraca każdego jednego ciągu w czasie przy użyciu `Yield` instrukcji i `Iterator` jest modyfikatora w deklaracji funkcji.</span><span class="sxs-lookup"><span data-stu-id="4791a-134">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>  
  
```vb  
Sub Main()  
    Dim days As New DaysOfTheWeek()  
    For Each day As String In days  
        Console.Write(day & " ")  
    Next  
    ' Output: Sun Mon Tue Wed Thu Fri Sat  
    Console.ReadKey()  
End Sub  
  
Private Class DaysOfTheWeek  
    Implements IEnumerable  
  
    Public days =  
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        ' Yield each day of the week.  
        For i As Integer = 0 To days.Length - 1  
            Yield days(i)  
        Next  
    End Function  
End Class  
```  
  
 <span data-ttu-id="4791a-135">Poniższy przykład tworzy `Zoo` klasy, która zawiera kolekcję zwierząt.</span><span class="sxs-lookup"><span data-stu-id="4791a-135">The following example creates a `Zoo` class that contains a collection of animals.</span></span>  
  
 <span data-ttu-id="4791a-136">`For Each` Instrukcji, która odwołuje się do wystąpienia klasy (`theZoo`) niejawnie wywołuje `GetEnumerator` metody.</span><span class="sxs-lookup"><span data-stu-id="4791a-136">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="4791a-137">`For Each` Instrukcje odwołujące się do `Birds` i `Mammals` Użyj właściwości `AnimalsForType` o nazwie metody iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="4791a-137">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>  
  
```vb  
Sub Main()  
    Dim theZoo As New Zoo()  
  
    theZoo.AddMammal("Whale")  
    theZoo.AddMammal("Rhinoceros")  
    theZoo.AddBird("Penguin")  
    theZoo.AddBird("Warbler")  
  
    For Each name As String In theZoo  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros Penguin Warbler  
  
    For Each name As String In theZoo.Birds  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Penguin Warbler  
  
    For Each name As String In theZoo.Mammals  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros  
  
    Console.ReadKey()  
End Sub  
  
Public Class Zoo  
    Implements IEnumerable  
  
    ' Private members.  
    Private animals As New List(Of Animal)  
  
    ' Public methods.  
    Public Sub AddMammal(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})  
    End Sub  
  
    Public Sub AddBird(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})  
    End Sub  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        For Each theAnimal As Animal In animals  
            Yield theAnimal.Name  
        Next  
    End Function  
  
    ' Public members.  
    Public ReadOnly Property Mammals As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Mammal)  
        End Get  
    End Property  
  
    Public ReadOnly Property Birds As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Bird)  
        End Get  
    End Property  
  
    ' Private methods.  
    Private Iterator Function AnimalsForType( _  
    ByVal type As Animal.TypeEnum) As IEnumerable  
        For Each theAnimal As Animal In animals  
            If (theAnimal.Type = type) Then  
                Yield theAnimal.Name  
            End If  
        Next  
    End Function  
  
    ' Private class.  
    Private Class Animal  
        Public Enum TypeEnum  
            Bird  
            Mammal  
        End Enum  
  
        Public Property Name As String  
        Public Property Type As TypeEnum  
    End Class  
End Class  
```  
  
##  <a name="BKMK_TryBlocks"></a> <span data-ttu-id="4791a-138">Bloki try</span><span class="sxs-lookup"><span data-stu-id="4791a-138">Try Blocks</span></span>  
 <span data-ttu-id="4791a-139">Visual Basic umożliwia `Yield` instrukcji w `Try` zablokować z [spróbuj... CATCH... Instrukcji finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4791a-139">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="4791a-140">A `Try` bloku, który ma `Yield` instrukcja może mieć `Catch` blokuje i może mieć `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="4791a-140">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="4791a-141">Poniższy przykład zawiera `Try`, `Catch`, i `Finally` bloki w funkcji iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="4791a-141">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="4791a-142">`Finally` Bloku w funkcji iteracyjnej wykonuje przed `For Each` zakończenie iteracji.</span><span class="sxs-lookup"><span data-stu-id="4791a-142">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In Test()  
        Console.WriteLine(number)  
    Next  
    Console.WriteLine("For Each is done.")  
  
    ' Output:  
    '  3  
    '  4  
    '  Something happened. Yields are done.  
    '  Finally is called.  
    '  For Each is done.  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function Test() As IEnumerable(Of Integer)  
    Try  
        Yield 3  
        Yield 4  
        Throw New Exception("Something happened. Yields are done.")  
        Yield 5  
        Yield 6  
    Catch ex As Exception  
        Console.WriteLine(ex.Message)  
    Finally  
        Console.WriteLine("Finally is called.")  
    End Try  
End Function  
```  
  
 <span data-ttu-id="4791a-143">A `Yield` instrukcja nie może być wewnątrz `Catch` bloku lub `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="4791a-143">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="4791a-144">Jeśli `For Each` treści (zamiast metody iterator) zgłasza wyjątek, `Catch` bloku w funkcji iteracyjnej nie została wykonana, ale `Finally` wykonaniu bloku w funkcji iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="4791a-144">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="4791a-145">A `Catch` bloku wewnątrz funkcji iteracyjnej przechwytuje tylko wyjątki, które występuje wewnątrz funkcji iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="4791a-145">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
##  <a name="BKMK_AnonymousMethods"></a> <span data-ttu-id="4791a-146">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="4791a-146">Anonymous Methods</span></span>  
 <span data-ttu-id="4791a-147">W języku Visual Basic funkcji anonimowej może być funkcji iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="4791a-147">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="4791a-148">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="4791a-148">The following example illustrates this.</span></span>  
  
```vb  
Dim iterateSequence = Iterator Function() _  
                      As IEnumerable(Of Integer)  
                          Yield 1  
                          Yield 2  
                      End Function  
  
For Each number As Integer In iterateSequence()  
    Console.Write(number & " ")  
Next  
' Output: 1 2  
Console.ReadKey()  
```  
  
 <span data-ttu-id="4791a-149">W poniższym przykładzie przedstawiono metodę iteratora nie sprawdza poprawność argumentów.</span><span class="sxs-lookup"><span data-stu-id="4791a-149">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="4791a-150">Metoda zwraca wynik anonimowe iteratora opisujący elementów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4791a-150">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In GetSequence(5, 10)  
        Console.Write(number & " ")  
    Next  
    ' Output: 5 6 7 8 9 10  
    Console.ReadKey()  
End Sub  
  
Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _  
As IEnumerable  
    ' Validate the arguments.  
    If low < 1 Then  
        Throw New ArgumentException("low is too low")  
    End If  
    If high > 140 Then  
        Throw New ArgumentException("high is too high")  
    End If  
  
    ' Return an anonymous iterator function.  
    Dim iterateSequence = Iterator Function() As IEnumerable  
                              For index = low To high  
                                  Yield index  
                              Next  
                          End Function  
    Return iterateSequence()  
End Function  
```  
  
 <span data-ttu-id="4791a-151">Jeśli weryfikacja jest wewnątrz funkcji iteracyjnej, do momentu rozpoczęcia pierwszej iteracji nie można wykonać walidacji `For Each` treści.</span><span class="sxs-lookup"><span data-stu-id="4791a-151">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>  
  
##  <a name="BKMK_GenericList"></a> <span data-ttu-id="4791a-152">Przy użyciu Iteratory z listą ogólnych</span><span class="sxs-lookup"><span data-stu-id="4791a-152">Using Iterators with a Generic List</span></span>  
 <span data-ttu-id="4791a-153">W poniższym przykładzie `Stack(Of T)` implementuje klasy ogólnej <xref:System.Collections.Generic.IEnumerable%601> interfejs generyczny.</span><span class="sxs-lookup"><span data-stu-id="4791a-153">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="4791a-154">`Push` Metody przypisuje wartości do tablicy typu `T`.</span><span class="sxs-lookup"><span data-stu-id="4791a-154">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="4791a-155"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Metoda zwraca wartości w tablicy przy użyciu `Yield` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4791a-155">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>  
  
 <span data-ttu-id="4791a-156">Oprócz ogólnego <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoda, inny niż ogólny <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda musi zostać wdrożona.</span><span class="sxs-lookup"><span data-stu-id="4791a-156">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="4791a-157">Jest to spowodowane <xref:System.Collections.Generic.IEnumerable%601> dziedziczy <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="4791a-157">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="4791a-158">Implementację nieogólnego różni się do ogólnego implementacji.</span><span class="sxs-lookup"><span data-stu-id="4791a-158">The non-generic implementation defers to the generic implementation.</span></span>  
  
 <span data-ttu-id="4791a-159">W przykładzie użyto nazwanego Iteratory do obsługi różnych sposobów iteracji w tej samej kolekcji danych.</span><span class="sxs-lookup"><span data-stu-id="4791a-159">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="4791a-160">Są one o nazwie Iteratory `TopToBottom` i `BottomToTop` właściwości oraz `TopN` metody.</span><span class="sxs-lookup"><span data-stu-id="4791a-160">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>  
  
 <span data-ttu-id="4791a-161">`BottomToTop` Obejmuje deklaracja właściwości `Iterator` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="4791a-161">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>  
  
```vb  
Sub Main()  
    Dim theStack As New Stack(Of Integer)  
  
    ' Add items to the stack.  
    For number As Integer = 0 To 9  
        theStack.Push(number)  
    Next  
  
    ' Retrieve items from the stack.  
    ' For Each is allowed because theStack implements  
    ' IEnumerable(Of Integer).  
    For Each number As Integer In theStack  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    ' For Each is allowed, because theStack.TopToBottom  
    ' returns IEnumerable(Of Integer).  
    For Each number As Integer In theStack.TopToBottom  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    For Each number As Integer In theStack.BottomToTop  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 0 1 2 3 4 5 6 7 8 9   
  
    For Each number As Integer In theStack.TopN(7)  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3  
  
    Console.ReadKey()  
End Sub  
  
Public Class Stack(Of T)  
    Implements IEnumerable(Of T)  
  
    Private values As T() = New T(99) {}  
    Private top As Integer = 0  
  
    Public Sub Push(ByVal t As T)  
        values(top) = t  
        top = top + 1  
    End Sub  
  
    Public Function Pop() As T  
        top = top - 1  
        Return values(top)  
    End Function  
  
    ' This function implements the GetEnumerator method. It allows  
    ' an instance of the class to be used in a For Each statement.  
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _  
        Implements IEnumerable(Of T).GetEnumerator  
  
        For index As Integer = top - 1 To 0 Step -1  
            Yield values(index)  
        Next  
    End Function  
  
    Public Iterator Function GetEnumerator1() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        Yield GetEnumerator()  
    End Function  
  
    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)  
        Get  
            Return Me  
        End Get  
    End Property  
  
    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)  
        Get  
            For index As Integer = 0 To top - 1  
                Yield values(index)  
            Next  
        End Get  
    End Property  
  
    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _  
        As IEnumerable(Of T)  
  
        ' Return less than itemsFromTop if necessary.  
        Dim startIndex As Integer =  
            If(itemsFromTop >= top, 0, top - itemsFromTop)  
  
        For index As Integer = top - 1 To startIndex Step -1  
            Yield values(index)  
        Next  
    End Function  
End Class  
```  
  
##  <a name="BKMK_SyntaxInformation"></a> <span data-ttu-id="4791a-162">Informacje o składni</span><span class="sxs-lookup"><span data-stu-id="4791a-162">Syntax Information</span></span>  
 <span data-ttu-id="4791a-163">Iteratora może wystąpić jako metody lub `get` dostępu.</span><span class="sxs-lookup"><span data-stu-id="4791a-163">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="4791a-164">Iterator nie może wystąpić w zdarzenia, konstruktora wystąpienia, statycznego konstruktora lub destruktora statycznych.</span><span class="sxs-lookup"><span data-stu-id="4791a-164">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="4791a-165">Niejawna konwersja musi istnieć od typ wyrażenia w `Yield` instrukcji, aby zwracany typ iteratora.</span><span class="sxs-lookup"><span data-stu-id="4791a-165">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="4791a-166">W języku Visual Basic, metody iteracyjne nie mogą zawierać `ByRef` parametrów.</span><span class="sxs-lookup"><span data-stu-id="4791a-166">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="4791a-167">W języku Visual Basic "Yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest on używany w `Iterator` metody lub `get` dostępu.</span><span class="sxs-lookup"><span data-stu-id="4791a-167">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>  
  
##  <a name="BKMK_Technical"></a> <span data-ttu-id="4791a-168">Implementacja techniczna</span><span class="sxs-lookup"><span data-stu-id="4791a-168">Technical Implementation</span></span>  
 <span data-ttu-id="4791a-169">Mimo że pisania iteratora jako metoda kompilator tłumaczy go na zagnieżdżona klasa oznacza to, w efekcie automatu stanów.</span><span class="sxs-lookup"><span data-stu-id="4791a-169">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="4791a-170">Ta klasa przechowuje informacje o pozycja iteratora, jak długo `For Each...Next` nadal pętli w kodzie klienta.</span><span class="sxs-lookup"><span data-stu-id="4791a-170">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>  
  
 <span data-ttu-id="4791a-171">Aby zobaczyć, co oznacza kompilatora, narzędzie Ildasm.exe służy do wyświetlania kod języka pośredniego firmy Microsoft, który jest generowany dla metody iterator.</span><span class="sxs-lookup"><span data-stu-id="4791a-171">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>  
  
 <span data-ttu-id="4791a-172">Po utworzeniu iteratora dla [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md), nie masz do zaimplementowania całości <xref:System.Collections.IEnumerator> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4791a-172">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="4791a-173">Kompilator wykrycie iteratora automatycznie generuje `Current`, `MoveNext`, i `Dispose` metody <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4791a-173">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>  
  
 <span data-ttu-id="4791a-174">W każdej iteracji kolejnych `For Each…Next` pętli (lub bezpośrednie wywołanie `IEnumerator.MoveNext`), treść kodu dalej iteratora zostanie wznowione po poprzedniej `Yield` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4791a-174">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="4791a-175">Następnie jest kontynuowana do następnego `Yield` instrukcji, dopóki nie zostanie osiągnięty koniec treści iteratora, lub do czasu `Exit Function` lub `Return` napotkano instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4791a-175">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>  
  
 <span data-ttu-id="4791a-176">Iteratory nie obsługują <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="4791a-176">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4791a-177">Aby ponownie przejść od początku, należy uzyskać nowe iteratora.</span><span class="sxs-lookup"><span data-stu-id="4791a-177">To re-iterate from the start, you must obtain a new iterator.</span></span>  
  
 <span data-ttu-id="4791a-178">Aby uzyskać dodatkowe informacje, zobacz [specyfikacja języka Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4791a-178">For additional information, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>  
  
##  <a name="BKMK_UseOfIterators"></a> <span data-ttu-id="4791a-179">Użyj Iteratory</span><span class="sxs-lookup"><span data-stu-id="4791a-179">Use of Iterators</span></span>  
 <span data-ttu-id="4791a-180">Iteratory umożliwiają zachować prostotę `For Each` pętli, gdy musisz użyć złożonego kodu do wypełniania kolejność listy.</span><span class="sxs-lookup"><span data-stu-id="4791a-180">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="4791a-181">Może to być przydatne, jeśli chcesz wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4791a-181">This can be useful when you want to do the following:</span></span>  
  
-   <span data-ttu-id="4791a-182">Zmodyfikuj kolejność listy po pierwszym `For Each` iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="4791a-182">Modify the list sequence after the first `For Each` loop iteration.</span></span>  
  
-   <span data-ttu-id="4791a-183">Unikaj pełni ładowania dużych listy przed pierwszym iteracji `For Each` pętli.</span><span class="sxs-lookup"><span data-stu-id="4791a-183">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="4791a-184">Przykładem jest stronicowana pobierania załadować partii wierszy tabeli.</span><span class="sxs-lookup"><span data-stu-id="4791a-184">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="4791a-185">Innym przykładem jest <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metodę, która implementuje Iteratory w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4791a-185">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>  
  
-   <span data-ttu-id="4791a-186">Hermetyzuj Tworzenie listy w iteratora.</span><span class="sxs-lookup"><span data-stu-id="4791a-186">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="4791a-187">W metodzie iteracyjnej można utworzyć listy i instrukcji yield każdy wynik w pętli.</span><span class="sxs-lookup"><span data-stu-id="4791a-187">In the iterator method, you can build the list and then yield each result in a loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4791a-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4791a-188">See Also</span></span>  
 <xref:System.Collections.Generic>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="4791a-189">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4791a-189">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="4791a-190">Yield, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4791a-190">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)  
 [<span data-ttu-id="4791a-191">Iterator</span><span class="sxs-lookup"><span data-stu-id="4791a-191">Iterator</span></span>](../../../visual-basic/language-reference/modifiers/iterator.md)
