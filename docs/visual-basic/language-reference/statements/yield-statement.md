---
title: Yield — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 72a8dafdc5aa834a644e1e70a309cfc0827b5fdf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352727"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="69f8d-102">Yield — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69f8d-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="69f8d-103">Wysyła następny element kolekcji do instrukcji `For Each...Next`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f8d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69f8d-104">Syntax</span></span>  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a><span data-ttu-id="69f8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69f8d-105">Parameters</span></span>  
  
|<span data-ttu-id="69f8d-106">Termin</span><span class="sxs-lookup"><span data-stu-id="69f8d-106">Term</span></span>|<span data-ttu-id="69f8d-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="69f8d-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="69f8d-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="69f8d-108">Required.</span></span> <span data-ttu-id="69f8d-109">Wyrażenie, które jest niejawnie konwertowane na typ funkcji iteratora lub metody dostępu `Get`, która zawiera instrukcję `Yield`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69f8d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69f8d-110">Remarks</span></span>  
 <span data-ttu-id="69f8d-111">Instrukcja `Yield` zwraca jeden element kolekcji w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="69f8d-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="69f8d-112">Instrukcja `Yield` jest zawarta w funkcji iteratora lub metodzie dostępu `Get`, która wykonuje niestandardowe iteracje w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="69f8d-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="69f8d-113">Używasz funkcji iteratora przy użyciu [for each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md) lub zapytanie LINQ.</span><span class="sxs-lookup"><span data-stu-id="69f8d-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="69f8d-114">Każda iteracja pętli `For Each` wywołuje funkcję iteratora.</span><span class="sxs-lookup"><span data-stu-id="69f8d-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="69f8d-115">Po osiągnięciu instrukcji `Yield` w funkcji iteratora zwracana jest wartość `expression`, a bieżąca lokalizacja w kodzie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="69f8d-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="69f8d-116">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="69f8d-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="69f8d-117">Niejawna konwersja musi istnieć na podstawie typu `expression` w instrukcji `Yield` do zwracanego typu iteratora.</span><span class="sxs-lookup"><span data-stu-id="69f8d-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="69f8d-118">Aby zakończyć iterację, można użyć instrukcji `Exit Function` lub `Return`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="69f8d-119">"Yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używany w funkcji `Iterator` lub metodzie dostępu `Get`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="69f8d-120">Aby uzyskać więcej informacji na temat funkcji iteratora i metod dostępu `Get`, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="69f8d-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="69f8d-121">Funkcje iteratora i metody uzyskiwania dostępu</span><span class="sxs-lookup"><span data-stu-id="69f8d-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="69f8d-122">Deklaracja funkcji iteratora lub metody dostępu `Get` musi spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="69f8d-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
- <span data-ttu-id="69f8d-123">Musi zawierać modyfikator [iteratora](../../../visual-basic/language-reference/modifiers/iterator.md) .</span><span class="sxs-lookup"><span data-stu-id="69f8d-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
- <span data-ttu-id="69f8d-124">Typem zwracanym musi być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="69f8d-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
- <span data-ttu-id="69f8d-125">Nie może mieć żadnych parametrów `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="69f8d-126">Nie można wykonać funkcji iteratora w zdarzeniu, konstruktorze wystąpień, konstruktorze statycznym lub destruktorze statycznym.</span><span class="sxs-lookup"><span data-stu-id="69f8d-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="69f8d-127">Funkcja iteratora może być funkcją anonimową.</span><span class="sxs-lookup"><span data-stu-id="69f8d-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="69f8d-128">Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="69f8d-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="69f8d-129">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="69f8d-129">Exception Handling</span></span>  
 <span data-ttu-id="69f8d-130">Instrukcja `Yield` może znajdować się wewnątrz bloku `Try` [try... Catch... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="69f8d-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="69f8d-131">Blok `Try`, który zawiera instrukcję `Yield` może mieć `Catch` bloków i może mieć blok `Finally`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="69f8d-132">Instrukcja `Yield` nie może znajdować się wewnątrz bloku `Catch` lub bloku `Finally`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="69f8d-133">Jeśli treść `For Each` (poza funkcją iteratora) zgłasza wyjątek, blok `Catch` w funkcji iteratora nie zostanie wykonany, ale jest wykonywany blok `Finally` w funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="69f8d-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="69f8d-134">Blok `Catch` wewnątrz funkcji iteratora przechwytuje tylko wyjątki występujące wewnątrz funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="69f8d-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="69f8d-135">Realizacja techniczna</span><span class="sxs-lookup"><span data-stu-id="69f8d-135">Technical Implementation</span></span>  
 <span data-ttu-id="69f8d-136">Poniższy kod zwraca `IEnumerable (Of String)` z funkcji iteratora, a następnie iteruje elementy `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="69f8d-137">Wywołanie `MyIteratorFunction` nie wykonuje treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="69f8d-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="69f8d-138">Zamiast tego wywołanie zwraca `IEnumerable(Of String)` do zmiennej `elements`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="69f8d-139">W przypadku iteracji pętli `For Each` Metoda <xref:System.Collections.IEnumerator.MoveNext%2A> jest wywoływana dla `elements`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="69f8d-140">To wywołanie wykonuje treść `MyIteratorFunction` do momentu osiągnięcia następnej instrukcji `Yield`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="69f8d-141">Instrukcja `Yield` zwraca wyrażenie, które określa nie tylko wartość zmiennej `element` do użycia przez treść pętli, ale również właściwość <xref:System.Collections.Generic.IEnumerator%601.Current%2A> elementów, która jest `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="69f8d-142">W każdej kolejnej iteracji pętli `For Each` wykonywanie treści iteratora jest kontynuowane od miejsca, w którym została pozostawiona, i ponownie zatrzymywane, gdy dociera do instrukcji `Yield`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="69f8d-143">Pętla `For Each` kończy się, gdy zostanie osiągnięty koniec funkcji iteratora lub `Return` lub `Exit Function`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69f8d-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="69f8d-144">Example</span></span>  
 <span data-ttu-id="69f8d-145">Poniższy przykład zawiera instrukcję `Yield`, która znajduje się wewnątrz elementu [... Następna](../../../visual-basic/language-reference/statements/for-next-statement.md) pętla.</span><span class="sxs-lookup"><span data-stu-id="69f8d-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="69f8d-146">Każda iteracja [dla każdej](../../../visual-basic/language-reference/statements/for-each-next-statement.md) treści instrukcji w `Main` tworzy wywołanie funkcji iteratora `Power`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="69f8d-147">Każde wywołanie funkcji iteratora przechodzi do następnego wykonania instrukcji `Yield`, która występuje w następnej iteracji pętli `For…Next`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="69f8d-148">Zwracany typ metody iteratora to <xref:System.Collections.Generic.IEnumerable%601>, typ interfejsu iteratora.</span><span class="sxs-lookup"><span data-stu-id="69f8d-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="69f8d-149">Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.</span><span class="sxs-lookup"><span data-stu-id="69f8d-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="69f8d-150">Przykład</span><span class="sxs-lookup"><span data-stu-id="69f8d-150">Example</span></span>  
 <span data-ttu-id="69f8d-151">Poniższy przykład demonstruje metodę dostępu `Get`, która jest iteratorem.</span><span class="sxs-lookup"><span data-stu-id="69f8d-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="69f8d-152">Deklaracja właściwości zawiera modyfikator `Iterator`.</span><span class="sxs-lookup"><span data-stu-id="69f8d-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="69f8d-153">Aby uzyskać więcej przykładów, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="69f8d-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69f8d-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69f8d-154">See also</span></span>

- [<span data-ttu-id="69f8d-155">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="69f8d-155">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
