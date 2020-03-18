---
title: dla instrukcji - odwołanie do języka C#
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: fc6a23cabd93323cacc33dfc4388116881c1fc84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74552267"
---
# <a name="for-c-reference"></a><span data-ttu-id="584d7-102">dla (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="584d7-102">for (C# reference)</span></span>

<span data-ttu-id="584d7-103">Instrukcja `for` wykonuje instrukcję lub blok instrukcji, podczas gdy określone `true`wyrażenie logiczne oblicza .</span><span class="sxs-lookup"><span data-stu-id="584d7-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="584d7-104">W dowolnym momencie `for` w bloku instrukcji można wyrwać się z pętli za pomocą [instrukcji break](break.md) lub przejść do następnej iteracji w pętli przy użyciu [instrukcji continue.](continue.md)</span><span class="sxs-lookup"><span data-stu-id="584d7-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="584d7-105">Możesz również wyjść `for` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="584d7-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="584d7-106">Struktura oświadczenia `for`</span><span class="sxs-lookup"><span data-stu-id="584d7-106">Structure of the `for` statement</span></span>

<span data-ttu-id="584d7-107">Instrukcja `for` definiuje *sekcje inicjatora*, *warunek*i *iteratora:*</span><span class="sxs-lookup"><span data-stu-id="584d7-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="584d7-108">Wszystkie trzy sekcje są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="584d7-108">All three sections are optional.</span></span> <span data-ttu-id="584d7-109">Treść pętli jest instrukcją lub blokiem instrukcji.</span><span class="sxs-lookup"><span data-stu-id="584d7-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="584d7-110">W poniższym `for` przykładzie przedstawiono instrukcję ze wszystkimi zdefiniowanymi sekcjami:</span><span class="sxs-lookup"><span data-stu-id="584d7-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="584d7-111">Sekcja *inicjatora*</span><span class="sxs-lookup"><span data-stu-id="584d7-111">The *initializer* section</span></span>

<span data-ttu-id="584d7-112">Instrukcje w sekcji *inicjatora* są wykonywane tylko raz, przed wejściem do pętli.</span><span class="sxs-lookup"><span data-stu-id="584d7-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="584d7-113">Sekcja *inicjatora* jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="584d7-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="584d7-114">Deklaracja i inicjowanie zmiennej pętli lokalnej, do której nie można uzyskać dostępu spoza pętli.</span><span class="sxs-lookup"><span data-stu-id="584d7-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="584d7-115">Zero lub więcej wyrażeń instrukcji z poniższej listy, oddzielone przecinkami:</span><span class="sxs-lookup"><span data-stu-id="584d7-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="584d7-116">[instrukcja przypisania](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="584d7-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="584d7-117">wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="584d7-117">invocation of a method</span></span>

  - <span data-ttu-id="584d7-118">prefiks lub wyrażenie [przyrostu](../operators/arithmetic-operators.md#increment-operator-) postfix, takie jak `++i` lub`i++`</span><span class="sxs-lookup"><span data-stu-id="584d7-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="584d7-119">prefiks lub wyrażenie [dekrementacji,](../operators/arithmetic-operators.md#decrement-operator---) takie jak `--i` lub`i--`</span><span class="sxs-lookup"><span data-stu-id="584d7-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="584d7-120">stworzenie obiektu przy użyciu [nowego](../operators/new-operator.md) operatora</span><span class="sxs-lookup"><span data-stu-id="584d7-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="584d7-121">[oczekiwanie na](../operators/await.md) wyrażenie</span><span class="sxs-lookup"><span data-stu-id="584d7-121">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="584d7-122">Sekcja *inicjatora* w powyższym przykładzie deklaruje i `i`inicjuje zmienną pętli lokalnej:</span><span class="sxs-lookup"><span data-stu-id="584d7-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="584d7-123">Sekcja *warunków*</span><span class="sxs-lookup"><span data-stu-id="584d7-123">The *condition* section</span></span>

<span data-ttu-id="584d7-124">Sekcja *warunku,* jeśli jest obecna, musi być wyrażeniem wartości ą logiczną.</span><span class="sxs-lookup"><span data-stu-id="584d7-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="584d7-125">To wyrażenie jest oceniane przed każdą iteracją pętli.</span><span class="sxs-lookup"><span data-stu-id="584d7-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="584d7-126">Jeśli sekcja *warunku* nie jest obecny lub `true`wyrażenie logiczne oblicza , następna iteracja pętli jest wykonywana; w przeciwnym razie pętla zostanie wycofana.</span><span class="sxs-lookup"><span data-stu-id="584d7-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="584d7-127">Sekcja *warunku* w powyższym przykładzie określa, czy pętla kończy się na podstawie wartości zmiennej pętli lokalnej:</span><span class="sxs-lookup"><span data-stu-id="584d7-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="584d7-128">Sekcja *iterator*</span><span class="sxs-lookup"><span data-stu-id="584d7-128">The *iterator* section</span></span>

<span data-ttu-id="584d7-129">Sekcja *iterator* określa, co dzieje się po każdej iteracji treści pętli.</span><span class="sxs-lookup"><span data-stu-id="584d7-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="584d7-130">Sekcja *iterator* zawiera zero lub więcej z następujących wyrażeń instrukcji, oddzielonych przecinkami:</span><span class="sxs-lookup"><span data-stu-id="584d7-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="584d7-131">[instrukcja przypisania](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="584d7-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="584d7-132">wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="584d7-132">invocation of a method</span></span>

- <span data-ttu-id="584d7-133">prefiks lub wyrażenie [przyrostu](../operators/arithmetic-operators.md#increment-operator-) postfix, takie jak `++i` lub`i++`</span><span class="sxs-lookup"><span data-stu-id="584d7-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="584d7-134">prefiks lub wyrażenie [dekrementacji,](../operators/arithmetic-operators.md#decrement-operator---) takie jak `--i` lub`i--`</span><span class="sxs-lookup"><span data-stu-id="584d7-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="584d7-135">stworzenie obiektu przy użyciu [nowego](../operators/new-operator.md) operatora</span><span class="sxs-lookup"><span data-stu-id="584d7-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="584d7-136">[oczekiwanie na](../operators/await.md) wyrażenie</span><span class="sxs-lookup"><span data-stu-id="584d7-136">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="584d7-137">Sekcja *iterator* w powyższym przykładzie zwiększa zmienną pętli lokalnej:</span><span class="sxs-lookup"><span data-stu-id="584d7-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="584d7-138">Przykłady</span><span class="sxs-lookup"><span data-stu-id="584d7-138">Examples</span></span>

<span data-ttu-id="584d7-139">W poniższym przykładzie przedstawiono kilka mniej `for` typowych zastosowań sekcji instrukcji: przypisywanie wartości do zmiennej pętli zewnętrznej w sekcji *inicjatora,* wywoływanie metody w sekcjach *inicjatora* i *iteratorze* oraz zmiana wartości dwóch zmiennych w sekcji *iteratora.*</span><span class="sxs-lookup"><span data-stu-id="584d7-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="584d7-140">Wybierz **uruchom,** aby uruchomić przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="584d7-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="584d7-141">Następnie można zmodyfikować kod i uruchomić go ponownie.</span><span class="sxs-lookup"><span data-stu-id="584d7-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="584d7-142">Poniższy przykład definiuje nieskończoną `for` pętlę:</span><span class="sxs-lookup"><span data-stu-id="584d7-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="584d7-143">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="584d7-143">C# language specification</span></span>

<span data-ttu-id="584d7-144">Aby uzyskać więcej informacji, zobacz [sekcję Instrukcja dla](~/_csharplang/spec/statements.md#the-for-statement) [specyfikacji języka Języka Języka Języka C#.](/dotnet/csharp/language-reference/language-specification/introduction)</span><span class="sxs-lookup"><span data-stu-id="584d7-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="584d7-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="584d7-145">See also</span></span>

- [<span data-ttu-id="584d7-146">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="584d7-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="584d7-147">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="584d7-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="584d7-148">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="584d7-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="584d7-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="584d7-149">foreach, in</span></span>](foreach-in.md)
