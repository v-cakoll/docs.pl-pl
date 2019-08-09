---
title: zwraca kontekstowe słowo C# kluczowe — odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: 0d2c3f67715b9b2161a6c908576ac9f964ff13d6
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363128"
---
# <a name="yield-c-reference"></a><span data-ttu-id="cfdd2-102">yield (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cfdd2-102">yield (C# Reference)</span></span>

<span data-ttu-id="cfdd2-103">W przypadku użycia `yield` [kontekstowego słowa kluczowego](index.md#contextual-keywords) w instrukcji wskazuje, że metoda, operator lub `get` akcesor, w którym występuje, jest iteratorem.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-103">When you use the `yield` [contextual keyword](index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="cfdd2-104">Użycie `yield` do zdefiniowania iteratora eliminuje potrzebę jawnej dodatkowej klasy (klasy, która przechowuje stan wyliczenia, zobacz <xref:System.Collections.Generic.IEnumerator%601> na przykład <xref:System.Collections.IEnumerable> ) podczas implementowania wzorca i <xref:System.Collections.IEnumerator> dla kolekcji niestandardowej Wprowadź.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>

<span data-ttu-id="cfdd2-105">Poniższy przykład pokazuje dwie formy `yield` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-105">The following example shows the two forms of the `yield` statement.</span></span>

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a><span data-ttu-id="cfdd2-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfdd2-106">Remarks</span></span>

<span data-ttu-id="cfdd2-107">`yield return` Używasz instrukcji, aby zwrócić każdy element po jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-107">You use a `yield return` statement to return each element one at a time.</span></span>

<span data-ttu-id="cfdd2-108">Sekwencja zwrócona przez metodę iteratora może być używana przy użyciu instrukcji [foreach](foreach-in.md) lub zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-108">The sequence returned from an iterator method can be consumed by using a [foreach](foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="cfdd2-109">Każda iteracja `foreach` pętli wywołuje metodę iteratora.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="cfdd2-110">Gdy instrukcja zostanie osiągnięta w metodzie iteratora `expression` , jest zwracana, a bieżąca lokalizacja w kodzie jest zachowywana. `yield return`</span><span class="sxs-lookup"><span data-stu-id="cfdd2-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="cfdd2-111">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>

<span data-ttu-id="cfdd2-112">Możesz użyć `yield break` instrukcji, aby zakończyć iterację.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-112">You can use a `yield break` statement to end the iteration.</span></span>

<span data-ttu-id="cfdd2-113">Aby uzyskać więcej informacji na temat iteratorów [Iteratory](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="cfdd2-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>

## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="cfdd2-114">Metody iteratorów i uzyskiwania dostępu</span><span class="sxs-lookup"><span data-stu-id="cfdd2-114">Iterator methods and get accessors</span></span>

<span data-ttu-id="cfdd2-115">Deklaracja iteratora musi spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="cfdd2-115">The declaration of an iterator must meet the following requirements:</span></span>

- <span data-ttu-id="cfdd2-116">Typem zwracanym musi być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

- <span data-ttu-id="cfdd2-117">Deklaracja nie może [zawierać żadnych parametrów](in-parameter-modifier.md) [ref](ref.md) ani [out](out-parameter-modifier.md) .</span><span class="sxs-lookup"><span data-stu-id="cfdd2-117">The declaration can't have any [in](in-parameter-modifier.md) [ref](ref.md) or [out](out-parameter-modifier.md) parameters.</span></span>

<span data-ttu-id="cfdd2-118">Typ iteratora, który zwraca <xref:System.Collections.IEnumerable> lub <xref:System.Collections.IEnumerator> jest `object`. `yield`</span><span class="sxs-lookup"><span data-stu-id="cfdd2-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="cfdd2-119">Jeśli iterator zwraca <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.Generic.IEnumerator%601>, musi istnieć niejawna konwersja z typu wyrażenia w `yield return` instrukcji do parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>

<span data-ttu-id="cfdd2-120">Nie można uwzględnić `yield return` instrukcji or `yield break` w:</span><span class="sxs-lookup"><span data-stu-id="cfdd2-120">You can't include a `yield return` or `yield break` statement in:</span></span>

- <span data-ttu-id="cfdd2-121">[Wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) i [metody anonimowe](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="cfdd2-121">[Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) and [anonymous methods](../operators/delegate-operator.md).</span></span>

- <span data-ttu-id="cfdd2-122">Metody, które zawierają bloki ze słowem kluczowym unsafe.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-122">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="cfdd2-123">Aby uzyskać więcej informacji, [niebezpieczny](unsafe.md)</span><span class="sxs-lookup"><span data-stu-id="cfdd2-123">For more information, see [unsafe](unsafe.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="cfdd2-124">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="cfdd2-124">Exception handling</span></span>

<span data-ttu-id="cfdd2-125">`yield return` Instrukcja nie może znajdować się w bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-125">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="cfdd2-126">`yield return` Instrukcja może znajdować się w bloku try instrukcji try-finally.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-126">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>

<span data-ttu-id="cfdd2-127">`yield break` Instrukcja może znajdować się w bloku try lub bloku catch, ale nie w bloku finally.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-127">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>

<span data-ttu-id="cfdd2-128">Jeśli treść (poza metodą iteratora) zgłasza wyjątek `finally` , zostaje wykonany blok w metodzie iteratora. `foreach`</span><span class="sxs-lookup"><span data-stu-id="cfdd2-128">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="cfdd2-129">Implementacja techniczna</span><span class="sxs-lookup"><span data-stu-id="cfdd2-129">Technical implementation</span></span>

<span data-ttu-id="cfdd2-130">Poniższy kod zwraca `IEnumerable<string>` metodę z metody iteratora, a następnie wykonuje iterację za pośrednictwem jej elementów.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-130">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

<span data-ttu-id="cfdd2-131">Wywołanie `MyIteratorMethod` nie wykonuje treści metody.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-131">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="cfdd2-132">Zamiast tego wywołanie zwraca `IEnumerable<string>` `elements` zmienną.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-132">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>

<span data-ttu-id="cfdd2-133">W iteracji `foreach` pętli <xref:System.Collections.IEnumerator.MoveNext%2A> Metoda jest wywoływana dla `elements`.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-133">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="cfdd2-134">To wywołanie wykonuje treść `MyIteratorMethod` przed osiągnięciem następnej `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-134">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="cfdd2-135">Wyrażenie zwrócone `yield return` przez instrukcję określa nie tylko wartość <xref:System.Collections.Generic.IEnumerator%601.Current%2A> `element` zmiennej do użycia przez treść pętli `elements`, ale również właściwość, która jest `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-135">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>

<span data-ttu-id="cfdd2-136">W każdej kolejnej iteracji `foreach` pętli wykonywanie treści iteratora jest kontynuowane od miejsca, w którym została pozostawiona, po `yield return` osiągnięciu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-136">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="cfdd2-137">Pętla kończy się, gdy zostanie osiągnięty koniec metody iteratora `yield break` lub instrukcji. `foreach`</span><span class="sxs-lookup"><span data-stu-id="cfdd2-137">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>

## <a name="example"></a><span data-ttu-id="cfdd2-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfdd2-138">Example</span></span>

<span data-ttu-id="cfdd2-139">Poniższy przykład zawiera `yield return` instrukcję, która znajduje się `for` wewnątrz pętli.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-139">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="cfdd2-140">Każda iteracja `foreach` treści instrukcji `Main` w metodzie `Power` tworzy wywołanie funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-140">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="cfdd2-141">Każde wywołanie funkcji iteratora przechodzi do następnego wykonania `yield return` instrukcji, która występuje w następnej iteracji `for` pętli.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-141">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>

<span data-ttu-id="cfdd2-142">Zwracanym typem metody iteratora jest <xref:System.Collections.IEnumerable>, który jest typem interfejsu iteratora.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-142">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="cfdd2-143">Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-143">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a><span data-ttu-id="cfdd2-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfdd2-144">Example</span></span>

<span data-ttu-id="cfdd2-145">Poniższy przykład ilustruje `get` metodę dostępu, która jest iteratorem.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-145">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="cfdd2-146">W przykładzie każda `yield return` instrukcja zwraca wystąpienie klasy zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-146">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a><span data-ttu-id="cfdd2-147">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cfdd2-147">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cfdd2-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfdd2-148">See also</span></span>

- [<span data-ttu-id="cfdd2-149">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cfdd2-149">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="cfdd2-150">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cfdd2-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cfdd2-151">foreach, in</span><span class="sxs-lookup"><span data-stu-id="cfdd2-151">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="cfdd2-152">Iteratory</span><span class="sxs-lookup"><span data-stu-id="cfdd2-152">Iterators</span></span>](../../iterators.md)
