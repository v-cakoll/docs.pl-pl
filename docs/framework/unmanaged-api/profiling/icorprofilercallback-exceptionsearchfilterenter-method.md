---
title: ICorProfilerCallback::ExceptionSearchFilterEnter — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type:
- apiref
ms.openlocfilehash: 65765795c13948175a7eb5bd78843968d55953d8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445383"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="377f8-102">ICorProfilerCallback::ExceptionSearchFilterEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="377f8-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="377f8-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span><span class="sxs-lookup"><span data-stu-id="377f8-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="377f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="377f8-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="377f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="377f8-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="377f8-106">[in] The ID of the function that contains the filter.</span><span class="sxs-lookup"><span data-stu-id="377f8-106">[in] The ID of the function that contains the filter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="377f8-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="377f8-107">Requirements</span></span>  
 <span data-ttu-id="377f8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="377f8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="377f8-109">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="377f8-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="377f8-110">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="377f8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="377f8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="377f8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="377f8-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="377f8-112">See also</span></span>

- [<span data-ttu-id="377f8-113">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="377f8-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="377f8-114">ExceptionSearchFilterLeave, metoda</span><span class="sxs-lookup"><span data-stu-id="377f8-114">ExceptionSearchFilterLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)
