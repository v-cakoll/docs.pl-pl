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
ms.openlocfilehash: 5d108937e6ab2483cd1633d4b398c1e250f5c098
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453016"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="1bf92-102">Porady: obsługa wyjątków w pętlach równoległych</span><span class="sxs-lookup"><span data-stu-id="1bf92-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="1bf92-103">Przeciążenia <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> nie mają żadnego specjalnego mechanizmu do obsługi wyjątków, które mogą być zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="1bf92-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="1bf92-104">W tym względzie są one podobne do zwykłych `for` i `foreach` pętli (`For` i `For Each` w Visual Basic); nieobsługiwany wyjątek powoduje, że pętla zostanie zakończona zaraz po zakończeniu wszystkich aktualnie uruchomionych iteracji.</span><span class="sxs-lookup"><span data-stu-id="1bf92-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate as soon as all currently running iterations finish.</span></span>
  
 <span data-ttu-id="1bf92-105">W przypadku dodawania własnej logiki obsługi wyjątków do pętli równoległych należy obsłużyć przypadek, w którym mogą zostać zgłoszone podobne wyjątki w wielu wątkach jednocześnie, a w przypadku, gdy wyjątek zgłoszony w jednym wątku powoduje zgłoszenie innego wyjątku w innym nici.</span><span class="sxs-lookup"><span data-stu-id="1bf92-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="1bf92-106">Oba przypadki można obsługiwać, zawijając wszystkie wyjątki z pętli w <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1bf92-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1bf92-107">W poniższym przykładzie pokazano jedno z możliwych podejścia.</span><span class="sxs-lookup"><span data-stu-id="1bf92-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1bf92-108">Po włączeniu "Tylko mój kod" program Visual Studio będzie przerywał pracę w wierszu, który zgłosi wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika".</span><span class="sxs-lookup"><span data-stu-id="1bf92-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="1bf92-109">Ten błąd jest niegroźny.</span><span class="sxs-lookup"><span data-stu-id="1bf92-109">This error is benign.</span></span> <span data-ttu-id="1bf92-110">Możesz nacisnąć klawisz F5, aby kontynuować z niego i zobaczyć zachowanie obsługi wyjątków, które zostało przedstawione w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1bf92-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="1bf92-111">Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **Narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="1bf92-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bf92-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="1bf92-112">Example</span></span>  
 <span data-ttu-id="1bf92-113">W tym przykładzie wszystkie wyjątki są przechwytywane, a następnie pakowane w <xref:System.AggregateException?displayProperty=nameWithType>, które jest zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="1bf92-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="1bf92-114">Obiekt wywołujący może zdecydować, które wyjątki mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="1bf92-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="1bf92-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1bf92-115">See also</span></span>

- [<span data-ttu-id="1bf92-116">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="1bf92-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="1bf92-117">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="1bf92-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
