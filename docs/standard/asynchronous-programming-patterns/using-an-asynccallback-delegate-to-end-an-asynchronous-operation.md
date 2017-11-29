---
title: "Używanie delegata AsyncCallback do kończenia operacji asynchronicznej"
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
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbe170588776daa97fec4c736d4b1bdd871de518
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="49c35-102">Używanie delegata AsyncCallback do kończenia operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="49c35-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="49c35-103">Aplikacje, które mogą wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej nie powinny blokować oczekiwania przed zakończeniem operacji.</span><span class="sxs-lookup"><span data-stu-id="49c35-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="49c35-104">Do kontynuowania wykonywania instrukcji podczas oczekiwania na zakończenie operacji asynchronicznych, użyj jednej z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="49c35-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="49c35-105">Użyj <xref:System.AsyncCallback> pełnomocnika, aby przetworzyć wyników operacji asynchronicznych w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="49c35-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="49c35-106">Takie podejście jest przedstawiona w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="49c35-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="49c35-107">Użyj <xref:System.IAsyncResult.IsCompleted%2A> właściwość <xref:System.IAsyncResult> zwrócony przez operację asynchroniczną **rozpocząć** *OperationName* metodę, aby określić, czy operacja została ukończona.</span><span class="sxs-lookup"><span data-stu-id="49c35-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="49c35-108">Na przykład, który pokazuje tej metody, zobacz [sondowanie stanu operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="49c35-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="49c35-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="49c35-109">Example</span></span>  
 <span data-ttu-id="49c35-110">Poniższy przykład kodu pokazuje używanie metod asynchronicznych w <xref:System.Net.Dns> klasy można pobrać informacji o systemie nazw domen (DNS, Domain Name System) dla komputerów określonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="49c35-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="49c35-111">Ten przykład tworzy <xref:System.AsyncCallback> delegata, który odwołuje się do `ProcessDnsInformation` metody.</span><span class="sxs-lookup"><span data-stu-id="49c35-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="49c35-112">Ta metoda jest wywoływana raz dla każdego żądania asynchroniczne, aby uzyskać informacje dotyczące systemu DNS.</span><span class="sxs-lookup"><span data-stu-id="49c35-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="49c35-113">Należy pamiętać, że host określone przez użytkownika są przekazywane do <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> parametru.</span><span class="sxs-lookup"><span data-stu-id="49c35-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="49c35-114">Na przykład przedstawiający definiowanie i przy użyciu bardziej złożonych obiekt stanu zobacz [przy użyciu delegata AsyncCallback i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span><span class="sxs-lookup"><span data-stu-id="49c35-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="49c35-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49c35-115">See Also</span></span>  
 [<span data-ttu-id="49c35-116">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="49c35-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="49c35-117">Omówienie wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="49c35-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="49c35-118">Wywołanie metod asynchronicznych za pomocą interfejsu IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="49c35-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [<span data-ttu-id="49c35-119">Przy użyciu delegata AsyncCallback i obiektu stanu</span><span class="sxs-lookup"><span data-stu-id="49c35-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
