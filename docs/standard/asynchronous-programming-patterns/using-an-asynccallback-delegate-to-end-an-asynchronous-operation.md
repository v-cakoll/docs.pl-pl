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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 856273c9592aa32feb3e8cc66c850cb34ad0812f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079139"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="fda62-102">Używanie delegata AsyncCallback do kończenia operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="fda62-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="fda62-103">Aplikacji, które mogą wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej nie powinny blokować oczekiwanie, aż do zakończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="fda62-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="fda62-104">Do kontynuowania wykonywania instrukcji podczas oczekiwania na zakończenie operacji asynchronicznej, użyj jednej z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="fda62-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="fda62-105">Użyj <xref:System.AsyncCallback> delegata do przetwarzania wyników operacji asynchronicznych w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="fda62-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="fda62-106">To podejście jest przedstawiona w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="fda62-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="fda62-107">Użyj <xref:System.IAsyncResult.IsCompleted%2A> właściwość <xref:System.IAsyncResult> zwrócony przez operację asynchroniczną \**rozpocząć \*\*\* OperationName* metodę pozwala ustalić, czy operacja została ukończona.</span><span class="sxs-lookup"><span data-stu-id="fda62-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's \**Begin\*\*\*OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="fda62-108">Aby uzyskać przykład demonstrujący takie podejście, zobacz [sondowanie stanu operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="fda62-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fda62-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="fda62-109">Example</span></span>  
 <span data-ttu-id="fda62-110">Poniższy przykład kodu demonstruje, za pomocą metod asynchronicznych we <xref:System.Net.Dns> klasy do pobrania informacji systemu nazw domen (DNS, Domain Name System) dla komputerów z określonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fda62-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="fda62-111">Ten przykład tworzy <xref:System.AsyncCallback> delegata, który odwołuje się do `ProcessDnsInformation` metody.</span><span class="sxs-lookup"><span data-stu-id="fda62-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="fda62-112">Ta metoda jest wywoływana jeden raz dla każdego żądania asynchronicznego, aby uzyskać informacje dotyczące systemu DNS.</span><span class="sxs-lookup"><span data-stu-id="fda62-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="fda62-113">Należy zauważyć, że host określonych przez użytkownika jest przekazywany do <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> parametru.</span><span class="sxs-lookup"><span data-stu-id="fda62-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="fda62-114">Na przykład demonstrujący definiowanie i korzystanie z bardziej złożonych obiekt stanu zobacz [używanie delegata AsyncCallback i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span><span class="sxs-lookup"><span data-stu-id="fda62-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="fda62-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fda62-115">See also</span></span>

- [<span data-ttu-id="fda62-116">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="fda62-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [<span data-ttu-id="fda62-117">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="fda62-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
- [<span data-ttu-id="fda62-118">Wywoływanie metod asynchronicznych za pomocą interfejsu IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="fda62-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
- [<span data-ttu-id="fda62-119">Używanie delegata AsyncCallback i obiektu stanu</span><span class="sxs-lookup"><span data-stu-id="fda62-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
