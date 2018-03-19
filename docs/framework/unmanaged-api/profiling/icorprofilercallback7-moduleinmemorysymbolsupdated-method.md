---
title: "ICorProfilerCallback7::ModuleInMemorySymbolsUpdated — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- ICorProfiler7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 898adf043e425c00d6e311e2f67c53ed65cacb33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="d167a-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated — metoda</span><span class="sxs-lookup"><span data-stu-id="d167a-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="d167a-103">[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="d167a-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="d167a-104">Powiadamia profilera przy każdej aktualizacji strumienia symbol skojarzone z modułu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d167a-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d167a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d167a-105">Syntax</span></span>  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d167a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d167a-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="d167a-107">Identyfikator modułu w pamięci, których strumienia symbol jest aktualizowany.</span><span class="sxs-lookup"><span data-stu-id="d167a-107">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d167a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d167a-108">Remarks</span></span>  
 <span data-ttu-id="d167a-109">To wywołanie zwrotne jest kontrolowany przez ustawienie [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) flagi Maska zdarzenia podczas wywoływania metody [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d167a-109">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d167a-110">To zdarzenie nie jest wywoływane dla symboli niejawnie utworzone lub zmodyfikowane za pośrednictwem <xref:System.Reflection.Emit> interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="d167a-110">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="d167a-111">Nawet gdy symbole znajdują się na początku w wywołaniu do jednego z przeciążeń zarządzanej <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> metod, które obejmuje `rawSymbolStore` argument zawierać symboli dla zestawu środowiska wykonawczego nie może faktycznie powiązania danych symboliczne z modułu dopóki po [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) podczas wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="d167a-111">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="d167a-112">To zdarzenie zawiera nowsze możliwość zbierania symbole dla tych modułów.</span><span class="sxs-lookup"><span data-stu-id="d167a-112">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d167a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d167a-113">Requirements</span></span>  
 <span data-ttu-id="d167a-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d167a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d167a-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d167a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d167a-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d167a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d167a-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d167a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d167a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d167a-118">See Also</span></span>  
 [<span data-ttu-id="d167a-119">ModuleLoadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="d167a-119">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [<span data-ttu-id="d167a-120">SetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="d167a-120">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)  
 [<span data-ttu-id="d167a-121">ICorProfilerCallback7, interfejs</span><span class="sxs-lookup"><span data-stu-id="d167a-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
