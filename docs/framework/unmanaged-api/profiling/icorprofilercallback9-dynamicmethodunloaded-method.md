---
title: ICorProfilerCallback9::DynamicMethodUnloaded Method
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
ms.openlocfilehash: 96cdfb79c1573648173305d6ee789aa8db030ff8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211013"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="41b26-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span><span class="sxs-lookup"><span data-stu-id="41b26-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="41b26-103">[Obsługiwane w programie .NET Framework 4.7.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="41b26-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="41b26-104">Powiadamia program profilujący, zawsze wtedy, gdy metoda dynamiczna pamięci zbierane i następnie zwolnione.</span><span class="sxs-lookup"><span data-stu-id="41b26-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41b26-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="41b26-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41b26-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="41b26-106">Parameters</span></span>  
<span data-ttu-id="41b26-107">[in]</span><span class="sxs-lookup"><span data-stu-id="41b26-107">[in]</span></span> `functionId`  
<span data-ttu-id="41b26-108">Identyfikator funkcji w pamięci, która została pamięci pobrane i załadowane.</span><span class="sxs-lookup"><span data-stu-id="41b26-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="41b26-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41b26-109">Requirements</span></span>  
 <span data-ttu-id="41b26-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41b26-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41b26-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="41b26-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="41b26-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41b26-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="41b26-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="41b26-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="41b26-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41b26-114">See also</span></span>

- [<span data-ttu-id="41b26-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span><span class="sxs-lookup"><span data-stu-id="41b26-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="41b26-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span><span class="sxs-lookup"><span data-stu-id="41b26-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="41b26-117">ICorProfilerCallback9, interfejs</span><span class="sxs-lookup"><span data-stu-id="41b26-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="41b26-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="41b26-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
