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
ms.openlocfilehash: 87405425e85ed16d10b3e8b382c6e414fff10ddf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278535"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="31821-102">Instrukcje: Obsługa wyjątków w pętlach równoległych</span><span class="sxs-lookup"><span data-stu-id="31821-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="31821-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>Przeciążenia i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> nie mają żadnego specjalnego mechanizmu do obsługi wyjątków, które mogą być zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="31821-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="31821-104">W tym aspekcie przypominają one regularne `for` i `foreach` pętle ( `For` i `For Each` w Visual Basic); nieobsłużony wyjątek powoduje przerwanie działania pętli zaraz po zakończeniu wszystkich aktualnie uruchomionych iteracji.</span><span class="sxs-lookup"><span data-stu-id="31821-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate as soon as all currently running iterations finish.</span></span>
  
 <span data-ttu-id="31821-105">W przypadku dodawania własnej logiki obsługi wyjątków do pętli równoległych, należy obsłużyć przypadek, w którym mogą być zgłaszane podobne wyjątki w wielu wątkach jednocześnie, a w przypadku, gdy wyjątek zgłoszony w jednym wątku powoduje zgłoszenie innego wyjątku w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="31821-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="31821-106">Oba przypadki można obsługiwać, zawijając wszystkie wyjątki z pętli w <xref:System.AggregateException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="31821-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="31821-107">W poniższym przykładzie pokazano jedno z możliwych podejścia.</span><span class="sxs-lookup"><span data-stu-id="31821-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31821-108">Po włączeniu "Tylko mój kod" program Visual Studio będzie przerywał pracę w wierszu, który zgłosi wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika".</span><span class="sxs-lookup"><span data-stu-id="31821-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="31821-109">Ten błąd jest niegroźny.</span><span class="sxs-lookup"><span data-stu-id="31821-109">This error is benign.</span></span> <span data-ttu-id="31821-110">Możesz nacisnąć klawisz F5, aby kontynuować z niego i zobaczyć zachowanie obsługi wyjątków, które zostało przedstawione w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="31821-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="31821-111">Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **Narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="31821-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31821-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="31821-112">Example</span></span>  
 <span data-ttu-id="31821-113">W tym przykładzie wszystkie wyjątki są przechwytywane, a następnie zawijane w <xref:System.AggregateException?displayProperty=nameWithType> , które są generowane.</span><span class="sxs-lookup"><span data-stu-id="31821-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="31821-114">Obiekt wywołujący może zdecydować, które wyjątki mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="31821-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="31821-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31821-115">See also</span></span>

- [<span data-ttu-id="31821-116">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="31821-116">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="31821-117">Wyrażenia lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="31821-117">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
