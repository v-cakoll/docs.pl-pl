---
title: reportAvOnComRelease MDA
description: Zapoznaj się z programem reportAvOnComRelease Managed Debug Assistant (MDA), który może być aktywowany z powodu naruszeń dostępu i uszkodzenia pamięci w programie .NET.
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
ms.openlocfilehash: f9ba343060cb4d16de5909a5b619353546aca8ca
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803613"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="42643-103">reportAvOnComRelease MDA</span><span class="sxs-lookup"><span data-stu-id="42643-103">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="42643-104">`reportAvOnComRelease`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy wyjątki są zgłaszane z powodu błędów zliczania odwołań do użytkownika podczas wykonywania międzyoperacyjności modelu COM i używania <xref:System.Runtime.InteropServices.Marshal.Release%2A> metody lub w <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> połączeniu z nieprzetworzonymi wywołaniami com.</span><span class="sxs-lookup"><span data-stu-id="42643-104">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="42643-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="42643-105">Symptoms</span></span>  
 <span data-ttu-id="42643-106">Naruszenia dostępu i uszkodzenie pamięci.</span><span class="sxs-lookup"><span data-stu-id="42643-106">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="42643-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="42643-107">Cause</span></span>  
 <span data-ttu-id="42643-108">Czasami wyjątek jest zgłaszany z powodu błędów zliczania odwołań użytkownika podczas wykonywania międzyoperacyjności modelu COM i używania <xref:System.Runtime.InteropServices.Marshal.Release%2A> metody lub w <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> połączeniu z nieprzetworzonymi wywołaniami com.</span><span class="sxs-lookup"><span data-stu-id="42643-108">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="42643-109">Zwykle ten wyjątek jest odrzucany, ponieważ nie spowoduje to naruszenia zasad dostępu w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="42643-109">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="42643-110">Po włączeniu tego asystenta takie wyjątki mogą być wykrywane i raportowane zamiast po prostu odrzucone.</span><span class="sxs-lookup"><span data-stu-id="42643-110">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="42643-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="42643-111">Resolution</span></span>  
 <span data-ttu-id="42643-112">Zbadaj kod zliczania odwołań i Wyszukaj błędy, a także Zbadaj natywnych klientów obiektu, aby uzyskać odwołania do błędów.</span><span class="sxs-lookup"><span data-stu-id="42643-112">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="42643-113">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="42643-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="42643-114">Dostępne są dwa tryby.</span><span class="sxs-lookup"><span data-stu-id="42643-114">Two modes are available.</span></span> <span data-ttu-id="42643-115">Jeśli `allowAv` atrybut ma wartość `true` , asystent uniemożliwia odrzucanie naruszenia zasad dostępu przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="42643-115">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="42643-116">Jeśli `allowAv` jest to `false` ustawienie domyślne, środowisko uruchomieniowe odrzuca naruszenie zasad dostępu, ale komunikat ostrzegawczy jest raportowany użytkownikowi, aby wskazać, że wyjątek został zgłoszony i odrzucony.</span><span class="sxs-lookup"><span data-stu-id="42643-116">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="42643-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="42643-117">Output</span></span>  
 <span data-ttu-id="42643-118">Jeśli to możliwe, dane wyjściowe zawierają oryginalną tablicę sieciową wskaźnika interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="42643-118">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="42643-119">W przeciwnym razie zostanie wyświetlony komunikat informacyjny.</span><span class="sxs-lookup"><span data-stu-id="42643-119">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="42643-120">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="42643-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="42643-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42643-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="42643-122">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="42643-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="42643-123">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="42643-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
