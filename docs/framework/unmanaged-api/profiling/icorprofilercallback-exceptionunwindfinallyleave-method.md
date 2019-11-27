---
title: ICorProfilerCallback::ExceptionUnwindFinallyLeave — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
ms.openlocfilehash: b6ef54297b69892f07df1aa92a92600fb20756e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445305"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="de606-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="de606-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="de606-103">Powiadamia profiler, że faza unwind dla obsługi wyjątków opuściła klauzulę `finally`.</span><span class="sxs-lookup"><span data-stu-id="de606-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de606-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de606-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="de606-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de606-105">Remarks</span></span>  
 <span data-ttu-id="de606-106">Profiler nie powinien blokować tego wywołania, ponieważ stos może nie znajdować się w stanie, który zezwala na wyrzucanie elementów bezużytecznych, a tym samym nie można włączyć przerzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="de606-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="de606-107">Jeśli profiler blokuje się w tym miejscu i podjęto próbę wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="de606-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="de606-108">Ponadto w trakcie tego wywołania Profiler nie może wywołać kodu zarządzanego lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="de606-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de606-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de606-109">Requirements</span></span>  
 <span data-ttu-id="de606-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de606-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de606-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="de606-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="de606-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="de606-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de606-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de606-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de606-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de606-114">See also</span></span>

- [<span data-ttu-id="de606-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="de606-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="de606-116">ExceptionUnwindFinallyEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="de606-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
