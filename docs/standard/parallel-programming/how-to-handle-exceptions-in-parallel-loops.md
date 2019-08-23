---
title: 'Instrukcje: Obsługa wyjątków w pętlach równoległych'
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
ms.openlocfilehash: 2ffc522b2ab13ae2098c01e6716e00aef5bef8e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962495"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="e00a6-102">Instrukcje: Obsługa wyjątków w pętlach równoległych</span><span class="sxs-lookup"><span data-stu-id="e00a6-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="e00a6-103">Przeciążenia <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> nie mają żadnego specjalnego mechanizmu do obsługi wyjątków, które mogą być zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="e00a6-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="e00a6-104">W tym `for` aspekcie przypominają one regularne i `foreach` pętle (`For` i `For Each` w Visual Basic); nieobsługiwany wyjątek powoduje natychmiastowe zakończenie działania pętli.</span><span class="sxs-lookup"><span data-stu-id="e00a6-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate immediately.</span></span>  
  
 <span data-ttu-id="e00a6-105">W przypadku dodawania własnej logiki obsługi wyjątków do pętli równoległych należy obsłużyć przypadek, w którym mogą zostać zgłoszone podobne wyjątki w wielu wątkach jednocześnie, a w przypadku, gdy wyjątek zgłoszony w jednym wątku powoduje zgłoszenie innego wyjątku w innym nici.</span><span class="sxs-lookup"><span data-stu-id="e00a6-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="e00a6-106">Oba przypadki można obsługiwać, zawijając wszystkie wyjątki z pętli w <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e00a6-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e00a6-107">W poniższym przykładzie pokazano jedno z możliwych podejścia.</span><span class="sxs-lookup"><span data-stu-id="e00a6-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e00a6-108">Po włączeniu "Tylko mój kod" program Visual Studio będzie przerywał pracę w wierszu, który zgłosi wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika".</span><span class="sxs-lookup"><span data-stu-id="e00a6-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="e00a6-109">Ten błąd jest niegroźny.</span><span class="sxs-lookup"><span data-stu-id="e00a6-109">This error is benign.</span></span> <span data-ttu-id="e00a6-110">Możesz nacisnąć klawisz F5, aby kontynuować z niego i zobaczyć zachowanie obsługi wyjątków, które zostało przedstawione w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e00a6-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="e00a6-111">Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **Narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="e00a6-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e00a6-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e00a6-112">Example</span></span>  
 <span data-ttu-id="e00a6-113">W tym przykładzie wszystkie wyjątki są przechwytywane, a następnie zawijane <xref:System.AggregateException?displayProperty=nameWithType> w, które są generowane.</span><span class="sxs-lookup"><span data-stu-id="e00a6-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="e00a6-114">Obiekt wywołujący może zdecydować, które wyjątki mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e00a6-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="e00a6-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e00a6-115">See also</span></span>

- [<span data-ttu-id="e00a6-116">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="e00a6-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="e00a6-117">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="e00a6-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
