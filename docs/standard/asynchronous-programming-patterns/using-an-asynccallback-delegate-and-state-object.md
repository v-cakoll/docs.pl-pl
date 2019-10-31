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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094604"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="a3902-102">Używanie delegata AsyncCallback i obiektu stanu</span><span class="sxs-lookup"><span data-stu-id="a3902-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="a3902-103">W przypadku użycia delegata <xref:System.AsyncCallback> do przetwarzania wyników operacji asynchronicznej w osobnym wątku, można użyć obiektu stanu do przekazywania informacji między wywołaniami zwrotnymi i pobrania końcowego wyniku.</span><span class="sxs-lookup"><span data-stu-id="a3902-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="a3902-104">W tym temacie pokazano, jak to zrobić, rozszerzając przykład przy [użyciu delegata AsyncCallback w celu zakończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="a3902-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3902-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3902-105">Example</span></span>  
 <span data-ttu-id="a3902-106">Poniższy przykład kodu demonstruje użycie metod asynchronicznych w klasie <xref:System.Net.Dns> do pobierania informacji o systemie nazw domen (DNS) dla komputerów określonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a3902-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="a3902-107">Ten przykład definiuje i używa klasy `HostRequest` do przechowywania informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="a3902-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="a3902-108">Tworzony jest obiekt `HostRequest` dla każdej nazwy komputera wprowadzonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a3902-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="a3902-109">Ten obiekt jest przesyłany do metody <xref:System.Net.Dns.BeginGetHostByName%2A>.</span><span class="sxs-lookup"><span data-stu-id="a3902-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="a3902-110">Metoda `ProcessDnsInformation` jest wywoływana za każdym razem, gdy żądanie zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="a3902-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="a3902-111">Obiekt `HostRequest` jest pobierany przy użyciu właściwości <xref:System.IAsyncResult.AsyncState%2A>.</span><span class="sxs-lookup"><span data-stu-id="a3902-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="a3902-112">Metoda `ProcessDnsInformation` używa obiektu `HostRequest` do przechowywania <xref:System.Net.IPHostEntry> zwrócone przez żądanie lub <xref:System.Net.Sockets.SocketException> zgłoszone przez żądanie.</span><span class="sxs-lookup"><span data-stu-id="a3902-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="a3902-113">Po zakończeniu wszystkich żądań aplikacja iteruje `HostRequest` obiektów i wyświetla informacje DNS lub <xref:System.Net.Sockets.SocketException> komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="a3902-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a3902-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3902-114">See also</span></span>

- [<span data-ttu-id="a3902-115">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="a3902-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="a3902-116">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="a3902-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="a3902-117">Używanie delegata AsyncCallback do kończenia operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="a3902-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
