---
title: try-finally- C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: a8d18a6ae8b3f8f6cde76b1b296ac6a317ca1ed1
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168578"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="03c20-102">try-finally (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="03c20-102">try-finally (C# Reference)</span></span>

<span data-ttu-id="03c20-103">Za pomocą `finally` bloku, można wyczyścić wszystkie zasoby, które są przydzielone w bloku [try](try-catch.md) , i można uruchomić kod nawet wtedy, gdy wystąpi `try` wyjątek w bloku.</span><span class="sxs-lookup"><span data-stu-id="03c20-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="03c20-104">Zazwyczaj instrukcje `finally` bloku są uruchamiane, gdy kontrolka `try` opuszcza instrukcję.</span><span class="sxs-lookup"><span data-stu-id="03c20-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="03c20-105">Transfer kontroli może wystąpić w wyniku `break`normalnego wykonania, wykonania instrukcji, `continue`, `goto`, lub `return` `try` , lub propagacji wyjątku z instrukcji.</span><span class="sxs-lookup"><span data-stu-id="03c20-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="03c20-106">W ramach obsłużonego wyjątku zagwarantowany jest, że skojarzony `finally` blok jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="03c20-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="03c20-107">Jeśli jednak wyjątek nie jest obsługiwany, wykonanie `finally` bloku jest zależne od tego, w jaki sposób wyzwalany jest wyjątek operacji unwind.</span><span class="sxs-lookup"><span data-stu-id="03c20-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="03c20-108">To z kolei zależy od konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="03c20-108">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="03c20-109">Zwykle, gdy nieobsługiwany wyjątek kończący aplikację, niezależnie od tego `finally` , czy blok jest uruchomiony, nie jest ważne.</span><span class="sxs-lookup"><span data-stu-id="03c20-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="03c20-110">Jednakże `finally` Jeśli istnieją instrukcje w bloku, który musi być uruchamiany nawet w takiej sytuacji, jedno rozwiązanie ma `catch` dodać blok do `try` - `finally` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="03c20-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="03c20-111">Alternatywnie można przechwytywać wyjątek, który może `try` zostać wygenerowany w bloku `try` - `finally` instrukcji wyższej w górę stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="03c20-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="03c20-112">Oznacza to, że można przechwytywać wyjątek w metodzie, która wywołuje metodę, która zawiera `try` - `finally` instrukcję, lub w metodzie, która wywołuje tę metodę, lub w dowolnej metodzie w stosie wywołań.</span><span class="sxs-lookup"><span data-stu-id="03c20-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="03c20-113">Jeśli wyjątek nie zostanie przechwycony, wykonanie `finally` bloku zależy od tego, czy system operacyjny wybiera wyzwalacz operacji unwind.</span><span class="sxs-lookup"><span data-stu-id="03c20-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="03c20-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="03c20-114">Example</span></span>

<span data-ttu-id="03c20-115">W poniższym przykładzie instrukcja konwersji nieprawidłowa powoduje `System.InvalidCastException` wyjątek.</span><span class="sxs-lookup"><span data-stu-id="03c20-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="03c20-116">Wyjątek nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="03c20-116">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="03c20-117">W poniższym przykładzie wyjątek z `TryCast` metody jest przechwytywany w metodzie dalej w stosie wywołań.</span><span class="sxs-lookup"><span data-stu-id="03c20-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="03c20-118">Aby uzyskać więcej informacji `finally`na temat, zobacz [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="03c20-118">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="03c20-119">C#zawiera również [instrukcję using](using-statement.md), która zapewnia podobną funkcjonalność dla <xref:System.IDisposable> obiektów w wygodnej składni.</span><span class="sxs-lookup"><span data-stu-id="03c20-119">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="03c20-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="03c20-120">C# language specification</span></span>

<span data-ttu-id="03c20-121">Aby uzyskać więcej informacji, zobacz sekcję [try instrukcji](~/_csharplang/spec/statements.md#the-try-statement) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="03c20-121">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03c20-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03c20-122">See also</span></span>

- [<span data-ttu-id="03c20-123">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="03c20-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="03c20-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="03c20-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="03c20-125">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="03c20-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="03c20-126">Instrukcje try, throw i catch (C++)</span><span class="sxs-lookup"><span data-stu-id="03c20-126">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="03c20-127">throw</span><span class="sxs-lookup"><span data-stu-id="03c20-127">throw</span></span>](throw.md)
- [<span data-ttu-id="03c20-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="03c20-128">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="03c20-129">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="03c20-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
