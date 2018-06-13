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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ea53e02cc20964a43bc4784b4354d429e238295
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450859"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="23201-102">ICorProfilerCallback::ExceptionCatcherLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="23201-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="23201-103">Powiadamia profilera, że formant jest przekazywany z odpowiednią `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="23201-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23201-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23201-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="23201-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23201-105">Remarks</span></span>  
 <span data-ttu-id="23201-106">Profilera nie należy zablokować w jej implementacja tej metody, ponieważ stos nie może być w stanie, który umożliwia odzyskiwanie pamięci i dlatego nie można włączyć cenią sobie wcześniejsze wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="23201-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="23201-107">Jeśli profilera blokuje tutaj i nastąpiła wyrzucanie elementów bezużytecznych, środowisko uruchomieniowe zablokuje dopóki zwraca tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="23201-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="23201-108">Profiler implementacja tej metody nie powinny wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="23201-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23201-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23201-109">Requirements</span></span>  
 <span data-ttu-id="23201-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23201-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23201-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="23201-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="23201-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23201-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23201-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23201-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23201-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23201-114">See Also</span></span>  
 [<span data-ttu-id="23201-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="23201-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="23201-116">ExceptionCatcherEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="23201-116">ExceptionCatcherEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)
