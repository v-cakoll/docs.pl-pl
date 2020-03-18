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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77453016"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="78e11-102">Porady: obsługa wyjątków w pętlach równoległych</span><span class="sxs-lookup"><span data-stu-id="78e11-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="78e11-103">I <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> przeciążenia nie mają żadnego specjalnego mechanizmu do obsługi wyjątków, które mogą być generowane.</span><span class="sxs-lookup"><span data-stu-id="78e11-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="78e11-104">W związku z tym `for` przypominają `foreach` one`For` regularne `For Each` i pętle ( i w visual basic); nieobsługiwany wyjątek powoduje, że pętla kończy się natychmiast po zakończeniu wszystkich aktualnie uruchomionych iteracji.</span><span class="sxs-lookup"><span data-stu-id="78e11-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate as soon as all currently running iterations finish.</span></span>
  
 <span data-ttu-id="78e11-105">Po dodaniu własnej logiki obsługi wyjątków do pętli równoległych, należy obsługiwać przypadek, w którym podobne wyjątki mogą być generowane na wiele wątków jednocześnie, a przypadek, w którym wyjątek w jednym wątku powoduje, że inny wyjątek ma zostać wygenerowany w innym Wątku.</span><span class="sxs-lookup"><span data-stu-id="78e11-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="78e11-106">Obie sprawy można obsługiwać, zawijając <xref:System.AggregateException?displayProperty=nameWithType>wszystkie wyjątki z pętli w pliku .</span><span class="sxs-lookup"><span data-stu-id="78e11-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="78e11-107">W poniższym przykładzie przedstawiono jedno możliwe podejście.</span><span class="sxs-lookup"><span data-stu-id="78e11-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78e11-108">Gdy opcja "Tylko mój kod" jest włączona, visual studio w niektórych przypadkach zostanie przerwana w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie z komunikatem "wyjątek nie jest obsługiwany przez kod użytkownika".</span><span class="sxs-lookup"><span data-stu-id="78e11-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="78e11-109">Ten błąd jest niegroźny.</span><span class="sxs-lookup"><span data-stu-id="78e11-109">This error is benign.</span></span> <span data-ttu-id="78e11-110">Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, który został pokazany w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="78e11-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="78e11-111">Aby zapobiec przerywaniu pierwszego błędu przez program Visual Studio, wystarczy odznaczyć pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.</span><span class="sxs-lookup"><span data-stu-id="78e11-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78e11-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="78e11-112">Example</span></span>  
 <span data-ttu-id="78e11-113">W tym przykładzie wszystkie wyjątki są przechwycone, a następnie zawinięte w który <xref:System.AggregateException?displayProperty=nameWithType> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="78e11-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="78e11-114">Obiekt wywołujący może zdecydować, które wyjątki do obsługi.</span><span class="sxs-lookup"><span data-stu-id="78e11-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="78e11-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78e11-115">See also</span></span>

- [<span data-ttu-id="78e11-116">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="78e11-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="78e11-117">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="78e11-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
