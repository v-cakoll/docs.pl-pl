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
ms.openlocfilehash: beb54cf6c4e6dc87b9a08b81586b24d72f92b84b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001425"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="3f681-102">try-finally (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3f681-102">try-finally (C# Reference)</span></span>
<span data-ttu-id="3f681-103">Za pomocą `finally` bloku, można oczyścić wszystkie zasoby, które są przydzielane w [spróbuj](../../../csharp/language-reference/keywords/try-catch.md) bloku, a może uruchamiać kod, nawet jeśli wystąpi wyjątek w `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="3f681-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](../../../csharp/language-reference/keywords/try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="3f681-104">Typowo, instrukcje `finally` uruchamiania, kiedy formant opuszcza blok `try` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3f681-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="3f681-105">Przeniesienie kontroli może wystąpić w wyniku normalnego wykonania, wykonanie `break`, `continue`, `goto`, lub `return` instrukcji lub propagacji wyjątku z `try` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3f681-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>  
  
 <span data-ttu-id="3f681-106">Wewnątrz obsługiwanego wyjątku, powiązany `finally` bloku jest gwarantowane do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="3f681-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="3f681-107">Jednak jeśli nieobsługiwanego wyjątku wykonanie `finally` bloku jest zależny od jest wyzwalany, jak wyjątku operacji rozwijania.</span><span class="sxs-lookup"><span data-stu-id="3f681-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="3f681-108">Który z kolei jest zależny od konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="3f681-108">That, in turn, is dependent on how your computer is set up.</span></span>
  
 <span data-ttu-id="3f681-109">Zwykle, kiedy nieobsłużony wyjątek kończy aplikację, czy `finally` uruchomieniu bloku nie jest ważna.</span><span class="sxs-lookup"><span data-stu-id="3f681-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="3f681-110">Jednak jeśli masz instrukcje `finally` blok, który musi być uruchamiany nawet w tej sytuacji, rozwiązaniem jest dodanie `catch` za pomocą bloku `try` - `finally` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3f681-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="3f681-111">Alternatywnie, można wychwycić wyjątek, który może zostać wygenerowany w `try` bloku `try` - `finally` instrukcji wyższego rzędu stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="3f681-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="3f681-112">Oznacza to, że może przechwycić wyjątek w metodzie, która wywołuje metodę, która zawiera `try` - `finally` instrukcji, lub w metodzie, która wywołuje tę metodę, lub dowolną metodę w stosie wywołań.</span><span class="sxs-lookup"><span data-stu-id="3f681-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="3f681-113">Jeśli wyjątek nie zostanie przechwycony, wykonanie `finally` bloku zależy od tego, czy system operacyjny wybierze wywołanie wyjątku operacji rozwijania.</span><span class="sxs-lookup"><span data-stu-id="3f681-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f681-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f681-114">Example</span></span>  
 <span data-ttu-id="3f681-115">W poniższym przykładzie instrukcja nieprawidłowej konwersji powoduje, że `System.InvalidCastException` wyjątku.</span><span class="sxs-lookup"><span data-stu-id="3f681-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="3f681-116">Wyjątek jest nieobsługiwany.</span><span class="sxs-lookup"><span data-stu-id="3f681-116">The exception is unhandled.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 <span data-ttu-id="3f681-117">W poniższym przykładzie, wyjątek od `TryCast` metoda padł w metodzie dalej położonej w stosie wywołań.</span><span class="sxs-lookup"><span data-stu-id="3f681-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 <span data-ttu-id="3f681-118">Aby uzyskać więcej informacji na temat `finally`, zobacz [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="3f681-118">For more information about `finally`, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
 <span data-ttu-id="3f681-119">C# zawiera również [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md), który zapewnia podobną funkcjonalność dla <xref:System.IDisposable> obiektów w wygodnej składni.</span><span class="sxs-lookup"><span data-stu-id="3f681-119">C# also contains the [using statement](../../../csharp/language-reference/keywords/using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3f681-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3f681-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3f681-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f681-121">See Also</span></span>

- [<span data-ttu-id="3f681-122">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3f681-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="3f681-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3f681-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3f681-124">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="3f681-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="3f681-125">Instrukcje try, throw i catch (C++)</span><span class="sxs-lookup"><span data-stu-id="3f681-125">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
- [<span data-ttu-id="3f681-126">Instrukcje obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="3f681-126">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
- [<span data-ttu-id="3f681-127">throw</span><span class="sxs-lookup"><span data-stu-id="3f681-127">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
- [<span data-ttu-id="3f681-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="3f681-128">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
- [<span data-ttu-id="3f681-129">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="3f681-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
