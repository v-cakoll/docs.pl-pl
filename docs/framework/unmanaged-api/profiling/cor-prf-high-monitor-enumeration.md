---
title: Wyliczenie COR_PRF_HIGH_MONITOR
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ec30d19af133b4f0734dadf8775dc8682666e22
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corprfhighmonitor-enumeration"></a><span data-ttu-id="a0f48-102">Wyliczenie COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="a0f48-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>
<span data-ttu-id="a0f48-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="a0f48-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a0f48-104">Udostępnia flagi oprócz występujące w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia, które można określić profilera [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody podczas jego ładowania.</span><span class="sxs-lookup"><span data-stu-id="a0f48-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0f48-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0f48-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES     = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED     = 0x00000002,     
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE       = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH      = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE           = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="a0f48-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a0f48-106">Members</span></span>  
  
|<span data-ttu-id="a0f48-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a0f48-107">Member</span></span>|<span data-ttu-id="a0f48-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a0f48-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="a0f48-109">Ustawiono żadnych flag.</span><span class="sxs-lookup"><span data-stu-id="a0f48-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="a0f48-110">Formanty [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego do dodawania odwołania do zestawów podczas przeszukiwania zamknięcia odwołanie do zestawu CLR.</span><span class="sxs-lookup"><span data-stu-id="a0f48-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="a0f48-111">Formanty [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) wywołania zwrotnego aktualizacji w strumieniu symbol skojarzone z modułu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a0f48-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="a0f48-112">Reprezentuje wszystkie `COR_PRF_HIGH_MONITOR` flagi, które wymagają rozszerzone profilu obrazów.</span><span class="sxs-lookup"><span data-stu-id="a0f48-112">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="a0f48-113">Odpowiadający mu `COR_PRF_REQUIRE_PROFILE_IMAGE` oflagowane w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a0f48-113">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="a0f48-114">Reprezentuje wszystkie `COR_PRF_HIGH_MONITOR` flagi, które można ustawić po profiler jest dołączony do uruchomionej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0f48-114">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="a0f48-115">Reprezentuje wszystkie `COR_PRF_HIGH_MONITOR` flagi, które można ustawić tylko podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="a0f48-115">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="a0f48-116">Aby zmienić dowolne z tych flag, gdzie indziej powoduje w trakcie `HRESULT` wartość, która wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="a0f48-116">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0f48-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0f48-117">Remarks</span></span>  
 <span data-ttu-id="a0f48-118">`COR_PRF_HIGH_MONITOR` Flagi są używane z `pdwEventsHigh` parametr [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) i [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a0f48-118">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
 <span data-ttu-id="a0f48-119">Począwszy od [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], wartość `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` zmienione od 0 do `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="a0f48-119">Starting with the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0f48-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0f48-120">Requirements</span></span>  
 <span data-ttu-id="a0f48-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0f48-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0f48-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0f48-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0f48-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0f48-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0f48-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0f48-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0f48-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0f48-125">See Also</span></span>  
 [<span data-ttu-id="a0f48-126">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a0f48-126">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [<span data-ttu-id="a0f48-127">COR_PRF_MONITOR, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a0f48-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 [<span data-ttu-id="a0f48-128">ICorProfilerInfo5, interfejs</span><span class="sxs-lookup"><span data-stu-id="a0f48-128">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
