---
title: Sondowanie stanu operacji asynchronicznych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d380e369d9620fc0fc87a2c443be318083174882
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036265"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="21230-102">Sondowanie stanu operacji asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="21230-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="21230-103">Aplikacji, które mogą wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej nie powinny blokować oczekiwanie, aż do zakończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="21230-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="21230-104">Do kontynuowania wykonywania instrukcji podczas oczekiwania na zakończenie operacji asynchronicznej, użyj jednej z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="21230-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="21230-105">Użyj <xref:System.IAsyncResult.IsCompleted%2A> właściwość <xref:System.IAsyncResult> zwrócony przez operację asynchroniczną \**rozpocząć \*\*\* OperationName* metodę pozwala ustalić, czy operacja została ukończona.</span><span class="sxs-lookup"><span data-stu-id="21230-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's \**Begin\*\*\*OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="21230-106">To podejście jest znany jako sondowania i została przedstawiona w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="21230-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="21230-107">Użyj <xref:System.AsyncCallback> delegata do przetwarzania wyników operacji asynchronicznych w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="21230-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="21230-108">Aby uzyskać przykład demonstrujący takie podejście, zobacz [używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="21230-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21230-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="21230-109">Example</span></span>  
 <span data-ttu-id="21230-110">Poniższy przykład kodu demonstruje, za pomocą metod asynchronicznych we <xref:System.Net.Dns> klasy do pobrania informacji System nazw domen dla komputera określonego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="21230-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="21230-111">W tym przykładzie rozpoczyna operację asynchroniczną, a następnie drukuje kropki (".") w konsoli aż do zakończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="21230-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="21230-112">Należy pamiętać, że **null** (**nic** w języku Visual Basic) jest przekazywana <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> i <xref:System.Object> parametry ponieważ tych argumentów nie są wymagane w przypadku korzystania z tej metody.</span><span class="sxs-lookup"><span data-stu-id="21230-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="21230-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21230-113">See also</span></span>

- [<span data-ttu-id="21230-114">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="21230-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [<span data-ttu-id="21230-115">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="21230-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
