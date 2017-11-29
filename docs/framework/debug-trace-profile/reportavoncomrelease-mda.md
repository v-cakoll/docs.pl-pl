---
title: reportAvOnComRelease MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: de48fca818f8456627c9507756cc2d8a200c50e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="7d1d6-102">reportAvOnComRelease MDA</span><span class="sxs-lookup"><span data-stu-id="7d1d6-102">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="7d1d6-103">`reportAvOnComRelease` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy istnieją wyjątki zgłaszane z powodu użytkownika zliczanie błędów podczas wykonywania COM interop i użycie <xref:System.Runtime.InteropServices.Marshal.Release%2A> lub <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metody połączone z pierwotnych wywołania COM.</span><span class="sxs-lookup"><span data-stu-id="7d1d6-103">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7d1d6-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="7d1d6-104">Symptoms</span></span>  
 <span data-ttu-id="7d1d6-105">Naruszenia zasad dostępu i uszkodzenie pamięci.</span><span class="sxs-lookup"><span data-stu-id="7d1d6-105">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7d1d6-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="7d1d6-106">Cause</span></span>  
 <span data-ttu-id="7d1d6-107">Czasami jest zgłaszany wyjątek z powodu użytkownika zliczanie błędów podczas wykonywania COM interop i użycie <xref:System.Runtime.InteropServices.Marshal.Release%2A> lub <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metody połączone z pierwotnych wywołania COM.</span><span class="sxs-lookup"><span data-stu-id="7d1d6-107">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="7d1d6-108">Zazwyczaj tego wyjątku jest odrzucona, ponieważ nie w ten sposób spowodowałoby naruszenie zasad dostępu w środowisku CLR, wyłączania go.</span><span class="sxs-lookup"><span data-stu-id="7d1d6-108">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="7d1d6-109">Po włączeniu tego Asystenta takie wyjątki można wykryte i zgłosił zamiast po prostu zostanie odrzucony.</span><span class="sxs-lookup"><span data-stu-id="7d1d6-109">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7d1d6-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="7d1d6-110">Resolution</span></span>  
 <span data-ttu-id="7d1d6-111">Sprawdź, czy użytkownikowi zliczania kodu i wyszukać błędy, a także badanie klientach natywnych obiektu dla zliczanie błędów odwołań.</span><span class="sxs-lookup"><span data-stu-id="7d1d6-111">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7d1d6-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7d1d6-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="7d1d6-113">Dostępne są dwa tryby.</span><span class="sxs-lookup"><span data-stu-id="7d1d6-113">Two modes are available.</span></span> <span data-ttu-id="7d1d6-114">Jeśli `allowAv` atrybutu `true`, Asystenta uniemożliwia środowiska uruchomieniowego odrzucanie naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="7d1d6-114">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="7d1d6-115">Jeśli `allowAv` jest `false`, co jest ustawieniem domyślnym, środowisko uruchomieniowe odrzuca naruszenia zasad dostępu, ale komunikat ostrzegawczy jest zgłaszany użytkownikowi wskazująca, czy wyjątek został zgłoszony i odrzucone.</span><span class="sxs-lookup"><span data-stu-id="7d1d6-115">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7d1d6-116">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="7d1d6-116">Output</span></span>  
 <span data-ttu-id="7d1d6-117">Jeśli to możliwe dane wyjściowe zawierają oryginalnego vtable wskaźnika interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="7d1d6-117">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="7d1d6-118">W przeciwnym razie zostanie wyświetlony komunikat informacyjny.</span><span class="sxs-lookup"><span data-stu-id="7d1d6-118">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7d1d6-119">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="7d1d6-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d1d6-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d1d6-120">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="7d1d6-121">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="7d1d6-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="7d1d6-122">Przekazywanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="7d1d6-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
