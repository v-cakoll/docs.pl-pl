---
title: try-finally (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 696eb531fe3e340f7fe0ae12483648119cf5a7eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288297"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="c4af9-102">try-finally (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c4af9-102">try-finally (C# Reference)</span></span>
<span data-ttu-id="c4af9-103">Za pomocą `finally` bloku, możesz wyczyścić wszystkie zasoby, które są przydzielane w [spróbuj](../../../csharp/language-reference/keywords/try-catch.md) bloku, a można uruchomić kod, nawet jeśli wystąpienia wyjątku w `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="c4af9-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](../../../csharp/language-reference/keywords/try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="c4af9-104">Zazwyczaj instrukcje `finally` bloku uruchamiany, gdy formant pozostawia `try` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c4af9-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="c4af9-105">Przekazanie sterowania może wystąpić w wyniku normalnego wykonywania wykonywania `break`, `continue`, `goto`, lub `return` instrukcji lub propagacji wyjątek poza `try` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c4af9-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>  
  
 <span data-ttu-id="c4af9-106">W ramach obsłużył wyjątek skojarzony `finally` bloku jest gwarantowana do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="c4af9-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="c4af9-107">Jednak jeśli nieobsłużony wyjątek, wykonywanie `finally` bloku jest zależna od jak wyjątek unwind operacji zostanie wywołany.</span><span class="sxs-lookup"><span data-stu-id="c4af9-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="c4af9-108">Który z kolei jest zależny od konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="c4af9-108">That, in turn, is dependent on how your computer is set up.</span></span>
  
 <span data-ttu-id="c4af9-109">Zwykle, gdy wystąpił nieobsługiwany wyjątek kończy się aplikacji, czy `finally` uruchomieniu bloku nie jest ważna.</span><span class="sxs-lookup"><span data-stu-id="c4af9-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="c4af9-110">Jednak jeśli w instrukcji `finally` bloku, które muszą być uruchamiane, nawet w takiej sytuacji jedno rozwiązanie polega na dodaniu `catch` za pomocą bloku `try` - `finally` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c4af9-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="c4af9-111">Alternatywnie można przechwycić wyjątek, który może zostać zgłoszone w `try` zablokować z `try` - `finally` instrukcji górę stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="c4af9-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="c4af9-112">Oznacza to, że zostaną wychwycone wyjątek w metodzie, która wywołuje metodę, która zawiera `try` - `finally` instrukcji, lub w metodzie, która wywołuje tę metodę, lub w dowolnej metody w stosie wywołań.</span><span class="sxs-lookup"><span data-stu-id="c4af9-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="c4af9-113">Jeśli nie zostanie przechwycony wyjątek, wykonywanie `finally` bloku zależy od tego, czy system operacyjny wybierze do wyzwolenia wyjątek operacji unwind.</span><span class="sxs-lookup"><span data-stu-id="c4af9-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4af9-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4af9-114">Example</span></span>  
 <span data-ttu-id="c4af9-115">W poniższym przykładzie instrukcja Nieprawidłowa konwersja powoduje `System.InvalidCastException` wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c4af9-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="c4af9-116">Wyjątkiem jest nieobsługiwany.</span><span class="sxs-lookup"><span data-stu-id="c4af9-116">The exception is unhandled.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 <span data-ttu-id="c4af9-117">W poniższym przykładzie wyjątku z `TryCast` metody zostanie przechwycony w metodzie dalej górę stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="c4af9-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 <span data-ttu-id="c4af9-118">Aby uzyskać więcej informacji na temat `finally`, zobacz [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="c4af9-118">For more information about `finally`, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
 <span data-ttu-id="c4af9-119">C# zawiera także [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md), która oferuje podobne funkcje dla <xref:System.IDisposable> obiektów w dogodnym składni.</span><span class="sxs-lookup"><span data-stu-id="c4af9-119">C# also contains the [using statement](../../../csharp/language-reference/keywords/using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c4af9-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c4af9-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c4af9-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4af9-121">See Also</span></span>  
 [<span data-ttu-id="c4af9-122">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="c4af9-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c4af9-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c4af9-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c4af9-124">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c4af9-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c4af9-125">Instrukcje try, throw i catch (C++)</span><span class="sxs-lookup"><span data-stu-id="c4af9-125">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [<span data-ttu-id="c4af9-126">Instrukcje obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="c4af9-126">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="c4af9-127">throw</span><span class="sxs-lookup"><span data-stu-id="c4af9-127">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
 [<span data-ttu-id="c4af9-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="c4af9-128">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="c4af9-129">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="c4af9-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
