---
title: EClrOperation — Wyliczenie
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
ms.openlocfilehash: 6becc44b061ff2baac63437b6a72375d1c3735b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131160"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="1f70a-102">EClrOperation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1f70a-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="1f70a-103">Opisuje zestaw operacji, dla których host może stosować akcje zasad.</span><span class="sxs-lookup"><span data-stu-id="1f70a-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f70a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f70a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a><span data-ttu-id="1f70a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1f70a-105">Members</span></span>  
  
|<span data-ttu-id="1f70a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1f70a-106">Member</span></span>|<span data-ttu-id="1f70a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1f70a-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="1f70a-108">Host może określać akcje zasad, które mają zostać podjęte, gdy <xref:System.AppDomain> zostanie zwolnione w sposób niebezpieczny (prosta).</span><span class="sxs-lookup"><span data-stu-id="1f70a-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="1f70a-109">Host może określać akcje zasad, które mają zostać podjęte, gdy <xref:System.AppDomain> zostanie zwolniona.</span><span class="sxs-lookup"><span data-stu-id="1f70a-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="1f70a-110">Host może określać akcje zasad, które mają być podejmowane po uruchomieniu finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="1f70a-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="1f70a-111">Host może określić akcje zasad, które mają zostać wykonane po zakończeniu procesu.</span><span class="sxs-lookup"><span data-stu-id="1f70a-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="1f70a-112">Host może określać akcje zasad, które mają być podejmowane w przypadku przerwania wątku.</span><span class="sxs-lookup"><span data-stu-id="1f70a-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="1f70a-113">Host może określać akcje zasad, które mają być podejmowane w przypadku przerwania wątku prosta w krytycznym regionie kodu.</span><span class="sxs-lookup"><span data-stu-id="1f70a-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="1f70a-114">Host może określać akcje zasad, które mają być podejmowane po przerwaniu wątku prosta w niekrytycznym regionie kodu.</span><span class="sxs-lookup"><span data-stu-id="1f70a-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f70a-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f70a-115">Remarks</span></span>  
 <span data-ttu-id="1f70a-116">Infrastruktura niezawodności aparatu plików wykonywalnych języka wspólnego (CLR) odróżnia między przerwami a błędami alokacji zasobów, które występują w krytycznych regionach kodu i tych, które występują w niekrytycznych regionach kodu.</span><span class="sxs-lookup"><span data-stu-id="1f70a-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="1f70a-117">Ta różnica została zaprojektowana tak, aby umożliwić hostom Ustawianie różnych zasad w zależności od tego, gdzie wystąpi błąd w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1f70a-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="1f70a-118">*Krytyczny region kodu* jest dowolnym miejscem, w którym środowisko CLR nie może zagwarantować, że przerywanie zadania lub niepowodzenie żądania dla zasobów będzie wpływać tylko na bieżące zadanie.</span><span class="sxs-lookup"><span data-stu-id="1f70a-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="1f70a-119">Na przykład, jeśli zadanie utrzymuje blokadę i otrzymuje wynik HRESULT wskazujący błąd podczas tworzenia żądania alokacji pamięci, to nie wystarczy po prostu przerwać to zadanie, aby zapewnić stabilność <xref:System.AppDomain>, ponieważ <xref:System.AppDomain> może zawierać inne zadania oczekiwanie na tę samą blokadę.</span><span class="sxs-lookup"><span data-stu-id="1f70a-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="1f70a-120">Aby porzucić bieżące zadanie, może spowodować, że te inne zadania przestaną odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="1f70a-120">To abandon the current task might cause those other tasks to stop responding.</span></span> <span data-ttu-id="1f70a-121">W takim przypadku host wymaga możliwości zwolnienia całego <xref:System.AppDomain>, a nie zagrożenia potencjalnej niestabilności.</span><span class="sxs-lookup"><span data-stu-id="1f70a-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="1f70a-122">*Niekrytyczny region kodu*, z drugiej strony, to region, w którym środowisko CLR może zagwarantować, że przerwanie lub awaria będzie wpływać tylko na zadanie, na którym wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="1f70a-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="1f70a-123">Środowisko CLR rozróżnia również łagodne i niebezpieczne przerwania (prosta).</span><span class="sxs-lookup"><span data-stu-id="1f70a-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="1f70a-124">Ogólnie rzecz biorąc, normalne lub bezpieczne przerwanie podejmuje wszelkie wysiłki, aby uruchomić procedury obsługi wyjątków i finalizatory przed przerwaniem zadania, podczas gdy przerwanie prosta nie daje takich gwarancji.</span><span class="sxs-lookup"><span data-stu-id="1f70a-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f70a-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f70a-125">Requirements</span></span>  
 <span data-ttu-id="1f70a-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f70a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f70a-127">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1f70a-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f70a-128">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1f70a-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f70a-129">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f70a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f70a-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f70a-130">See also</span></span>

- [<span data-ttu-id="1f70a-131">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1f70a-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="1f70a-132">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1f70a-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="1f70a-133">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f70a-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="1f70a-134">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f70a-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="1f70a-135">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1f70a-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
