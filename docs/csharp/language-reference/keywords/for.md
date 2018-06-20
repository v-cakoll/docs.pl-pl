---
title: for (odwołanie w C#)
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: beac7727c8ce83d8ea20f0fc578f80ceef3053e7
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208388"
---
# <a name="for-c-reference"></a><span data-ttu-id="8a713-102">Aby uzyskać (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8a713-102">for (C# reference)</span></span>

<span data-ttu-id="8a713-103">`for` Instrukcji wykonuje instrukcję lub blok instrukcji, podczas określonego wyrażenia logicznego daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="8a713-103">The `for` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="8a713-104">W dowolnym punktu w `for` blok instrukcji, można przerwać poza pętli przy użyciu [podziału](break.md) instrukcji lub krok do następnej iteracji w pętli przy użyciu [kontynuować](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8a713-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="8a713-105">Możesz również zakończyć działanie `for` pętli przez [przejdź do](goto.md), [zwracać](return.md), lub [throw](throw.md) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="8a713-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>
  
## <a name="structure-of-the-for-statement"></a><span data-ttu-id="8a713-106">Struktura `for` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8a713-106">Structure of the `for` statement</span></span>

<span data-ttu-id="8a713-107">`for` Definiuje instrukcji *inicjatora*, *warunku*, i *iterator* sekcje:</span><span class="sxs-lookup"><span data-stu-id="8a713-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>
  
```csharp
for (initializer; condition; iterator)  
    body  
```

<span data-ttu-id="8a713-108">Wszystkie trzy sekcje są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8a713-108">All three sections are optional.</span></span> <span data-ttu-id="8a713-109">Treść pętli jest instrukcji lub bloku instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8a713-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="8a713-110">W poniższym przykładzie przedstawiono `for` instrukcji z wszystkich zdefiniowanych sekcji:</span><span class="sxs-lookup"><span data-stu-id="8a713-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="8a713-111">*Inicjatora* sekcji</span><span class="sxs-lookup"><span data-stu-id="8a713-111">The *initializer* section</span></span>

<span data-ttu-id="8a713-112">Instrukcje w *inicjatora* sekcji są wykonywane tylko raz, przed wprowadzeniem pętli.</span><span class="sxs-lookup"><span data-stu-id="8a713-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="8a713-113">*Inicjatora* sekcja jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8a713-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="8a713-114">Deklaracji i inicjowania zmiennej lokalnej nie mogą być dostępne spoza pętli.</span><span class="sxs-lookup"><span data-stu-id="8a713-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="8a713-115">Zero lub więcej wyrażenia instrukcji z poniższej listy rozdzielonych przecinkami:</span><span class="sxs-lookup"><span data-stu-id="8a713-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="8a713-116">[Przypisanie](../operators/assignment-operator.md) — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8a713-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="8a713-117">Wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="8a713-117">invocation of a method</span></span>  

  - <span data-ttu-id="8a713-118">Prefiks lub przyrostka [przyrostu](../operators/increment-operator.md) wyrażenia, takich jak `++i` lub `i++`</span><span class="sxs-lookup"><span data-stu-id="8a713-118">prefix or postfix [increment](../operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  

  - <span data-ttu-id="8a713-119">Prefiks lub przyrostka [dekrementacji](../operators/decrement-operator.md) wyrażenia, takich jak `--i` lub `i--`</span><span class="sxs-lookup"><span data-stu-id="8a713-119">prefix or postfix [decrement](../operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  

  - <span data-ttu-id="8a713-120">Tworzenie obiektu przy użyciu [nowe](new-operator.md) — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="8a713-120">creation of an object by using [new](new-operator.md) keyword</span></span>

  - <span data-ttu-id="8a713-121">[await](await.md) wyrażenia</span><span class="sxs-lookup"><span data-stu-id="8a713-121">[await](await.md) expression</span></span>

<span data-ttu-id="8a713-122">*Inicjatora* sekcji w powyższym przykładzie deklaruje i inicjuje zmiennej lokalnej `i`:</span><span class="sxs-lookup"><span data-stu-id="8a713-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="8a713-123">*Warunku* sekcji</span><span class="sxs-lookup"><span data-stu-id="8a713-123">The *condition* section</span></span>

<span data-ttu-id="8a713-124">*Warunku* sekcji, jeśli jest obecny, musi być wyrażenie logiczne.</span><span class="sxs-lookup"><span data-stu-id="8a713-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="8a713-125">Czy wyrażenie jest obliczane przed każdym iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="8a713-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="8a713-126">Jeśli *warunku* sekcji nie istnieje lub wyrażenie warunkowe daje w wyniku `true`następnej iteracji pętli jest wykonywane; w przeciwnym razie, pętla zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="8a713-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="8a713-127">*Warunku* sekcja w powyższym przykładzie określa, czy pętli kończy się na podstawie wartości zmiennej lokalnej:</span><span class="sxs-lookup"><span data-stu-id="8a713-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="8a713-128">*Iterator* sekcji</span><span class="sxs-lookup"><span data-stu-id="8a713-128">The *iterator* section</span></span>

<span data-ttu-id="8a713-129">*Iterator* sekcja definiuje co się stanie po każdej iteracji pętli treści.</span><span class="sxs-lookup"><span data-stu-id="8a713-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="8a713-130">*Iterator* sekcja zawiera zero lub więcej z następujących wyrażenia instrukcji, oddzielonych przecinkami:</span><span class="sxs-lookup"><span data-stu-id="8a713-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>  

- <span data-ttu-id="8a713-131">[Przypisanie](../operators/assignment-operator.md) — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8a713-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="8a713-132">Wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="8a713-132">invocation of a method</span></span>  

- <span data-ttu-id="8a713-133">Prefiks lub przyrostka [przyrostu](../operators/increment-operator.md) wyrażenia, takich jak `++i` lub `i++`</span><span class="sxs-lookup"><span data-stu-id="8a713-133">prefix or postfix [increment](../operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  

- <span data-ttu-id="8a713-134">Prefiks lub przyrostka [dekrementacji](../operators/decrement-operator.md) wyrażenia, takich jak `--i` lub `i--`</span><span class="sxs-lookup"><span data-stu-id="8a713-134">prefix or postfix [decrement](../operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  

- <span data-ttu-id="8a713-135">Tworzenie obiektu przy użyciu [nowe](new-operator.md) — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="8a713-135">creation of an object by using [new](new-operator.md) keyword</span></span>

- <span data-ttu-id="8a713-136">[await](await.md) wyrażenia</span><span class="sxs-lookup"><span data-stu-id="8a713-136">[await](await.md) expression</span></span>

<span data-ttu-id="8a713-137">*Iterator* sekcji w powyższym przykładzie zwiększa zmiennej lokalnej:</span><span class="sxs-lookup"><span data-stu-id="8a713-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="8a713-138">Przykłady</span><span class="sxs-lookup"><span data-stu-id="8a713-138">Examples</span></span>

<span data-ttu-id="8a713-139">Poniższy przykład przedstawia kilka mniej typowe zastosowania `for` sekcje instrukcji: przypisywanie wartości do zmiennej pętli zewnętrznych w *inicjatora* sekcji wywołania metody w obu  *Inicjator* i *iterator* sekcje i zmianę wartości dwie zmienne *iterator* sekcji.</span><span class="sxs-lookup"><span data-stu-id="8a713-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="8a713-140">Wybierz **Uruchom** do uruchomienia przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="8a713-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="8a713-141">Następnie można zmodyfikować kod i uruchom go ponownie.</span><span class="sxs-lookup"><span data-stu-id="8a713-141">After that you can modify the code and run it again.</span></span>
  
[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]
  
<span data-ttu-id="8a713-142">W poniższym przykładzie zdefiniowano nieskończone `for` Pętla:</span><span class="sxs-lookup"><span data-stu-id="8a713-142">The following example defines the infinite `for` loop:</span></span>
  
[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]
  
## <a name="c-language-specification"></a><span data-ttu-id="8a713-143">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8a713-143">C# language specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a><span data-ttu-id="8a713-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a713-144">See also</span></span>

[<span data-ttu-id="8a713-145">For — instrukcja (specyfikacja języka C#)</span><span class="sxs-lookup"><span data-stu-id="8a713-145">The for statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[<span data-ttu-id="8a713-146">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8a713-146">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="8a713-147">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8a713-147">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="8a713-148">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="8a713-148">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="8a713-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="8a713-149">foreach, in</span></span>](foreach-in.md)  
[<span data-ttu-id="8a713-150">for, instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="8a713-150">for Statement (C++)</span></span>](/cpp/cpp/for-statement-cpp)  
[<span data-ttu-id="8a713-151">Instrukcje iteracji</span><span class="sxs-lookup"><span data-stu-id="8a713-151">Iteration Statements</span></span>](iteration-statements.md)
