---
title: ICorProfilerCallback2::HandleCreated — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
ms.openlocfilehash: 0c25a5cad01ef0eb268e90c38bd24d638b6f8cc4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865769"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="df66c-102">ICorProfilerCallback2::HandleCreated — Metoda</span><span class="sxs-lookup"><span data-stu-id="df66c-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="df66c-103">Powiadamia profiler kodu o utworzeniu dojścia do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="df66c-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df66c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df66c-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df66c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df66c-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="df66c-106">podczas Identyfikator dojścia do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="df66c-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="df66c-107">podczas Identyfikator obiektu, dla którego utworzono dojście do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="df66c-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df66c-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df66c-108">Requirements</span></span>  
 <span data-ttu-id="df66c-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df66c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df66c-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="df66c-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="df66c-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="df66c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df66c-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df66c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df66c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df66c-113">See also</span></span>

- [<span data-ttu-id="df66c-114">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="df66c-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="df66c-115">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="df66c-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
