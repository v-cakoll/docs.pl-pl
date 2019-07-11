---
title: ICorProfilerCallback::ExceptionUnwindFunctionEnter — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85f788ec61cc441e7271fb7a8aba843f37d20a57
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782725"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="43b3e-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="43b3e-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="43b3e-103">Powiadamia program profilujący, że na odpoczynek, funkcja rozpoczął fazy unwind dla obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="43b3e-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43b3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43b3e-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43b3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="43b3e-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="43b3e-106">[in] Identyfikator funkcji, która jest on odwinięty.</span><span class="sxs-lookup"><span data-stu-id="43b3e-106">[in] The ID of the function that is being unwound.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43b3e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43b3e-107">Remarks</span></span>  
 <span data-ttu-id="43b3e-108">Program profilujący nie powinna blokować w jego implementacja tej metody, ponieważ stos może nie być w stanie umożliwiającym wyrzucania elementów bezużytecznych, a w związku z tym nie można włączyć preemptive wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="43b3e-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="43b3e-109">Jeśli program profilujący blokuje tutaj i wyrzucania elementów bezużytecznych jest podejmowana próba, środowisko uruchomieniowe spowoduje zablokowanie, dopóki nie zwróci to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="43b3e-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="43b3e-110">Implementacja tej metody program profilujący nie powinien wywoływać wywołanie kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="43b3e-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43b3e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43b3e-111">Requirements</span></span>  
 <span data-ttu-id="43b3e-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43b3e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43b3e-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="43b3e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="43b3e-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43b3e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43b3e-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43b3e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b3e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43b3e-116">See also</span></span>

- [<span data-ttu-id="43b3e-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="43b3e-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="43b3e-118">ExceptionUnwindFunctionLeave, metoda</span><span class="sxs-lookup"><span data-stu-id="43b3e-118">ExceptionUnwindFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)
