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
ms.openlocfilehash: 6d20aa04b292fd29b60d68b844ef410258d90d31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546585"
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="e168d-102">ICorProfilerCallback::ExceptionSearchFunctionLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="e168d-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>
<span data-ttu-id="e168d-103">Powiadamia program profilujący fazy wyszukiwania dla obsługi wyjątków zakończenie funkcji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="e168d-103">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e168d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e168d-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="e168d-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e168d-105">Requirements</span></span>  
 <span data-ttu-id="e168d-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e168d-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e168d-107">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e168d-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e168d-108">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e168d-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e168d-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e168d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e168d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e168d-110">See also</span></span>
- [<span data-ttu-id="e168d-111">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="e168d-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e168d-112">ExceptionSearchFunctionEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="e168d-112">ExceptionSearchFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)
