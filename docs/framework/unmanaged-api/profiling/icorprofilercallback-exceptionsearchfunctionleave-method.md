---
title: ICorProfilerCallback::ExceptionSearchFunctionLeave — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionLeave
helpviewer_keywords:
- ExceptionSearchFunctionLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionLeave method [.NET Framework profiling]
ms.assetid: 01de7ac6-0aad-42ef-bf93-50737667b0a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bdea3b0cc5b21cd881fe0ff3e0278444a22d083d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598308"
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="06361-102">ICorProfilerCallback::ExceptionSearchFunctionLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="06361-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>
<span data-ttu-id="06361-103">Powiadamia program profilujący fazy wyszukiwania dla obsługi wyjątków zakończenie funkcji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="06361-103">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06361-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06361-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="06361-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06361-105">Requirements</span></span>  
 <span data-ttu-id="06361-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06361-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06361-107">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="06361-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06361-108">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06361-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06361-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06361-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06361-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06361-110">See also</span></span>

- [<span data-ttu-id="06361-111">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="06361-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="06361-112">ExceptionSearchFunctionEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="06361-112">ExceptionSearchFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)
