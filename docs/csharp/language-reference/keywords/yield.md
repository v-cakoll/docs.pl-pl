---
title: "yield (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4735ab33faea71b792cbc6b567884b64bd6ca029
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="yield-c-reference"></a><span data-ttu-id="084f4-102">yield (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="084f4-102">yield (C# Reference)</span></span>
<span data-ttu-id="084f4-103">Jeśli używasz `yield` — słowo kluczowe w instrukcji, możesz wskazują, że metoda, operator lub `get` dostępu, w których występuje jest iteratora.</span><span class="sxs-lookup"><span data-stu-id="084f4-103">When you use the `yield` keyword in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="084f4-104">Przy użyciu `yield` do definiowania iteratora eliminuje to potrzebę jawnego dodatkowe klasy (klasy, która przechowuje stan wyliczania, zobacz <xref:System.Collections.Generic.IEnumerator%601> przykład) podczas implementacji <xref:System.Collections.IEnumerable> i <xref:System.Collections.IEnumerator> wzorzec do kolekcji niestandardowej Typ.</span><span class="sxs-lookup"><span data-stu-id="084f4-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>  
  
 <span data-ttu-id="084f4-105">W poniższym przykładzie przedstawiono dwie formy `yield` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="084f4-105">The following example shows the two forms of the `yield` statement.</span></span>  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a><span data-ttu-id="084f4-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="084f4-106">Remarks</span></span>  
 <span data-ttu-id="084f4-107">Możesz użyć `yield return` instrukcji, aby zwracany był każdy element jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="084f4-107">You use a `yield return` statement to return each element one at a time.</span></span>  
  
 <span data-ttu-id="084f4-108">Korzystać z metodę iteratora za pomocą [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji lub zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="084f4-108">You consume an iterator method by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="084f4-109">Każdej iteracji `foreach` pętli wywołuje metodę iteratora.</span><span class="sxs-lookup"><span data-stu-id="084f4-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="084f4-110">Gdy `yield return` osiągnięciu instrukcji w metodzie iteracyjnej `expression` jest zwracany, i są przechowywane w bieżącej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="084f4-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="084f4-111">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="084f4-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="084f4-112">Można użyć `yield break` instrukcji, aby zakończyć iterację.</span><span class="sxs-lookup"><span data-stu-id="084f4-112">You can use a `yield break` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="084f4-113">Aby uzyskać więcej informacji na temat Iteratory, zobacz [Iteratory](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="084f4-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>  
  
## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="084f4-114">Metody iteratorów i pobranie akcesora</span><span class="sxs-lookup"><span data-stu-id="084f4-114">Iterator Methods and get Accessors</span></span>  
 <span data-ttu-id="084f4-115">Deklaracja iteratora musi spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="084f4-115">The declaration of an iterator must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="084f4-116">Zwracany typ musi być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="084f4-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="084f4-117">Deklaracja nie mogą zawierać [ref](../../../csharp/language-reference/keywords/ref.md) lub [limit](../../../csharp/language-reference/keywords/out.md) parametrów.</span><span class="sxs-lookup"><span data-stu-id="084f4-117">The declaration can't have any [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters.</span></span>  
  
 <span data-ttu-id="084f4-118">`yield` Typu zwracającą iterator <xref:System.Collections.IEnumerable> lub <xref:System.Collections.IEnumerator> jest `object`.</span><span class="sxs-lookup"><span data-stu-id="084f4-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="084f4-119">Jeśli zwróci iteratora <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.Generic.IEnumerator%601>, musi być niejawna konwersja z typu wyrażenia w `yield return` instrukcji do parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="084f4-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>  
  
 <span data-ttu-id="084f4-120">Nie można uwzględnić `yield return` lub `yield break` instrukcji metod, które mają następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="084f4-120">You can't include a `yield return` or `yield break` statement in methods that have the following characteristics:</span></span>  
  
-   <span data-ttu-id="084f4-121">Metody anonimowe.</span><span class="sxs-lookup"><span data-stu-id="084f4-121">Anonymous methods.</span></span> <span data-ttu-id="084f4-122">Aby uzyskać więcej informacji, zobacz [metod anonimowych](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="084f4-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
-   <span data-ttu-id="084f4-123">Metody, które zawierają bloki ze słowem kluczowym unsafe.</span><span class="sxs-lookup"><span data-stu-id="084f4-123">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="084f4-124">Aby uzyskać więcej informacji, zobacz [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="084f4-124">For more information, see [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="084f4-125">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="084f4-125">Exception Handling</span></span>  
 <span data-ttu-id="084f4-126">A `yield return` instrukcja nie może znajdować się w bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="084f4-126">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="084f4-127">A `yield return` instrukcja może znajdować się w bloku try instrukcji try-finally.</span><span class="sxs-lookup"><span data-stu-id="084f4-127">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>  
  
 <span data-ttu-id="084f4-128">A `yield break` instrukcja może znajdować się w bloku try lub bloku catch, ale nie bloku finally.</span><span class="sxs-lookup"><span data-stu-id="084f4-128">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>  
  
 <span data-ttu-id="084f4-129">Jeśli `foreach` treści (poza metodą iteratora) zgłasza wyjątek, `finally` wykonaniu bloku w metodzie iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="084f4-129">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="084f4-130">Realizacja techniczna</span><span class="sxs-lookup"><span data-stu-id="084f4-130">Technical Implementation</span></span>  
 <span data-ttu-id="084f4-131">Poniższy kod zwraca `IEnumerable<string>` z metody iteracyjne, a następnie iteruje po jej elementów.</span><span class="sxs-lookup"><span data-stu-id="084f4-131">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 <span data-ttu-id="084f4-132">Wywołanie `MyIteratorMethod` treść metody nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="084f4-132">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="084f4-133">Zamiast tego wywołanie zwraca `IEnumerable<string>` do `elements` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="084f4-133">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="084f4-134">Na iterację `foreach` pętli, <xref:System.Collections.IEnumerator.MoveNext%2A> metoda jest wywoływana dla `elements`.</span><span class="sxs-lookup"><span data-stu-id="084f4-134">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="084f4-135">To wywołanie wykonuje treści `MyIteratorMethod` aż do następnego `yield return` osiągnięciu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="084f4-135">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="084f4-136">Wyrażenie zwracane przez `yield return` instrukcji określa nie tylko wartość `element` zmienna do użycia przez pętli, ale także <xref:System.Collections.Generic.IEnumerator%601.Current%2A> właściwość `elements`, która jest `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="084f4-136">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>  
  
 <span data-ttu-id="084f4-137">W każdej iteracji kolejnych `foreach` pętli, wykonanie treści iteratora kontynuuje działanie od miejsca przerwał, ponownie zatrzymywanie po osiągnięciu `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="084f4-137">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="084f4-138">`foreach` Pętli działanie jest kończone po na końcu metody iterator lub `yield break` osiągnięciu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="084f4-138">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="084f4-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="084f4-139">Example</span></span>  
 <span data-ttu-id="084f4-140">W poniższym przykładzie przedstawiono `yield return` instrukcji, która znajduje się wewnątrz `for` pętli.</span><span class="sxs-lookup"><span data-stu-id="084f4-140">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="084f4-141">Każdej iteracji `foreach` treść instrukcji w `Process` tworzy wywołanie `Power` funkcji iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="084f4-141">Each iteration of the `foreach` statement body in `Process` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="084f4-142">Każde wywołanie funkcji iteracyjnej przechodzi do następnego wykonywanie `yield return` instrukcja, która występuje w ciągu następnej iteracji `for` pętli.</span><span class="sxs-lookup"><span data-stu-id="084f4-142">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>  
  
 <span data-ttu-id="084f4-143">Zwracany typ metody iteracyjnej jest <xref:System.Collections.IEnumerable>, który jest typem interfejsu iteratora.</span><span class="sxs-lookup"><span data-stu-id="084f4-143">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="084f4-144">Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.</span><span class="sxs-lookup"><span data-stu-id="084f4-144">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="084f4-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="084f4-145">Example</span></span>  
 <span data-ttu-id="084f4-146">W poniższym przykładzie pokazano `get` dostępu, który jest iteratora.</span><span class="sxs-lookup"><span data-stu-id="084f4-146">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="084f4-147">W tym przykładzie każdy `yield return` instrukcja zwraca wystąpienia klasy zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="084f4-147">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="084f4-148">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="084f4-148">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="084f4-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="084f4-149">See Also</span></span>  
 [<span data-ttu-id="084f4-150">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="084f4-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="084f4-151">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="084f4-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="084f4-152">Instrukcja foreach w</span><span class="sxs-lookup"><span data-stu-id="084f4-152">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="084f4-153">Iteratory</span><span class="sxs-lookup"><span data-stu-id="084f4-153">Iterators</span></span>](../../iterators.md)
