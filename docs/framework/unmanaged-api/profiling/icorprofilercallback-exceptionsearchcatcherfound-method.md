---
title: ICorProfilerCallback::ExceptionSearchCatcherFound — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4dc6b66aff34bae869737591040e5fc1e552834
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499670"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="ffd7e-102">ICorProfilerCallback::ExceptionSearchCatcherFound — Metoda</span><span class="sxs-lookup"><span data-stu-id="ffd7e-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="ffd7e-103">Powiadamia program profilujący, że faza wyszukiwania dla obsługi wyjątków znajduje się program obsługi wyjątku, który został zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="ffd7e-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffd7e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffd7e-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffd7e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffd7e-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ffd7e-106">[in] Identyfikator funkcji, która zawiera program obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="ffd7e-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffd7e-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ffd7e-107">Requirements</span></span>  
 <span data-ttu-id="ffd7e-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffd7e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffd7e-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ffd7e-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ffd7e-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffd7e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffd7e-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffd7e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffd7e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffd7e-112">See also</span></span>
- [<span data-ttu-id="ffd7e-113">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ffd7e-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
