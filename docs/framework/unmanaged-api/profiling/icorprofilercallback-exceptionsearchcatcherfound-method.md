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
ms.openlocfilehash: 2fca83d952e139b0f141dcd75362f31c5235644d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678736"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="e9324-102">ICorProfilerCallback::ExceptionSearchCatcherFound — Metoda</span><span class="sxs-lookup"><span data-stu-id="e9324-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="e9324-103">Powiadamia program profilujący, że faza wyszukiwania dla obsługi wyjątków znajduje się program obsługi wyjątku, który został zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="e9324-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9324-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9324-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9324-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9324-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e9324-106">[in] Identyfikator funkcji, która zawiera program obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="e9324-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9324-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9324-107">Requirements</span></span>  
 <span data-ttu-id="e9324-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9324-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9324-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9324-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9324-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9324-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9324-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9324-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9324-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9324-112">See also</span></span>
- [<span data-ttu-id="e9324-113">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="e9324-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
