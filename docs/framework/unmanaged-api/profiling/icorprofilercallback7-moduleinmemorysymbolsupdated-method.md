---
title: Metoda ICorProfilerCallback7::ModuleInMemorySymbolsUpdated
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f33eef5c405b98b9dbf88973a8b7cafad06308b6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466456"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="174d5-102">Metoda ICorProfilerCallback7::ModuleInMemorySymbolsUpdated</span><span class="sxs-lookup"><span data-stu-id="174d5-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="174d5-103">[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="174d5-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="174d5-104">Powiadamia program profilujący, zawsze wtedy, gdy strumień symbol skojarzone z modułem w pamięci zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="174d5-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="174d5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="174d5-105">Syntax</span></span>  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="174d5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="174d5-106">Parameters</span></span>  
 <span data-ttu-id="174d5-107">[in] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="174d5-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="174d5-108">Identyfikator modułu w pamięci, w której symbol strumień zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="174d5-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="174d5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="174d5-109">Remarks</span></span>  
 <span data-ttu-id="174d5-110">To wywołanie zwrotne jest kontrolowany przez ustawienie [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) flagi maski zdarzenia podczas wywoływania [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="174d5-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="174d5-111">To zdarzenie nie jest inicjowane dla symboli niejawnie utworzone lub zmodyfikowane za pośrednictwem <xref:System.Reflection.Emit> interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="174d5-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="174d5-112">Nawet gdy symbole znajdują się na początku w wywołaniu do jednego z przeciążeń zarządzaną <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> metody, które obejmuje `rawSymbolStore` argument określający symbole dla zestawu, środowisko uruchomieniowe nie może faktycznie kojarzyć dane symboliczne przy użyciu modułu do momentu po [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wystąpiło wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="174d5-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="174d5-113">To zdarzenie zawiera nowsze możliwość zbierania symbole dla tych modułów.</span><span class="sxs-lookup"><span data-stu-id="174d5-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="174d5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="174d5-114">Requirements</span></span>  
 <span data-ttu-id="174d5-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="174d5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="174d5-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="174d5-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="174d5-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="174d5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="174d5-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="174d5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="174d5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="174d5-119">See also</span></span>
- [<span data-ttu-id="174d5-120">ModuleLoadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="174d5-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="174d5-121">SetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="174d5-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="174d5-122">ICorProfilerCallback7, interfejs</span><span class="sxs-lookup"><span data-stu-id="174d5-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
