---
title: C# for, instrukcja
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: c6ef926d6fb2c79b7b7f71c3b24b86a7ab057c88
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43256794"
---
# <a name="for-c-reference"></a><span data-ttu-id="9709a-102">Aby uzyskać (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9709a-102">for (C# reference)</span></span>

<span data-ttu-id="9709a-103">`for` Instrukcji wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne, które daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="9709a-103">The `for` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="9709a-104">W dowolnym punkcie w `for` blok instrukcji, można zerwać pętlę za pomocą [podziału](break.md) instrukcji lub krok do następnej iteracji w pętli za pomocą [nadal](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9709a-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="9709a-105">Możesz również wyjść `for` pętli przez [przejdź do](goto.md), [zwracają](return.md), lub [throw](throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9709a-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="9709a-106">Struktura `for` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9709a-106">Structure of the `for` statement</span></span>

<span data-ttu-id="9709a-107">`for` Instrukcja definiuje *inicjatora*, *warunek*, i *iteratora* sekcje:</span><span class="sxs-lookup"><span data-stu-id="9709a-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="9709a-108">Wszystkie trzy sekcje są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="9709a-108">All three sections are optional.</span></span> <span data-ttu-id="9709a-109">Treść pętli jest instrukcję lub blok instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9709a-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="9709a-110">W poniższym przykładzie przedstawiono `for` instrukcję, określając wszystkie sekcje zdefiniowane:</span><span class="sxs-lookup"><span data-stu-id="9709a-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="9709a-111">*Inicjatora* sekcji</span><span class="sxs-lookup"><span data-stu-id="9709a-111">The *initializer* section</span></span>

<span data-ttu-id="9709a-112">Instrukcje w *inicjatora* sekcji są wykonywane tylko raz, przed wprowadzeniem pętli.</span><span class="sxs-lookup"><span data-stu-id="9709a-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="9709a-113">*Inicjatora* sekcja jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9709a-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="9709a-114">Deklaracji i inicjowania zmiennej lokalnej, co nie jest dostępny z zewnątrz pętli.</span><span class="sxs-lookup"><span data-stu-id="9709a-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="9709a-115">Zero lub więcej wyrażenia instrukcji z następującej listy, rozdzielonych przecinkami:</span><span class="sxs-lookup"><span data-stu-id="9709a-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="9709a-116">[Przypisanie](../operators/assignment-operator.md) — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9709a-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="9709a-117">Wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="9709a-117">invocation of a method</span></span>

  - <span data-ttu-id="9709a-118">Wstawianie prefiksu lub przyrostkowe [przyrostu](../operators/increment-operator.md) wyrażenie, takie jak `++i` lub `i++`</span><span class="sxs-lookup"><span data-stu-id="9709a-118">prefix or postfix [increment](../operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="9709a-119">Wstawianie prefiksu lub przyrostkowe [dekrementacji](../operators/decrement-operator.md) wyrażenie, takie jak `--i` lub `i--`</span><span class="sxs-lookup"><span data-stu-id="9709a-119">prefix or postfix [decrement](../operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="9709a-120">Tworzenie obiektu za pomocą [nowe](new-operator.md) — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="9709a-120">creation of an object by using [new](new-operator.md) keyword</span></span>

  - <span data-ttu-id="9709a-121">[await](await.md) wyrażenia</span><span class="sxs-lookup"><span data-stu-id="9709a-121">[await](await.md) expression</span></span>

<span data-ttu-id="9709a-122">*Inicjatora* sekcji w powyższym przykładzie deklaruje i inicjuje zmienną lokalnej `i`:</span><span class="sxs-lookup"><span data-stu-id="9709a-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="9709a-123">*Warunek* sekcji</span><span class="sxs-lookup"><span data-stu-id="9709a-123">The *condition* section</span></span>

<span data-ttu-id="9709a-124">*Warunek* sekcji, jeśli jest obecna, musi być wyrażenie logiczne.</span><span class="sxs-lookup"><span data-stu-id="9709a-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="9709a-125">To wyrażenie jest oceniane przed każdą iteracją pętli.</span><span class="sxs-lookup"><span data-stu-id="9709a-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="9709a-126">Jeśli *warunek* sekcja nie istnieje lub wyrażenie logiczne, które daje w wyniku `true`, następnej iteracji pętli wykonane; w przeciwnym razie, pętla zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="9709a-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="9709a-127">*Warunek* określa sekcji w powyższym przykładzie, jeśli pętla kończy się na podstawie wartości zmiennej lokalnej:</span><span class="sxs-lookup"><span data-stu-id="9709a-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="9709a-128">*Iteratora* sekcji</span><span class="sxs-lookup"><span data-stu-id="9709a-128">The *iterator* section</span></span>

<span data-ttu-id="9709a-129">*Iteratora* sekcja definiuje, co się dzieje po każdej iteracji w treści pętli.</span><span class="sxs-lookup"><span data-stu-id="9709a-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="9709a-130">*Iteratora* sekcja zawiera zero lub więcej z następujących wyrażeń instrukcji, oddzielonych przecinkami:</span><span class="sxs-lookup"><span data-stu-id="9709a-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="9709a-131">[Przypisanie](../operators/assignment-operator.md) — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9709a-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="9709a-132">Wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="9709a-132">invocation of a method</span></span>

- <span data-ttu-id="9709a-133">Wstawianie prefiksu lub przyrostkowe [przyrostu](../operators/increment-operator.md) wyrażenie, takie jak `++i` lub `i++`</span><span class="sxs-lookup"><span data-stu-id="9709a-133">prefix or postfix [increment](../operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="9709a-134">Wstawianie prefiksu lub przyrostkowe [dekrementacji](../operators/decrement-operator.md) wyrażenie, takie jak `--i` lub `i--`</span><span class="sxs-lookup"><span data-stu-id="9709a-134">prefix or postfix [decrement](../operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="9709a-135">Tworzenie obiektu za pomocą [nowe](new-operator.md) — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="9709a-135">creation of an object by using [new](new-operator.md) keyword</span></span>

- <span data-ttu-id="9709a-136">[await](await.md) wyrażenia</span><span class="sxs-lookup"><span data-stu-id="9709a-136">[await](await.md) expression</span></span>

<span data-ttu-id="9709a-137">*Iteratora* sekcji w powyższym przykładzie zwiększa zmiennej lokalnej:</span><span class="sxs-lookup"><span data-stu-id="9709a-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="9709a-138">Przykłady</span><span class="sxs-lookup"><span data-stu-id="9709a-138">Examples</span></span>

<span data-ttu-id="9709a-139">W poniższym przykładzie pokazano kilka mniej typowe sposoby użycia `for` sekcje instrukcji: przypisywanie wartości do zmiennej w zewnętrznej pętli *inicjatora* sekcji wywołania metody w obu  *Inicjator* i *iteratora* sekcje i zmianę wartości dwóch zmiennych w *iteratora* sekcji.</span><span class="sxs-lookup"><span data-stu-id="9709a-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="9709a-140">Wybierz **Uruchom** do uruchamiania kodu przykładu.</span><span class="sxs-lookup"><span data-stu-id="9709a-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="9709a-141">Po tym można zmodyfikować kod i uruchom go ponownie.</span><span class="sxs-lookup"><span data-stu-id="9709a-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="9709a-142">W poniższym przykładzie zdefiniowano nieskończone `for` Pętla:</span><span class="sxs-lookup"><span data-stu-id="9709a-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="9709a-143">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9709a-143">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9709a-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9709a-144">See also</span></span>

- [<span data-ttu-id="9709a-145">For — instrukcja (specyfikacja języka C#)</span><span class="sxs-lookup"><span data-stu-id="9709a-145">The for statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)
- [<span data-ttu-id="9709a-146">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9709a-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9709a-147">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9709a-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9709a-148">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9709a-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9709a-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="9709a-149">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="9709a-150">for, instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="9709a-150">for Statement (C++)</span></span>](/cpp/cpp/for-statement-cpp)
- [<span data-ttu-id="9709a-151">Instrukcje iteracji</span><span class="sxs-lookup"><span data-stu-id="9709a-151">Iteration Statements</span></span>](iteration-statements.md)
