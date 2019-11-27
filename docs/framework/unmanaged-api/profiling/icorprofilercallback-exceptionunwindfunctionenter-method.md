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
ms.openlocfilehash: 3f6320d6d962e40acf494acbb5c95adda62d1461
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445290"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="eb434-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="eb434-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="eb434-103">Powiadamia program profilujący, że faza unwind w obsłudze wyjątków rozpoczęła funkcję unwind.</span><span class="sxs-lookup"><span data-stu-id="eb434-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb434-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb434-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb434-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb434-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="eb434-106">podczas Identyfikator funkcji, która jest usuwana.</span><span class="sxs-lookup"><span data-stu-id="eb434-106">[in] The ID of the function that is being unwound.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb434-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb434-107">Remarks</span></span>  
 <span data-ttu-id="eb434-108">Profiler nie powinien blokować swojej implementacji tej metody, ponieważ stos może nie znajdować się w stanie, który zezwala na wyrzucanie elementów bezużytecznych i dlatego nie można włączyć zastępujący elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="eb434-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="eb434-109">Jeśli profiler blokuje tutaj i zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="eb434-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="eb434-110">Implementacja profilera nie powinna być wywoływana w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="eb434-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb434-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb434-111">Requirements</span></span>  
 <span data-ttu-id="eb434-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb434-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb434-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eb434-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb434-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="eb434-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb434-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb434-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb434-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb434-116">See also</span></span>

- [<span data-ttu-id="eb434-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb434-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="eb434-118">ExceptionUnwindFunctionLeave, metoda</span><span class="sxs-lookup"><span data-stu-id="eb434-118">ExceptionUnwindFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)
