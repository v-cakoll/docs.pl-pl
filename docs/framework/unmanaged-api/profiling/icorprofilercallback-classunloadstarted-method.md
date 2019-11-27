---
title: ICorProfilerCallback::ClassUnloadStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 3b729d3be84571a48cc9a770d7f06b99723c0d1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445067"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="9ec0f-102">ICorProfilerCallback::ClassUnloadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="9ec0f-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="9ec0f-103">Powiadamia profiler o tym, że Klasa jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="9ec0f-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ec0f-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ec0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ec0f-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="9ec0f-106">podczas Identyfikuje klasę, która jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="9ec0f-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ec0f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ec0f-107">Remarks</span></span>  
 <span data-ttu-id="9ec0f-108">Wartość `classId` nie jest prawidłowa dla żądania informacji po powrocie metody `ClassUnloadStarted` — jest to Ostatnia szansa dla profilera do uzyskania informacji o tej klasie.</span><span class="sxs-lookup"><span data-stu-id="9ec0f-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ec0f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ec0f-109">Requirements</span></span>  
 <span data-ttu-id="9ec0f-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ec0f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ec0f-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9ec0f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ec0f-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9ec0f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ec0f-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ec0f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec0f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ec0f-114">See also</span></span>

- [<span data-ttu-id="9ec0f-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ec0f-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9ec0f-116">ClassUnloadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="9ec0f-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
