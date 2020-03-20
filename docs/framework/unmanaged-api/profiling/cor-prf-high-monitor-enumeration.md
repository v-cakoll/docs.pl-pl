---
title: Wyliczenie COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 5c6e34746368a7658c43fe0e2472000c29292569
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175216"
---
# <a name="cor_prf_high_monitor-enumeration"></a><span data-ttu-id="44e9e-102">Wyliczenie COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="44e9e-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>

<span data-ttu-id="44e9e-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="44e9e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
<span data-ttu-id="44e9e-104">Zawiera flagi oprócz tych znalezionych w [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) wyliczenie, które profiler można określić do [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) metody podczas ładowania.</span><span class="sxs-lookup"><span data-stu-id="44e9e-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e9e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="44e9e-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="44e9e-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="44e9e-106">Members</span></span>  
  
|<span data-ttu-id="44e9e-107">Członek</span><span class="sxs-lookup"><span data-stu-id="44e9e-107">Member</span></span>|<span data-ttu-id="44e9e-108">Opis</span><span class="sxs-lookup"><span data-stu-id="44e9e-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="44e9e-109">Nie ustawiono żadnych flag.</span><span class="sxs-lookup"><span data-stu-id="44e9e-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="44e9e-110">Steruje [wywołaniami zwrotnymi ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) do dodawania odwołań do zestawu podczas przejścia zamknięcia odwołania do odwołania clr.</span><span class="sxs-lookup"><span data-stu-id="44e9e-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="44e9e-111">Steruje [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback dla aktualizacji strumienia symbolu skojarzonego z modułem w pamięci.</span><span class="sxs-lookup"><span data-stu-id="44e9e-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="44e9e-112">Steruje [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) wywołania zwrotnego do wskazania, gdy metoda dynamiczna została pobrana i zwolniona.</span><span class="sxs-lookup"><span data-stu-id="44e9e-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="44e9e-113">.NET Core 3.0 i nowsze wersje tylko: Wyłącza [kompilacji warstwowej](../../../core/whats-new/dotnet-core-3-0.md) dla profilerów.</span><span class="sxs-lookup"><span data-stu-id="44e9e-113">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="44e9e-114">.NET Core 3.0 i nowsze wersje tylko: Zapewnia [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)lekką opcję profilowania GC w porównaniu do .</span><span class="sxs-lookup"><span data-stu-id="44e9e-114">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="44e9e-115">Steruje tylko [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)i [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="44e9e-115">Controls only the  [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="44e9e-116">W `COR_PRF_MONITOR_GC` przeciwieństwie `COR_PRF_HIGH_BASIC_GC` do flagi, nie wyłącza równoczesnych wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="44e9e-116">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="44e9e-117">.NET Core 3.0 i nowsze wersje tylko: Włącza [MovedReferences](icorprofilercallback-movedreferences-method.md) i [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) wywołania zwrotne tylko do kompaktowania kontrolerów GC.</span><span class="sxs-lookup"><span data-stu-id="44e9e-117">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="44e9e-118">.NET Core 3.0 i nowsze wersje tylko: Podobne do [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), ale zawiera informacje na temat alokacji obiektów dla sterty dużych obiektów (LOH) tylko.</span><span class="sxs-lookup"><span data-stu-id="44e9e-118">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the large object heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="44e9e-119">Reprezentuje `COR_PRF_HIGH_MONITOR` wszystkie flagi, które wymagają obrazów o rozszerzonej profili.</span><span class="sxs-lookup"><span data-stu-id="44e9e-119">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="44e9e-120">Odpowiada `COR_PRF_REQUIRE_PROFILE_IMAGE` flagi w wyliczeniu [COR_PRF_MONITOR.](cor-prf-monitor-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="44e9e-120">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="44e9e-121">Reprezentuje `COR_PRF_HIGH_MONITOR` wszystkie flagi, które można ustawić po profiler jest dołączony do uruchomionej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="44e9e-121">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="44e9e-122">Reprezentuje `COR_PRF_HIGH_MONITOR` wszystkie flagi, które można ustawić tylko podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="44e9e-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="44e9e-123">Próba zmiany dowolnej z tych flag `HRESULT` w innym miejscu powoduje wartość, która wskazuje na niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="44e9e-123">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44e9e-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44e9e-124">Remarks</span></span>

<span data-ttu-id="44e9e-125">Flagi `COR_PRF_HIGH_MONITOR` są używane `pdwEventsHigh` z [parametrem ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) i [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="44e9e-125">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="44e9e-126">Począwszy od .NET Framework 4.6.1, `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` wartość zmieniona `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` z 0 na (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="44e9e-126">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="44e9e-127">Począwszy od programu .NET Framework 4.7.2, jego wartość zmieniła się z `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` na `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span><span class="sxs-lookup"><span data-stu-id="44e9e-127">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>

<span data-ttu-id="44e9e-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE`ma być maską bitową, która reprezentuje wszystkie flagi, które można ustawić tylko podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="44e9e-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="44e9e-129">Próba zmiany któregokolwiek z tych flag `HRESULT`w innym miejscu powoduje niepowodzenie .</span><span class="sxs-lookup"><span data-stu-id="44e9e-129">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="44e9e-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44e9e-130">Requirements</span></span>

<span data-ttu-id="44e9e-131">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44e9e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="44e9e-132">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="44e9e-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="44e9e-133">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44e9e-133">**Library:** CorGuids.lib</span></span>  
  
<span data-ttu-id="44e9e-134">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44e9e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e9e-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44e9e-135">See also</span></span>

- [<span data-ttu-id="44e9e-136">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="44e9e-136">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="44e9e-137">COR_PRF_MONITOR, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="44e9e-137">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="44e9e-138">ICorProfilerInfo5, interfejs</span><span class="sxs-lookup"><span data-stu-id="44e9e-138">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
