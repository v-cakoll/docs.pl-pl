---
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
ms.openlocfilehash: 645c9dd9319dfdf9cb070366d2c389f879e1b1d2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448047"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="e0d0d-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="e0d0d-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="e0d0d-103">Powiadamia profiler, że faza unwind dla obsługi wyjątków zakończyła odwinięcie funkcji.</span><span class="sxs-lookup"><span data-stu-id="e0d0d-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0d0d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0d0d-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e0d0d-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0d0d-105">Remarks</span></span>  
 <span data-ttu-id="e0d0d-106">Po wywołaniu metody `ExceptionUnwindFunctionLeave`, wystąpienie funkcji i jego dane stosu są usuwane ze stosu.</span><span class="sxs-lookup"><span data-stu-id="e0d0d-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="e0d0d-107">Profiler nie powinien blokować tego wywołania, ponieważ stos może nie znajdować się w stanie, który zezwala na wyrzucanie elementów bezużytecznych, a tym samym nie można włączyć przerzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e0d0d-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="e0d0d-108">Jeśli profiler blokuje się w tym miejscu i podjęto próbę wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e0d0d-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="e0d0d-109">Ponadto w trakcie tego wywołania Profiler nie może wywołać kodu zarządzanego lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="e0d0d-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0d0d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0d0d-110">Requirements</span></span>  
 <span data-ttu-id="e0d0d-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0d0d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0d0d-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e0d0d-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e0d0d-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e0d0d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0d0d-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0d0d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0d0d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0d0d-115">See also</span></span>

- [<span data-ttu-id="e0d0d-116">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="e0d0d-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e0d0d-117">ExceptionUnwindFunctionEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="e0d0d-117">ExceptionUnwindFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
