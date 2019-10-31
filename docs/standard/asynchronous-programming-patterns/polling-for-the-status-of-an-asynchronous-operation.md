---
title: Sondowanie stanu operacji asynchronicznych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
ms.openlocfilehash: ff9cefc73adfe1ece1bf7545c75ccb6cc618e89f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123959"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="78b08-102">Sondowanie stanu operacji asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="78b08-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="78b08-103">Aplikacje, które mogą wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej, nie powinny blokować oczekiwania na zakończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="78b08-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="78b08-104">Użyj jednej z następujących opcji, aby kontynuować wykonywanie instrukcji podczas oczekiwania na zakończenie operacji asynchronicznej:</span><span class="sxs-lookup"><span data-stu-id="78b08-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="78b08-105">Użyj właściwości <xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> zwróconej przez metodę **BEGIN**_OperationName_ operacji asynchronicznej, aby określić, czy operacja została ukończona.</span><span class="sxs-lookup"><span data-stu-id="78b08-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="78b08-106">Takie podejście jest nazywane sondami i przedstawiono w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="78b08-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="78b08-107">Użyj delegata <xref:System.AsyncCallback>, aby przetwarzać wyniki operacji asynchronicznej w osobnym wątku.</span><span class="sxs-lookup"><span data-stu-id="78b08-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="78b08-108">Przykład demonstrujący to podejście, zobacz [Używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="78b08-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="78b08-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="78b08-109">Example</span></span>  
 <span data-ttu-id="78b08-110">Poniższy przykład kodu demonstruje użycie metod asynchronicznych w klasie <xref:System.Net.Dns> do pobrania informacji o systemie nazw domen dla komputera określonego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="78b08-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="78b08-111">Ten przykład uruchamia asynchroniczną operację, a następnie drukuje kropki (".") w konsoli do momentu ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="78b08-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="78b08-112">Należy zauważyć, że **wartość null** (**Nothing** w Visual Basic) jest przesyłana do <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> i <xref:System.Object> parametrów, ponieważ te argumenty nie są wymagane podczas korzystania z tego podejścia.</span><span class="sxs-lookup"><span data-stu-id="78b08-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="78b08-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78b08-113">See also</span></span>

- [<span data-ttu-id="78b08-114">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="78b08-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="78b08-115">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="78b08-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
