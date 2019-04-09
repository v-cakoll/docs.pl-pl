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
ms.openlocfilehash: f7f1b2756dd180cb0a701429978a34ea80447a86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107643"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="0b170-102">ICorProfilerCallback::ExceptionCatcherLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b170-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="0b170-103">Powiadamia program profilujący, że kontrola jest przekazywana poza odpowiednie `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="0b170-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b170-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b170-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0b170-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b170-105">Remarks</span></span>  
 <span data-ttu-id="0b170-106">Program profilujący nie powinna blokować w jego implementacja tej metody, ponieważ stos może nie być w stanie umożliwiającym wyrzucania elementów bezużytecznych, a w związku z tym nie można włączyć preemptive wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0b170-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="0b170-107">Jeśli program profilujący blokuje tutaj i wyrzucania elementów bezużytecznych jest podejmowana próba, środowisko uruchomieniowe spowoduje zablokowanie, dopóki nie zwróci to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="0b170-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="0b170-108">Implementacja tej metody program profilujący nie powinien wywoływać wywołanie kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="0b170-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b170-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b170-109">Requirements</span></span>  
 <span data-ttu-id="0b170-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b170-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b170-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0b170-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0b170-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b170-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0b170-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0b170-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0b170-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b170-114">See also</span></span>

- [<span data-ttu-id="0b170-115">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0b170-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="0b170-116">ExceptionCatcherEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="0b170-116">ExceptionCatcherEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)
