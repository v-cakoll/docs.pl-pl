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
ms.openlocfilehash: 41c9793900c3e7accd5463a19de10d1cb81afd59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503836"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="f4994-102">Programowanie asynchroniczne przy użyciu delegatów</span><span class="sxs-lookup"><span data-stu-id="f4994-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="f4994-103">Delegaty umożliwiają wywołanie metody synchronicznej w sposób asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="f4994-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="f4994-104">Podczas wywoływania delegata synchronicznie, `Invoke` metoda wywołuje metodę docelową bezpośrednio w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="f4994-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="f4994-105">Jeśli `BeginInvoke` metoda jest wywoływana, środowisko uruchomieniowe języka wspólnego (CLR) kolejkuje żądanie i natychmiast zwraca do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f4994-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="f4994-106">Metoda docelowy jest wywoływana asynchronicznie w wątku z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="f4994-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="f4994-107">Oryginalnego wątku, który przesłał żądanie, jest bezpłatne kontynuować wykonywanie równoległe przy użyciu metody docelowej.</span><span class="sxs-lookup"><span data-stu-id="f4994-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="f4994-108">Jeśli metoda wywołania zwrotnego zostały określone w wywołaniu `BeginInvoke` , metody wywołania zwrotnego wywoływana jest metoda po zakończeniu metody docelowej.</span><span class="sxs-lookup"><span data-stu-id="f4994-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="f4994-109">W przypadku metody wywołania zwrotnego `EndInvoke` metoda uzyskuje wartość zwracaną oraz wszelkie parametry wejścia/wyjścia lub tylko do danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="f4994-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="f4994-110">Jeśli zostanie określona żadna metoda wywołania zwrotnego, podczas wywoływania `BeginInvoke`, `EndInvoke` może być wywoływana z wątku, który wywołał `BeginInvoke`.</span><span class="sxs-lookup"><span data-stu-id="f4994-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f4994-111">Kompilatory, powinny wysyłać klasy obiektów delegowanych z `Invoke`, `BeginInvoke`, i `EndInvoke` metod za pomocą podpis delegata, określone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f4994-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="f4994-112">`BeginInvoke` i `EndInvoke` metody powinny być dekorowane jako natywny.</span><span class="sxs-lookup"><span data-stu-id="f4994-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="f4994-113">Ponieważ te metody są oznaczone jako natywnego, środowisko CLR oferuje automatycznie implementacji w czasie ładowania klasy.</span><span class="sxs-lookup"><span data-stu-id="f4994-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="f4994-114">Moduł ładujący gwarantuje, że nie są zastępowane.</span><span class="sxs-lookup"><span data-stu-id="f4994-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4994-115">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f4994-115">In This Section</span></span>  
 [<span data-ttu-id="f4994-116">Wywoływanie metod synchronicznych w sposób asynchroniczny</span><span class="sxs-lookup"><span data-stu-id="f4994-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="f4994-117">W tym artykule omówiono Użyj obiektów delegowanych, wykonywanie wywołań asynchronicznych do zwykłych metod i zawiera przykłady prostego kodu, które przedstawiono cztery sposoby oczekiwania na wywołanie asynchroniczne do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="f4994-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f4994-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="f4994-118">Related Sections</span></span>  
 [<span data-ttu-id="f4994-119">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="f4994-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="f4994-120">W tym artykule opisano programowania asynchronicznego przy użyciu programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4994-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4994-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4994-121">See also</span></span>

- <xref:System.Delegate>
