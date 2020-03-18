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
ms.openlocfilehash: c7bd0a7606b5f93289cf39d33794457265e7e453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73094604"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="fecd9-102">Używanie delegata AsyncCallback i obiektu stanu</span><span class="sxs-lookup"><span data-stu-id="fecd9-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="fecd9-103">Korzystając z <xref:System.AsyncCallback> pełnomocnika do przetwarzania wyników operacji asynchronicznej w oddzielnym wątku, można użyć obiektu stanu do przekazywania informacji między wywołaniami zwrotu i pobrać wynik końcowy.</span><span class="sxs-lookup"><span data-stu-id="fecd9-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="fecd9-104">W tym temacie przedstawiono tę praktykę, rozszerzając przykład w [using asyncCallback delegate do zakończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="fecd9-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fecd9-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="fecd9-105">Example</span></span>  
 <span data-ttu-id="fecd9-106">Poniższy przykład kodu pokazuje przy użyciu metod asynchronicznych w <xref:System.Net.Dns> klasie do pobierania informacji dns (Domain Name System) dla komputerów określonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fecd9-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="fecd9-107">W tym przykładzie definiuje `HostRequest` i używa klasy do przechowywania informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="fecd9-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="fecd9-108">Obiekt `HostRequest` zostanie utworzony dla każdej nazwy komputera wprowadzonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fecd9-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="fecd9-109">Ten obiekt jest <xref:System.Net.Dns.BeginGetHostByName%2A> przekazywany do metody.</span><span class="sxs-lookup"><span data-stu-id="fecd9-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="fecd9-110">Metoda `ProcessDnsInformation` jest wywoływana za każdym razem, gdy żądanie zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="fecd9-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="fecd9-111">Obiekt `HostRequest` jest pobierany <xref:System.IAsyncResult.AsyncState%2A> przy użyciu właściwości.</span><span class="sxs-lookup"><span data-stu-id="fecd9-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="fecd9-112">Metoda `ProcessDnsInformation` używa `HostRequest` obiektu do <xref:System.Net.IPHostEntry> przechowywania zwróconych przez <xref:System.Net.Sockets.SocketException> żądanie lub thrown przez żądanie.</span><span class="sxs-lookup"><span data-stu-id="fecd9-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="fecd9-113">Po zakończeniu wszystkich żądań aplikacja iteruje `HostRequest` obiekty i wyświetla <xref:System.Net.Sockets.SocketException> informacje DNS lub komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="fecd9-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="fecd9-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fecd9-114">See also</span></span>

- [<span data-ttu-id="fecd9-115">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="fecd9-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="fecd9-116">Asynchroniczny wzorzec oparty na zdarzeniach — przegląd</span><span class="sxs-lookup"><span data-stu-id="fecd9-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="fecd9-117">Używanie delegata AsyncCallback do kończenia operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="fecd9-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
