---
title: try-finally - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2c4c69b1e104aed968bc24bac690de83026643a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713017"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="c5bdd-102">try-finally (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c5bdd-102">try-finally (C# Reference)</span></span>

<span data-ttu-id="c5bdd-103">Za pomocą `finally` bloku, można oczyścić wszystkie zasoby, które są przydzielane w [try](try-catch.md) bloku `try` i można uruchomić kod, nawet jeśli wystąpi wyjątek w bloku.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="c5bdd-104">Zazwyczaj instrukcje `finally` bloku uruchomić, gdy formant `try` pozostawia instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="c5bdd-105">Przeniesienie kontroli może nastąpić w wyniku normalnego wykonania, `break` `continue`wykonania `goto`, `return` , lub instrukcji lub propagacji `try` wyjątku z instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="c5bdd-106">W ramach obsługiwanego wyjątku skojarzony `finally` blok jest gwarantowany do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="c5bdd-107">Jednak jeśli wyjątek jest nieobsługiwany, wykonanie `finally` bloku zależy od sposobu wyzwalania operacji unwind wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="c5bdd-108">To z kolei zależy od konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-108">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="c5bdd-109">Zazwyczaj po zakończeniu nieobsługiwanego wyjątku aplikacja, `finally` czy blok jest uruchamiany nie jest ważne.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="c5bdd-110">Jednak jeśli masz instrukcje `finally` w bloku, które muszą być uruchamiane nawet `catch` w tej `try` - `finally` sytuacji, jednym rozwiązaniem jest dodanie bloku do instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="c5bdd-111">Alternatywnie można przechwycić wyjątek, który może `try` zostać `try` - `finally` wygenerowany w bloku instrukcji wyżej stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="c5bdd-112">Oznacza to, że można przechwycić wyjątek w metodzie, która wywołuje metodę, która zawiera instrukcję `try` - `finally` lub w metodzie, która wywołuje tę metodę lub w dowolnej metody w stosie wywołań.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="c5bdd-113">Jeśli wyjątek nie zostanie przechwycona, wykonanie `finally` bloku zależy od tego, czy system operacyjny zdecyduje się wyzwolić operację unwind wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="c5bdd-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5bdd-114">Example</span></span>

<span data-ttu-id="c5bdd-115">W poniższym przykładzie nieprawidłowe oświadczenie konwersji `System.InvalidCastException` powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="c5bdd-116">Wyjątek jest nieobsługiwany.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-116">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="c5bdd-117">W poniższym przykładzie wyjątek `TryCast` od metody jest przechwycone w metodzie dalej stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="c5bdd-118">Aby uzyskać `finally`więcej informacji na temat , zobacz [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="c5bdd-118">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="c5bdd-119">C# zawiera również [using instrukcji](using-statement.md), który <xref:System.IDisposable> zapewnia podobne funkcje dla obiektów w składni wygodne.</span><span class="sxs-lookup"><span data-stu-id="c5bdd-119">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c5bdd-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c5bdd-120">C# language specification</span></span>

<span data-ttu-id="c5bdd-121">Aby uzyskać więcej informacji, zobacz sekcję [instrukcja wypróbuj](~/_csharplang/spec/statements.md#the-try-statement) [specyfikację języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="c5bdd-121">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c5bdd-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5bdd-122">See also</span></span>

- [<span data-ttu-id="c5bdd-123">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="c5bdd-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c5bdd-124">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="c5bdd-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c5bdd-125">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c5bdd-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c5bdd-126">Instrukcje try, throw i catch (C++)</span><span class="sxs-lookup"><span data-stu-id="c5bdd-126">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="c5bdd-127">throw</span><span class="sxs-lookup"><span data-stu-id="c5bdd-127">throw</span></span>](throw.md)
- [<span data-ttu-id="c5bdd-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="c5bdd-128">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="c5bdd-129">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="c5bdd-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
