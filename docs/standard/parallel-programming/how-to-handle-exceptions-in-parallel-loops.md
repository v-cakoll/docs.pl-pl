---
title: 'Porady: obsługa wyjątków w pętlach równoległych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddf311ad2b79e615f5c3097686035e7bbfbc49c9
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47113351"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="bdd3f-102">Porady: obsługa wyjątków w pętlach równoległych</span><span class="sxs-lookup"><span data-stu-id="bdd3f-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="bdd3f-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> przeciążenia nie mają żadnych specjalnych mechanizm obsługi wyjątków, które może zostać wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="bdd3f-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="bdd3f-104">W związku z tym przypominają zwykłe `for` i `foreach` pętli (`For` i `For Each` w języku Visual Basic); wystąpił nieobsługiwany wyjątek powoduje pętlę, można od razu zakończyć.</span><span class="sxs-lookup"><span data-stu-id="bdd3f-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate immediately.</span></span>  
  
 <span data-ttu-id="bdd3f-105">Po dodaniu własną logiką obsługi wyjątków, równoległe pętli, obsłużyć przypadek, w którym podobne wyjątków może być wyrzucanych na wiele wątków jednocześnie, a także przypadek, w którym wyjątek zgłoszony w jednym wątku powoduje zgłoszenie wyjątku inny od innego Wątek.</span><span class="sxs-lookup"><span data-stu-id="bdd3f-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="bdd3f-106">Może obsługiwać obu przypadkach dzięki zawijaniu wszystkie wyjątki z pętli w <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bdd3f-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bdd3f-107">Poniższy przykład przedstawia jedno z możliwych podejść.</span><span class="sxs-lookup"><span data-stu-id="bdd3f-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdd3f-108">Po włączeniu "Tylko mój kod" Visual Studio, w niektórych przypadkach przerwania w wierszu, który zgłasza wyjątek i wyświetlić komunikat o błędzie informujący, że "wyjątek nie obsłużony przez kod użytkownika."</span><span class="sxs-lookup"><span data-stu-id="bdd3f-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="bdd3f-109">Ten błąd jest nieszkodliwe.</span><span class="sxs-lookup"><span data-stu-id="bdd3f-109">This error is benign.</span></span> <span data-ttu-id="bdd3f-110">Naciśnij klawisz F5, aby nadal z niego i sprawdzić sposób obsługi wyjątków, przedstawionej w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bdd3f-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="bdd3f-111">Aby zapobiec istotne w przypadku pierwszego błędu programu Visual Studio, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="bdd3f-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdd3f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="bdd3f-112">Example</span></span>  
 <span data-ttu-id="bdd3f-113">W tym przykładzie wszystkie wyjątki są przechwytywane i następnie otoczona <xref:System.AggregateException?displayProperty=nameWithType> której zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="bdd3f-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="bdd3f-114">Obiekt wywołujący można zdecydować, której wyjątki, aby obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="bdd3f-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="bdd3f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bdd3f-115">See also</span></span>

- [<span data-ttu-id="bdd3f-116">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="bdd3f-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [<span data-ttu-id="bdd3f-117">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="bdd3f-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
