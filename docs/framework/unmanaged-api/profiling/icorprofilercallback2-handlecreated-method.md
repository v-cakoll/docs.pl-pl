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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d5ea547066663564d76008434884b6e34150efb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779324"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="7ffe6-102">ICorProfilerCallback2::HandleCreated — Metoda</span><span class="sxs-lookup"><span data-stu-id="7ffe6-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="7ffe6-103">Powiadamia program profilujący kodu utworzono uchwyt kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="7ffe6-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ffe6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ffe6-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ffe6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ffe6-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="7ffe6-106">[in] Identyfikator dojścia do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7ffe6-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="7ffe6-107">[in] Identyfikator obiektu, dla którego utworzono dojście kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="7ffe6-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ffe6-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ffe6-108">Requirements</span></span>  
 <span data-ttu-id="7ffe6-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ffe6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ffe6-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7ffe6-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7ffe6-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ffe6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ffe6-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ffe6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ffe6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ffe6-113">See also</span></span>

- [<span data-ttu-id="7ffe6-114">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ffe6-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7ffe6-115">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ffe6-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
