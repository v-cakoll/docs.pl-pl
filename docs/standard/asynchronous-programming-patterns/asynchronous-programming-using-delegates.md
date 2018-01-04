---
title: "Programowanie asynchroniczne przy użyciu delegatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e84c004c8efc58c6d6ad55674470bec13fc0bab8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="67be5-102">Programowanie asynchroniczne przy użyciu delegatów</span><span class="sxs-lookup"><span data-stu-id="67be5-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="67be5-103">Obiekty delegowane umożliwiają wywołania metody synchroniczne w sposób asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="67be5-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="67be5-104">Gdy delegata należy wywołać synchronicznie, `Invoke` metoda wywołuje metodę docelowego bezpośrednio w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="67be5-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="67be5-105">Jeśli `BeginInvoke` metoda jest wywoływana, środowisko uruchomieniowe języka wspólnego (CLR) kolejkuje żądanie i natychmiast zwraca do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="67be5-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="67be5-106">Metoda docelowy jest wywoływana asynchronicznie w wątku z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="67be5-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="67be5-107">Oryginalnego wątku przesłane żądanie, będzie mógł kontynuować równolegle z metodą docelową.</span><span class="sxs-lookup"><span data-stu-id="67be5-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="67be5-108">Jeśli metoda wywołania zwrotnego został określony w wywołaniu `BeginInvoke` , metody wywołania zwrotnego wywoływana jest metoda po zakończeniu metody docelowej.</span><span class="sxs-lookup"><span data-stu-id="67be5-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="67be5-109">W przypadku metody wywołania zwrotnego `EndInvoke` metoda uzyskuje wartość zwracaną i wszelkie parametry wejścia/wyjścia lub w trybie tylko do danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="67be5-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="67be5-110">Jeśli zostanie określona żadna metoda wywołania zwrotnego, podczas wywoływania metody `BeginInvoke`, `EndInvoke` można wywołać z wątku, który wywołuje `BeginInvoke`.</span><span class="sxs-lookup"><span data-stu-id="67be5-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="67be5-111">Kompilatory powinien Emituj klasy obiektów delegowanych z `Invoke`, `BeginInvoke`, i `EndInvoke` metody za pomocą podpisu delegata określone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="67be5-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="67be5-112">`BeginInvoke` i `EndInvoke` metody powinny być dekorowane jako natywne.</span><span class="sxs-lookup"><span data-stu-id="67be5-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="67be5-113">Ponieważ te metody są oznaczone jako natywną, CLR automatycznie udostępnia implementację w czasie ładowania klasy.</span><span class="sxs-lookup"><span data-stu-id="67be5-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="67be5-114">Moduł ładujący gwarantuje, że nie zostały zastąpione.</span><span class="sxs-lookup"><span data-stu-id="67be5-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="67be5-115">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="67be5-115">In This Section</span></span>  
 [<span data-ttu-id="67be5-116">Wywoływanie metod synchronicznych w sposób asynchroniczny</span><span class="sxs-lookup"><span data-stu-id="67be5-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="67be5-117">Omówiono korzystanie z obiektów delegowanych z wywołań asynchronicznych metod zwykłej i przykłady kodu, które przedstawiono cztery sposoby oczekiwania na wywołanie asynchroniczne do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="67be5-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="67be5-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="67be5-118">Related Sections</span></span>  
 [<span data-ttu-id="67be5-119">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="67be5-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="67be5-120">W tym artykule opisano programowanie asynchroniczne z programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67be5-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67be5-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67be5-121">See Also</span></span>  
 <xref:System.Delegate>
