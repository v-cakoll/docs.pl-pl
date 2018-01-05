---
title: "ICorProfilerCallback::ExceptionSearchCatcherFound — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionSearchCatcherFound
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc226b6102c50b118a4b13f9cd25700dd1ca7301
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="e8ec1-102">ICorProfilerCallback::ExceptionSearchCatcherFound — Metoda</span><span class="sxs-lookup"><span data-stu-id="e8ec1-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="e8ec1-103">Powiadamia profilera, że fazy wyszukiwania obsługi wyjątków ma się program obsługi wyjątku, który został zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="e8ec1-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8ec1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8ec1-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8ec1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8ec1-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e8ec1-106">[in] Identyfikator funkcji, który zawiera program obsługi wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e8ec1-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8ec1-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8ec1-107">Requirements</span></span>  
 <span data-ttu-id="e8ec1-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8ec1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8ec1-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e8ec1-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8ec1-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8ec1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8ec1-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8ec1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ec1-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8ec1-112">See Also</span></span>  
 [<span data-ttu-id="e8ec1-113">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8ec1-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
