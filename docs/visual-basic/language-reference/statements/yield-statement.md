---
title: Yield, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: cc89e6f9bc2ccb4fff9a9fe12cd190a6b2d212dc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401371"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="fb38c-102">Yield — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb38c-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="fb38c-103">Wysyła następny element kolekcji do `For Each...Next` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fb38c-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb38c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb38c-104">Syntax</span></span>  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb38c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb38c-105">Parameters</span></span>  
  
|<span data-ttu-id="fb38c-106">Termin</span><span class="sxs-lookup"><span data-stu-id="fb38c-106">Term</span></span>|<span data-ttu-id="fb38c-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="fb38c-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="fb38c-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="fb38c-108">Required.</span></span> <span data-ttu-id="fb38c-109">Wyrażenie, które jest niejawnie konwertowane na typ funkcji iteratora lub `Get` metody dostępu, która zawiera `Yield` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="fb38c-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb38c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb38c-110">Remarks</span></span>  
 <span data-ttu-id="fb38c-111">`Yield`Instrukcja zwraca jeden element kolekcji w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="fb38c-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="fb38c-112">`Yield`Instrukcja jest zawarta w funkcji iteratora lub `Get` metodzie dostępu, która wykonuje niestandardowe iteracje w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fb38c-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="fb38c-113">Używasz funkcji iteratora przy użyciu [for each... Następna instrukcja](for-each-next-statement.md) lub zapytanie LINQ.</span><span class="sxs-lookup"><span data-stu-id="fb38c-113">You consume an iterator function by using a [For Each...Next Statement](for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="fb38c-114">Każda iteracja `For Each` pętli wywołuje funkcję iteratora.</span><span class="sxs-lookup"><span data-stu-id="fb38c-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="fb38c-115">Gdy `Yield` instrukcja zostanie osiągnięta w funkcji iteratora, `expression` jest zwracana, a bieżąca lokalizacja w kodzie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="fb38c-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="fb38c-116">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="fb38c-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="fb38c-117">Niejawna konwersja musi istnieć z typu `expression` w `Yield` instrukcji na zwracany typ iteratora.</span><span class="sxs-lookup"><span data-stu-id="fb38c-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="fb38c-118">Możesz użyć `Exit Function` instrukcji lub, `Return` Aby zakończyć iterację.</span><span class="sxs-lookup"><span data-stu-id="fb38c-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="fb38c-119">"Yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używany w `Iterator` funkcji lub `Get` metodzie dostępu.</span><span class="sxs-lookup"><span data-stu-id="fb38c-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="fb38c-120">Aby uzyskać więcej informacji na temat funkcji iteratora i `Get` metod dostępu, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="fb38c-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="fb38c-121">Funkcje iteratora i metody uzyskiwania dostępu</span><span class="sxs-lookup"><span data-stu-id="fb38c-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="fb38c-122">Deklaracja funkcji iteratora lub `Get` metody dostępu musi spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="fb38c-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
- <span data-ttu-id="fb38c-123">Musi zawierać modyfikator [iteratora](../modifiers/iterator.md) .</span><span class="sxs-lookup"><span data-stu-id="fb38c-123">It must include an [Iterator](../modifiers/iterator.md) modifier.</span></span>  
  
- <span data-ttu-id="fb38c-124">Typem zwracanym musi być <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> ,, <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="fb38c-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
- <span data-ttu-id="fb38c-125">Nie może mieć żadnych `ByRef` parametrów.</span><span class="sxs-lookup"><span data-stu-id="fb38c-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="fb38c-126">Nie można wykonać funkcji iteratora w zdarzeniu, konstruktorze wystąpień, konstruktorze statycznym lub destruktorze statycznym.</span><span class="sxs-lookup"><span data-stu-id="fb38c-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="fb38c-127">Funkcja iteratora może być funkcją anonimową.</span><span class="sxs-lookup"><span data-stu-id="fb38c-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="fb38c-128">Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="fb38c-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="fb38c-129">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="fb38c-129">Exception Handling</span></span>  
 <span data-ttu-id="fb38c-130">`Yield`Instrukcja może znajdować się wewnątrz `Try` bloku [try... Catch... Finally — instrukcja](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fb38c-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span> <span data-ttu-id="fb38c-131">`Try`Blok, który ma `Yield` instrukcję, może mieć `Catch` bloki i może mieć `Finally` blok.</span><span class="sxs-lookup"><span data-stu-id="fb38c-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="fb38c-132">`Yield`Instrukcja nie może znajdować się wewnątrz `Catch` bloku lub `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="fb38c-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="fb38c-133">Jeśli `For Each` treść (poza funkcją iteratora) zgłasza wyjątek, `Catch` blok w funkcji iteratora nie jest wykonywany, ale `Finally` jest wykonywany blok w funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="fb38c-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="fb38c-134">`Catch`Blok wewnątrz funkcji iteratora przechwytuje tylko wyjątki, które występują wewnątrz funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="fb38c-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="fb38c-135">Realizacja techniczna</span><span class="sxs-lookup"><span data-stu-id="fb38c-135">Technical Implementation</span></span>  
 <span data-ttu-id="fb38c-136">Poniższy kod zwraca element `IEnumerable (Of String)` z funkcji iteratora, a następnie iteruje elementy `IEnumerable (Of String)` .</span><span class="sxs-lookup"><span data-stu-id="fb38c-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="fb38c-137">Wywołanie `MyIteratorFunction` nie wykonuje treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="fb38c-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="fb38c-138">Zamiast tego wywołanie zwraca `IEnumerable(Of String)` `elements` zmienną.</span><span class="sxs-lookup"><span data-stu-id="fb38c-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="fb38c-139">W iteracji `For Each` pętli <xref:System.Collections.IEnumerator.MoveNext%2A> Metoda jest wywoływana dla `elements` .</span><span class="sxs-lookup"><span data-stu-id="fb38c-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="fb38c-140">To wywołanie wykonuje treść `MyIteratorFunction` przed `Yield` osiągnięciem następnej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fb38c-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="fb38c-141">`Yield`Instrukcja zwraca wyrażenie, które określa nie tylko wartość `element` zmiennej do użycia przez treść pętli, ale również <xref:System.Collections.Generic.IEnumerator%601.Current%2A> Właściwość elementów, która jest `IEnumerable (Of String)` .</span><span class="sxs-lookup"><span data-stu-id="fb38c-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="fb38c-142">W każdej kolejnej iteracji `For Each` pętli wykonywanie treści iteratora jest kontynuowane od miejsca, w którym została pozostawiona, po osiągnięciu `Yield` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fb38c-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="fb38c-143">`For Each`Pętla kończy się, gdy zostanie osiągnięty koniec funkcji iteratora lub `Return` `Exit Function` instrukcji lub.</span><span class="sxs-lookup"><span data-stu-id="fb38c-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb38c-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb38c-144">Example</span></span>  
 <span data-ttu-id="fb38c-145">Poniższy przykład zawiera `Yield` instrukcję, która znajduje się wewnątrz elementu [... Następna](for-next-statement.md) pętla.</span><span class="sxs-lookup"><span data-stu-id="fb38c-145">The following example has a `Yield` statement that is inside a [For…Next](for-next-statement.md) loop.</span></span> <span data-ttu-id="fb38c-146">Każda iteracja [dla każdej](for-each-next-statement.md) treści instrukcji w programie `Main` tworzy wywołanie `Power` funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="fb38c-146">Each iteration of the [For Each](for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="fb38c-147">Każde wywołanie funkcji iteratora przechodzi do następnego wykonania `Yield` instrukcji, która występuje w następnej iteracji `For…Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="fb38c-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="fb38c-148">Typem zwracanym metody iteratora jest <xref:System.Collections.Generic.IEnumerable%601> Typ interfejsu iteratora.</span><span class="sxs-lookup"><span data-stu-id="fb38c-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="fb38c-149">Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.</span><span class="sxs-lookup"><span data-stu-id="fb38c-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="fb38c-150">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb38c-150">Example</span></span>  
 <span data-ttu-id="fb38c-151">Poniższy przykład ilustruje `Get` metodę dostępu, która jest iteratorem.</span><span class="sxs-lookup"><span data-stu-id="fb38c-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="fb38c-152">Deklaracja właściwości zawiera `Iterator` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="fb38c-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="fb38c-153">Aby uzyskać więcej przykładów, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="fb38c-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb38c-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb38c-154">See also</span></span>

- [<span data-ttu-id="fb38c-155">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="fb38c-155">Statements</span></span>](index.md)
