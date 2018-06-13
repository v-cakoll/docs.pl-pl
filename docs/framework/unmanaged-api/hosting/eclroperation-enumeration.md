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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b18c89cee0c3f5088a9978e448a0d61de1b9848
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434248"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="58ae9-102">EClrOperation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="58ae9-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="58ae9-103">W tym artykule opisano zestaw działań, dla których hosta można zastosować akcje zasady.</span><span class="sxs-lookup"><span data-stu-id="58ae9-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58ae9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58ae9-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="58ae9-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="58ae9-105">Members</span></span>  
  
|<span data-ttu-id="58ae9-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="58ae9-106">Member</span></span>|<span data-ttu-id="58ae9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="58ae9-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="58ae9-108">Hosta można określić zasady akcje do wykonania, kiedy <xref:System.AppDomain> jest zwalnianie w sposób (niegrzeczny) nie jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="58ae9-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="58ae9-109">Hosta można określić zasady akcje do wykonania, kiedy <xref:System.AppDomain> zostanie zwolniona.</span><span class="sxs-lookup"><span data-stu-id="58ae9-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="58ae9-110">Hosta można określić zasady akcje do wykonania podczas uruchamiania finalizatory.</span><span class="sxs-lookup"><span data-stu-id="58ae9-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="58ae9-111">Hosta można określić zasady akcje do wykonania, gdy kończy proces.</span><span class="sxs-lookup"><span data-stu-id="58ae9-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="58ae9-112">Hosta można określić zasady akcje do wykonania, gdy wątek został przerwany.</span><span class="sxs-lookup"><span data-stu-id="58ae9-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="58ae9-113">Hosta można określić zasady akcje do wykonania, kiedy występuje przerwania niegrzeczny wątku w regionie krytyczne kodu.</span><span class="sxs-lookup"><span data-stu-id="58ae9-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="58ae9-114">Hosta można określić zasady akcje podjęcie sytuacji przerwania niegrzeczny wątku w regionie niekrytyczne kodu.</span><span class="sxs-lookup"><span data-stu-id="58ae9-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58ae9-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58ae9-115">Remarks</span></span>  
 <span data-ttu-id="58ae9-116">Wspólna infrastruktura niezawodności środowiska uruchomieniowego (języka wspólnego CLR) języka rozróżnia przerwań i zasobów alokacji błędów występujących w regionach krytyczne kodu i tych, które występują w regionach niekrytyczne kodu.</span><span class="sxs-lookup"><span data-stu-id="58ae9-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="58ae9-117">Ta różnica umożliwia hostom skonfigurowanie różnych zasad w zależności od tego, gdzie występuje błąd w kodzie.</span><span class="sxs-lookup"><span data-stu-id="58ae9-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="58ae9-118">A *krytyczne region kodu* dowolnego miejsca, gdzie CLR nie może zagwarantować, że przerywanie zadania lub nie można ukończyć żądania dla zasobów wpłynie na bieżące zadanie.</span><span class="sxs-lookup"><span data-stu-id="58ae9-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="58ae9-119">Na przykład, jeśli zadanie jest blokada i otrzyma HRESULT wskazujący błąd podczas tworzenia żądania alokacji pamięci, jest za mało, aby po prostu przerwać tego zadania w celu zapewnienia stabilności <xref:System.AppDomain>, ponieważ <xref:System.AppDomain> może zawierać inne Oczekiwanie na tym samym blokady zadania.</span><span class="sxs-lookup"><span data-stu-id="58ae9-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="58ae9-120">Aby odrzucić bieżący zadania może spowodować, że te inne zadania przestać odpowiadać (lub Rozłącz) przez nieograniczony czas.</span><span class="sxs-lookup"><span data-stu-id="58ae9-120">To abandon the current task might cause those other tasks to stop responding (or hang) indefinitely.</span></span> <span data-ttu-id="58ae9-121">W takim przypadku host musi mieć możliwość zwolnienia całą <xref:System.AppDomain> zamiast niestabilność potencjalne zagrożenia.</span><span class="sxs-lookup"><span data-stu-id="58ae9-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="58ae9-122">A *niekrytyczne region kodu*, z drugiej strony, jest regionu, w którym środowiska CLR może zagwarantować, że przerwania lub awarii będzie miało wpływ na zadania, na których występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="58ae9-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="58ae9-123">Środowisko CLR rozróżnia również bezpieczne i łagodne przerwań (niegrzeczny).</span><span class="sxs-lookup"><span data-stu-id="58ae9-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="58ae9-124">Ogólnie rzecz biorąc przerwania normalne lub bezpieczne sprawia, że wszelkich starań, aby uruchomić procedury obsługi wyjątków i finalizatory przed przerwaniem zadania, podczas gdy niegrzeczny przerwania sprawia, że nie gwarancje.</span><span class="sxs-lookup"><span data-stu-id="58ae9-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58ae9-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="58ae9-125">Requirements</span></span>  
 <span data-ttu-id="58ae9-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58ae9-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58ae9-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="58ae9-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58ae9-128">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="58ae9-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58ae9-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58ae9-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ae9-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58ae9-130">See Also</span></span>  
 [<span data-ttu-id="58ae9-131">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="58ae9-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="58ae9-132">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="58ae9-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="58ae9-133">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="58ae9-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="58ae9-134">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="58ae9-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="58ae9-135">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="58ae9-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
