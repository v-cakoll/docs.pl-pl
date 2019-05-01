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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0ecb05dba70dc9c8aba7f04928fd0ab49c900c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61873954"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="918d9-102">reportAvOnComRelease MDA</span><span class="sxs-lookup"><span data-stu-id="918d9-102">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="918d9-103">`reportAvOnComRelease` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy wyjątki zostaną zgłoszone ze względu na użytkownika zliczanie błędów podczas wykonywania COM międzyoperacyjności i korzystać z funkcji <xref:System.Runtime.InteropServices.Marshal.Release%2A> lub <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metody w połączeniu z pierwotnych wywołania COM.</span><span class="sxs-lookup"><span data-stu-id="918d9-103">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="918d9-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="918d9-104">Symptoms</span></span>  
 <span data-ttu-id="918d9-105">Naruszenia zasad dostępu i uszkodzenie pamięci.</span><span class="sxs-lookup"><span data-stu-id="918d9-105">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="918d9-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="918d9-106">Cause</span></span>  
 <span data-ttu-id="918d9-107">Czasami wyjątek jest zgłaszany z powodu użytkownika zliczanie błędów podczas wykonywania COM międzyoperacyjności i korzystać z funkcji <xref:System.Runtime.InteropServices.Marshal.Release%2A> lub <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metody w połączeniu z pierwotnych wywołania COM.</span><span class="sxs-lookup"><span data-stu-id="918d9-107">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="918d9-108">Zazwyczaj ten wyjątek jest pomijany, ponieważ w przeciwnym razie mogłoby spowodować naruszenie zasad dostępu w środowisku CLR, wyłączania go.</span><span class="sxs-lookup"><span data-stu-id="918d9-108">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="918d9-109">Po włączeniu tego Asystenta wyjątków można wykryte i zgłaszane zamiast po prostu zostanie odrzucony.</span><span class="sxs-lookup"><span data-stu-id="918d9-109">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="918d9-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="918d9-110">Resolution</span></span>  
 <span data-ttu-id="918d9-111">Sprawdź, której można się odwołać zliczanie kodu i poszukaj błędów, a także sprawdzając klientów natywnych obiektów dla zliczanie błędów odwołań.</span><span class="sxs-lookup"><span data-stu-id="918d9-111">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="918d9-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="918d9-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="918d9-113">Dostępne są dwa tryby.</span><span class="sxs-lookup"><span data-stu-id="918d9-113">Two modes are available.</span></span> <span data-ttu-id="918d9-114">Jeśli `allowAv` atrybut jest `true`, Asystenta zapobiega środowiska uruchomieniowego odrzucanie naruszenie zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="918d9-114">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="918d9-115">Jeśli `allowAv` jest `false`, co jest ustawieniem domyślnym, środowisko uruchomieniowe odrzuca naruszenie zasad dostępu, ale komunikat ostrzegawczy jest zgłaszany użytkownikowi, aby wskazać, czy wyjątek został zgłoszony i odrzucone.</span><span class="sxs-lookup"><span data-stu-id="918d9-115">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="918d9-116">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="918d9-116">Output</span></span>  
 <span data-ttu-id="918d9-117">Jeśli to możliwe dane wyjściowe zawierają wskaźnika interfejsu COM vtable oryginalnej.</span><span class="sxs-lookup"><span data-stu-id="918d9-117">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="918d9-118">W przeciwnym razie zostanie wyświetlony komunikat informacyjny.</span><span class="sxs-lookup"><span data-stu-id="918d9-118">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="918d9-119">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="918d9-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="918d9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="918d9-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="918d9-121">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="918d9-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="918d9-122">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="918d9-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
