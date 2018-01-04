---
title: "Blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
dev_langs:
- csharp
- vb
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d9e7a80a9012e85038b72f429e2da569cc43f0bf
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="8b5ec-102">Blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="8b5ec-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="8b5ec-103">Aplikacje, których nie można nadal wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej zablokować przed zakończeniem operacji.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="8b5ec-104">Mają być blokowane podczas oczekiwania na zakończenie operacji asynchronicznych wątku głównego aplikacji, użyj jednej z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="8b5ec-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="8b5ec-105">Operacje asynchroniczne wywołanie **zakończenia** *OperationName* metody.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-105">Call the asynchronous operations **End** *OperationName* method.</span></span> <span data-ttu-id="8b5ec-106">Takie podejście jest przedstawiona w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="8b5ec-107">Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwość <xref:System.IAsyncResult> zwrócony przez operację asynchroniczną **rozpocząć** *OperationName* metody.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method.</span></span> <span data-ttu-id="8b5ec-108">Na przykład, który pokazuje tej metody, zobacz [blokowania aplikacji wykonywania za pomocą właściwości AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="8b5ec-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="8b5ec-109">Aplikacje używające **zakończenia** *OperationName* zwykle wywoła metodę, aby zablokować aż do zakończenia operacji asynchronicznej **rozpocząć**  *OperationName* metody wykonywania pracy mogą być przeprowadzane bez wyniki operacji, a następnie wywołać **zakończenia** *OperationName*.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-109">Applications that use the **End** *OperationName* method to block until an asynchronous operation is complete will typically call the **Begin** *OperationName* method, perform any work that can be done without the results of the operation, and then call **End** *OperationName*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b5ec-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="8b5ec-110">Example</span></span>  
 <span data-ttu-id="8b5ec-111">Poniższy przykład kodu pokazuje używanie metod asynchronicznych w <xref:System.Net.Dns> klasy można pobrać informacji o systemie nazw domen dla komputera określone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="8b5ec-112">Należy pamiętać, że `null` (`Nothing` w języku Visual Basic) jest przekazywana <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` i `stateObject` parametry ponieważ tych argumentów nie są wymagane w przypadku korzystania z tej metody.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8b5ec-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b5ec-113">See Also</span></span>  
 [<span data-ttu-id="8b5ec-114">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="8b5ec-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="8b5ec-115">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="8b5ec-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
