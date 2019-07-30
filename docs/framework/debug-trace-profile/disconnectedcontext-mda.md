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
ms.openlocfilehash: 5d97ee808ef7d2a14902259c47227b787f0830fb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629377"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="ba53f-102">disconnectedContext MDA</span><span class="sxs-lookup"><span data-stu-id="ba53f-102">disconnectedContext MDA</span></span>
<span data-ttu-id="ba53f-103">Asystent `disconnectedContext` debugowania zarządzanego (MDA) jest uaktywniany, gdy środowisko CLR próbuje przejść do odłączonego apartamentu lub kontekstu podczas obsługi żądania dotyczącego obiektu com.</span><span class="sxs-lookup"><span data-stu-id="ba53f-103">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ba53f-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="ba53f-104">Symptoms</span></span>  
 <span data-ttu-id="ba53f-105">Wywołania wywoływanej [otoki środowiska uruchomieniowego](../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW) są dostarczane do źródłowego składnika COM w bieżącym elemencie Apartment lub Context, a nie na tym, w którym istnieją.</span><span class="sxs-lookup"><span data-stu-id="ba53f-105">Calls made on a [Runtime Callable Wrapper](../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="ba53f-106">Może to spowodować uszkodzenie lub utratę danych, jeśli składnik COM nie jest wielowątkowy, tak jak w przypadku składników jednowątkowego apartamentu (STA).</span><span class="sxs-lookup"><span data-stu-id="ba53f-106">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="ba53f-107">Alternatywnie, jeśli otoka jest samodzielnym serwerem proxy, wywołanie może spowodować wyrzucanie <xref:System.Runtime.InteropServices.COMException> z wynikami HRESULT RPC_E_WRONG_THREAD.</span><span class="sxs-lookup"><span data-stu-id="ba53f-107">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ba53f-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="ba53f-108">Cause</span></span>  
 <span data-ttu-id="ba53f-109">Obiekt OLE Apartment lub kontekst został zamknięty, gdy środowisko CLR podejmie próbę przejścia do niego.</span><span class="sxs-lookup"><span data-stu-id="ba53f-109">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="ba53f-110">Jest to najczęściej spowodowane tym, że STA apartamentach jest zamykany zanim wszystkie składniki COM będące własnością elementu Apartment zostały całkowicie wydane, może się to zdarzyć w wyniku jawnego wywołania kodu użytkownika na otoki RCW lub gdy samo środowisko CLR operuje na składniku COM. na przykład gdy środowisko CLR zwalnia składnik COM, gdy skojarzona Otoka RCW została odtworzona.</span><span class="sxs-lookup"><span data-stu-id="ba53f-110">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ba53f-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ba53f-111">Resolution</span></span>  
 <span data-ttu-id="ba53f-112">Aby uniknąć tego problemu, upewnij się, że wątek, który jest właścicielem STA, nie zakończy się przed zakończeniem działania aplikacji ze wszystkimi obiektami, które znajdują się w apartamentu.</span><span class="sxs-lookup"><span data-stu-id="ba53f-112">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="ba53f-113">To samo dotyczy kontekstów; Upewnij się, że konteksty nie są zamykane, zanim aplikacja zostanie całkowicie zakończona wszystkimi składnikami COM znajdującymi się wewnątrz tego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="ba53f-113">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ba53f-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ba53f-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="ba53f-115">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="ba53f-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="ba53f-116">Raport dotyczy tylko danych o rozłączonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="ba53f-116">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ba53f-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="ba53f-117">Output</span></span>  
 <span data-ttu-id="ba53f-118">Raportuje plik cookie kontekstu odłączonego apartamentu lub kontekstu.</span><span class="sxs-lookup"><span data-stu-id="ba53f-118">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ba53f-119">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ba53f-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba53f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba53f-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="ba53f-121">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="ba53f-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ba53f-122">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="ba53f-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
