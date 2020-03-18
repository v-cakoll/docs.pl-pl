---
title: yield contextual — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: e3c9e37e7b543eaddae837a85604c4ba91fbc744
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712783"
---
# <a name="yield-c-reference"></a><span data-ttu-id="b0682-102">yield (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b0682-102">yield (C# Reference)</span></span>

<span data-ttu-id="b0682-103">Korzystając z `yield` [kontekstowe słowo kluczowe](index.md#contextual-keywords) w instrukcji, należy wskazać, `get` że metoda, operator lub akcesor, w którym pojawia się jest iteratorem.</span><span class="sxs-lookup"><span data-stu-id="b0682-103">When you use the `yield` [contextual keyword](index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="b0682-104">Za `yield` pomocą do definiowania iterator eliminuje potrzebę jawne klasy dodatkowej (klasa, <xref:System.Collections.Generic.IEnumerator%601> która przechowuje stan dla <xref:System.Collections.IEnumerable> wyliczenia, zobacz na przykład) podczas implementowania i <xref:System.Collections.IEnumerator> wzorzec dla typu kolekcji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="b0682-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>

<span data-ttu-id="b0682-105">W poniższym przykładzie przedstawiono `yield` dwie formy instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b0682-105">The following example shows the two forms of the `yield` statement.</span></span>

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a><span data-ttu-id="b0682-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0682-106">Remarks</span></span>

<span data-ttu-id="b0682-107">Instrukcja `yield return` służy do zwracania każdego elementu po jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="b0682-107">You use a `yield return` statement to return each element one at a time.</span></span>

<span data-ttu-id="b0682-108">Sekwencja zwrócona z metody iteratora mogą być używane przy użyciu [foreach](foreach-in.md) instrukcji lub kwerendy LINQ.</span><span class="sxs-lookup"><span data-stu-id="b0682-108">The sequence returned from an iterator method can be consumed by using a [foreach](foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="b0682-109">Każda iteracja `foreach` pętli wywołuje metodę iterator.</span><span class="sxs-lookup"><span data-stu-id="b0682-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="b0682-110">Po `yield return` osiągnięciu instrukcji w metodzie iterator, `expression` jest zwracany, a bieżąca lokalizacja w kodzie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="b0682-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="b0682-111">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="b0682-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>

<span data-ttu-id="b0682-112">Można użyć `yield break` instrukcji, aby zakończyć iterację.</span><span class="sxs-lookup"><span data-stu-id="b0682-112">You can use a `yield break` statement to end the iteration.</span></span>

<span data-ttu-id="b0682-113">Aby uzyskać więcej informacji na temat iteratorów, zobacz [Iterytory](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="b0682-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>

## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="b0682-114">Metody iteratori i uzyskać akcesory</span><span class="sxs-lookup"><span data-stu-id="b0682-114">Iterator methods and get accessors</span></span>

<span data-ttu-id="b0682-115">Deklaracja iteratora musi spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="b0682-115">The declaration of an iterator must meet the following requirements:</span></span>

- <span data-ttu-id="b0682-116">Typ powrotu <xref:System.Collections.IEnumerable>musi <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator>być <xref:System.Collections.Generic.IEnumerator%601>, , , lub .</span><span class="sxs-lookup"><span data-stu-id="b0682-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

- <span data-ttu-id="b0682-117">Deklaracja nie może mieć żadnych [parametrów](in-parameter-modifier.md) [ref](ref.md) lub [out.](out-parameter-modifier.md)</span><span class="sxs-lookup"><span data-stu-id="b0682-117">The declaration can't have any [in](in-parameter-modifier.md) [ref](ref.md) or [out](out-parameter-modifier.md) parameters.</span></span>

<span data-ttu-id="b0682-118">Typ `yield` iterator, który <xref:System.Collections.IEnumerable> zwraca <xref:System.Collections.IEnumerator> `object`lub jest .</span><span class="sxs-lookup"><span data-stu-id="b0682-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="b0682-119">Jeśli iterator <xref:System.Collections.Generic.IEnumerable%601> zwraca <xref:System.Collections.Generic.IEnumerator%601>lub , musi istnieć niejawna konwersja z typu wyrażenia w `yield return` instrukcji do parametru typu ogólnego .</span><span class="sxs-lookup"><span data-stu-id="b0682-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>

<span data-ttu-id="b0682-120">Nie można dołączyć `yield return` ani `yield break` oświadczenia w:</span><span class="sxs-lookup"><span data-stu-id="b0682-120">You can't include a `yield return` or `yield break` statement in:</span></span>

- <span data-ttu-id="b0682-121">[Wyrażenia Lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) i [metody anonimowe](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b0682-121">[Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) and [anonymous methods](../operators/delegate-operator.md).</span></span>

- <span data-ttu-id="b0682-122">Metody, które zawierają bloki ze słowem kluczowym unsafe.</span><span class="sxs-lookup"><span data-stu-id="b0682-122">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="b0682-123">Aby uzyskać więcej informacji, zobacz [niebezpieczne](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="b0682-123">For more information, see [unsafe](unsafe.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="b0682-124">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="b0682-124">Exception handling</span></span>

<span data-ttu-id="b0682-125">Instrukcji `yield return` nie można zlokalizować w bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="b0682-125">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="b0682-126">Instrukcja `yield return` może znajdować się w bloku try instrukcji try-finally.</span><span class="sxs-lookup"><span data-stu-id="b0682-126">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>

<span data-ttu-id="b0682-127">Instrukcja `yield break` może znajdować się w bloku try lub catch bloku, ale nie finally bloku.</span><span class="sxs-lookup"><span data-stu-id="b0682-127">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>

<span data-ttu-id="b0682-128">Jeśli `foreach` treść (poza metody iterator) zgłasza wyjątek, `finally` blok w metodzie iteratorem jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="b0682-128">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="b0682-129">Wdrożenie techniczne</span><span class="sxs-lookup"><span data-stu-id="b0682-129">Technical implementation</span></span>

<span data-ttu-id="b0682-130">Poniższy kod zwraca `IEnumerable<string>` z metody iterator, a następnie iteruje za pośrednictwem jego elementów.</span><span class="sxs-lookup"><span data-stu-id="b0682-130">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

<span data-ttu-id="b0682-131">Wywołanie `MyIteratorMethod` nie wykonuje treści metody.</span><span class="sxs-lookup"><span data-stu-id="b0682-131">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="b0682-132">Zamiast tego wywołanie zwraca do `IEnumerable<string>` zmiennej. `elements`</span><span class="sxs-lookup"><span data-stu-id="b0682-132">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>

<span data-ttu-id="b0682-133">W iteracji `foreach` pętli <xref:System.Collections.IEnumerator.MoveNext%2A> metoda jest wywoływana `elements`dla .</span><span class="sxs-lookup"><span data-stu-id="b0682-133">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="b0682-134">To wywołanie wykonuje `MyIteratorMethod` treść aż `yield return` do osiągnięcia następnej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b0682-134">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="b0682-135">Wyrażenie zwracane przez `yield return` instrukcję określa nie tylko `element` wartość zmiennej do zużycia <xref:System.Collections.Generic.IEnumerator%601.Current%2A> przez `elements`treść pętli, ale także właściwość , która jest . `IEnumerable<string>`</span><span class="sxs-lookup"><span data-stu-id="b0682-135">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>

<span data-ttu-id="b0682-136">Przy każdej kolejnej `foreach` iteracji pętli wykonanie treści iteratora jest kontynuowane od miejsca, w `yield return` którym zostało wyłączone, ponownie zatrzymując się, gdy osiągnie oświadczenie.</span><span class="sxs-lookup"><span data-stu-id="b0682-136">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="b0682-137">Pętla `foreach` kończy się po osiągnięciu końca metody iterator lub `yield break` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b0682-137">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>

## <a name="example"></a><span data-ttu-id="b0682-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0682-138">Example</span></span>

<span data-ttu-id="b0682-139">Poniższy przykład ma `yield return` instrukcję, która `for` znajduje się wewnątrz pętli.</span><span class="sxs-lookup"><span data-stu-id="b0682-139">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="b0682-140">Każda iteracja `foreach` treści instrukcji `Main` w metodzie tworzy `Power` wywołanie funkcji iterator.</span><span class="sxs-lookup"><span data-stu-id="b0682-140">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="b0682-141">Każde wywołanie funkcji iterator przechodzi do następnego wykonania `yield return` instrukcji, która występuje podczas `for` następnej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="b0682-141">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>

<span data-ttu-id="b0682-142">Zwracany typ metody iteratorem jest <xref:System.Collections.IEnumerable>, który jest typem interfejsu iteratorego.</span><span class="sxs-lookup"><span data-stu-id="b0682-142">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="b0682-143">Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.</span><span class="sxs-lookup"><span data-stu-id="b0682-143">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a><span data-ttu-id="b0682-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0682-144">Example</span></span>

<span data-ttu-id="b0682-145">W poniższym `get` przykładzie przedstawiono akcesor, który jest iteratorem.</span><span class="sxs-lookup"><span data-stu-id="b0682-145">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="b0682-146">W przykładzie każda `yield return` instrukcja zwraca wystąpienie klasy zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b0682-146">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a><span data-ttu-id="b0682-147">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b0682-147">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b0682-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0682-148">See also</span></span>

- [<span data-ttu-id="b0682-149">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="b0682-149">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="b0682-150">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="b0682-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b0682-151">foreach, in</span><span class="sxs-lookup"><span data-stu-id="b0682-151">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="b0682-152">Iteratory</span><span class="sxs-lookup"><span data-stu-id="b0682-152">Iterators</span></span>](../../iterators.md)
