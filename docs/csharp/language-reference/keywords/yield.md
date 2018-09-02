---
title: yield (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: c566e2c83a6c40acfd85c1822d28cbaa097e4449
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388169"
---
# <a name="yield-c-reference"></a><span data-ttu-id="c6b5d-102">yield (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c6b5d-102">yield (C# Reference)</span></span>
<span data-ttu-id="c6b5d-103">Kiedy używasz `yield` — słowo kluczowe w instrukcji powoduje wskazanie metody, operatora lub `get` dostępu, w której występuje jest iteratorem.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-103">When you use the `yield` keyword in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="c6b5d-104">Za pomocą `yield` do zdefiniowania iteratora eliminuje konieczność jawnego użycia dodatkowej klasy (klasy przechowującej stan wyliczenia, zobacz <xref:System.Collections.Generic.IEnumerator%601> przykład) podczas implementacji <xref:System.Collections.IEnumerable> i <xref:System.Collections.IEnumerator> wzorca dla kolekcji niestandardowej Typ.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>  
  
 <span data-ttu-id="c6b5d-105">W poniższym przykładzie pokazano dwa rodzaje `yield` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-105">The following example shows the two forms of the `yield` statement.</span></span>  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a><span data-ttu-id="c6b5d-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6b5d-106">Remarks</span></span>  
 <span data-ttu-id="c6b5d-107">Możesz użyć `yield return` instrukcja zwraca każdy element w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-107">You use a `yield return` statement to return each element one at a time.</span></span>  
  
 <span data-ttu-id="c6b5d-108">Korzystanie z metody iteratora przy użyciu [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji lub zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-108">You consume an iterator method by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="c6b5d-109">Każda iteracja `foreach` pętli wywołuje metodę iteratora.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="c6b5d-110">Gdy `yield return` osiągnięciu instrukcji w metodzie iteratora `expression` jest zwracany, a bieżąca lokalizacja w kodzie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="c6b5d-111">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="c6b5d-112">Możesz użyć `yield break` instrukcję, aby zakończyć iterację.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-112">You can use a `yield break` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="c6b5d-113">Aby uzyskać więcej informacji dotyczących iteratorów, zobacz [Iteratory](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="c6b5d-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>  
  
## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="c6b5d-114">Metody iteratorów i pobranie akcesora</span><span class="sxs-lookup"><span data-stu-id="c6b5d-114">Iterator Methods and get Accessors</span></span>  
 <span data-ttu-id="c6b5d-115">Deklaracja iteratora musi spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="c6b5d-115">The declaration of an iterator must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="c6b5d-116">Zwracany typ musi być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="c6b5d-117">Deklaracja nie może zawierać żadnych [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-117">The declaration can't have any [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>  
  
 <span data-ttu-id="c6b5d-118">`yield` Typ iteratora zwracającego <xref:System.Collections.IEnumerable> lub <xref:System.Collections.IEnumerator> jest `object`.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="c6b5d-119">Jeśli iterator zwraca <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.Generic.IEnumerator%601>, musi istnieć niejawna konwersja z typu wyrażenia w `yield return` instrukcję, aby parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>  
  
 <span data-ttu-id="c6b5d-120">Nie można uwzględnić `yield return` lub `yield break` instrukcji w metodach mających następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="c6b5d-120">You can't include a `yield return` or `yield break` statement in methods that have the following characteristics:</span></span>  
  
-   <span data-ttu-id="c6b5d-121">Metody anonimowe.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-121">Anonymous methods.</span></span> <span data-ttu-id="c6b5d-122">Aby uzyskać więcej informacji, zobacz [anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="c6b5d-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
-   <span data-ttu-id="c6b5d-123">Metody, które zawierają bloki ze słowem kluczowym unsafe.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-123">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="c6b5d-124">Aby uzyskać więcej informacji, zobacz [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="c6b5d-124">For more information, see [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="c6b5d-125">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="c6b5d-125">Exception Handling</span></span>  
 <span data-ttu-id="c6b5d-126">A `yield return` instrukcja nie może znajdować się w bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-126">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="c6b5d-127">A `yield return` instrukcji może znajdować się w bloku try instrukcji try-finally.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-127">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>  
  
 <span data-ttu-id="c6b5d-128">A `yield break` instrukcji może znajdować się w bloku try lub bloku catch, ale nie bloku finally.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-128">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>  
  
 <span data-ttu-id="c6b5d-129">Jeśli `foreach` treści (poza metodą iteratora) zgłasza wyjątek, `finally` blokowanie w metodzie iteratora jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-129">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="c6b5d-130">Realizacja techniczna</span><span class="sxs-lookup"><span data-stu-id="c6b5d-130">Technical Implementation</span></span>  
 <span data-ttu-id="c6b5d-131">Poniższy kod zwraca `IEnumerable<string>` z metody iteratora i następnie iterację przez jego elementów.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-131">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 <span data-ttu-id="c6b5d-132">Wywołanie `MyIteratorMethod` treści metody nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-132">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="c6b5d-133">Zamiast tego to wywołanie zwraca `IEnumerable<string>` do `elements` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-133">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="c6b5d-134">Podczas iteracji `foreach` pętli, <xref:System.Collections.IEnumerator.MoveNext%2A> metoda jest wywoływana dla `elements`.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-134">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="c6b5d-135">To wywołanie wykonuje treść `MyIteratorMethod` aż do następnej `yield return` osiągnięta zostanie instrukcja.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-135">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="c6b5d-136">Wyrażenie zwracane przez `yield return` Instrukcja określa nie tylko wartość `element` do użycia w treści pętli, ale także <xref:System.Collections.Generic.IEnumerator%601.Current%2A> właściwość `elements`, czyli `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-136">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>  
  
 <span data-ttu-id="c6b5d-137">Na poszczególnych kolejnych iteracjach `foreach` pętli, wykonywanie treści iteratora jest kontynuowane od miejsca zostało przerwane, zatrzymywane ponownie po osiągnięciu `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-137">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="c6b5d-138">`foreach` Pętli jest ukończone Kiedy koniec metody iteratora lub `yield break` osiągnięta zostanie instrukcja.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-138">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6b5d-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="c6b5d-139">Example</span></span>  
 <span data-ttu-id="c6b5d-140">W poniższym przykładzie przedstawiono `yield return` instrukcji, która znajduje się wewnątrz `for` pętli.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-140">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="c6b5d-141">Każda iteracja `foreach` treść instrukcji w `Main` metoda tworzy wywołanie `Power` funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-141">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="c6b5d-142">Każde wywołanie funkcji iteratora przechodzi do następnego wykonania `yield return` instrukcję, która występuje w ciągu następnej iteracji `for` pętli.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-142">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>  
  
 <span data-ttu-id="c6b5d-143">Zwracany typ metody iteratora jest <xref:System.Collections.IEnumerable>, który jest typem interfejsu iteratora.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-143">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="c6b5d-144">Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-144">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="c6b5d-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="c6b5d-145">Example</span></span>  
 <span data-ttu-id="c6b5d-146">W poniższym przykładzie pokazano `get` metodę dostępu, która jest iteratorem.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-146">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="c6b5d-147">W tym przykładzie każdy `yield return` instrukcja zwraca wystąpienie klasy zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c6b5d-147">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c6b5d-148">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c6b5d-148">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c6b5d-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6b5d-149">See Also</span></span>

- [<span data-ttu-id="c6b5d-150">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c6b5d-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c6b5d-151">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c6b5d-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c6b5d-152">foreach, in</span><span class="sxs-lookup"><span data-stu-id="c6b5d-152">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
- [<span data-ttu-id="c6b5d-153">Iteratory</span><span class="sxs-lookup"><span data-stu-id="c6b5d-153">Iterators</span></span>](../../iterators.md)
