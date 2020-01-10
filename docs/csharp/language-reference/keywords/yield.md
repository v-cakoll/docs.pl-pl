---
title: zwraca kontekstowe słowo C# kluczowe — odwołanie
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: e3c9e37e7b543eaddae837a85604c4ba91fbc744
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712783"
---
# <a name="yield-c-reference"></a><span data-ttu-id="7c10c-102">yield (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7c10c-102">yield (C# Reference)</span></span>

<span data-ttu-id="7c10c-103">W przypadku korzystania z `yield` [kontekstowego słowa kluczowego](index.md#contextual-keywords) w instrukcji wskazuje, że metoda, operator lub akcesor `get`, w którym występuje, jest to iterator.</span><span class="sxs-lookup"><span data-stu-id="7c10c-103">When you use the `yield` [contextual keyword](index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="7c10c-104">Użycie `yield` do zdefiniowania iteratora eliminuje potrzebę jawnej dodatkowej klasy (klasy, która przechowuje stan wyliczenia, zobacz <xref:System.Collections.Generic.IEnumerator%601> na przykład) podczas implementowania wzorca <xref:System.Collections.IEnumerable> i <xref:System.Collections.IEnumerator> dla niestandardowego typu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7c10c-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>

<span data-ttu-id="7c10c-105">Poniższy przykład przedstawia dwie formy instrukcji `yield`.</span><span class="sxs-lookup"><span data-stu-id="7c10c-105">The following example shows the two forms of the `yield` statement.</span></span>

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a><span data-ttu-id="7c10c-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c10c-106">Remarks</span></span>

<span data-ttu-id="7c10c-107">Używasz instrukcji `yield return`, aby zwrócić każdy element po jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="7c10c-107">You use a `yield return` statement to return each element one at a time.</span></span>

<span data-ttu-id="7c10c-108">Sekwencja zwrócona przez metodę iteratora może być używana przy użyciu instrukcji [foreach](foreach-in.md) lub zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="7c10c-108">The sequence returned from an iterator method can be consumed by using a [foreach](foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="7c10c-109">Każda iteracja pętli `foreach` wywołuje metodę iteratora.</span><span class="sxs-lookup"><span data-stu-id="7c10c-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="7c10c-110">Po osiągnięciu instrukcji `yield return` w metodzie iteratora jest zwracana `expression`, a bieżąca lokalizacja w kodzie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="7c10c-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="7c10c-111">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="7c10c-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>

<span data-ttu-id="7c10c-112">Możesz użyć instrukcji `yield break`, aby zakończyć iterację.</span><span class="sxs-lookup"><span data-stu-id="7c10c-112">You can use a `yield break` statement to end the iteration.</span></span>

<span data-ttu-id="7c10c-113">Aby uzyskać więcej informacji na temat iteratorów [Iteratory](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="7c10c-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>

## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="7c10c-114">Metody iteratorów i uzyskiwania dostępu</span><span class="sxs-lookup"><span data-stu-id="7c10c-114">Iterator methods and get accessors</span></span>

<span data-ttu-id="7c10c-115">Deklaracja iteratora musi spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="7c10c-115">The declaration of an iterator must meet the following requirements:</span></span>

- <span data-ttu-id="7c10c-116">Typem zwracanym musi być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="7c10c-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

- <span data-ttu-id="7c10c-117">Deklaracja nie może [zawierać żadnych parametrów](in-parameter-modifier.md) [ref](ref.md) ani [out](out-parameter-modifier.md) .</span><span class="sxs-lookup"><span data-stu-id="7c10c-117">The declaration can't have any [in](in-parameter-modifier.md) [ref](ref.md) or [out](out-parameter-modifier.md) parameters.</span></span>

<span data-ttu-id="7c10c-118">`yield` typ iteratora zwracającego <xref:System.Collections.IEnumerable> lub <xref:System.Collections.IEnumerator> jest `object`.</span><span class="sxs-lookup"><span data-stu-id="7c10c-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="7c10c-119">Jeśli iterator zwraca <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.Generic.IEnumerator%601>, musi istnieć niejawna konwersja z typu wyrażenia w instrukcji `yield return` do parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="7c10c-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>

<span data-ttu-id="7c10c-120">Nie można uwzględnić instrukcji `yield return` lub `yield break` w:</span><span class="sxs-lookup"><span data-stu-id="7c10c-120">You can't include a `yield return` or `yield break` statement in:</span></span>

- <span data-ttu-id="7c10c-121">[Wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) i [metody anonimowe](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="7c10c-121">[Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) and [anonymous methods](../operators/delegate-operator.md).</span></span>

- <span data-ttu-id="7c10c-122">Metody, które zawierają bloki ze słowem kluczowym unsafe.</span><span class="sxs-lookup"><span data-stu-id="7c10c-122">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="7c10c-123">Aby uzyskać więcej informacji, [niebezpieczny](unsafe.md)</span><span class="sxs-lookup"><span data-stu-id="7c10c-123">For more information, see [unsafe](unsafe.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="7c10c-124">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="7c10c-124">Exception handling</span></span>

<span data-ttu-id="7c10c-125">Instrukcja `yield return` nie może znajdować się w bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="7c10c-125">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="7c10c-126">Instrukcja `yield return` może znajdować się w bloku try instrukcji try-finally.</span><span class="sxs-lookup"><span data-stu-id="7c10c-126">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>

<span data-ttu-id="7c10c-127">Instrukcja `yield break` może znajdować się w bloku try lub bloku catch, ale nie w bloku finally.</span><span class="sxs-lookup"><span data-stu-id="7c10c-127">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>

<span data-ttu-id="7c10c-128">Jeśli treść `foreach` (poza metodą iteratora) zgłosi wyjątek, zostanie wykonany blok `finally` w metodzie iteratora.</span><span class="sxs-lookup"><span data-stu-id="7c10c-128">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="7c10c-129">Implementacja techniczna</span><span class="sxs-lookup"><span data-stu-id="7c10c-129">Technical implementation</span></span>

<span data-ttu-id="7c10c-130">Poniższy kod zwraca `IEnumerable<string>` z metody iteratora, a następnie iteruje przez jego elementy.</span><span class="sxs-lookup"><span data-stu-id="7c10c-130">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

<span data-ttu-id="7c10c-131">Wywołanie `MyIteratorMethod` nie wykonuje treści metody.</span><span class="sxs-lookup"><span data-stu-id="7c10c-131">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="7c10c-132">Zamiast tego wywołanie zwraca `IEnumerable<string>` do zmiennej `elements`.</span><span class="sxs-lookup"><span data-stu-id="7c10c-132">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>

<span data-ttu-id="7c10c-133">W przypadku iteracji pętli `foreach` Metoda <xref:System.Collections.IEnumerator.MoveNext%2A> jest wywoływana dla `elements`.</span><span class="sxs-lookup"><span data-stu-id="7c10c-133">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="7c10c-134">To wywołanie wykonuje treść `MyIteratorMethod` do momentu osiągnięcia następnej instrukcji `yield return`.</span><span class="sxs-lookup"><span data-stu-id="7c10c-134">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="7c10c-135">Wyrażenie zwrócone przez instrukcję `yield return` określa nie tylko wartość zmiennej `element` do użycia przez treść pętli, ale również właściwość <xref:System.Collections.Generic.IEnumerator%601.Current%2A> `elements`, która jest `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="7c10c-135">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>

<span data-ttu-id="7c10c-136">W każdej kolejnej iteracji pętli `foreach` wykonywanie treści iteratora jest kontynuowane od miejsca, w którym została pozostawiona, i ponownie zatrzymywane, gdy dociera do instrukcji `yield return`.</span><span class="sxs-lookup"><span data-stu-id="7c10c-136">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="7c10c-137">Pętla `foreach` kończy się, gdy zostanie osiągnięty koniec metody iteratora lub instrukcji `yield break`.</span><span class="sxs-lookup"><span data-stu-id="7c10c-137">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>

## <a name="example"></a><span data-ttu-id="7c10c-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c10c-138">Example</span></span>

<span data-ttu-id="7c10c-139">Poniższy przykład zawiera instrukcję `yield return`, która znajduje się wewnątrz pętli `for`.</span><span class="sxs-lookup"><span data-stu-id="7c10c-139">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="7c10c-140">Każda iteracja treści instrukcji `foreach` w metodzie `Main` tworzy wywołanie funkcji iteratora `Power`.</span><span class="sxs-lookup"><span data-stu-id="7c10c-140">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="7c10c-141">Każde wywołanie funkcji iteratora przechodzi do następnego wykonania instrukcji `yield return`, która występuje w następnej iteracji pętli `for`.</span><span class="sxs-lookup"><span data-stu-id="7c10c-141">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>

<span data-ttu-id="7c10c-142">Zwracany typ metody iteratora to <xref:System.Collections.IEnumerable>, który jest typem interfejsu iteratora.</span><span class="sxs-lookup"><span data-stu-id="7c10c-142">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="7c10c-143">Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.</span><span class="sxs-lookup"><span data-stu-id="7c10c-143">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a><span data-ttu-id="7c10c-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c10c-144">Example</span></span>

<span data-ttu-id="7c10c-145">Poniższy przykład demonstruje metodę dostępu `get`, która jest iteratorem.</span><span class="sxs-lookup"><span data-stu-id="7c10c-145">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="7c10c-146">W przykładzie każda instrukcja `yield return` zwraca wystąpienie klasy zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7c10c-146">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a><span data-ttu-id="7c10c-147">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7c10c-147">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7c10c-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c10c-148">See also</span></span>

- [<span data-ttu-id="7c10c-149">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7c10c-149">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="7c10c-150">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7c10c-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7c10c-151">foreach, in</span><span class="sxs-lookup"><span data-stu-id="7c10c-151">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="7c10c-152">Iteratory</span><span class="sxs-lookup"><span data-stu-id="7c10c-152">Iterators</span></span>](../../iterators.md)
