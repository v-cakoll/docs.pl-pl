---
title: disconnectedContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5232a01d877484591df63afc68f672327d4b9d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="188a2-102">disconnectedContext MDA</span><span class="sxs-lookup"><span data-stu-id="188a2-102">disconnectedContext MDA</span></span>
<span data-ttu-id="188a2-103">`disconnectedContext` Zarządzany Asystent debugowania (MDA) została aktywowana, podczas próby przejścia do odłączonego apartamentu lub kontekstu podczas obsługi żądania dotyczące obiektu COM środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="188a2-103">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="188a2-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="188a2-104">Symptoms</span></span>  
 <span data-ttu-id="188a2-105">Wywołania [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) (otoki RCW) są dostarczane do podstawowy składnik modelu COM w bieżącego apartamentu lub kontekstu zamiast takie istnieją.</span><span class="sxs-lookup"><span data-stu-id="188a2-105">Calls made on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="188a2-106">Może to spowodować uszkodzenie i lub utratę danych, jeśli składnik modelu COM nie jest wielowątkowe, tak jak w przypadku składników jednowątkowego apartamentu (STA).</span><span class="sxs-lookup"><span data-stu-id="188a2-106">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="188a2-107">Alternatywnie, jeśli Otoka RCW jest serwer proxy, wywołanie może spowodować przerzucane o <xref:System.Runtime.InteropServices.COMException> z HRESULT RPC_E_WRONG_THREAD.</span><span class="sxs-lookup"><span data-stu-id="188a2-107">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="188a2-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="188a2-108">Cause</span></span>  
 <span data-ttu-id="188a2-109">OLE apartamentu lub kontekstu została zamknięta podczas próby przejścia do niego środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="188a2-109">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="188a2-110">Najczęściej jest to spowodowane apartamentach STA, zamykana przed wszystkie składniki COM własnością apartamencie całkowicie zostały zwolnione, to może wystąpić w wyniku jawnym wywołaniem z kodu użytkownika otoki RCW lub gdy sam CLR jest manipulowanie składnika modelu COM , na przykład podczas CLR udostępnia składnika modelu COM, gdy skojarzona Otoka RCW została wyrzucona jako element bezużyteczny.</span><span class="sxs-lookup"><span data-stu-id="188a2-110">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="188a2-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="188a2-111">Resolution</span></span>  
 <span data-ttu-id="188a2-112">Aby uniknąć tego problemu, upewnij się, że wątek, który jest właścicielem STA nie kończy się przed wszystkie obiekty, które znajdują się w apartamencie aplikacji zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="188a2-112">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="188a2-113">To samo dotyczy kontekstów; Upewnij się, że kontekstach nie są zamknięte przed całkowicie zakończono z wszystkie składniki modelu COM, które na żywo w kontekście aplikacji.</span><span class="sxs-lookup"><span data-stu-id="188a2-113">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="188a2-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="188a2-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="188a2-115">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="188a2-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="188a2-116">Zwraca tylko dane o rozłączona kontekście.</span><span class="sxs-lookup"><span data-stu-id="188a2-116">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="188a2-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="188a2-117">Output</span></span>  
 <span data-ttu-id="188a2-118">Raporty cookie kontekstu odłączonego apartamentu lub kontekstu.</span><span class="sxs-lookup"><span data-stu-id="188a2-118">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="188a2-119">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="188a2-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="188a2-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="188a2-120">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="188a2-121">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="188a2-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="188a2-122">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="188a2-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
