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
ms.openlocfilehash: 9c9cd0b042dc22f35c38e349ab8881dafc602731
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445013"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="8efee-102">ICorProfilerCallback::ExceptionCatcherEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="8efee-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="8efee-103">Powiadamia profiler, że sterowanie jest przesyłane do odpowiedniego bloku `catch`.</span><span class="sxs-lookup"><span data-stu-id="8efee-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8efee-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8efee-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8efee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8efee-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="8efee-106">podczas Identyfikator funkcji zawierającej blok `catch`.</span><span class="sxs-lookup"><span data-stu-id="8efee-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="8efee-107">podczas Identyfikator obsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8efee-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8efee-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8efee-108">Remarks</span></span>  
 <span data-ttu-id="8efee-109">Metoda `ExceptionCatcherEnter` jest wywoływana tylko wtedy, gdy punkt catch jest w kodzie skompilowanym za pomocą kompilatora just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="8efee-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="8efee-110">Wyjątek przechwytywany w kodzie niezarządzanym lub w kodzie wewnętrznym środowiska uruchomieniowego nie wywoła tego powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="8efee-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="8efee-111">Wartość `objectId` jest przenoszona ponownie, ponieważ wyrzucanie elementów bezużytecznych mogło przenieść obiekt od momentu powiadomienia `ExceptionThrown`.</span><span class="sxs-lookup"><span data-stu-id="8efee-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="8efee-112">Profiler nie powinien blokować swojej implementacji tej metody, ponieważ stos może nie znajdować się w stanie, który zezwala na wyrzucanie elementów bezużytecznych i dlatego nie można włączyć zastępujący elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="8efee-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="8efee-113">Jeśli profiler blokuje tutaj i zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8efee-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="8efee-114">Implementacja profilera nie powinna być wywoływana w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="8efee-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8efee-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8efee-115">Requirements</span></span>  
 <span data-ttu-id="8efee-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8efee-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8efee-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8efee-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8efee-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8efee-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8efee-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8efee-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8efee-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8efee-120">See also</span></span>

- [<span data-ttu-id="8efee-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="8efee-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="8efee-122">ExceptionCatcherLeave, metoda</span><span class="sxs-lookup"><span data-stu-id="8efee-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
