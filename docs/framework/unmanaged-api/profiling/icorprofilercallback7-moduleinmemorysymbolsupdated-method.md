---
title: 'ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated, Metoda'
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
ms.openlocfilehash: 860ecde22dead112a42b6ac868e34f0e9cd3531d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916199"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="38258-102">ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated, Metoda</span><span class="sxs-lookup"><span data-stu-id="38258-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="38258-103">[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="38258-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="38258-104">Powiadamia profiler za każdym razem, gdy zostanie zaktualizowany strumień symboli skojarzony z modułem w pamięci.</span><span class="sxs-lookup"><span data-stu-id="38258-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38258-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="38258-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38258-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="38258-106">Parameters</span></span>  
 <span data-ttu-id="38258-107">podczas`moduleId`</span><span class="sxs-lookup"><span data-stu-id="38258-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="38258-108">Identyfikator modułu w pamięci, którego strumień symboli został zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="38258-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38258-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38258-109">Remarks</span></span>  
 <span data-ttu-id="38258-110">To wywołanie zwrotne jest kontrolowane przez ustawienie flagi maski zdarzeń [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) podczas wywoływania metody [ICorProfilerCallback5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="38258-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38258-111">To zdarzenie nie jest obecnie wywoływane dla symboli niejawnie utworzonych lub zmodyfikowanych za pośrednictwem <xref:System.Reflection.Emit> interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="38258-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="38258-112">Nawet jeśli symbole są dostarczane z góry w wywołaniu jednego z przeciążeń metod zarządzanych <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> , które `rawSymbolStore` zawierają argument, aby określić symbole dla zestawu, środowisko uruchomieniowe może w rzeczywistości nie skojarzyć danych symbolicznych z modułem do momentu wystąpienia wywołania zwrotnego [ModuleLoadFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="38258-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="38258-113">To zdarzenie umożliwia późniejsze zbieranie symboli dla takich modułów.</span><span class="sxs-lookup"><span data-stu-id="38258-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38258-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38258-114">Requirements</span></span>  
 <span data-ttu-id="38258-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38258-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38258-116">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="38258-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="38258-117">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38258-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38258-118">**.NET Framework wersje:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38258-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38258-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38258-119">See also</span></span>

- [<span data-ttu-id="38258-120">ModuleLoadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="38258-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="38258-121">SetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="38258-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="38258-122">ICorProfilerCallback7, interfejs</span><span class="sxs-lookup"><span data-stu-id="38258-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
