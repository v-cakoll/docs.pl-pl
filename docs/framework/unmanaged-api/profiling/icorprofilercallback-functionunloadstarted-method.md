---
title: ICorProfilerCallback::FunctionUnloadStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: 320aaf074452fd02cd8ee8e80194a4c35b831eb4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503383"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="c21c5-102">ICorProfilerCallback::FunctionUnloadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="c21c5-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="c21c5-103">Powiadamia profiler o rozpoczęciu pracy przez środowisko uruchomieniowe w celu zwolnienia funkcji.</span><span class="sxs-lookup"><span data-stu-id="c21c5-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c21c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c21c5-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="c21c5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c21c5-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="c21c5-106">\[in] identyfikator funkcji, która jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="c21c5-106">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="c21c5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c21c5-107">Remarks</span></span>  
 <span data-ttu-id="c21c5-108">Wartość `functionId` parametru nie jest już prawidłowa po powrocie tej metody do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="c21c5-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c21c5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c21c5-109">Requirements</span></span>  
 <span data-ttu-id="c21c5-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c21c5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c21c5-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c21c5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c21c5-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c21c5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c21c5-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c21c5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c21c5-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c21c5-114">See also</span></span>

- [<span data-ttu-id="c21c5-115">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c21c5-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
