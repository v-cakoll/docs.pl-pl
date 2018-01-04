---
title: "Używanie delegata AsyncCallback i obiektu stanu"
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
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cb0cdc9e98dcaf3c9f9879359eff0b31c8435773
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="b0dcd-102">Używanie delegata AsyncCallback i obiektu stanu</span><span class="sxs-lookup"><span data-stu-id="b0dcd-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="b0dcd-103">Jeśli używasz <xref:System.AsyncCallback> delegować do przetworzenia wyniki operacji asynchronicznych w oddzielnym wątku, obiekt stanu może być używany do przekazywania informacji między wywołaniami zwrotnymi oraz do pobierania wynik końcowy.</span><span class="sxs-lookup"><span data-stu-id="b0dcd-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="b0dcd-104">W tym temacie przedstawiono tej praktyki rozwijając przykład [używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="b0dcd-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0dcd-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0dcd-105">Example</span></span>  
 <span data-ttu-id="b0dcd-106">Poniższy przykład kodu pokazuje używanie metod asynchronicznych w <xref:System.Net.Dns> klasy można pobrać informacji o systemie nazw domen (DNS, Domain Name System) dla komputerów określonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b0dcd-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="b0dcd-107">W tym przykładzie definiuje i używa `HostRequest` klasę do przechowywania informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="b0dcd-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="b0dcd-108">A `HostRequest` obiekt pobiera utworzony dla każdej wprowadzonej przez użytkownika nazwy komputera.</span><span class="sxs-lookup"><span data-stu-id="b0dcd-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="b0dcd-109">Ten obiekt jest przekazywany do <xref:System.Net.Dns.BeginGetHostByName%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b0dcd-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="b0dcd-110">`ProcessDnsInformation` Metoda jest wywoływana za każdym razem kończy żądanie.</span><span class="sxs-lookup"><span data-stu-id="b0dcd-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="b0dcd-111">`HostRequest` Pobrać obiektu przy użyciu <xref:System.IAsyncResult.AsyncState%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0dcd-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="b0dcd-112">`ProcessDnsInformation` Używa metody `HostRequest` obiekt, aby zapisać <xref:System.Net.IPHostEntry> zwracane przez żądanie lub <xref:System.Net.Sockets.SocketException> zgłoszony przez żądanie.</span><span class="sxs-lookup"><span data-stu-id="b0dcd-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="b0dcd-113">Po zakończeniu wszystkich żądań aplikacji przechodzi przez `HostRequest` obiekty i wyświetla informacje dotyczące systemu DNS lub <xref:System.Net.Sockets.SocketException> komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="b0dcd-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b0dcd-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0dcd-114">See Also</span></span>  
 [<span data-ttu-id="b0dcd-115">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="b0dcd-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="b0dcd-116">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="b0dcd-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="b0dcd-117">Używanie delegata AsyncCallback do kończenia operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="b0dcd-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
