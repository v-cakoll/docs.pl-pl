---
title: C#for — instrukcja
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 61315a04ca8d5a619a3dcaf43b15a309919d3c42
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167870"
---
# <a name="for-c-reference"></a><span data-ttu-id="9a518-102">for (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="9a518-102">for (C# reference)</span></span>

<span data-ttu-id="9a518-103">Instrukcja wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne zwraca wartość `true`. `for`</span><span class="sxs-lookup"><span data-stu-id="9a518-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="9a518-104">W dowolnym momencie w `for` bloku instrukcji można przerwać pętlę przy użyciu instrukcji [Break](break.md) lub przejść do następnej iteracji w pętli przy użyciu instrukcji [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="9a518-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="9a518-105">`for` Możesz również wyjść z pętli przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="9a518-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="9a518-106">`for` Struktura instrukcji</span><span class="sxs-lookup"><span data-stu-id="9a518-106">Structure of the `for` statement</span></span>

<span data-ttu-id="9a518-107">Instrukcja definiuje *inicjator*, *warunek*i sekcje iteratora: `for`</span><span class="sxs-lookup"><span data-stu-id="9a518-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="9a518-108">Wszystkie trzy sekcje są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="9a518-108">All three sections are optional.</span></span> <span data-ttu-id="9a518-109">Treść pętli jest instrukcją lub blokiem instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9a518-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="9a518-110">Poniższy przykład pokazuje `for` instrukcję ze wszystkimi zdefiniowanymi sekcjami:</span><span class="sxs-lookup"><span data-stu-id="9a518-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="9a518-111">Sekcja *inicjatora*</span><span class="sxs-lookup"><span data-stu-id="9a518-111">The *initializer* section</span></span>

<span data-ttu-id="9a518-112">Instrukcje w sekcji *inicjatora* są wykonywane tylko raz, przed wprowadzeniem pętli.</span><span class="sxs-lookup"><span data-stu-id="9a518-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="9a518-113">Sekcja *inicjatora* jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9a518-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="9a518-114">Deklaracja i inicjalizacja zmiennej pętli lokalnej, do której nie można uzyskać dostępu spoza pętli.</span><span class="sxs-lookup"><span data-stu-id="9a518-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="9a518-115">Zero lub więcej wyrażeń instrukcji z następującej listy oddzielonych przecinkami:</span><span class="sxs-lookup"><span data-stu-id="9a518-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="9a518-116">instrukcja [przypisania](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="9a518-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="9a518-117">wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="9a518-117">invocation of a method</span></span>

  - <span data-ttu-id="9a518-118">wyrażenie przyrostu [](../operators/arithmetic-operators.md#increment-operator-) prefiksu lub przyrostkowego `++i` , takie jak lub`i++`</span><span class="sxs-lookup"><span data-stu-id="9a518-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="9a518-119">wyrażenie lub [zmniejszanie](../operators/arithmetic-operators.md#decrement-operator---) przyrostowe, takie `--i` jak lub`i--`</span><span class="sxs-lookup"><span data-stu-id="9a518-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="9a518-120">Tworzenie obiektu za pomocą operatora [New](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="9a518-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="9a518-121">wyrażenie [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="9a518-121">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="9a518-122">Sekcja *inicjatora* w powyższym przykładzie deklaruje i inicjuje zmienną `i`pętli lokalnej:</span><span class="sxs-lookup"><span data-stu-id="9a518-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="9a518-123">Sekcja *warunku*</span><span class="sxs-lookup"><span data-stu-id="9a518-123">The *condition* section</span></span>

<span data-ttu-id="9a518-124">Sekcja *warunku* , jeśli jest obecna, musi być wyrażeniem logicznym.</span><span class="sxs-lookup"><span data-stu-id="9a518-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="9a518-125">To wyrażenie jest oceniane przed każdą iteracją pętli.</span><span class="sxs-lookup"><span data-stu-id="9a518-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="9a518-126">Jeśli sekcja *Condition* nie istnieje lub wyrażenie logiczne zwraca `true`wartość, wykonywana jest iteracja następnej pętli. w przeciwnym razie pętla zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="9a518-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="9a518-127">Sekcja *warunek* w powyższym przykładzie określa, czy pętla kończy się na podstawie wartości zmiennej pętli lokalnej:</span><span class="sxs-lookup"><span data-stu-id="9a518-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="9a518-128">Sekcja *iteratora*</span><span class="sxs-lookup"><span data-stu-id="9a518-128">The *iterator* section</span></span>

<span data-ttu-id="9a518-129">Sekcja *iterator* definiuje, co się stanie po każdej iteracji treści pętli.</span><span class="sxs-lookup"><span data-stu-id="9a518-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="9a518-130">Sekcja *iteratora* zawiera zero lub więcej następujących wyrażeń instrukcji, rozdzielonych przecinkami:</span><span class="sxs-lookup"><span data-stu-id="9a518-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="9a518-131">instrukcja [przypisania](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="9a518-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="9a518-132">wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="9a518-132">invocation of a method</span></span>

- <span data-ttu-id="9a518-133">wyrażenie przyrostu [](../operators/arithmetic-operators.md#increment-operator-) prefiksu lub przyrostkowego `++i` , takie jak lub`i++`</span><span class="sxs-lookup"><span data-stu-id="9a518-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="9a518-134">wyrażenie lub [zmniejszanie](../operators/arithmetic-operators.md#decrement-operator---) przyrostowe, takie `--i` jak lub`i--`</span><span class="sxs-lookup"><span data-stu-id="9a518-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="9a518-135">Tworzenie obiektu za pomocą operatora [New](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="9a518-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="9a518-136">wyrażenie [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="9a518-136">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="9a518-137">Sekcja *iterator* w powyższym przykładzie zwiększa zmienną pętli lokalnej:</span><span class="sxs-lookup"><span data-stu-id="9a518-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="9a518-138">Przykłady</span><span class="sxs-lookup"><span data-stu-id="9a518-138">Examples</span></span>

<span data-ttu-id="9a518-139">Poniższy przykład ilustruje kilka mniej typowych zastosowań `for` sekcji instrukcji: Przypisywanie wartości do zmiennej pętli zewnętrznej w sekcji *inicjatora* , wywoływanie metody w *inicjatorze* i *iterator* i zmiana wartości dwóch zmiennych w sekcji *iterator* .</span><span class="sxs-lookup"><span data-stu-id="9a518-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="9a518-140">Wybierz pozycję **Uruchom** , aby uruchomić przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="9a518-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="9a518-141">Następnie można zmodyfikować kod i uruchomić go ponownie.</span><span class="sxs-lookup"><span data-stu-id="9a518-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="9a518-142">W poniższym przykładzie zdefiniowano pętlę nieskończoną `for` :</span><span class="sxs-lookup"><span data-stu-id="9a518-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="9a518-143">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9a518-143">C# language specification</span></span>

<span data-ttu-id="9a518-144">Aby uzyskać więcej informacji, zobacz sekcję [dotyczącą instrukcji](~/_csharplang/spec/statements.md#the-for-statement) [ C# języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="9a518-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a518-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a518-145">See also</span></span>

- [<span data-ttu-id="9a518-146">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9a518-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9a518-147">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9a518-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9a518-148">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9a518-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9a518-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="9a518-149">foreach, in</span></span>](foreach-in.md)
