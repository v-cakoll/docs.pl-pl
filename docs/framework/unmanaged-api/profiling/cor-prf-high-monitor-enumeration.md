---
title: Wyliczenie COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: fc0251624738a06d1be7081ebd099e97f7278a15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283142"
---
# <a name="cor_prf_high_monitor-enumeration"></a><span data-ttu-id="72daa-102">Wyliczenie COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="72daa-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>

<span data-ttu-id="72daa-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="72daa-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
<span data-ttu-id="72daa-104">Oferuje flagi oprócz tych, które znajdują się w wyliczeniu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) , który profiler może określić do metody [ICorProfilerInfo5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) podczas ładowania.</span><span class="sxs-lookup"><span data-stu-id="72daa-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72daa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="72daa-105">Syntax</span></span>  
  
```cpp
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,
    COR_PRF_HIGH_DISABLE_TIERED_COMPILATION       = 0x00000008,
    COR_PRF_HIGH_BASIC_GC                         = 0x00000010,
    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS         = 0x00000020,
    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED    = 0x00000040,
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS |
                                                    COR_PRF_HIGH_BASIC_GC |
                                                    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS |
                                                    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = COR_PRF_HIGH_DISABLE_TIERED_COMPILATION  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="72daa-106">Members</span><span class="sxs-lookup"><span data-stu-id="72daa-106">Members</span></span>  
  
|<span data-ttu-id="72daa-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="72daa-107">Member</span></span>|<span data-ttu-id="72daa-108">Opis</span><span class="sxs-lookup"><span data-stu-id="72daa-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="72daa-109">Nie ustawiono żadnych flag.</span><span class="sxs-lookup"><span data-stu-id="72daa-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="72daa-110">Kontroluje wywołanie zwrotne [ICorProfilerCallback6:: GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) w celu dodania odwołań do zestawu podczas przeszukiwania odwołań do zestawów CLR.</span><span class="sxs-lookup"><span data-stu-id="72daa-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="72daa-111">Kontroluje wywołanie zwrotne [ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) dla aktualizacji strumienia symboli skojarzonego z modułem w pamięci.</span><span class="sxs-lookup"><span data-stu-id="72daa-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="72daa-112">Steruje wywołaniem zwrotnym [ICorProfilerCallback9::D ynamicmethodunloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) , aby wskazać, kiedy metoda dynamiczna została odtworzona i zwolniona.</span><span class="sxs-lookup"><span data-stu-id="72daa-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="72daa-113">Tylko .NET Core 3,0 i nowsze wersje: wyłącza [kompilację warstwową](../../../core/whats-new/dotnet-core-3-0.md) dla plików profilowanych.</span><span class="sxs-lookup"><span data-stu-id="72daa-113">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="72daa-114">Tylko .NET Core 3,0 i nowsze wersje: zapewnia uproszczoną opcję profilowania GC w porównaniu do [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="72daa-114">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="72daa-115">Kontroluje tylko wywołania zwrotne [GarbageCollectionStarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)i [GetGenerationBounds —](icorprofilerinfo2-getgenerationbounds-method.md) .</span><span class="sxs-lookup"><span data-stu-id="72daa-115">Controls only the  [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="72daa-116">W przeciwieństwie do flagi `COR_PRF_MONITOR_GC`, `COR_PRF_HIGH_BASIC_GC` nie wyłącza współbieżnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="72daa-116">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="72daa-117">Tylko .NET Core 3,0 i nowsze wersje: włącza wywołania zwrotne [MovedReferences —](icorprofilercallback-movedreferences-method.md) i [MovedReferences2 —](icorprofilercallback4-movedreferences2-method.md) tylko do kompaktowania operacje odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="72daa-117">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="72daa-118">Tylko .NET Core 3,0 i nowsze wersje: podobne do [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), ale zawierają informacje dotyczące alokacji obiektów dla sterty dużych obiektów (LOH).</span><span class="sxs-lookup"><span data-stu-id="72daa-118">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the large object heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="72daa-119">Reprezentuje wszystkie flagi `COR_PRF_HIGH_MONITOR`, które wymagają obrazów z rozszerzonym profilem.</span><span class="sxs-lookup"><span data-stu-id="72daa-119">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="72daa-120">Odnosi się do flagi `COR_PRF_REQUIRE_PROFILE_IMAGE` w wyliczeniu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="72daa-120">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="72daa-121">Reprezentuje wszystkie flagi `COR_PRF_HIGH_MONITOR`, które można ustawić po dołączeniu profilera do uruchomionej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="72daa-121">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="72daa-122">Reprezentuje wszystkie flagi `COR_PRF_HIGH_MONITOR`, które można ustawić tylko podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="72daa-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="72daa-123">Próba zmiany którejkolwiek z tych flag w innym miejscu powoduje, że wartość `HRESULT`, która wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="72daa-123">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72daa-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72daa-124">Remarks</span></span>

<span data-ttu-id="72daa-125">Flagi `COR_PRF_HIGH_MONITOR` są używane z parametrem `pdwEventsHigh` metod [ICorProfilerInfo5:: GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) i [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="72daa-125">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="72daa-126">Począwszy od .NET Framework 4.6.1 wartość `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` zmieniona z 0 na `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="72daa-126">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="72daa-127">Począwszy od .NET Framework 4.7.2, jego wartość zmieniła się z `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` na `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span><span class="sxs-lookup"><span data-stu-id="72daa-127">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>   

<span data-ttu-id="72daa-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` ma być maską bitowej, która reprezentuje wszystkie flagi, które można ustawić tylko podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="72daa-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="72daa-129">Próba zmiany którejkolwiek z tych flag w innym miejscu powoduje niepowodzenie `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="72daa-129">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="72daa-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="72daa-130">Requirements</span></span>

<span data-ttu-id="72daa-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72daa-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="72daa-132">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="72daa-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="72daa-133">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="72daa-133">**Library:** CorGuids.lib</span></span>  
  
<span data-ttu-id="72daa-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72daa-134">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72daa-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72daa-135">See also</span></span>

- [<span data-ttu-id="72daa-136">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="72daa-136">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [<span data-ttu-id="72daa-137">COR_PRF_MONITOR, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="72daa-137">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="72daa-138">ICorProfilerInfo5, interfejs</span><span class="sxs-lookup"><span data-stu-id="72daa-138">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
