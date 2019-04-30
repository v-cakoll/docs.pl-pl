---
title: Używanie delegata AsyncCallback i obiektu stanu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb62b191dc3b3246745f9f0ea3737ed74a2bf57b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699009"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="a5a3a-102">Używanie delegata AsyncCallback i obiektu stanu</span><span class="sxs-lookup"><span data-stu-id="a5a3a-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="a5a3a-103">Kiedy używasz <xref:System.AsyncCallback> delegować do przetwarzania wyników operacji asynchronicznych w oddzielnym wątku, można użyć obiektu stanu do przekazywania informacji między wywołania zwrotne i pobrać wynik końcowy.</span><span class="sxs-lookup"><span data-stu-id="a5a3a-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="a5a3a-104">W tym temacie przedstawiono tej praktyką, rozszerzając przykład przedstawiony w [używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="a5a3a-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5a3a-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5a3a-105">Example</span></span>  
 <span data-ttu-id="a5a3a-106">Poniższy przykład kodu demonstruje, za pomocą metod asynchronicznych we <xref:System.Net.Dns> klasy do pobrania informacji systemu nazw domen (DNS, Domain Name System) dla komputerów z określonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a5a3a-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="a5a3a-107">W tym przykładzie definiuje i używa `HostRequest` klasę do przechowywania informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="a5a3a-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="a5a3a-108">A `HostRequest` obiekt tworzony dla każdej wprowadzonej przez użytkownika nazwy komputera.</span><span class="sxs-lookup"><span data-stu-id="a5a3a-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="a5a3a-109">Ten obiekt jest przekazywany do <xref:System.Net.Dns.BeginGetHostByName%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a5a3a-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="a5a3a-110">`ProcessDnsInformation` Metoda jest wywoływana za każdym razem, kończy żądanie.</span><span class="sxs-lookup"><span data-stu-id="a5a3a-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="a5a3a-111">`HostRequest` Obiektu są pobierane przy użyciu <xref:System.IAsyncResult.AsyncState%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a5a3a-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="a5a3a-112">`ProcessDnsInformation` Metoda używa `HostRequest` obiekt ma być przechowywany <xref:System.Net.IPHostEntry> zwróconym przez żądanie jest lub <xref:System.Net.Sockets.SocketException> generowane przez żądanie.</span><span class="sxs-lookup"><span data-stu-id="a5a3a-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="a5a3a-113">Po ukończeniu wszystkich żądań aplikacji wykonuje iterację na `HostRequest` obiektów i wyświetla informacje DNS lub <xref:System.Net.Sockets.SocketException> komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="a5a3a-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a5a3a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5a3a-114">See also</span></span>

- [<span data-ttu-id="a5a3a-115">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="a5a3a-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="a5a3a-116">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="a5a3a-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="a5a3a-117">Używanie delegata AsyncCallback do kończenia operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="a5a3a-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
