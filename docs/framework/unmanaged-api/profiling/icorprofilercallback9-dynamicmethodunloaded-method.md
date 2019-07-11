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
ms.openlocfilehash: 680bd351a64632e67432ee03352ee7caa8f4b2d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780388"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="8e6e1-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span><span class="sxs-lookup"><span data-stu-id="8e6e1-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="8e6e1-103">[Obsługiwane w programie .NET Framework 4.7.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="8e6e1-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="8e6e1-104">Powiadamia program profilujący, zawsze wtedy, gdy metoda dynamiczna pamięci zbierane i następnie zwolnione.</span><span class="sxs-lookup"><span data-stu-id="8e6e1-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e6e1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e6e1-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e6e1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e6e1-106">Parameters</span></span>  
<span data-ttu-id="8e6e1-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="8e6e1-107">[in] `functionId`</span></span>  
<span data-ttu-id="8e6e1-108">Identyfikator funkcji w pamięci, która została pamięci pobrane i załadowane.</span><span class="sxs-lookup"><span data-stu-id="8e6e1-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="8e6e1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e6e1-109">Requirements</span></span>  
 <span data-ttu-id="8e6e1-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e6e1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e6e1-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8e6e1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8e6e1-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e6e1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e6e1-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8e6e1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e6e1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e6e1-114">See also</span></span>

- [<span data-ttu-id="8e6e1-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span><span class="sxs-lookup"><span data-stu-id="8e6e1-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="8e6e1-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span><span class="sxs-lookup"><span data-stu-id="8e6e1-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="8e6e1-117">ICorProfilerCallback9, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e6e1-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="8e6e1-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="8e6e1-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
