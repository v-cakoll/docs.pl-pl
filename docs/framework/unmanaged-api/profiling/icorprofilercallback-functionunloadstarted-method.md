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
ms.openlocfilehash: c1c1c9a15e9f56765710ffb2015a29b4206b3bd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597301"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="d6068-102">ICorProfilerCallback::FunctionUnloadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="d6068-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="d6068-103">Powiadamia program profilujący uruchomienia wyładować funkcji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d6068-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6068-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6068-104">Syntax</span></span>  
  
```  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="d6068-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6068-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d6068-106">[in] Identyfikator funkcji, która jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="d6068-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6068-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6068-107">Remarks</span></span>  
 <span data-ttu-id="d6068-108">Wartość `functionId` parametr nie jest już prawidłowa po powrocie z tej metody do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="d6068-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6068-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6068-109">Requirements</span></span>  
 <span data-ttu-id="d6068-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6068-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6068-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d6068-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6068-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6068-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6068-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6068-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6068-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6068-114">See also</span></span>

- [<span data-ttu-id="d6068-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d6068-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
