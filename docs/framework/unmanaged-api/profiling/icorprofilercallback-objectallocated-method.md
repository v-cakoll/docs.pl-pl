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
ms.openlocfilehash: 9a402b7dfc3ece9d38994ed897162fe0d81ff0b9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503305"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="d96ee-102">ICorProfilerCallback::ObjectAllocated — Metoda</span><span class="sxs-lookup"><span data-stu-id="d96ee-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="d96ee-103">Powiadamia program profilujący, że pamięć w stercie została przypisana dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="d96ee-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d96ee-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d96ee-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d96ee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d96ee-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="d96ee-106">podczas Identyfikator obiektu, dla którego przydzielono pamięć.</span><span class="sxs-lookup"><span data-stu-id="d96ee-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="d96ee-107">podczas Identyfikator klasy, której obiekt jest wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="d96ee-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d96ee-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d96ee-108">Remarks</span></span>  
 <span data-ttu-id="d96ee-109">`ObjectedAllocated`Metoda nie jest wywoływana dla alokacji z pamięci stosu lub niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="d96ee-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="d96ee-110">`classId`Parametr może odwoływać się do klasy w zarządzanym kodzie, który nie został jeszcze załadowany.</span><span class="sxs-lookup"><span data-stu-id="d96ee-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="d96ee-111">Profiler otrzyma wywołanie zwrotne ładowania klasy dla tej klasy bezpośrednio po `ObjectAllocated` wywołaniu zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="d96ee-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d96ee-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d96ee-112">Requirements</span></span>  
 <span data-ttu-id="d96ee-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d96ee-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d96ee-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d96ee-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d96ee-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d96ee-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d96ee-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d96ee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d96ee-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d96ee-117">See also</span></span>

- [<span data-ttu-id="d96ee-118">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d96ee-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d96ee-119">ClassLoadStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="d96ee-119">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="d96ee-120">ClassLoadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="d96ee-120">ClassLoadFinished Method</span></span>](icorprofilercallback-classloadfinished-method.md)
