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
ms.openlocfilehash: 988843559e55cc4cacd2a40bb3e6ac51721e99b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175164"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="2fa74-102">ICorProfilerCallback::FunctionUnloadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="2fa74-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="2fa74-103">Powiadamia profiler, że środowisko wykonawcze rozpoczęło zwalnianie funkcji.</span><span class="sxs-lookup"><span data-stu-id="2fa74-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa74-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2fa74-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="2fa74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fa74-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="2fa74-106">\[w] Identyfikator funkcji, która jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="2fa74-106">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="2fa74-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2fa74-107">Remarks</span></span>  
 <span data-ttu-id="2fa74-108">Wartość parametru `functionId` nie jest już prawidłowa po tym, jak ta metoda zwraca do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2fa74-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fa74-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2fa74-109">Requirements</span></span>  
 <span data-ttu-id="2fa74-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fa74-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fa74-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2fa74-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2fa74-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fa74-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fa74-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fa74-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa74-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fa74-114">See also</span></span>

- [<span data-ttu-id="2fa74-115">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2fa74-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
