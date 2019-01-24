---
title: Wyliczenie COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24fde3901f4a866fb14461533a24f0ce265847ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600131"
---
# <a name="corprfhighmonitor-enumeration"></a><span data-ttu-id="6592b-102">Wyliczenie COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="6592b-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>
<span data-ttu-id="6592b-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="6592b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6592b-104">Zawiera flagi, oprócz tych dostępnych w [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenie, które można określić profiler [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metodą podczas wczytywania.</span><span class="sxs-lookup"><span data-stu-id="6592b-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6592b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6592b-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,     
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,    
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="6592b-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6592b-106">Members</span></span>  
  
|<span data-ttu-id="6592b-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6592b-107">Member</span></span>|<span data-ttu-id="6592b-108">Opis</span><span class="sxs-lookup"><span data-stu-id="6592b-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="6592b-109">Flagi nie są ustawione.</span><span class="sxs-lookup"><span data-stu-id="6592b-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="6592b-110">Formanty [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego do dodawania odwołania do zestawów podczas przeszukiwania zamknięcia odwołania zestawów CLR.</span><span class="sxs-lookup"><span data-stu-id="6592b-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="6592b-111">Formanty [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) wywołanie zwrotne dla aktualizacji w strumieniu symbol skojarzone z modułem w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6592b-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="6592b-112">Formanty [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) wywołanie zwrotne wskazujące, gdy metoda dynamiczna został wyrzucania elementów zbierane i zwolnione.</span><span class="sxs-lookup"><span data-stu-id="6592b-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|   
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="6592b-113">Reprezentuje wszystkie `COR_PRF_HIGH_MONITOR` flagi, które wymagają obrazów rozszerzone profilu.</span><span class="sxs-lookup"><span data-stu-id="6592b-113">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="6592b-114">Odnosi się do `COR_PRF_REQUIRE_PROFILE_IMAGE` znacznik w [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="6592b-114">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="6592b-115">Reprezentuje wszystkie `COR_PRF_HIGH_MONITOR` flagi, które można ustawić po profiler jest dołączony do uruchomionej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6592b-115">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="6592b-116">Reprezentuje wszystkie `COR_PRF_HIGH_MONITOR` flagi, które można ustawić tylko podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="6592b-116">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="6592b-117">Podjęcie próby zmienić dowolne z tych flag, gdzie indziej skutkuje `HRESULT` wartość, która wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="6592b-117">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6592b-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6592b-118">Remarks</span></span>  
 <span data-ttu-id="6592b-119">`COR_PRF_HIGH_MONITOR` Flagi są używane wraz z `pdwEventsHigh` parametru [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) i [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6592b-119">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="6592b-120">Począwszy od [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], wartość `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` zmienione od 0 do `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="6592b-120">Starting with the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="6592b-121">Począwszy od programu .NET Framework 4.7.2, jego wartość zmieniła się z `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` do `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span><span class="sxs-lookup"><span data-stu-id="6592b-121">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>   

<span data-ttu-id="6592b-122">`COR_PRF_HIGH_MONITOR_IMMUTABLE` ma być maską bitów, który reprezentuje wszystkie flagi, które można ustawić tylko podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="6592b-122">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="6592b-123">Podjęcie próby zmienić dowolne z tych flag, gdzie indziej powoduje niepowodzenie `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="6592b-123">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="6592b-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6592b-124">Requirements</span></span>  
 <span data-ttu-id="6592b-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6592b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6592b-126">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6592b-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6592b-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6592b-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6592b-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6592b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6592b-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6592b-129">See also</span></span>
- [<span data-ttu-id="6592b-130">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="6592b-130">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [<span data-ttu-id="6592b-131">COR_PRF_MONITOR, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6592b-131">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="6592b-132">ICorProfilerInfo5, interfejs</span><span class="sxs-lookup"><span data-stu-id="6592b-132">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
