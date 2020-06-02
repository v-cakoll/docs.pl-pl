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
ms.openlocfilehash: e52ed550510253aba9401931c0f612211c7d1bf5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276429"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="5afab-102">Używanie delegata AsyncCallback i obiektu stanu</span><span class="sxs-lookup"><span data-stu-id="5afab-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="5afab-103">Gdy obiekt <xref:System.AsyncCallback> delegowany jest używany do przetwarzania wyników operacji asynchronicznej w osobnym wątku, można użyć obiektu stanu do przekazywania informacji między wywołaniami zwrotnymi i pobrania końcowego wyniku.</span><span class="sxs-lookup"><span data-stu-id="5afab-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="5afab-104">W tym temacie pokazano, jak to zrobić, rozszerzając przykład przy [użyciu delegata AsyncCallback w celu zakończenia operacji asynchronicznej](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="5afab-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5afab-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="5afab-105">Example</span></span>  
 <span data-ttu-id="5afab-106">Poniższy przykład kodu demonstruje użycie metod asynchronicznych w <xref:System.Net.Dns> klasie w celu pobrania informacji o systemie nazw domen (DNS) dla komputerów określonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5afab-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="5afab-107">Ten przykład definiuje i używa `HostRequest` klasy do przechowywania informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="5afab-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="5afab-108">`HostRequest`Tworzony jest obiekt dla każdej nazwy komputera wprowadzonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5afab-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="5afab-109">Ten obiekt jest przesyłany do <xref:System.Net.Dns.BeginGetHostByName%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5afab-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="5afab-110">`ProcessDnsInformation`Metoda jest wywoływana za każdym razem, gdy żądanie zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="5afab-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="5afab-111">`HostRequest`Obiekt zostanie pobrany przy użyciu <xref:System.IAsyncResult.AsyncState%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5afab-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="5afab-112">`ProcessDnsInformation`Metoda używa `HostRequest` obiektu do przechowywania <xref:System.Net.IPHostEntry> zwracanych przez żądanie lub <xref:System.Net.Sockets.SocketException> zgłoszone przez żądanie.</span><span class="sxs-lookup"><span data-stu-id="5afab-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="5afab-113">Po zakończeniu wszystkich żądań aplikacja wykonuje iterację `HostRequest` obiektów i wyświetla informacje DNS lub <xref:System.Net.Sockets.SocketException> komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="5afab-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="5afab-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5afab-114">See also</span></span>

- [<span data-ttu-id="5afab-115">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="5afab-115">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="5afab-116">Asynchroniczny wzorzec oparty na zdarzeniach — przegląd</span><span class="sxs-lookup"><span data-stu-id="5afab-116">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="5afab-117">Używanie delegata AsyncCallback do kończenia operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="5afab-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
