---
title: C#for — instrukcja
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 5ebc478f8840173cacc0bc211061f3013379abd9
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422791"
---
# <a name="for-c-reference"></a><span data-ttu-id="c1099-102">for (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="c1099-102">for (C# reference)</span></span>

<span data-ttu-id="c1099-103">Instrukcja `for` wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="c1099-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="c1099-104">W dowolnym momencie w bloku instrukcji `for` można przerwać pętlę przy użyciu instrukcji [Break](break.md) lub przejść do następnej iteracji w pętli przy użyciu instrukcji [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="c1099-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="c1099-105">Możesz również wyjść z pętli `for` przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="c1099-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="c1099-106">Struktura instrukcji `for`</span><span class="sxs-lookup"><span data-stu-id="c1099-106">Structure of the `for` statement</span></span>

<span data-ttu-id="c1099-107">Instrukcja `for` definiuje *inicjatora*, *warunek*i sekcje *iteratora* :</span><span class="sxs-lookup"><span data-stu-id="c1099-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="c1099-108">Wszystkie trzy sekcje są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="c1099-108">All three sections are optional.</span></span> <span data-ttu-id="c1099-109">Treść pętli jest instrukcją lub blokiem instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c1099-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="c1099-110">W poniższym przykładzie pokazano instrukcję `for` ze wszystkimi zdefiniowanymi sekcjami:</span><span class="sxs-lookup"><span data-stu-id="c1099-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="c1099-111">Sekcja *inicjatora*</span><span class="sxs-lookup"><span data-stu-id="c1099-111">The *initializer* section</span></span>

<span data-ttu-id="c1099-112">Instrukcje w sekcji *inicjatora* są wykonywane tylko raz, przed wprowadzeniem pętli.</span><span class="sxs-lookup"><span data-stu-id="c1099-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="c1099-113">Sekcja *inicjatora* jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c1099-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="c1099-114">Deklaracja i inicjalizacja zmiennej pętli lokalnej, do której nie można uzyskać dostępu spoza pętli.</span><span class="sxs-lookup"><span data-stu-id="c1099-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="c1099-115">Zero lub więcej wyrażeń instrukcji z następującej listy oddzielonych przecinkami:</span><span class="sxs-lookup"><span data-stu-id="c1099-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="c1099-116">instrukcja [przypisania](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="c1099-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="c1099-117">wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="c1099-117">invocation of a method</span></span>

  - <span data-ttu-id="c1099-118">wyrażenie [przyrostu](../operators/arithmetic-operators.md#increment-operator-) prefiksu lub przyrostkowego, takie jak `++i` lub `i++`</span><span class="sxs-lookup"><span data-stu-id="c1099-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="c1099-119">[wyrażenie "](../operators/arithmetic-operators.md#decrement-operator---) prefix" lub "przyrostka", takie jak `--i` lub `i--`</span><span class="sxs-lookup"><span data-stu-id="c1099-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="c1099-120">Tworzenie obiektu za pomocą operatora [New](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="c1099-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="c1099-121">wyrażenie [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="c1099-121">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="c1099-122">Sekcja *inicjatora* w powyższym przykładzie deklaruje i inicjuje zmienną pętli lokalnej `i`:</span><span class="sxs-lookup"><span data-stu-id="c1099-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="c1099-123">Sekcja *warunku*</span><span class="sxs-lookup"><span data-stu-id="c1099-123">The *condition* section</span></span>

<span data-ttu-id="c1099-124">Sekcja *warunku* , jeśli jest obecna, musi być wyrażeniem logicznym.</span><span class="sxs-lookup"><span data-stu-id="c1099-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="c1099-125">To wyrażenie jest oceniane przed każdą iteracją pętli.</span><span class="sxs-lookup"><span data-stu-id="c1099-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="c1099-126">Jeśli sekcja *Condition* nie istnieje lub wyrażenie logiczne zwróci wartość `true`, wykonywana jest iteracja następnej pętli. w przeciwnym razie pętla zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="c1099-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="c1099-127">Sekcja *warunek* w powyższym przykładzie określa, czy pętla kończy się na podstawie wartości zmiennej pętli lokalnej:</span><span class="sxs-lookup"><span data-stu-id="c1099-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="c1099-128">Sekcja *iteratora*</span><span class="sxs-lookup"><span data-stu-id="c1099-128">The *iterator* section</span></span>

<span data-ttu-id="c1099-129">Sekcja *iterator* definiuje, co się stanie po każdej iteracji treści pętli.</span><span class="sxs-lookup"><span data-stu-id="c1099-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="c1099-130">Sekcja *iteratora* zawiera zero lub więcej następujących wyrażeń instrukcji, rozdzielonych przecinkami:</span><span class="sxs-lookup"><span data-stu-id="c1099-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="c1099-131">instrukcja [przypisania](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="c1099-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="c1099-132">wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="c1099-132">invocation of a method</span></span>

- <span data-ttu-id="c1099-133">wyrażenie [przyrostu](../operators/arithmetic-operators.md#increment-operator-) prefiksu lub przyrostkowego, takie jak `++i` lub `i++`</span><span class="sxs-lookup"><span data-stu-id="c1099-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="c1099-134">[wyrażenie "](../operators/arithmetic-operators.md#decrement-operator---) prefix" lub "przyrostka", takie jak `--i` lub `i--`</span><span class="sxs-lookup"><span data-stu-id="c1099-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="c1099-135">Tworzenie obiektu za pomocą operatora [New](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="c1099-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="c1099-136">wyrażenie [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="c1099-136">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="c1099-137">Sekcja *iterator* w powyższym przykładzie zwiększa zmienną pętli lokalnej:</span><span class="sxs-lookup"><span data-stu-id="c1099-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="c1099-138">Przykłady</span><span class="sxs-lookup"><span data-stu-id="c1099-138">Examples</span></span>

<span data-ttu-id="c1099-139">Poniższy przykład ilustruje kilka rzadziej używanych części instrukcji `for`: przypisanie wartości do zmiennej pętla zewnętrzna w sekcji *inicjatora* , wywoływanie metody w *inicjatorze* i *iterator* i zmiana wartości dwóch zmiennych w sekcji *iterator* .</span><span class="sxs-lookup"><span data-stu-id="c1099-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="c1099-140">Wybierz pozycję **Uruchom** , aby uruchomić przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="c1099-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="c1099-141">Następnie można zmodyfikować kod i uruchomić go ponownie.</span><span class="sxs-lookup"><span data-stu-id="c1099-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="c1099-142">W poniższym przykładzie zdefiniowano nieskończoną pętlę `for`:</span><span class="sxs-lookup"><span data-stu-id="c1099-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="c1099-143">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c1099-143">C# language specification</span></span>

<span data-ttu-id="c1099-144">Aby uzyskać więcej informacji, zobacz sekcję [dotyczącą instrukcji](~/_csharplang/spec/statements.md#the-for-statement) [ C# języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="c1099-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="c1099-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1099-145">See also</span></span>

- [<span data-ttu-id="c1099-146">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="c1099-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c1099-147">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c1099-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c1099-148">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c1099-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c1099-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="c1099-149">foreach, in</span></span>](foreach-in.md)
