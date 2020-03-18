---
title: Wywołanie metod asynchronicznych za pomocą interfejsu IAsyncResult
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 2a9ce8bc2d2edd09ef79c060b9bb173d4d054d02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121311"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="e8507-102">Wywołanie metod asynchronicznych za pomocą interfejsu IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="e8507-102">Calling Asynchronous Methods Using IAsyncResult</span></span>
<span data-ttu-id="e8507-103">Typy w .NET Framework i bibliotek klas innych firm może zapewnić metody, które umożliwiają aplikacji kontynuować wykonywanie podczas wykonywania operacji asynchronicznych w wątkach innych niż główny wątek aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e8507-103">Types in the .NET Framework and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="e8507-104">W poniższych sekcjach opisano i podano przykłady kodu, które demonstrują <xref:System.IAsyncResult> różne sposoby wywoływania metod asynchronicznych, które używają wzorca projektu.</span><span class="sxs-lookup"><span data-stu-id="e8507-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
- <span data-ttu-id="e8507-105">[Blokowanie wykonywania aplikacji przez zakończenie operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="e8507-105">[Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
- <span data-ttu-id="e8507-106">[Blokowanie wykonywania aplikacji za pomocą AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="e8507-106">[Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
- <span data-ttu-id="e8507-107">[Sondowanie stanu operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="e8507-107">[Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
- <span data-ttu-id="e8507-108">[Za pomocą delegata AsyncCallback do zakończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="e8507-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8507-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8507-109">See also</span></span>

- [<span data-ttu-id="e8507-110">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="e8507-110">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="e8507-111">Asynchroniczny wzorzec oparty na zdarzeniach — przegląd</span><span class="sxs-lookup"><span data-stu-id="e8507-111">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
