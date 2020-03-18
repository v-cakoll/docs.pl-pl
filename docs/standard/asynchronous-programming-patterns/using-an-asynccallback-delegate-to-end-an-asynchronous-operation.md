---
title: Używanie delegata AsyncCallback do kończenia operacji asynchronicznej
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: c3cac2db57a24bf6a0f5640e4ad8101686e6c3e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130923"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="27cbb-102">Używanie delegata AsyncCallback do kończenia operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="27cbb-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="27cbb-103">Aplikacje, które mogą wykonywać inne prace podczas oczekiwania na wyniki operacji asynchronicznej, nie powinny blokować oczekiwania, aż operacja zostanie ukończona.</span><span class="sxs-lookup"><span data-stu-id="27cbb-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="27cbb-104">Użyj jednej z następujących opcji, aby kontynuować wykonywanie instrukcji podczas oczekiwania na zakończenie operacji asynchronicznej:</span><span class="sxs-lookup"><span data-stu-id="27cbb-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="27cbb-105">Pełnomocnika <xref:System.AsyncCallback> do przetwarzania wyników operacji asynchronicznej w osobnym wątku.</span><span class="sxs-lookup"><span data-stu-id="27cbb-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="27cbb-106">Takie podejście przedstawiono w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="27cbb-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="27cbb-107">Użyj <xref:System.IAsyncResult.IsCompleted%2A> właściwości zwróconej <xref:System.IAsyncResult> przez operację asynchroniczną **Begin**_OperationName_ metody, aby ustalić, czy operacja została ukończona.</span><span class="sxs-lookup"><span data-stu-id="27cbb-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="27cbb-108">Na przykład, który demonstruje to podejście, zobacz [Sondowanie stanu operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="27cbb-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27cbb-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="27cbb-109">Example</span></span>  
 <span data-ttu-id="27cbb-110">Poniższy przykład kodu pokazuje przy użyciu metod asynchronicznych w <xref:System.Net.Dns> klasie do pobierania informacji dns (Domain Name System) dla komputerów określonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="27cbb-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="27cbb-111">W tym <xref:System.AsyncCallback> przykładzie tworzy delegata, który odwołuje się do `ProcessDnsInformation` metody.</span><span class="sxs-lookup"><span data-stu-id="27cbb-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="27cbb-112">Ta metoda jest wywoływana raz dla każdego asynchronicznego żądania informacji DNS.</span><span class="sxs-lookup"><span data-stu-id="27cbb-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="27cbb-113">Należy zauważyć, że host określony przez <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> użytkownika jest przekazywany do parametru.</span><span class="sxs-lookup"><span data-stu-id="27cbb-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="27cbb-114">Na przykład, który demonstruje definiowanie i używanie bardziej złożonego obiektu stanu, zobacz [Korzystanie z delegata asynurowania i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span><span class="sxs-lookup"><span data-stu-id="27cbb-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="27cbb-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27cbb-115">See also</span></span>

- [<span data-ttu-id="27cbb-116">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="27cbb-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="27cbb-117">Asynchroniczny wzorzec oparty na zdarzeniach — przegląd</span><span class="sxs-lookup"><span data-stu-id="27cbb-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="27cbb-118">Wywoływanie metod asynchronicznych za pomocą interfejsu IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="27cbb-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [<span data-ttu-id="27cbb-119">Używanie delegata AsyncCallback i obiektu stanu</span><span class="sxs-lookup"><span data-stu-id="27cbb-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
