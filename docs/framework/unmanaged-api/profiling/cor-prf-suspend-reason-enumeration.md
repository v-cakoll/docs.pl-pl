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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b40533553ccd7a3339a8a3ee0c8b47879efd38ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742464"
---
# <a name="corprfsuspendreason-enumeration"></a><span data-ttu-id="80483-102">COR_PRF_SUSPEND_REASON — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="80483-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="80483-103">Wskazuje powód, że środowisko uruchomieniowe została wstrzymana.</span><span class="sxs-lookup"><span data-stu-id="80483-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80483-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80483-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="80483-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="80483-105">Members</span></span>  
  
|<span data-ttu-id="80483-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="80483-106">Member</span></span>|<span data-ttu-id="80483-107">Opis</span><span class="sxs-lookup"><span data-stu-id="80483-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="80483-108">Środowisko uruchomieniowe jest zawieszona z nieokreślonego powodu.</span><span class="sxs-lookup"><span data-stu-id="80483-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="80483-109">Środowisko uruchomieniowe jest zawieszona do obsłużenia żądania kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="80483-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="80483-110">Wywołania zwrotne dotyczące kolekcji wyrzucania elementów wystąpić między [icorprofilercallback::runtimesuspendfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) i [icorprofilercallback::runtimeresumestarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="80483-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="80483-111">Środowisko uruchomieniowe jest wstrzymana, aby `AppDomain` może zostać wyłączony.</span><span class="sxs-lookup"><span data-stu-id="80483-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="80483-112">Gdy środowisko uruchomieniowe jest wstrzymane, środowisko uruchomieniowe określi, które wątki są `AppDomain` czyli jest zamknięta i je przerwać po ich wznowić.</span><span class="sxs-lookup"><span data-stu-id="80483-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="80483-113">Istnieją nie `AppDomain`-określonych wywołania zwrotne podczas tego zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="80483-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="80483-114">Środowisko uruchomieniowe jest wstrzymana, tak, aby kod pitching mogą wystąpić.</span><span class="sxs-lookup"><span data-stu-id="80483-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="80483-115">Kod pitching ensues, tylko gdy kompilator just-in-time (JIT) jest aktywny za pomocą kodu pitching włączone.</span><span class="sxs-lookup"><span data-stu-id="80483-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="80483-116">Kod pitching wywołania zwrotne wystąpić między `ICorProfilerCallback::RuntimeSuspendFinished` i `ICorProfilerCallback::RuntimeResumeStarted` wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="80483-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="80483-117">**Uwaga:**  CLR JIT nie zawodowcom funkcje w wersji 2.0, .NET Framework, dlatego ta wartość nie jest używany w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="80483-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="80483-118">Środowisko uruchomieniowe jest wstrzymana, dzięki czemu można zamknąć.</span><span class="sxs-lookup"><span data-stu-id="80483-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="80483-119">Należy je zawiesić wszystkich wątków do wykonania danej operacji.</span><span class="sxs-lookup"><span data-stu-id="80483-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="80483-120">Środowisko uruchomieniowe jest zawieszony w procesie debugowania.</span><span class="sxs-lookup"><span data-stu-id="80483-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="80483-121">Środowisko uruchomieniowe jest zawieszony, aby przygotować się do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="80483-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="80483-122">Środowisko uruchomieniowe jest zawieszona na potrzeby ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="80483-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80483-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80483-123">Remarks</span></span>  
 <span data-ttu-id="80483-124">Wszystkie wątki środowiska uruchomieniowego, które są w niezarządzanym kodzie są dozwolone, aby kontynuować, dopóki użytkownik podejmie próbę ponownego wprowadzania środowiska uruchomieniowego, w tym momencie one będą również zawieszone, dopóki nie zostanie wznowione środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="80483-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="80483-125">Dotyczy to również nowe wątki, które wprowadzać środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="80483-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="80483-126">Wszystkie wątki w ramach środowiska uruchomieniowego są zawieszone natychmiast, jeśli są one w kodzie są albo monit wstrzymać, gdy osiągną oni limit przerywania kodu.</span><span class="sxs-lookup"><span data-stu-id="80483-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80483-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80483-127">Requirements</span></span>  
 <span data-ttu-id="80483-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80483-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80483-129">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="80483-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="80483-130">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80483-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80483-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80483-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80483-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80483-132">See also</span></span>
- [<span data-ttu-id="80483-133">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="80483-133">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
