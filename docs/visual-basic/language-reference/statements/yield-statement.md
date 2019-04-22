---
title: Yield — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: fea91731694f18625e43c5545b353851e72234a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821091"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="bd464-102">Yield — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd464-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="bd464-103">Wysyła następnego elementu kolekcji do `For Each...Next` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bd464-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd464-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd464-104">Syntax</span></span>  
  
```  
Yield expression  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd464-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd464-105">Parameters</span></span>  
  
|<span data-ttu-id="bd464-106">Termin</span><span class="sxs-lookup"><span data-stu-id="bd464-106">Term</span></span>|<span data-ttu-id="bd464-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="bd464-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="bd464-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="bd464-108">Required.</span></span> <span data-ttu-id="bd464-109">Wyrażenie, które jest niejawnie konwertowany na typ funkcji iteratora lub `Get` dostępu, który zawiera `Yield` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bd464-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd464-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd464-110">Remarks</span></span>  
 <span data-ttu-id="bd464-111">`Yield` Instrukcja zwraca jeden element kolekcji naraz.</span><span class="sxs-lookup"><span data-stu-id="bd464-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="bd464-112">`Yield` Instrukcja znajduje się w funkcji iteratora lub `Get` akcesora wykonywania niestandardowych iteracji przez kolekcję.</span><span class="sxs-lookup"><span data-stu-id="bd464-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="bd464-113">Korzystać z funkcji iteratora przy użyciu [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md) lub kwerendę LINQ.</span><span class="sxs-lookup"><span data-stu-id="bd464-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="bd464-114">Każda iteracja `For Each` pętli wywołuje funkcję iteratora.</span><span class="sxs-lookup"><span data-stu-id="bd464-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="bd464-115">Gdy `Yield` w funkcji iteratora osiągnięta zostanie instrukcja `expression` jest zwracany, a bieżąca lokalizacja w kodzie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="bd464-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="bd464-116">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="bd464-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="bd464-117">Musi istnieć niejawna konwersja typu `expression` w `Yield` instrukcję, aby zwracany typ iteratora.</span><span class="sxs-lookup"><span data-stu-id="bd464-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="bd464-118">Możesz użyć `Exit Function` lub `Return` instrukcję, aby zakończyć iterację.</span><span class="sxs-lookup"><span data-stu-id="bd464-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="bd464-119">"Yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest on używany w `Iterator` funkcji lub `Get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="bd464-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="bd464-120">Aby uzyskać więcej informacji na temat funkcji iteratora i `Get` metod dostępu, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="bd464-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="bd464-121">Iterator funkcje i metody dostępu Get</span><span class="sxs-lookup"><span data-stu-id="bd464-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="bd464-122">Deklaracja funkcji iteratora lub `Get` metody dostępu muszą spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="bd464-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="bd464-123">Musi on zawierać [iteratora](../../../visual-basic/language-reference/modifiers/iterator.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="bd464-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
-   <span data-ttu-id="bd464-124">Zwracany typ musi być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="bd464-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="bd464-125">Nie może zawierać żadnych `ByRef` parametrów.</span><span class="sxs-lookup"><span data-stu-id="bd464-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="bd464-126">Funkcji iteratora nie może wystąpić w zdarzeń, konstruktora wystąpienia, statyczny Konstruktor lub destruktor statyczne.</span><span class="sxs-lookup"><span data-stu-id="bd464-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="bd464-127">Funkcji iteratora, może być funkcją anonimową.</span><span class="sxs-lookup"><span data-stu-id="bd464-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="bd464-128">Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="bd464-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="bd464-129">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="bd464-129">Exception Handling</span></span>  
 <span data-ttu-id="bd464-130">A `Yield` instrukcji może znajdować się wewnątrz `Try` bloku [spróbuj... CATCH... Na koniec instrukcji](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bd464-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="bd464-131">A `Try` blok, który ma `Yield` instrukcja może mieć `Catch` blokuje i może mieć `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="bd464-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="bd464-132">A `Yield` instrukcja nie może znajdować się wewnątrz `Catch` bloku lub `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="bd464-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="bd464-133">Jeśli `For Each` treści (poza funkcji iteratora) zgłasza wyjątek, `Catch` nie jest wykonywany blok w funkcji iteratora, ale `Finally` wykonaniu bloku w funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="bd464-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="bd464-134">A `Catch` bloku sterującego funkcji iteratora przechwytuje tylko wyjątki występujące wewnątrz funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="bd464-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="bd464-135">Realizacja techniczna</span><span class="sxs-lookup"><span data-stu-id="bd464-135">Technical Implementation</span></span>  
 <span data-ttu-id="bd464-136">Poniższy kod zwraca `IEnumerable (Of String)` z funkcji iteratora i następnie iterację przez elementy `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="bd464-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="bd464-137">Wywołanie `MyIteratorFunction` nie jest wykonywany treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="bd464-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="bd464-138">Zamiast tego to wywołanie zwraca `IEnumerable(Of String)` do `elements` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="bd464-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="bd464-139">Podczas iteracji `For Each` pętli, <xref:System.Collections.IEnumerator.MoveNext%2A> metoda jest wywoływana dla `elements`.</span><span class="sxs-lookup"><span data-stu-id="bd464-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="bd464-140">To wywołanie wykonuje treść `MyIteratorFunction` aż do następnej `Yield` osiągnięta zostanie instrukcja.</span><span class="sxs-lookup"><span data-stu-id="bd464-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="bd464-141">`Yield` Instrukcja zwraca wyrażenie, które określa nie tylko wartość `element` do użycia w treści pętli, ale także <xref:System.Collections.Generic.IEnumerator%601.Current%2A> właściwości elementów, która jest `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="bd464-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="bd464-142">Na poszczególnych kolejnych iteracjach `For Each` pętli, wykonywanie treści iteratora jest kontynuowane od miejsca zostało przerwane, zatrzymywane ponownie po osiągnięciu `Yield` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bd464-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="bd464-143">`For Each` Pętli działanie jest kończone po zakończeniu funkcji iteratora lub `Return` lub `Exit Function` osiągnięta zostanie instrukcja.</span><span class="sxs-lookup"><span data-stu-id="bd464-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd464-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd464-144">Example</span></span>  
 <span data-ttu-id="bd464-145">W poniższym przykładzie przedstawiono `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="bd464-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="bd464-146">Każda iteracja [dla każdego](../../../visual-basic/language-reference/statements/for-each-next-statement.md) treść instrukcji w `Main` tworzy wywołanie `Power` funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="bd464-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="bd464-147">Każde wywołanie funkcji iteratora przechodzi do następnego wykonania `Yield` instrukcję, która występuje w ciągu następnej iteracji `For…Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="bd464-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="bd464-148">Zwracany typ metody iteratora jest <xref:System.Collections.Generic.IEnumerable%601>, typem interfejsu iteratora.</span><span class="sxs-lookup"><span data-stu-id="bd464-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="bd464-149">Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.</span><span class="sxs-lookup"><span data-stu-id="bd464-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="bd464-150">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd464-150">Example</span></span>  
 <span data-ttu-id="bd464-151">W poniższym przykładzie pokazano `Get` metodę dostępu, która jest iteratorem.</span><span class="sxs-lookup"><span data-stu-id="bd464-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="bd464-152">Deklaracja właściwości zawiera `Iterator` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="bd464-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="bd464-153">Aby uzyskać więcej przykładów, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="bd464-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd464-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd464-154">See also</span></span>

- [<span data-ttu-id="bd464-155">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="bd464-155">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
