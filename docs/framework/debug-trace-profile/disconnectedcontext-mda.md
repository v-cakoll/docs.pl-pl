---
title: disconnectedContext MDA
description: Zapoznaj się z asystentem debugowania zarządzanego disconnectedContext w programie .NET, który jest wywoływany, gdy środowisko CLR podejmie próbę przejścia do odłączonego apartamentu lub kontekstu.
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
ms.openlocfilehash: 0b24aadefab7a7cb2a5294f25e674d188beec814
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416086"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="48f66-103">disconnectedContext MDA</span><span class="sxs-lookup"><span data-stu-id="48f66-103">disconnectedContext MDA</span></span>
<span data-ttu-id="48f66-104">`disconnectedContext`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy środowisko CLR próbuje przejść do odłączonego apartamentu lub kontekstu podczas obsługi żądania dotyczącego obiektu com.</span><span class="sxs-lookup"><span data-stu-id="48f66-104">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="48f66-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="48f66-105">Symptoms</span></span>  
 <span data-ttu-id="48f66-106">Wywołania wywoływanej [otoki środowiska uruchomieniowego](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) są dostarczane do źródłowego składnika COM w bieżącym elemencie Apartment lub Context, a nie na tym, w którym istnieją.</span><span class="sxs-lookup"><span data-stu-id="48f66-106">Calls made on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="48f66-107">Może to spowodować uszkodzenie lub utratę danych, jeśli składnik COM nie jest wielowątkowy, tak jak w przypadku składników jednowątkowego apartamentu (STA).</span><span class="sxs-lookup"><span data-stu-id="48f66-107">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="48f66-108">Alternatywnie, jeśli OTOKa jest samodzielnym serwerem proxy, wywołanie może spowodować wyrzucanie z wynikami <xref:System.Runtime.InteropServices.COMException> HRESULT RPC_E_WRONG_THREAD.</span><span class="sxs-lookup"><span data-stu-id="48f66-108">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="48f66-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="48f66-109">Cause</span></span>  
 <span data-ttu-id="48f66-110">Obiekt OLE Apartment lub kontekst został zamknięty, gdy środowisko CLR podejmie próbę przejścia do niego.</span><span class="sxs-lookup"><span data-stu-id="48f66-110">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="48f66-111">Jest to najczęściej spowodowane tym, że STA apartamentach jest zamykany przed całkowitym udostępnieniem wszystkich składników modelu COM należących do apartamentu. może się to zdarzyć w wyniku jawnego wywołania kodu użytkownika na otoki RCW lub gdy środowisko CLR operuje na składniku COM, na przykład gdy środowisko CLR zwalnia składnik COM, gdy skojarzona Otoka RCW została odtworzona.</span><span class="sxs-lookup"><span data-stu-id="48f66-111">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="48f66-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="48f66-112">Resolution</span></span>  
 <span data-ttu-id="48f66-113">Aby uniknąć tego problemu, upewnij się, że wątek, który jest właścicielem STA, nie zakończy się przed zakończeniem działania aplikacji ze wszystkimi obiektami, które znajdują się w apartamentu.</span><span class="sxs-lookup"><span data-stu-id="48f66-113">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="48f66-114">To samo dotyczy kontekstów; Upewnij się, że konteksty nie są zamykane, zanim aplikacja zostanie całkowicie zakończona wszystkimi składnikami COM znajdującymi się wewnątrz tego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="48f66-114">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="48f66-115">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="48f66-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="48f66-116">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="48f66-116">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="48f66-117">Raport dotyczy tylko danych o rozłączonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="48f66-117">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="48f66-118">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="48f66-118">Output</span></span>  
 <span data-ttu-id="48f66-119">Raportuje plik cookie kontekstu odłączonego apartamentu lub kontekstu.</span><span class="sxs-lookup"><span data-stu-id="48f66-119">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="48f66-120">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="48f66-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48f66-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48f66-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="48f66-122">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="48f66-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="48f66-123">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="48f66-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
