---
title: ICorProfilerCallback9::DynamicMethod Metoda nieoładowana
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0eb38c83e9ab706c96bdef971f0bf17cc096822b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177036"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="2bca4-102">ICorProfilerCallback9::DynamicMethod Metoda nieoładowana</span><span class="sxs-lookup"><span data-stu-id="2bca4-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="2bca4-103">[Obsługiwane w .NET Framework 4.7.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="2bca4-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="2bca4-104">Powiadamia profiler, gdy metoda dynamiczna jest wyrzucana, a następnie zwalniana.</span><span class="sxs-lookup"><span data-stu-id="2bca4-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bca4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2bca4-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bca4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2bca4-106">Parameters</span></span>  
<span data-ttu-id="2bca4-107">[w]`functionId`</span><span class="sxs-lookup"><span data-stu-id="2bca4-107">[in] `functionId`</span></span>  
<span data-ttu-id="2bca4-108">Identyfikator funkcji w pamięci, która została pobrana i zwolniona.</span><span class="sxs-lookup"><span data-stu-id="2bca4-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="2bca4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2bca4-109">Requirements</span></span>  
 <span data-ttu-id="2bca4-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bca4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bca4-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2bca4-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2bca4-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bca4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bca4-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2bca4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bca4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bca4-114">See also</span></span>

- [<span data-ttu-id="2bca4-115">Metoda uruchamiania ICorProfilerCallback8.DynamicMethodJITCompilation</span><span class="sxs-lookup"><span data-stu-id="2bca4-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="2bca4-116">ICorProfilerCallback8.DynamicMethodJITKończona metoda</span><span class="sxs-lookup"><span data-stu-id="2bca4-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="2bca4-117">ICorProfilerCallback9, interfejs</span><span class="sxs-lookup"><span data-stu-id="2bca4-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="2bca4-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="2bca4-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
