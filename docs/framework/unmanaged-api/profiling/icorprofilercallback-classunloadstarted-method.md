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
ms.openlocfilehash: 75fb92be078c40f49ddcdc6662535b2a0be7a6ad
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866562"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="8e80f-102">ICorProfilerCallback::ClassUnloadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="8e80f-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="8e80f-103">Powiadamia profiler o tym, że Klasa jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="8e80f-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e80f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e80f-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e80f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e80f-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="8e80f-106">\[in] określa klasę, która jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="8e80f-106">\[in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="8e80f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e80f-107">Remarks</span></span>  
 <span data-ttu-id="8e80f-108">Wartość `classId` nie jest prawidłowa dla żądania informacji po powrocie metody `ClassUnloadStarted` — jest to Ostatnia szansa dla profilera do uzyskania informacji o tej klasie.</span><span class="sxs-lookup"><span data-stu-id="8e80f-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e80f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e80f-109">Requirements</span></span>  
 <span data-ttu-id="8e80f-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e80f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e80f-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8e80f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8e80f-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8e80f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e80f-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e80f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e80f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e80f-114">See also</span></span>

- [<span data-ttu-id="8e80f-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e80f-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8e80f-116">ClassUnloadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="8e80f-116">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
