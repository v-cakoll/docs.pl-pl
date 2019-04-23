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
ms.openlocfilehash: e41378b314b91f42fca9d1039d3011b5eaafe502
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074303"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="ad6c4-102">ICorProfilerCallback::ExceptionSearchCatcherFound — Metoda</span><span class="sxs-lookup"><span data-stu-id="ad6c4-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="ad6c4-103">Powiadamia program profilujący, że faza wyszukiwania dla obsługi wyjątków znajduje się program obsługi wyjątku, który został zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="ad6c4-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad6c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad6c4-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad6c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad6c4-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ad6c4-106">[in] Identyfikator funkcji, która zawiera program obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="ad6c4-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad6c4-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad6c4-107">Requirements</span></span>  
 <span data-ttu-id="ad6c4-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad6c4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad6c4-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ad6c4-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ad6c4-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad6c4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad6c4-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad6c4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad6c4-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad6c4-112">See also</span></span>

- [<span data-ttu-id="ad6c4-113">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad6c4-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
