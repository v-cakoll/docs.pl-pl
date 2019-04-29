---
title: ICorProfilerCallback::ExceptionCatcherEnter — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9b47e1d1bfa1d8f6c970e95fe25f62a690d3b91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598211"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="c94b8-102">ICorProfilerCallback::ExceptionCatcherEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="c94b8-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="c94b8-103">Powiadamia program profilujący, że formant jest przekazywany do odpowiedniego `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="c94b8-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c94b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c94b8-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c94b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c94b8-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c94b8-106">[in] Identyfikator funkcji zawierającego `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="c94b8-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="c94b8-107">[in] Identyfikator obsługiwanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c94b8-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c94b8-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c94b8-108">Remarks</span></span>  
 <span data-ttu-id="c94b8-109">`ExceptionCatcherEnter` Metoda jest wywoływana tylko wtedy, gdy punkt catch w kodzie skompilowanym za pomocą kompilatora just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="c94b8-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="c94b8-110">Wyjątek, który zostanie przechwycony w niezarządzanym kodzie lub w kodzie wewnętrznego środowiska uruchomieniowego nie wywoła to powiadomienie.</span><span class="sxs-lookup"><span data-stu-id="c94b8-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="c94b8-111">`objectId` Wartość jest przekazywana ponownie, ponieważ wyrzucania elementów bezużytecznych można przenieść obiektu, ponieważ `ExceptionThrown` powiadomień.</span><span class="sxs-lookup"><span data-stu-id="c94b8-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="c94b8-112">Program profilujący nie powinna blokować w jego implementacja tej metody, ponieważ stos może nie być w stanie umożliwiającym wyrzucania elementów bezużytecznych, a w związku z tym nie można włączyć preemptive wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c94b8-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="c94b8-113">Jeśli program profilujący blokuje tutaj i wyrzucania elementów bezużytecznych jest podejmowana próba, środowisko uruchomieniowe spowoduje zablokowanie, dopóki nie zwróci to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="c94b8-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="c94b8-114">Implementacja tej metody program profilujący nie powinien wywoływać wywołanie kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="c94b8-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c94b8-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c94b8-115">Requirements</span></span>  
 <span data-ttu-id="c94b8-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c94b8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c94b8-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c94b8-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c94b8-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c94b8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c94b8-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c94b8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c94b8-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c94b8-120">See also</span></span>

- [<span data-ttu-id="c94b8-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="c94b8-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="c94b8-122">ExceptionCatcherLeave, metoda</span><span class="sxs-lookup"><span data-stu-id="c94b8-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
