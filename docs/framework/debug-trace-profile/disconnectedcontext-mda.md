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
ms.openlocfilehash: cb42c04df6e02ff43421b7af6bf2d51b53aa3e69
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181983"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="efa38-102">disconnectedContext MDA</span><span class="sxs-lookup"><span data-stu-id="efa38-102">disconnectedContext MDA</span></span>
<span data-ttu-id="efa38-103">`disconnectedContext` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy środowisko CLR podejmuje próbę przejścia do odłączonego apartamentu lub kontekstu podczas obsługi żądanie dotyczące obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="efa38-103">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="efa38-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="efa38-104">Symptoms</span></span>  
 <span data-ttu-id="efa38-105">Wywołania na [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) są dostarczane do podstawowego składnika modelu COM w bieżącym apartamentu lub kontekstu, zamiast jednego, w którym istnieją.</span><span class="sxs-lookup"><span data-stu-id="efa38-105">Calls made on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="efa38-106">Może to spowodować uszkodzenie i lub utraty danych, jeśli składnik COM nie jest wielowątkowych, tak jak w przypadku składniki apartamentem jednowątkowym (przedziale STA).</span><span class="sxs-lookup"><span data-stu-id="efa38-106">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="efa38-107">Alternatywnie, jeśli RCW jest serwer proxy, wywołanie może spowodować zgłaszanie z <xref:System.Runtime.InteropServices.COMException> z HRESULT RPC_E_WRONG_THREAD.</span><span class="sxs-lookup"><span data-stu-id="efa38-107">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="efa38-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="efa38-108">Cause</span></span>  
 <span data-ttu-id="efa38-109">OLE apartamentu lub kontekstu została zamknięta podczas prób środowiska CLR, do którego nastąpi przejście do niej.</span><span class="sxs-lookup"><span data-stu-id="efa38-109">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="efa38-110">Jest to najczęściej spowodowane apartamentach STA, który jest zamykana przed udostępnieniem wszystkich składników COM należące do typu apartment zostały całkowicie, to może wystąpić w wyniku jawnym wywołaniem z kodu użytkownika na RCW lub w przypadku, gdy środowisko CLR, sama jest manipulowanie składnika COM , na przykład po środowisko CLR udostępnia składnika COM po skojarzone RCW bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="efa38-110">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="efa38-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="efa38-111">Resolution</span></span>  
 <span data-ttu-id="efa38-112">Aby uniknąć tego problemu, sprawdź, czy wątek, który jest właścicielem STA skończył się, zanim wszystkie obiekty, które znajdują się w apartamentu aplikacji zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="efa38-112">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="efa38-113">To samo dotyczy kontekstów; Upewnij się, że kontekstach nie są zamykane, zanim aplikacja jest całkowicie zakończyło się z składników modelu COM, znajdujące się w ramach kontekstu.</span><span class="sxs-lookup"><span data-stu-id="efa38-113">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="efa38-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="efa38-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="efa38-115">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="efa38-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="efa38-116">Informuje jedynie dane o odłączony kontekst.</span><span class="sxs-lookup"><span data-stu-id="efa38-116">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="efa38-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="efa38-117">Output</span></span>  
 <span data-ttu-id="efa38-118">Raporty kontekstu plik cookie odłączonego apartamentu lub kontekstu.</span><span class="sxs-lookup"><span data-stu-id="efa38-118">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="efa38-119">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="efa38-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="efa38-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efa38-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="efa38-121">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="efa38-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="efa38-122">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="efa38-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
