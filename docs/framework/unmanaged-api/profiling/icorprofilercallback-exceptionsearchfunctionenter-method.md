---
title: ICorProfilerCallback::ExceptionSearchFunctionEnter — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type:
- apiref
ms.openlocfilehash: 244227aadb50720514f7511be563089d520b4bf5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500198"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="f950f-102">ICorProfilerCallback::ExceptionSearchFunctionEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="f950f-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="f950f-103">Powiadamia program profilujący o rozpoczęciu wyszukiwania funkcji, aby znaleźć procedurę obsługi dla bieżącego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f950f-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f950f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f950f-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f950f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f950f-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="f950f-106">\[in] identyfikator funkcji, która została wprowadzona.</span><span class="sxs-lookup"><span data-stu-id="f950f-106">\[in] The ID of the function that has been entered.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="f950f-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f950f-107">Requirements</span></span>  
 <span data-ttu-id="f950f-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f950f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f950f-109">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f950f-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f950f-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f950f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f950f-111">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f950f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f950f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f950f-112">See also</span></span>

- [<span data-ttu-id="f950f-113">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f950f-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f950f-114">ExceptionSearchFunctionLeave, metoda</span><span class="sxs-lookup"><span data-stu-id="f950f-114">ExceptionSearchFunctionLeave Method</span></span>](icorprofilercallback-exceptionsearchfunctionleave-method.md)
