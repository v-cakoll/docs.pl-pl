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
ms.openlocfilehash: 15d99ef6ef3ae089216e586fe873043fa03b0d7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="2fd4b-102">Programowanie asynchroniczne przy użyciu delegatów</span><span class="sxs-lookup"><span data-stu-id="2fd4b-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="2fd4b-103">Obiekty delegowane umożliwiają wywołania metody synchroniczne w sposób asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="2fd4b-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="2fd4b-104">Gdy delegata należy wywołać synchronicznie, `Invoke` metoda wywołuje metodę docelowego bezpośrednio w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="2fd4b-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="2fd4b-105">Jeśli `BeginInvoke` metoda jest wywoływana, środowisko uruchomieniowe języka wspólnego (CLR) kolejkuje żądanie i natychmiast zwraca do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2fd4b-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="2fd4b-106">Metoda docelowy jest wywoływana asynchronicznie w wątku z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="2fd4b-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="2fd4b-107">Oryginalnego wątku przesłane żądanie, będzie mógł kontynuować równolegle z metodą docelową.</span><span class="sxs-lookup"><span data-stu-id="2fd4b-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="2fd4b-108">Jeśli metoda wywołania zwrotnego został określony w wywołaniu `BeginInvoke` , metody wywołania zwrotnego wywoływana jest metoda po zakończeniu metody docelowej.</span><span class="sxs-lookup"><span data-stu-id="2fd4b-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="2fd4b-109">W przypadku metody wywołania zwrotnego `EndInvoke` metoda uzyskuje wartość zwracaną i wszelkie parametry wejścia/wyjścia lub w trybie tylko do danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="2fd4b-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="2fd4b-110">Jeśli zostanie określona żadna metoda wywołania zwrotnego, podczas wywoływania metody `BeginInvoke`, `EndInvoke` można wywołać z wątku, który wywołuje `BeginInvoke`.</span><span class="sxs-lookup"><span data-stu-id="2fd4b-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2fd4b-111">Kompilatory powinien Emituj klasy obiektów delegowanych z `Invoke`, `BeginInvoke`, i `EndInvoke` metody za pomocą podpisu delegata określone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2fd4b-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="2fd4b-112">`BeginInvoke` i `EndInvoke` metody powinny być dekorowane jako natywne.</span><span class="sxs-lookup"><span data-stu-id="2fd4b-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="2fd4b-113">Ponieważ te metody są oznaczone jako natywną, CLR automatycznie udostępnia implementację w czasie ładowania klasy.</span><span class="sxs-lookup"><span data-stu-id="2fd4b-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="2fd4b-114">Moduł ładujący gwarantuje, że nie zostały zastąpione.</span><span class="sxs-lookup"><span data-stu-id="2fd4b-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2fd4b-115">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2fd4b-115">In This Section</span></span>  
 [<span data-ttu-id="2fd4b-116">Wywoływanie metod synchronicznych w sposób asynchroniczny</span><span class="sxs-lookup"><span data-stu-id="2fd4b-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="2fd4b-117">Omówiono korzystanie z obiektów delegowanych z wywołań asynchronicznych metod zwykłej i przykłady kodu, które przedstawiono cztery sposoby oczekiwania na wywołanie asynchroniczne do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="2fd4b-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2fd4b-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2fd4b-118">Related Sections</span></span>  
 [<span data-ttu-id="2fd4b-119">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="2fd4b-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="2fd4b-120">W tym artykule opisano programowanie asynchroniczne z programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2fd4b-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fd4b-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fd4b-121">See Also</span></span>  
 <xref:System.Delegate>
