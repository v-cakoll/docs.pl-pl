---
title: ICorProfilerCallback9::D ynamicMethodUnloaded Metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 05a788179ff40a6889ed613b5f8659dd3f8e066f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196317"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="cca0c-102">ICorProfilerCallback9::D ynamicMethodUnloaded Metoda</span><span class="sxs-lookup"><span data-stu-id="cca0c-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="cca0c-103">[Obsługiwane w .NET Framework 4.7.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="cca0c-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="cca0c-104">Powiadamia profiler za każdym razem, gdy metoda dynamiczna jest odzyskiwana, a następnie zwalniana.</span><span class="sxs-lookup"><span data-stu-id="cca0c-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cca0c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cca0c-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cca0c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cca0c-106">Parameters</span></span>  
<span data-ttu-id="cca0c-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="cca0c-107">[in] `functionId`</span></span>  
<span data-ttu-id="cca0c-108">Identyfikator funkcji znajdującej się w pamięci, który został wyrzucony i zwolniony.</span><span class="sxs-lookup"><span data-stu-id="cca0c-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="cca0c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cca0c-109">Requirements</span></span>  
 <span data-ttu-id="cca0c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cca0c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cca0c-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cca0c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cca0c-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cca0c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cca0c-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cca0c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cca0c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cca0c-114">See also</span></span>

- [<span data-ttu-id="cca0c-115">ICorProfilerCallback8. DynamicMethodJITCompilationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="cca0c-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="cca0c-116">ICorProfilerCallback8. DynamicMethodJITCompilationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="cca0c-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="cca0c-117">ICorProfilerCallback9, interfejs</span><span class="sxs-lookup"><span data-stu-id="cca0c-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="cca0c-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="cca0c-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
