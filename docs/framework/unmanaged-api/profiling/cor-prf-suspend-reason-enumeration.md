---
title: "COR_PRF_SUSPEND_REASON — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 713360b3cdc30ce7bca3e0df115016d66e59b0df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corprfsuspendreason-enumeration"></a><span data-ttu-id="333ee-102">COR_PRF_SUSPEND_REASON — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="333ee-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="333ee-103">Wskazuje przyczynę zawieszenia środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="333ee-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="333ee-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="333ee-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="333ee-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="333ee-105">Members</span></span>  
  
|<span data-ttu-id="333ee-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="333ee-106">Member</span></span>|<span data-ttu-id="333ee-107">Opis</span><span class="sxs-lookup"><span data-stu-id="333ee-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="333ee-108">Środowisko wykonawcze jest wstrzymana z nieokreślonego powodu.</span><span class="sxs-lookup"><span data-stu-id="333ee-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="333ee-109">Środowisko uruchomieniowe zostanie zawieszony w celu obsługi żądania kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="333ee-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="333ee-110">Wywołania zwrotne dotyczące kolekcji pamięci, występują między [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) i [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="333ee-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="333ee-111">Środowisko wykonawcze jest wstrzymana, aby `AppDomain` może zostać wyłączony.</span><span class="sxs-lookup"><span data-stu-id="333ee-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="333ee-112">Gdy środowisko wykonawcze jest wstrzymane, środowiska uruchomieniowego określi wątków, które znajdują się w `AppDomain` czyli Trwa zamykanie i ustaw je, aby przerwać, gdy są one.</span><span class="sxs-lookup"><span data-stu-id="333ee-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="333ee-113">Istnieją nie `AppDomain`-określonych wywołań zwrotnych podczas tego zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="333ee-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="333ee-114">Środowisko uruchomieniowe został wstrzymany, dzięki czemu kod pitching może wystąpić.</span><span class="sxs-lookup"><span data-stu-id="333ee-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="333ee-115">Kod pitching ensues, tylko gdy przy użyciu kompilatora just in time (JIT) jest aktywny z kodu pitching włączone.</span><span class="sxs-lookup"><span data-stu-id="333ee-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="333ee-116">Kod pitching wywołania zwrotne występują między `ICorProfilerCallback::RuntimeSuspendFinished` i `ICorProfilerCallback::RuntimeResumeStarted` wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="333ee-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="333ee-117">**Uwaga:** CLR JIT nie osoba funkcji w programie .NET Framework w wersji 2.0, dlatego ta wartość nie jest używana w 2.0.</span><span class="sxs-lookup"><span data-stu-id="333ee-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="333ee-118">Środowisko uruchomieniowe zostało zawieszone, dzięki czemu można zamknąć.</span><span class="sxs-lookup"><span data-stu-id="333ee-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="333ee-119">Musi ona zawiesić wszystkie wątki do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="333ee-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="333ee-120">Zawieszone środowiska uruchomieniowego w trakcie debugowania.</span><span class="sxs-lookup"><span data-stu-id="333ee-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="333ee-121">Środowisko uruchomieniowe został wstrzymany, aby przygotować się do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="333ee-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="333ee-122">Środowisko wykonawcze jest wstrzymana na potrzeby ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="333ee-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="333ee-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="333ee-123">Remarks</span></span>  
 <span data-ttu-id="333ee-124">Wszystkie wątki środowiska uruchomieniowego znajdujących się za pomocą kodu niezarządzanego mogą nadal działać do chwili próbują ponownie wprowadzić środowiska uruchomieniowego w takim przypadku one będą również zawieszone, dopóki nie zostanie wznowione środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="333ee-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="333ee-125">Dotyczy to również nowy wątków, które należy wprowadzić środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="333ee-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="333ee-126">Wszystkie wątki wewnątrz środowiska uruchomieniowego są zawieszone natychmiast, gdy są one w kodzie przerywania albo zadawane wstrzymania po osiągnięciu przerywania kodu.</span><span class="sxs-lookup"><span data-stu-id="333ee-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="333ee-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="333ee-127">Requirements</span></span>  
 <span data-ttu-id="333ee-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="333ee-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="333ee-129">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="333ee-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="333ee-130">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="333ee-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="333ee-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="333ee-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="333ee-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="333ee-132">See Also</span></span>  
 [<span data-ttu-id="333ee-133">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="333ee-133">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
