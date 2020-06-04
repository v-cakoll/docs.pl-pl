---
title: for — odwołanie w C#
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: db7cecc697a9cc9e5ff6b94b78747b799ed7e505
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401904"
---
# <a name="for-c-reference"></a><span data-ttu-id="f17df-102">for (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f17df-102">for (C# reference)</span></span>

<span data-ttu-id="f17df-103">`for`Instrukcja wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne zwraca wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="f17df-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="f17df-104">W dowolnym momencie w `for` bloku instrukcji można przerwać pętlę przy użyciu instrukcji [Break](break.md) lub przejść do następnej iteracji w pętli przy użyciu instrukcji [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="f17df-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="f17df-105">Możesz również wyjść z `for` pętli przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="f17df-105">You can also exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="f17df-106">Struktura `for` instrukcji</span><span class="sxs-lookup"><span data-stu-id="f17df-106">Structure of the `for` statement</span></span>

<span data-ttu-id="f17df-107">`for`Instrukcja definiuje *inicjator*, *warunek*i sekcje *iteratora* :</span><span class="sxs-lookup"><span data-stu-id="f17df-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="f17df-108">Wszystkie trzy sekcje są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="f17df-108">All three sections are optional.</span></span> <span data-ttu-id="f17df-109">Treść pętli jest instrukcją lub blokiem instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f17df-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="f17df-110">Poniższy przykład pokazuje `for` instrukcję ze wszystkimi zdefiniowanymi sekcjami:</span><span class="sxs-lookup"><span data-stu-id="f17df-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](snippets/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="f17df-111">Sekcja *inicjatora*</span><span class="sxs-lookup"><span data-stu-id="f17df-111">The *initializer* section</span></span>

<span data-ttu-id="f17df-112">Instrukcje w sekcji *inicjatora* są wykonywane tylko raz, przed wprowadzeniem pętli.</span><span class="sxs-lookup"><span data-stu-id="f17df-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="f17df-113">Sekcja *inicjatora* jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="f17df-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="f17df-114">Deklaracja i inicjalizacja zmiennej pętli lokalnej, do której nie można uzyskać dostępu spoza pętli.</span><span class="sxs-lookup"><span data-stu-id="f17df-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="f17df-115">Zero lub więcej wyrażeń instrukcji z następującej listy oddzielonych przecinkami:</span><span class="sxs-lookup"><span data-stu-id="f17df-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="f17df-116">instrukcja [przypisania](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="f17df-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="f17df-117">wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="f17df-117">invocation of a method</span></span>

  - <span data-ttu-id="f17df-118">wyrażenie [przyrostu](../operators/arithmetic-operators.md#increment-operator-) prefiksu lub przyrostkowego, takie jak `++i` lub`i++`</span><span class="sxs-lookup"><span data-stu-id="f17df-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="f17df-119">wyrażenie lub [zmniejszanie](../operators/arithmetic-operators.md#decrement-operator---) przyrostowe, takie jak `--i` lub`i--`</span><span class="sxs-lookup"><span data-stu-id="f17df-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="f17df-120">Tworzenie obiektu za pomocą operatora [New](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="f17df-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="f17df-121">wyrażenie [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="f17df-121">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="f17df-122">Sekcja *inicjatora* w powyższym przykładzie deklaruje i inicjuje zmienną pętli lokalnej `i` :</span><span class="sxs-lookup"><span data-stu-id="f17df-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="f17df-123">Sekcja *warunku*</span><span class="sxs-lookup"><span data-stu-id="f17df-123">The *condition* section</span></span>

<span data-ttu-id="f17df-124">Sekcja *warunku* , jeśli jest obecna, musi być wyrażeniem logicznym.</span><span class="sxs-lookup"><span data-stu-id="f17df-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="f17df-125">To wyrażenie jest oceniane przed każdą iteracją pętli.</span><span class="sxs-lookup"><span data-stu-id="f17df-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="f17df-126">Jeśli sekcja *Condition* nie istnieje lub wyrażenie logiczne zwraca wartość `true` , wykonywana jest iteracja następnej pętli. w przeciwnym razie pętla zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="f17df-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="f17df-127">Sekcja *warunek* w powyższym przykładzie określa, czy pętla kończy się na podstawie wartości zmiennej pętli lokalnej:</span><span class="sxs-lookup"><span data-stu-id="f17df-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="f17df-128">Sekcja *iteratora*</span><span class="sxs-lookup"><span data-stu-id="f17df-128">The *iterator* section</span></span>

<span data-ttu-id="f17df-129">Sekcja *iterator* definiuje, co się stanie po każdej iteracji treści pętli.</span><span class="sxs-lookup"><span data-stu-id="f17df-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="f17df-130">Sekcja *iteratora* zawiera zero lub więcej następujących wyrażeń instrukcji, rozdzielonych przecinkami:</span><span class="sxs-lookup"><span data-stu-id="f17df-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="f17df-131">instrukcja [przypisania](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="f17df-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="f17df-132">wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="f17df-132">invocation of a method</span></span>

- <span data-ttu-id="f17df-133">wyrażenie [przyrostu](../operators/arithmetic-operators.md#increment-operator-) prefiksu lub przyrostkowego, takie jak `++i` lub`i++`</span><span class="sxs-lookup"><span data-stu-id="f17df-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="f17df-134">wyrażenie lub [zmniejszanie](../operators/arithmetic-operators.md#decrement-operator---) przyrostowe, takie jak `--i` lub`i--`</span><span class="sxs-lookup"><span data-stu-id="f17df-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="f17df-135">Tworzenie obiektu za pomocą operatora [New](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="f17df-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="f17df-136">wyrażenie [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="f17df-136">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="f17df-137">Sekcja *iterator* w powyższym przykładzie zwiększa zmienną pętli lokalnej:</span><span class="sxs-lookup"><span data-stu-id="f17df-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="f17df-138">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f17df-138">Examples</span></span>

<span data-ttu-id="f17df-139">Poniższy przykład ilustruje kilka rzadziej używanych części `for` instrukcji: Przypisywanie wartości do zmiennej pętli zewnętrznej w sekcji *inicjatora* , wywoływanie metody w *inicjatorze* i w sekcjach *iterator* i zmiana wartości dwóch zmiennych w sekcji *iteratora* .</span><span class="sxs-lookup"><span data-stu-id="f17df-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="f17df-140">Wybierz pozycję **Uruchom** , aby uruchomić przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="f17df-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="f17df-141">Następnie można zmodyfikować kod i uruchomić go ponownie.</span><span class="sxs-lookup"><span data-stu-id="f17df-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](snippets/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="f17df-142">W poniższym przykładzie zdefiniowano `for` pętlę nieskończoną:</span><span class="sxs-lookup"><span data-stu-id="f17df-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](snippets/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="f17df-143">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f17df-143">C# language specification</span></span>

<span data-ttu-id="f17df-144">Aby uzyskać więcej informacji, zobacz sekcję [dotyczącą instrukcji](~/_csharplang/spec/statements.md#the-for-statement) w [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="f17df-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="f17df-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f17df-145">See also</span></span>

- [<span data-ttu-id="f17df-146">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="f17df-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f17df-147">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f17df-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f17df-148">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f17df-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f17df-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="f17df-149">foreach, in</span></span>](foreach-in.md)
