---
title: "Porady: obsługa wyjątków w pętlach równoległych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f6df28a019c2a21cc6ef94367553e0e5eaa1ad30
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="6183c-102">Porady: obsługa wyjątków w pętlach równoległych</span><span class="sxs-lookup"><span data-stu-id="6183c-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="6183c-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> przeciążenia nie ma żadnych specjalnych mechanizm obsługi wyjątków, które może zostać zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="6183c-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="6183c-104">W związku z tym są podobne do zwykłych `for` i `foreach` pętli (`For` i `For Each` w języku Visual Basic); wystąpił nieobsługiwany wyjątek powoduje pętli zakończenie natychmiast.</span><span class="sxs-lookup"><span data-stu-id="6183c-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate immediately.</span></span>  
  
 <span data-ttu-id="6183c-105">Po dodaniu własną logikę obsługi wyjątków, aby pętle równoległe, obsługiwać przypadek, w którym podobne wyjątki może zostać zgłoszone na wiele wątków jednocześnie i przypadków, w którym wyjątek w wątku, co powoduje, że kolejny wyjątek zostanie wygenerowany na innym Wątek.</span><span class="sxs-lookup"><span data-stu-id="6183c-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="6183c-106">Może obsługiwać obu przypadkach zawijania wszystkie wyjątki pętlę w <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6183c-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6183c-107">W poniższym przykładzie przedstawiono jeden ze sposobów możliwe.</span><span class="sxs-lookup"><span data-stu-id="6183c-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6183c-108">Po włączeniu "Tylko mój kod" programu Visual Studio w niektórych przypadkach będzie podział wiersza, która zgłasza wyjątek i wyświetlony komunikat o błędzie stwierdzający "wyjątek nie obsłużony przez kod użytkownika."</span><span class="sxs-lookup"><span data-stu-id="6183c-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="6183c-109">Ten błąd jest niegroźne.</span><span class="sxs-lookup"><span data-stu-id="6183c-109">This error is benign.</span></span> <span data-ttu-id="6183c-110">Naciśnij klawisz F5, aby nadal z niego i zachowanie obsługi wyjątków, które przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6183c-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="6183c-111">Aby zapobiec dzieleniu pierwszego błędu w Visual Studio, wystarczy usunąć zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="6183c-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6183c-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="6183c-112">Example</span></span>  
 <span data-ttu-id="6183c-113">W tym przykładzie wszystkie wyjątki są przechwycony i następnie otoczona <xref:System.AggregateException?displayProperty=nameWithType> który jest generowany.</span><span class="sxs-lookup"><span data-stu-id="6183c-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="6183c-114">Obiekt wywołujący można zdecydować, które wyjątki, aby obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="6183c-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="6183c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6183c-115">See Also</span></span>  
 [<span data-ttu-id="6183c-116">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="6183c-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="6183c-117">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="6183c-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
