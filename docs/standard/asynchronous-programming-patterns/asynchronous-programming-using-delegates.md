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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121746"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="92c4b-102">Programowanie asynchroniczne przy użyciu delegatów</span><span class="sxs-lookup"><span data-stu-id="92c4b-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="92c4b-103">Delegaty umożliwiają wywoływanie metody synchronicznej w sposób asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="92c4b-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="92c4b-104">W przypadku wywołania delegata synchronicznie Metoda `Invoke` wywołuje metodę docelową bezpośrednio w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="92c4b-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="92c4b-105">Jeśli metoda `BeginInvoke` jest wywoływana, środowisko uruchomieniowe języka wspólnego (CLR) kolejkuje żądanie i natychmiast wraca do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="92c4b-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="92c4b-106">Metoda docelowa jest wywoływana asynchronicznie w wątku z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="92c4b-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="92c4b-107">Oryginalny wątek, który przesłał żądanie, jest bezpłatny, aby kontynuować wykonywanie równolegle z metodą docelową.</span><span class="sxs-lookup"><span data-stu-id="92c4b-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="92c4b-108">Jeśli metoda wywołania zwrotnego została określona w wywołaniu metody `BeginInvoke`, metoda wywołania zwrotnego jest wywoływana, gdy metoda docelowa zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="92c4b-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="92c4b-109">W metodzie wywołania zwrotnego Metoda `EndInvoke` uzyskuje wartość zwracaną oraz wszystkie parametry wejściowe/wyjściowe lub wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="92c4b-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="92c4b-110">Jeśli podczas wywoływania `BeginInvoke`nie zostanie określona metoda wywołania zwrotnego, `EndInvoke` można wywołać z wątku, który wywołał `BeginInvoke`.</span><span class="sxs-lookup"><span data-stu-id="92c4b-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="92c4b-111">Kompilatory powinny emitować klasy delegatów z metodami `Invoke`, `BeginInvoke`i `EndInvoke` przy użyciu podpisu delegata określonego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="92c4b-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="92c4b-112">Metody `BeginInvoke` i `EndInvoke` powinny być oznaczone jako natywne.</span><span class="sxs-lookup"><span data-stu-id="92c4b-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="92c4b-113">Ponieważ te metody są oznaczone jako natywne, środowisko CLR automatycznie udostępnia implementację w czasie ładowania klasy.</span><span class="sxs-lookup"><span data-stu-id="92c4b-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="92c4b-114">Moduł ładujący gwarantuje, że nie są one zastępowane.</span><span class="sxs-lookup"><span data-stu-id="92c4b-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92c4b-115">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="92c4b-115">In This Section</span></span>  
 [<span data-ttu-id="92c4b-116">Wywoływanie metod synchronicznych w sposób asynchroniczny</span><span class="sxs-lookup"><span data-stu-id="92c4b-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="92c4b-117">W tym artykule omówiono użycie delegatów do wykonywania wywołań asynchronicznych metod zwykłych i przedstawiono proste przykłady kodu, które pokazują cztery sposoby oczekiwania na zwrócenie wywołania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="92c4b-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="92c4b-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="92c4b-118">Related Sections</span></span>  
 [<span data-ttu-id="92c4b-119">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="92c4b-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="92c4b-120">Opisuje programowanie asynchroniczne przy użyciu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="92c4b-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c4b-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92c4b-121">See also</span></span>

- <xref:System.Delegate>
