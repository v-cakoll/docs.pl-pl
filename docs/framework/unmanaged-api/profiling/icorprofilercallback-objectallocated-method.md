---
title: ICorProfilerCallback::ObjectAllocated — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10a000fd98ad12dc39f8f8338485d6bb4093ee07
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782985"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="9a7a7-102">ICorProfilerCallback::ObjectAllocated — Metoda</span><span class="sxs-lookup"><span data-stu-id="9a7a7-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="9a7a7-103">Powiadamia program profilujący, która została przydzielona pamięci w stercie dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="9a7a7-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a7a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a7a7-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a7a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a7a7-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="9a7a7-106">[in] Identyfikator obiektu, dla którego pamięć została alokowana.</span><span class="sxs-lookup"><span data-stu-id="9a7a7-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="9a7a7-107">[in] Identyfikator klasy, którego wystąpienie jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="9a7a7-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a7a7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a7a7-108">Remarks</span></span>  
 <span data-ttu-id="9a7a7-109">`ObjectedAllocated` Metoda nie jest wywoływana dla alokacji stosu lub niezarządzanej pamięci.</span><span class="sxs-lookup"><span data-stu-id="9a7a7-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="9a7a7-110">`classId` Parametru może odwoływać się do klasy w kodzie zarządzanym, który nie został jeszcze załadowany.</span><span class="sxs-lookup"><span data-stu-id="9a7a7-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="9a7a7-111">Program profilujący otrzyma wywołanie zwrotne obciążenia klasy dla klasy natychmiast po `ObjectAllocated` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="9a7a7-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a7a7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a7a7-112">Requirements</span></span>  
 <span data-ttu-id="9a7a7-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a7a7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a7a7-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9a7a7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9a7a7-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a7a7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a7a7-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a7a7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a7a7-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a7a7-117">See also</span></span>

- [<span data-ttu-id="9a7a7-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a7a7-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9a7a7-119">ClassLoadStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="9a7a7-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="9a7a7-120">ClassLoadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="9a7a7-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
