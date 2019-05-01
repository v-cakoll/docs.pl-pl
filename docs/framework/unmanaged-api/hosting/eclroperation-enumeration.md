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
ms.openlocfilehash: 7d5f24d7415ff7ecceba6b0a5fbd3098d70dcd0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796025"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="8281a-102">EClrOperation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8281a-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="8281a-103">W tym artykule opisano zestaw operacji, dla których hostem akcje można zastosować zasad.</span><span class="sxs-lookup"><span data-stu-id="8281a-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8281a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8281a-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8281a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8281a-105">Members</span></span>  
  
|<span data-ttu-id="8281a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8281a-106">Member</span></span>|<span data-ttu-id="8281a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8281a-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="8281a-108">Hosta można określić zasady akcje do wykonania, kiedy <xref:System.AppDomain> zwalnianie w sposób łagodne (prosta).</span><span class="sxs-lookup"><span data-stu-id="8281a-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="8281a-109">Hosta można określić zasady akcje do wykonania, kiedy <xref:System.AppDomain> jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="8281a-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="8281a-110">Hosta można określić zasady akcje do wykonania po uruchomieniu finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="8281a-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="8281a-111">Hosta można określić zasady akcje do wykonania, gdy kończy proces.</span><span class="sxs-lookup"><span data-stu-id="8281a-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="8281a-112">Hosta można określić zasady akcje do wykonania, gdy wątek został przerwany.</span><span class="sxs-lookup"><span data-stu-id="8281a-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="8281a-113">Hosta można określić zasady akcje do wykonania, gdy przerwanie wątku prosta odbywa się na krytyczny obszar kodu.</span><span class="sxs-lookup"><span data-stu-id="8281a-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="8281a-114">Hosta można określić akcje zasad podjęcie sytuacji przerwanie wątku prosta w regionie niekrytyczne kodu.</span><span class="sxs-lookup"><span data-stu-id="8281a-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8281a-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8281a-115">Remarks</span></span>  
 <span data-ttu-id="8281a-116">Wspólnej infrastruktury języka wspólnego (CLR) niezawodność rozróżnia przerwań i zasobów błędów alokacji, występujących w regionach krytycznego kodu, i te, które występują w niekrytyczne regiony kodu.</span><span class="sxs-lookup"><span data-stu-id="8281a-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="8281a-117">Ta różnica jest przeznaczony do Zezwalaj na hostach w celu ustawienia zasad różne w zależności od tego, gdzie występuje błąd w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8281a-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="8281a-118">A *krytyczne obszar kodu* dowolnego miejsca, gdzie środowisko CLR nie może zagwarantować tego przerywanie zadania lub nieukończone żądania dla zasobów wpłynie na bieżące zadanie.</span><span class="sxs-lookup"><span data-stu-id="8281a-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="8281a-119">Na przykład, jeśli zadanie jest blokada, otrzymuje wartość HRESULT, który wskazuje niepowodzenie podczas żądania alokacji pamięci jest za mała, aby przerwać to zadanie, aby upewnić się, stabilności, po prostu <xref:System.AppDomain>, ponieważ <xref:System.AppDomain> mogą zawierać inne Oczekiwanie na blokadę tego samego zadania.</span><span class="sxs-lookup"><span data-stu-id="8281a-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="8281a-120">Aby wstrzymać bieżącą zadanie może spowodować, te inne zadania przestać odpowiadać (lub odłożyć) na czas nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="8281a-120">To abandon the current task might cause those other tasks to stop responding (or hang) indefinitely.</span></span> <span data-ttu-id="8281a-121">W takim przypadku host wymaga możliwości można zwolnić całej <xref:System.AppDomain> zamiast niestabilności potencjalne ryzyko.</span><span class="sxs-lookup"><span data-stu-id="8281a-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="8281a-122">A *niekrytyczne obszar kodu*, z drugiej strony, to region, w którym środowiska CLR może zagwarantować, że przerwania lub awarii będzie mieć wpływ na zadania, na którym występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="8281a-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="8281a-123">Środowisko CLR rozróżnia również bezpiecznie i łagodne przerwań (prosta).</span><span class="sxs-lookup"><span data-stu-id="8281a-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="8281a-124">Ogólnie rzecz biorąc przerwania normalne lub łagodne dokłada wszelkich starań, aby uruchomić procedury obsługi wyjątków i finalizatory przed przerwaniem zadania, natomiast prosta przerwania nie gwarantuje takie.</span><span class="sxs-lookup"><span data-stu-id="8281a-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8281a-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8281a-125">Requirements</span></span>  
 <span data-ttu-id="8281a-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8281a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8281a-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8281a-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8281a-128">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8281a-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8281a-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8281a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8281a-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8281a-130">See also</span></span>

- [<span data-ttu-id="8281a-131">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8281a-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="8281a-132">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8281a-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="8281a-133">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8281a-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="8281a-134">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8281a-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="8281a-135">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8281a-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
