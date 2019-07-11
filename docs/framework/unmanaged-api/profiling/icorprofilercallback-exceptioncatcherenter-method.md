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
ms.openlocfilehash: 6a90ae67a7d264273bd0e07a42aa6195122a06ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776143"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="221b5-102">ICorProfilerCallback::ExceptionCatcherEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="221b5-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="221b5-103">Powiadamia program profilujący, że formant jest przekazywany do odpowiedniego `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="221b5-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="221b5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="221b5-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="221b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="221b5-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="221b5-106">[in] Identyfikator funkcji zawierającego `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="221b5-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="221b5-107">[in] Identyfikator obsługiwanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="221b5-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="221b5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="221b5-108">Remarks</span></span>  
 <span data-ttu-id="221b5-109">`ExceptionCatcherEnter` Metoda jest wywoływana tylko wtedy, gdy punkt catch w kodzie skompilowanym za pomocą kompilatora just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="221b5-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="221b5-110">Wyjątek, który zostanie przechwycony w niezarządzanym kodzie lub w kodzie wewnętrznego środowiska uruchomieniowego nie wywoła to powiadomienie.</span><span class="sxs-lookup"><span data-stu-id="221b5-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="221b5-111">`objectId` Wartość jest przekazywana ponownie, ponieważ wyrzucania elementów bezużytecznych można przenieść obiektu, ponieważ `ExceptionThrown` powiadomień.</span><span class="sxs-lookup"><span data-stu-id="221b5-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="221b5-112">Program profilujący nie powinna blokować w jego implementacja tej metody, ponieważ stos może nie być w stanie umożliwiającym wyrzucania elementów bezużytecznych, a w związku z tym nie można włączyć preemptive wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="221b5-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="221b5-113">Jeśli program profilujący blokuje tutaj i wyrzucania elementów bezużytecznych jest podejmowana próba, środowisko uruchomieniowe spowoduje zablokowanie, dopóki nie zwróci to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="221b5-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="221b5-114">Implementacja tej metody program profilujący nie powinien wywoływać wywołanie kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="221b5-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="221b5-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="221b5-115">Requirements</span></span>  
 <span data-ttu-id="221b5-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="221b5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="221b5-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="221b5-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="221b5-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="221b5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="221b5-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="221b5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="221b5-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="221b5-120">See also</span></span>

- [<span data-ttu-id="221b5-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="221b5-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="221b5-122">ExceptionCatcherLeave, metoda</span><span class="sxs-lookup"><span data-stu-id="221b5-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
