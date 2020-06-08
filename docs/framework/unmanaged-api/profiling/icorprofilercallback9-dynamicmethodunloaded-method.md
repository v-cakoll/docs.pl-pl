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
ms.openlocfilehash: 2391ad854b17ec117940a3d3568c40d6cf7f4725
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498976"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="628d5-102">ICorProfilerCallback9::D ynamicMethodUnloaded Metoda</span><span class="sxs-lookup"><span data-stu-id="628d5-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="628d5-103">[Obsługiwane w .NET Framework 4.7.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="628d5-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="628d5-104">Powiadamia profiler za każdym razem, gdy metoda dynamiczna jest odzyskiwana, a następnie zwalniana.</span><span class="sxs-lookup"><span data-stu-id="628d5-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="628d5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="628d5-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="628d5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="628d5-106">Parameters</span></span>  
<span data-ttu-id="628d5-107">podczas`functionId`</span><span class="sxs-lookup"><span data-stu-id="628d5-107">[in] `functionId`</span></span>  
<span data-ttu-id="628d5-108">Identyfikator funkcji znajdującej się w pamięci, który został wyrzucony i zwolniony.</span><span class="sxs-lookup"><span data-stu-id="628d5-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="628d5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="628d5-109">Requirements</span></span>  
 <span data-ttu-id="628d5-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="628d5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="628d5-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="628d5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="628d5-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="628d5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="628d5-113">**.NET Framework wersje:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="628d5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="628d5-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="628d5-114">See also</span></span>

- [<span data-ttu-id="628d5-115">ICorProfilerCallback8. DynamicMethodJITCompilationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="628d5-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="628d5-116">ICorProfilerCallback8. DynamicMethodJITCompilationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="628d5-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="628d5-117">ICorProfilerCallback9, interfejs</span><span class="sxs-lookup"><span data-stu-id="628d5-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="628d5-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="628d5-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
