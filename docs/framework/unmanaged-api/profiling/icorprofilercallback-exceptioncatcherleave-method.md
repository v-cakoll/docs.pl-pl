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
ms.openlocfilehash: f4f6f5dd757fde9d49fe8b5a1709d6d5876ce5b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592211"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="54d1d-102">ICorProfilerCallback::ExceptionCatcherLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="54d1d-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="54d1d-103">Powiadamia program profilujący, że kontrola jest przekazywana poza odpowiednie `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="54d1d-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54d1d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54d1d-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="54d1d-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54d1d-105">Remarks</span></span>  
 <span data-ttu-id="54d1d-106">Program profilujący nie powinna blokować w jego implementacja tej metody, ponieważ stos może nie być w stanie umożliwiającym wyrzucania elementów bezużytecznych, a w związku z tym nie można włączyć preemptive wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="54d1d-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="54d1d-107">Jeśli program profilujący blokuje tutaj i wyrzucania elementów bezużytecznych jest podejmowana próba, środowisko uruchomieniowe spowoduje zablokowanie, dopóki nie zwróci to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="54d1d-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="54d1d-108">Implementacja tej metody program profilujący nie powinien wywoływać wywołanie kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="54d1d-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54d1d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54d1d-109">Requirements</span></span>  
 <span data-ttu-id="54d1d-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54d1d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54d1d-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="54d1d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="54d1d-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54d1d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54d1d-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54d1d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d1d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54d1d-114">See also</span></span>
- [<span data-ttu-id="54d1d-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="54d1d-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="54d1d-116">ExceptionCatcherEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="54d1d-116">ExceptionCatcherEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)
