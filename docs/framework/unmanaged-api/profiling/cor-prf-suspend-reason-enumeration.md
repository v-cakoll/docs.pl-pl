---
title: COR_PRF_SUSPEND_REASON — Wyliczenie
ms.date: 03/30/2017
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
ms.openlocfilehash: fdbcbb2da8f449b9275d820763c2a94cca86cd1e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500757"
---
# <a name="cor_prf_suspend_reason-enumeration"></a><span data-ttu-id="34493-102">COR_PRF_SUSPEND_REASON — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="34493-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="34493-103">Wskazuje przyczynę zawieszenia środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="34493-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34493-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="34493-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="34493-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="34493-105">Members</span></span>  
  
|<span data-ttu-id="34493-106">Członek</span><span class="sxs-lookup"><span data-stu-id="34493-106">Member</span></span>|<span data-ttu-id="34493-107">Opis</span><span class="sxs-lookup"><span data-stu-id="34493-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="34493-108">Środowisko uruchomieniowe jest zawieszone z nieokreślonego powodu.</span><span class="sxs-lookup"><span data-stu-id="34493-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="34493-109">Środowisko uruchomieniowe jest zawieszone w celu obsługi żądania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="34493-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="34493-110">Wywołania zwrotne dotyczące wyrzucania elementów bezużytecznych są wykonywane między elementami wywołania zwrotne [ICorProfilerCallback:: RuntimeSuspendFinished —](icorprofilercallback-runtimesuspendfinished-method.md) i [ICorProfilerCallback:: RuntimeResumeStarted —](icorprofilercallback-runtimeresumestarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="34493-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="34493-111">Środowisko uruchomieniowe jest zawieszone, aby `AppDomain` można było je wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="34493-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="34493-112">Gdy środowisko uruchomieniowe jest wstrzymane, środowisko uruchomieniowe określi, które wątki znajdują się w `AppDomain` zamykanym i ustawi przerwanie w momencie ich wznowienia.</span><span class="sxs-lookup"><span data-stu-id="34493-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="34493-113">Brak `AppDomain` określonych wywołań zwrotnych w trakcie tego zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="34493-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="34493-114">Środowisko uruchomieniowe jest zawieszone, aby można było następować w kodzie.</span><span class="sxs-lookup"><span data-stu-id="34493-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="34493-115">Pochylenia kodu nastąpią, gdy kompilator just in Time (JIT) jest aktywny z włączonym postawem kodu.</span><span class="sxs-lookup"><span data-stu-id="34493-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="34493-116">Wywołania zwrotne dotyczące pochylenia kodu są wykonywane między `ICorProfilerCallback::RuntimeSuspendFinished` `ICorProfilerCallback::RuntimeResumeStarted` wywołaniami zwrotnymi i.</span><span class="sxs-lookup"><span data-stu-id="34493-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="34493-117">**Uwaga:**  Środowisko CLR JIT nie ma skoku funkcji w .NET Framework w wersji 2,0, więc ta wartość nie jest używana w 2,0.</span><span class="sxs-lookup"><span data-stu-id="34493-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="34493-118">Środowisko uruchomieniowe jest zawieszone, aby można je było wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="34493-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="34493-119">Musi zawiesić wszystkie wątki, aby ukończyć operację.</span><span class="sxs-lookup"><span data-stu-id="34493-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="34493-120">Środowisko uruchomieniowe jest zawieszone na potrzeby debugowania w procesie.</span><span class="sxs-lookup"><span data-stu-id="34493-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="34493-121">Środowisko uruchomieniowe jest zawieszone, aby przygotować się do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="34493-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="34493-122">Środowisko uruchomieniowe jest zawieszone na potrzeby ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="34493-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34493-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34493-123">Remarks</span></span>  
 <span data-ttu-id="34493-124">Wszystkie wątki środowiska uruchomieniowego, które znajdują się w kodzie niezarządzanym, mogą kontynuować działanie, dopóki nie spróbują ponownie wprowadzić środowiska uruchomieniowego. w tym momencie zostaną one zawieszone do momentu wznowienia działania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="34493-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="34493-125">Dotyczy to również nowych wątków, które wprowadzają środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="34493-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="34493-126">Wszystkie wątki w środowisku uruchomieniowym są zawieszane natychmiast, jeśli znajdują się w kodzie przerywania lub zażądają zawieszenia, gdy docierają do kodu przerywania.</span><span class="sxs-lookup"><span data-stu-id="34493-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34493-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34493-127">Requirements</span></span>  
 <span data-ttu-id="34493-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34493-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34493-129">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="34493-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34493-130">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="34493-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34493-131">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34493-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34493-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34493-132">See also</span></span>

- [<span data-ttu-id="34493-133">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="34493-133">Profiling Enumerations</span></span>](profiling-enumerations.md)
