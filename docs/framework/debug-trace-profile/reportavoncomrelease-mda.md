---
title: reportAvOnComRelease MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
ms.openlocfilehash: fca6b209e6432678a264f10762adb3871e3596ce
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217222"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="5fa85-102">reportAvOnComRelease MDA</span><span class="sxs-lookup"><span data-stu-id="5fa85-102">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="5fa85-103">Asystent debugowania zarządzanego `reportAvOnComRelease` (MDA) jest uaktywniany, gdy wyjątki są zgłaszane z powodu błędów w odniesieniu do odwołań użytkownika podczas wykonywania międzyoperacyjności modelu COM i używania metody <xref:System.Runtime.InteropServices.Marshal.Release%2A> lub <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> połączonej z nieprzetworzonymi wywołaniami COM.</span><span class="sxs-lookup"><span data-stu-id="5fa85-103">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5fa85-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="5fa85-104">Symptoms</span></span>  
 <span data-ttu-id="5fa85-105">Naruszenia dostępu i uszkodzenie pamięci.</span><span class="sxs-lookup"><span data-stu-id="5fa85-105">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5fa85-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="5fa85-106">Cause</span></span>  
 <span data-ttu-id="5fa85-107">Czasami wyjątek jest zgłaszany z powodu błędów zliczania odwołań użytkownika podczas wykonywania międzyoperacyjności modelu COM i używania metody <xref:System.Runtime.InteropServices.Marshal.Release%2A> lub <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> połączonej z nieprzetworzonymi wywołaniami COM.</span><span class="sxs-lookup"><span data-stu-id="5fa85-107">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="5fa85-108">Zwykle ten wyjątek jest odrzucany, ponieważ nie spowoduje to naruszenia zasad dostępu w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="5fa85-108">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="5fa85-109">Po włączeniu tego asystenta takie wyjątki mogą być wykrywane i raportowane zamiast po prostu odrzucone.</span><span class="sxs-lookup"><span data-stu-id="5fa85-109">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5fa85-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="5fa85-110">Resolution</span></span>  
 <span data-ttu-id="5fa85-111">Zbadaj kod zliczania odwołań i Wyszukaj błędy, a także Zbadaj natywnych klientów obiektu, aby uzyskać odwołania do błędów.</span><span class="sxs-lookup"><span data-stu-id="5fa85-111">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5fa85-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="5fa85-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="5fa85-113">Dostępne są dwa tryby.</span><span class="sxs-lookup"><span data-stu-id="5fa85-113">Two modes are available.</span></span> <span data-ttu-id="5fa85-114">Jeśli atrybut `allowAv` jest `true`, asystent uniemożliwia odrzucanie naruszenia zasad dostępu przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="5fa85-114">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="5fa85-115">Jeśli `allowAv` jest `false`, co jest ustawieniem domyślnym, środowisko uruchomieniowe odrzuca naruszenie zasad dostępu, ale użytkownik zgłasza komunikat ostrzegawczy informujący o tym, że wyjątek został zgłoszony i odrzucony.</span><span class="sxs-lookup"><span data-stu-id="5fa85-115">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5fa85-116">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="5fa85-116">Output</span></span>  
 <span data-ttu-id="5fa85-117">Jeśli to możliwe, dane wyjściowe zawierają oryginalną tablicę sieciową wskaźnika interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="5fa85-117">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="5fa85-118">W przeciwnym razie zostanie wyświetlony komunikat informacyjny.</span><span class="sxs-lookup"><span data-stu-id="5fa85-118">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5fa85-119">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5fa85-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fa85-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5fa85-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="5fa85-121">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="5fa85-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5fa85-122">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="5fa85-122">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
