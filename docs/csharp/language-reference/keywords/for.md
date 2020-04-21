---
title: dla instrukcji — odwołanie do języka C#
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: cb83fa015eea19b156faebb5bed18cc1f0970cc1
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738796"
---
# <a name="for-c-reference"></a><span data-ttu-id="e88fd-102">dla (odwołanie C#)</span><span class="sxs-lookup"><span data-stu-id="e88fd-102">for (C# reference)</span></span>

<span data-ttu-id="e88fd-103">Instrukcja `for` wykonuje instrukcję lub blok instrukcji, podczas gdy określone `true`wyrażenie logiczne ocenia .</span><span class="sxs-lookup"><span data-stu-id="e88fd-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="e88fd-104">W dowolnym momencie w bloku `for` instrukcji można wyrwać z pętli przy użyciu [break](break.md) instrukcji lub krok do następnej iteracji w pętli przy użyciu [continue](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e88fd-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="e88fd-105">Można również wyjść `for` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e88fd-105">You can also exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="e88fd-106">Struktura `for` oświadczenia</span><span class="sxs-lookup"><span data-stu-id="e88fd-106">Structure of the `for` statement</span></span>

<span data-ttu-id="e88fd-107">Instrukcja `for` definiuje *inicjalizatora*, *warunek*i *iteratora* sekcje:</span><span class="sxs-lookup"><span data-stu-id="e88fd-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="e88fd-108">Wszystkie trzy sekcje są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e88fd-108">All three sections are optional.</span></span> <span data-ttu-id="e88fd-109">Treść pętli jest instrukcja lub blok instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e88fd-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="e88fd-110">Poniższy przykład `for` przedstawia instrukcję ze wszystkimi zdefiniowanymi sekcjami:</span><span class="sxs-lookup"><span data-stu-id="e88fd-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="e88fd-111">Sekcja *inicjatora*</span><span class="sxs-lookup"><span data-stu-id="e88fd-111">The *initializer* section</span></span>

<span data-ttu-id="e88fd-112">Instrukcje w sekcji *inicjatora* są wykonywane tylko raz, przed wprowadzeniem pętli.</span><span class="sxs-lookup"><span data-stu-id="e88fd-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="e88fd-113">Sekcja *inicjatora* jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e88fd-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="e88fd-114">Deklaracja i inicjowanie zmiennej pętli lokalnej, do której nie można uzyskać dostępu spoza pętli.</span><span class="sxs-lookup"><span data-stu-id="e88fd-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="e88fd-115">Zero lub więcej wyrażeń instrukcji z poniższej listy, oddzielonych przecinkami:</span><span class="sxs-lookup"><span data-stu-id="e88fd-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="e88fd-116">[instrukcja przydziału](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="e88fd-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="e88fd-117">powołanie się na metodę</span><span class="sxs-lookup"><span data-stu-id="e88fd-117">invocation of a method</span></span>

  - <span data-ttu-id="e88fd-118">prefiks lub wyrażenie [przyrostowe](../operators/arithmetic-operators.md#increment-operator-) postfix, takie jak `++i` lub`i++`</span><span class="sxs-lookup"><span data-stu-id="e88fd-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="e88fd-119">prefiks lub wyrażenie [dekrementacji](../operators/arithmetic-operators.md#decrement-operator---) postfix, takie jak `--i` lub`i--`</span><span class="sxs-lookup"><span data-stu-id="e88fd-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="e88fd-120">tworzenie obiektu przy użyciu [nowego](../operators/new-operator.md) operatora</span><span class="sxs-lookup"><span data-stu-id="e88fd-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="e88fd-121">[await](../operators/await.md) wyrażenie</span><span class="sxs-lookup"><span data-stu-id="e88fd-121">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="e88fd-122">Sekcja *inicjatora* w powyższym przykładzie deklaruje i inicjuje zmienną `i`pętli lokalnej:</span><span class="sxs-lookup"><span data-stu-id="e88fd-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="e88fd-123">Sekcja *warunek*</span><span class="sxs-lookup"><span data-stu-id="e88fd-123">The *condition* section</span></span>

<span data-ttu-id="e88fd-124">Sekcja *warunek,* jeśli jest obecny, musi być wyrażeniem logicznym.</span><span class="sxs-lookup"><span data-stu-id="e88fd-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="e88fd-125">To wyrażenie jest oceniane przed każdą iteracją pętli.</span><span class="sxs-lookup"><span data-stu-id="e88fd-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="e88fd-126">Jeśli sekcja *warunek* nie jest obecny lub wyrażenie `true`logiczne ocenia do , następna iteracja pętli jest wykonywana; w przeciwnym razie pętla zostanie przerwana.</span><span class="sxs-lookup"><span data-stu-id="e88fd-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="e88fd-127">Sekcja *warunek* w powyższym przykładzie określa, czy pętla kończy się na podstawie wartości zmiennej pętli lokalnej:</span><span class="sxs-lookup"><span data-stu-id="e88fd-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="e88fd-128">Sekcja *iteratora*</span><span class="sxs-lookup"><span data-stu-id="e88fd-128">The *iterator* section</span></span>

<span data-ttu-id="e88fd-129">Sekcja *iteratora* definiuje, co się dzieje po każdej iteracji treści pętli.</span><span class="sxs-lookup"><span data-stu-id="e88fd-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="e88fd-130">Sekcja *iteratora* zawiera zero lub więcej następujących wyrażeń instrukcji, oddzielonych przecinkami:</span><span class="sxs-lookup"><span data-stu-id="e88fd-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="e88fd-131">[instrukcja przydziału](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="e88fd-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="e88fd-132">powołanie się na metodę</span><span class="sxs-lookup"><span data-stu-id="e88fd-132">invocation of a method</span></span>

- <span data-ttu-id="e88fd-133">prefiks lub wyrażenie [przyrostowe](../operators/arithmetic-operators.md#increment-operator-) postfix, takie jak `++i` lub`i++`</span><span class="sxs-lookup"><span data-stu-id="e88fd-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="e88fd-134">prefiks lub wyrażenie [dekrementacji](../operators/arithmetic-operators.md#decrement-operator---) postfix, takie jak `--i` lub`i--`</span><span class="sxs-lookup"><span data-stu-id="e88fd-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="e88fd-135">tworzenie obiektu przy użyciu [nowego](../operators/new-operator.md) operatora</span><span class="sxs-lookup"><span data-stu-id="e88fd-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="e88fd-136">[await](../operators/await.md) wyrażenie</span><span class="sxs-lookup"><span data-stu-id="e88fd-136">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="e88fd-137">Sekcja *iteratora* w powyższym przykładzie zwiększa zmienną pętli lokalnej:</span><span class="sxs-lookup"><span data-stu-id="e88fd-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="e88fd-138">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e88fd-138">Examples</span></span>

<span data-ttu-id="e88fd-139">Poniższy przykład ilustruje kilka mniej `for` typowych zastosowań sekcji instrukcji: przypisywanie wartości do zmiennej pętli zewnętrznej w sekcji *inicjatora,* wywoływanie metody zarówno w sekcjach *inicjatora,* jak i *iteratora* oraz zmiana wartości dwóch zmiennych w sekcji *iteratora.*</span><span class="sxs-lookup"><span data-stu-id="e88fd-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="e88fd-140">Wybierz **uruchom,** aby uruchomić przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="e88fd-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="e88fd-141">Następnie można zmodyfikować kod i uruchomić go ponownie.</span><span class="sxs-lookup"><span data-stu-id="e88fd-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="e88fd-142">Poniższy przykład definiuje `for` nieskończoną pętlę:</span><span class="sxs-lookup"><span data-stu-id="e88fd-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="e88fd-143">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e88fd-143">C# language specification</span></span>

<span data-ttu-id="e88fd-144">Aby uzyskać więcej informacji, zobacz sekcja [instrukcji](~/_csharplang/spec/statements.md#the-for-statement) [specyfikacji języka języka C#.](/dotnet/csharp/language-reference/language-specification/introduction)</span><span class="sxs-lookup"><span data-stu-id="e88fd-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="e88fd-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e88fd-145">See also</span></span>

- [<span data-ttu-id="e88fd-146">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="e88fd-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e88fd-147">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="e88fd-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e88fd-148">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e88fd-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e88fd-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="e88fd-149">foreach, in</span></span>](foreach-in.md)
