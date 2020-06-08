---
title: ICorProfilerCallback::ExceptionCatcherLeave — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type:
- apiref
ms.openlocfilehash: cff2dd9fdb05ea4dd160dfa57df6f047beb57f69
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500302"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="f4fc3-102">ICorProfilerCallback::ExceptionCatcherLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="f4fc3-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="f4fc3-103">Powiadamia profiler, że sterowanie jest przesyłane z odpowiedniego `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="f4fc3-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4fc3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4fc3-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f4fc3-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f4fc3-105">Remarks</span></span>  
 <span data-ttu-id="f4fc3-106">Profiler nie powinien blokować swojej implementacji tej metody, ponieważ stos może nie znajdować się w stanie, który zezwala na wyrzucanie elementów bezużytecznych i dlatego nie można włączyć zastępujący elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f4fc3-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="f4fc3-107">Jeśli profiler blokuje tutaj i zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="f4fc3-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="f4fc3-108">Implementacja profilera nie powinna być wywoływana w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="f4fc3-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4fc3-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4fc3-109">Requirements</span></span>  
 <span data-ttu-id="f4fc3-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4fc3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4fc3-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f4fc3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f4fc3-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f4fc3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4fc3-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4fc3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4fc3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4fc3-114">See also</span></span>

- [<span data-ttu-id="f4fc3-115">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f4fc3-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f4fc3-116">ExceptionCatcherEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="f4fc3-116">ExceptionCatcherEnter Method</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)
