---
title: ICorProfilerCallback9::DynamicMethodUnloaded — metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16b3334647922f845645e6eb58db3146f4c9b936
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="fdf4a-102">ICorProfilerCallback9::DynamicMethodUnloaded — metoda</span><span class="sxs-lookup"><span data-stu-id="fdf4a-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="fdf4a-103">[Obsługiwane w programie .NET Framework 4.7.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="fdf4a-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="fdf4a-104">Powiadamia profilera zawsze, gdy dynamiczna metoda jest Odzyskiwanie zbierane i następnie zwalnianie.</span><span class="sxs-lookup"><span data-stu-id="fdf4a-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdf4a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdf4a-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fdf4a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdf4a-106">Parameters</span></span>  
<span data-ttu-id="fdf4a-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="fdf4a-107">[in] `functionId`</span></span>  
<span data-ttu-id="fdf4a-108">Identyfikator funkcji w pamięci, która została odzyskiwanie zbierane i zwalnianie modułu.</span><span class="sxs-lookup"><span data-stu-id="fdf4a-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="fdf4a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fdf4a-109">Requirements</span></span>  
 <span data-ttu-id="fdf4a-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdf4a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdf4a-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fdf4a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fdf4a-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdf4a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdf4a-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fdf4a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdf4a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fdf4a-114">See Also</span></span>  
[<span data-ttu-id="fdf4a-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted — metoda</span><span class="sxs-lookup"><span data-stu-id="fdf4a-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
[<span data-ttu-id="fdf4a-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished — metoda</span><span class="sxs-lookup"><span data-stu-id="fdf4a-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
<span data-ttu-id="fdf4a-117">[Interfejs ICorProfilerCallback9](icorprofilercallback9-interface.md) </span><span class="sxs-lookup"><span data-stu-id="fdf4a-117">[ICorProfilerCallback9 Interface](icorprofilercallback9-interface.md) </span></span>  
[<span data-ttu-id="fdf4a-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="fdf4a-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
