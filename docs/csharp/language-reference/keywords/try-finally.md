---
title: try-finally- C# Reference
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2c4c69b1e104aed968bc24bac690de83026643a0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713017"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="d33f2-102">try-finally (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d33f2-102">try-finally (C# Reference)</span></span>

<span data-ttu-id="d33f2-103">Za pomocą bloku `finally` można wyczyścić wszystkie zasoby, które są przydzielone w bloku [try](try-catch.md) , i można uruchomić kod nawet wtedy, gdy w bloku `try` wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d33f2-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="d33f2-104">Zazwyczaj instrukcje bloku `finally` są uruchamiane, gdy kontrolka opuszcza instrukcję `try`.</span><span class="sxs-lookup"><span data-stu-id="d33f2-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="d33f2-105">Transfer kontroli może odbywać się w wyniku normalnego wykonywania, wykonywania `break`, `continue`, `goto`lub instrukcji `return` lub propagacji wyjątku z `try` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d33f2-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="d33f2-106">W ramach obsłużonego wyjątku zagwarantowany jest, że skojarzony blok `finally` jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="d33f2-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="d33f2-107">Jeśli jednak wyjątek nie jest obsługiwany, wykonanie bloku `finally` jest zależne od tego, w jaki sposób wyzwalany jest wyjątek operacji unwind.</span><span class="sxs-lookup"><span data-stu-id="d33f2-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="d33f2-108">To z kolei zależy od konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="d33f2-108">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="d33f2-109">Zwykle, gdy nieobsługiwany wyjątek powoduje zakończenie aplikacji, niezależnie od tego, czy blok `finally` jest uruchomiony, nie jest ważne.</span><span class="sxs-lookup"><span data-stu-id="d33f2-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="d33f2-110">Jednakże jeśli masz instrukcje w bloku `finally`, który musi być uruchamiany nawet w takiej sytuacji, jedno rozwiązanie ma dodać blok `catch` do instrukcji `try`-`finally`.</span><span class="sxs-lookup"><span data-stu-id="d33f2-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="d33f2-111">Alternatywnie można przechwytywać wyjątek, który może zostać wygenerowany w bloku `try` `try`-`finally` instrukcji wyższej stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="d33f2-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="d33f2-112">Oznacza to, że można przechwytywać wyjątek w metodzie, która wywołuje metodę, która zawiera instrukcję `try`-`finally` lub w metodzie, która wywołuje tę metodę, lub w dowolnej metodzie stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="d33f2-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="d33f2-113">Jeśli wyjątek nie zostanie przechwycony, wykonanie bloku `finally` zależy od tego, czy system operacyjny wybiera wyzwalacz operacji unwind.</span><span class="sxs-lookup"><span data-stu-id="d33f2-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="d33f2-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d33f2-114">Example</span></span>

<span data-ttu-id="d33f2-115">W poniższym przykładzie instrukcja konwersji nieprawidłowa powoduje wyjątek `System.InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="d33f2-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="d33f2-116">Wyjątek nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="d33f2-116">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="d33f2-117">W poniższym przykładzie wyjątek z metody `TryCast` jest przechwytywany w metodzie dalej w stosie wywołań.</span><span class="sxs-lookup"><span data-stu-id="d33f2-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="d33f2-118">Aby uzyskać więcej informacji na temat `finally`, zobacz [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="d33f2-118">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="d33f2-119">C#zawiera również [instrukcję using](using-statement.md), która zapewnia podobną funkcjonalność dla <xref:System.IDisposable> obiektów w wygodnej składni.</span><span class="sxs-lookup"><span data-stu-id="d33f2-119">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d33f2-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d33f2-120">C# language specification</span></span>

<span data-ttu-id="d33f2-121">Aby uzyskać więcej informacji, zobacz sekcję [try instrukcji](~/_csharplang/spec/statements.md#the-try-statement) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d33f2-121">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d33f2-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d33f2-122">See also</span></span>

- [<span data-ttu-id="d33f2-123">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d33f2-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d33f2-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d33f2-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d33f2-125">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="d33f2-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d33f2-126">Instrukcje try, throw i catch (C++)</span><span class="sxs-lookup"><span data-stu-id="d33f2-126">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="d33f2-127">throw</span><span class="sxs-lookup"><span data-stu-id="d33f2-127">throw</span></span>](throw.md)
- [<span data-ttu-id="d33f2-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="d33f2-128">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="d33f2-129">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="d33f2-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
