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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce77e57eb049c031ed506e8812fff59ba97a978e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950862"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="946a1-102">Programowanie asynchroniczne przy użyciu delegatów</span><span class="sxs-lookup"><span data-stu-id="946a1-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="946a1-103">Delegaty umożliwiają wywoływanie metody synchronicznej w sposób asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="946a1-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="946a1-104">W `Invoke` przypadku wywołania delegata synchronicznie metoda wywołuje metodę docelową bezpośrednio w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="946a1-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="946a1-105">`BeginInvoke` Jeśli metoda jest wywoływana, środowisko uruchomieniowe języka wspólnego (CLR) kolejkuje żądanie i natychmiast wraca do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="946a1-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="946a1-106">Metoda docelowa jest wywoływana asynchronicznie w wątku z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="946a1-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="946a1-107">Oryginalny wątek, który przesłał żądanie, jest bezpłatny, aby kontynuować wykonywanie równolegle z metodą docelową.</span><span class="sxs-lookup"><span data-stu-id="946a1-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="946a1-108">Jeśli metoda wywołania zwrotnego została określona w wywołaniu `BeginInvoke` metody, metoda wywołania zwrotnego jest wywoływana, gdy metoda docelowa zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="946a1-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="946a1-109">W metodzie `EndInvoke` wywołania zwrotnego metoda uzyskuje wartość zwracaną oraz wszystkie parametry wejściowe/wyjściowe lub wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="946a1-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="946a1-110">Jeśli metoda wywołania zwrotnego nie zostanie określona `BeginInvoke`podczas `EndInvoke` wywoływania, można wywołać z wątku, który `BeginInvoke`wywołał.</span><span class="sxs-lookup"><span data-stu-id="946a1-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="946a1-111">Kompilatory powinny emitować klasy delegatów `Invoke`z `BeginInvoke`metodami `EndInvoke` , i przy użyciu podpisu delegata określonego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="946a1-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="946a1-112">Metody `BeginInvoke` i`EndInvoke` powinny być dekoracyjne.</span><span class="sxs-lookup"><span data-stu-id="946a1-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="946a1-113">Ponieważ te metody są oznaczone jako natywne, środowisko CLR automatycznie udostępnia implementację w czasie ładowania klasy.</span><span class="sxs-lookup"><span data-stu-id="946a1-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="946a1-114">Moduł ładujący gwarantuje, że nie są one zastępowane.</span><span class="sxs-lookup"><span data-stu-id="946a1-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="946a1-115">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="946a1-115">In This Section</span></span>  
 [<span data-ttu-id="946a1-116">Wywoływanie metod synchronicznych w sposób asynchroniczny</span><span class="sxs-lookup"><span data-stu-id="946a1-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="946a1-117">W tym artykule omówiono użycie delegatów do wykonywania wywołań asynchronicznych metod zwykłych i przedstawiono proste przykłady kodu, które pokazują cztery sposoby oczekiwania na zwrócenie wywołania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="946a1-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="946a1-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="946a1-118">Related Sections</span></span>  
 [<span data-ttu-id="946a1-119">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="946a1-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="946a1-120">Opisuje programowanie asynchroniczne przy użyciu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="946a1-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="946a1-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="946a1-121">See also</span></span>

- <xref:System.Delegate>
