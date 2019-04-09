---
title: ICorProfilerCallback::ExceptionThrown — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9cdbc2234519c0dba1a5004246492e7609ea2b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180495"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="82d7d-102">ICorProfilerCallback::ExceptionThrown — Metoda</span><span class="sxs-lookup"><span data-stu-id="82d7d-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="82d7d-103">Powiadamia program profilujący został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="82d7d-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82d7d-104">Ta funkcja jest wywoływana tylko wtedy, gdy wyjątek osiągnie kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="82d7d-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82d7d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="82d7d-105">Syntax</span></span>  
  
```  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82d7d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="82d7d-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="82d7d-107">[in] Identyfikator obiektu, który spowodował zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="82d7d-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82d7d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82d7d-108">Remarks</span></span>  
 <span data-ttu-id="82d7d-109">Program profilujący nie powinna blokować w jego implementacja tej metody, ponieważ stos może nie być w stanie umożliwiającym wyrzucania elementów bezużytecznych, a w związku z tym nie można włączyć preemptive wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="82d7d-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="82d7d-110">Jeśli program profilujący blokuje tutaj i wyrzucania elementów bezużytecznych jest podejmowana próba, środowisko uruchomieniowe spowoduje zablokowanie, dopóki nie zwróci to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="82d7d-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="82d7d-111">Implementacja tej metody program profilujący nie powinien wywoływać wywołanie kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="82d7d-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82d7d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82d7d-112">Requirements</span></span>  
 <span data-ttu-id="82d7d-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82d7d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82d7d-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="82d7d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82d7d-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82d7d-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="82d7d-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="82d7d-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="82d7d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82d7d-117">See also</span></span>

- [<span data-ttu-id="82d7d-118">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="82d7d-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
