---
title: "ICorProfilerCallback::ExceptionSearchFunctionEnter — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d410d6ef47dfb0ad33c2a6a03f80d05810182a3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="263f3-102">ICorProfilerCallback::ExceptionSearchFunctionEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="263f3-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="263f3-103">Powiadamia profilera fazy wyszukiwania obsługi wyjątków zostało uruchomione, wyszukiwanie funkcji można znaleźć programu obsługi dla bieżącego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="263f3-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="263f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="263f3-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="263f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="263f3-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="263f3-106">[in] Identyfikator funkcji, która została wprowadzona.</span><span class="sxs-lookup"><span data-stu-id="263f3-106">[in] The ID of the function that has been entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="263f3-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="263f3-107">Requirements</span></span>  
 <span data-ttu-id="263f3-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="263f3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="263f3-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="263f3-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="263f3-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="263f3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="263f3-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="263f3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="263f3-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="263f3-112">See Also</span></span>  
 [<span data-ttu-id="263f3-113">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="263f3-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="263f3-114">ExceptionSearchFunctionLeave, metoda</span><span class="sxs-lookup"><span data-stu-id="263f3-114">ExceptionSearchFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)
