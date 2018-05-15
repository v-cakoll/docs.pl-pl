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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e28aef4916d06218953236e3b29e19c68822bd6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="457c0-102">ICorProfilerCallback::FunctionUnloadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="457c0-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="457c0-103">Powiadamia profilera, czy można zwolnić funkcja została uruchomiona środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="457c0-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="457c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="457c0-104">Syntax</span></span>  
  
```  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="457c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="457c0-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="457c0-106">[in] Identyfikator funkcji, która jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="457c0-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="457c0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="457c0-107">Remarks</span></span>  
 <span data-ttu-id="457c0-108">Wartość `functionId` parametru nie jest już prawidłowe po powrocie z tej metody do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="457c0-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="457c0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="457c0-109">Requirements</span></span>  
 <span data-ttu-id="457c0-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="457c0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="457c0-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="457c0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="457c0-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="457c0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="457c0-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="457c0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="457c0-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="457c0-114">See Also</span></span>  
 [<span data-ttu-id="457c0-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="457c0-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
