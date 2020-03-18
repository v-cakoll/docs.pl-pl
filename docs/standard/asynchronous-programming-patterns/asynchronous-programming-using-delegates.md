---
title: Programowanie asynchroniczne przy użyciu delegatów
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 4e17e6a96a12b705cf455d70add7e12a30f5fa90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121746"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="5a5c7-102">Programowanie asynchroniczne przy użyciu delegatów</span><span class="sxs-lookup"><span data-stu-id="5a5c7-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="5a5c7-103">Delegaci umożliwiają wywołanie metody synchronicznej w sposób asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="5a5c7-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="5a5c7-104">Podczas wywoływania delegata synchronicznie, `Invoke` metoda wywołuje metodę docelową bezpośrednio w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="5a5c7-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="5a5c7-105">Jeśli `BeginInvoke` metoda jest wywoływana, program runtime języka wspólnego (CLR) kolejki żądania i zwraca natychmiast do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5a5c7-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="5a5c7-106">Metoda docelowa jest wywoływana asynchronicznie w wątku z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="5a5c7-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="5a5c7-107">Oryginalny wątek, który przesłał żądanie, może kontynuować wykonywanie równolegle z metodą docelową.</span><span class="sxs-lookup"><span data-stu-id="5a5c7-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="5a5c7-108">Jeśli metoda wywołania wywołania został określony `BeginInvoke` w wywołaniu metody, metoda wywołania wywołania wywołania jest wywoływana po zakończeniu metody docelowej.</span><span class="sxs-lookup"><span data-stu-id="5a5c7-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="5a5c7-109">W metodzie wywołania `EndInvoke` zwrotnego metoda uzyskuje wartość zwracaną i wszelkie parametry wejścia/wyjścia lub tylko do wyjścia.</span><span class="sxs-lookup"><span data-stu-id="5a5c7-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="5a5c7-110">Jeśli podczas wywoływania nie określono `BeginInvoke` `EndInvoke` żadnej metody wywołania wywołania, można wywołać z wątku, który o nazwie `BeginInvoke`.</span><span class="sxs-lookup"><span data-stu-id="5a5c7-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5a5c7-111">Kompilatory powinny emitować `BeginInvoke`klasy `EndInvoke` delegata z `Invoke`, i metody przy użyciu podpisu delegata określonego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5a5c7-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="5a5c7-112">I `BeginInvoke` `EndInvoke` metody powinny być urządzone jako rodzime.</span><span class="sxs-lookup"><span data-stu-id="5a5c7-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="5a5c7-113">Ponieważ te metody są oznaczone jako macierzyste, CLR automatycznie zapewnia implementację w czasie ładowania klasy.</span><span class="sxs-lookup"><span data-stu-id="5a5c7-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="5a5c7-114">Moduł ładujący zapewnia, że nie są one zastępowane.</span><span class="sxs-lookup"><span data-stu-id="5a5c7-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a5c7-115">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5a5c7-115">In This Section</span></span>  
 [<span data-ttu-id="5a5c7-116">Wywołanie metod synchronicznych w sposób asynchroniczny</span><span class="sxs-lookup"><span data-stu-id="5a5c7-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="5a5c7-117">W tym artykule omówiono użycie delegatów do wywoływania asynchronicznego zwykłych metod i zawiera proste przykłady kodu, które pokazują cztery sposoby oczekiwania na asynchroniczne wywołanie do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="5a5c7-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5a5c7-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5a5c7-118">Related Sections</span></span>  
 [<span data-ttu-id="5a5c7-119">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="5a5c7-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="5a5c7-120">Opisuje programowanie asynchroniczne z .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5a5c7-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a5c7-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a5c7-121">See also</span></span>

- <xref:System.Delegate>
