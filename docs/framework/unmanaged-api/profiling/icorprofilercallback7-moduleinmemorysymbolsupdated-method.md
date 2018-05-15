---
title: ICorProfilerCallback7::ModuleInMemorySymbolsUpdated — metoda
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
ms.openlocfilehash: 9aa690378a32ffee2def672f02dc8b5582647a5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="6f5c3-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated — metoda</span><span class="sxs-lookup"><span data-stu-id="6f5c3-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="6f5c3-103">[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="6f5c3-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="6f5c3-104">Powiadamia profilera przy każdej aktualizacji strumienia symbol skojarzone z modułu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6f5c3-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f5c3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f5c3-105">Syntax</span></span>  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f5c3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f5c3-106">Parameters</span></span>  
 <span data-ttu-id="6f5c3-107">[in] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="6f5c3-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="6f5c3-108">Identyfikator modułu w pamięci, których strumienia symbol jest aktualizowany.</span><span class="sxs-lookup"><span data-stu-id="6f5c3-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f5c3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f5c3-109">Remarks</span></span>  
 <span data-ttu-id="6f5c3-110">To wywołanie zwrotne jest kontrolowany przez ustawienie [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) flagi Maska zdarzenia podczas wywoływania metody [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6f5c3-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f5c3-111">To zdarzenie nie jest wywoływane dla symboli niejawnie utworzone lub zmodyfikowane za pośrednictwem <xref:System.Reflection.Emit> interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="6f5c3-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="6f5c3-112">Nawet gdy symbole znajdują się na początku w wywołaniu do jednego z przeciążeń zarządzanej <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> metod, które obejmuje `rawSymbolStore` argument zawierać symboli dla zestawu środowiska wykonawczego nie może faktycznie powiązania danych symboliczne z modułu dopóki po [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) podczas wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="6f5c3-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="6f5c3-113">To zdarzenie zawiera nowsze możliwość zbierania symbole dla tych modułów.</span><span class="sxs-lookup"><span data-stu-id="6f5c3-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f5c3-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6f5c3-114">Requirements</span></span>  
 <span data-ttu-id="6f5c3-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f5c3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f5c3-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f5c3-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f5c3-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f5c3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f5c3-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f5c3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f5c3-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f5c3-119">See Also</span></span>  
 [<span data-ttu-id="6f5c3-120">ModuleLoadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="6f5c3-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [<span data-ttu-id="6f5c3-121">SetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="6f5c3-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)  
 [<span data-ttu-id="6f5c3-122">ICorProfilerCallback7, interfejs</span><span class="sxs-lookup"><span data-stu-id="6f5c3-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
