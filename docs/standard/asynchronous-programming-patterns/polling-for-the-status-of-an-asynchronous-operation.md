---
title: Sondowanie stanu operacji asynchronicznych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 51e2ada4b493e8b1cbe0744c00fc2c25f9a266fb
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="43f63-102">Sondowanie stanu operacji asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="43f63-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="43f63-103">Aplikacje, które mogą wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej nie powinny blokować oczekiwania przed zakończeniem operacji.</span><span class="sxs-lookup"><span data-stu-id="43f63-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="43f63-104">Do kontynuowania wykonywania instrukcji podczas oczekiwania na zakończenie operacji asynchronicznych, użyj jednej z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="43f63-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="43f63-105">Użyj <xref:System.IAsyncResult.IsCompleted%2A> właściwość <xref:System.IAsyncResult> zwrócony przez operację asynchroniczną **rozpocząć *** OperationName* metodę, aby określić, czy operacja została ukończona.</span><span class="sxs-lookup"><span data-stu-id="43f63-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin***OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="43f63-106">Takie podejście jest znana jako sondowania i jest przedstawiona w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="43f63-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="43f63-107">Użyj <xref:System.AsyncCallback> pełnomocnika, aby przetworzyć wyników operacji asynchronicznych w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="43f63-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="43f63-108">Na przykład, który pokazuje tej metody, zobacz [używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="43f63-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43f63-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="43f63-109">Example</span></span>  
 <span data-ttu-id="43f63-110">Poniższy przykład kodu pokazuje używanie metod asynchronicznych w <xref:System.Net.Dns> klasy można pobrać informacji o systemie nazw domen dla komputera określone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="43f63-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="43f63-111">W tym przykładzie rozpoczyna operację asynchroniczną, a następnie drukuje kropki (".") w konsoli aż do zakończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="43f63-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="43f63-112">Należy pamiętać, że **null** (**nic** w języku Visual Basic) jest przekazywana <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> i <xref:System.Object> parametry ponieważ tych argumentów nie są wymagane w przypadku korzystania z tej metody.</span><span class="sxs-lookup"><span data-stu-id="43f63-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="43f63-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43f63-113">See Also</span></span>  
 [<span data-ttu-id="43f63-114">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="43f63-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="43f63-115">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="43f63-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
