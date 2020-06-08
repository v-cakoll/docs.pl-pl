---
title: ICorProfilerCallback::ClassLoadStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: 9a9fdc80c8f63dd5b004953266a5d7399655bc71
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500367"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="1eecb-102">ICorProfilerCallback::ClassLoadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="1eecb-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="1eecb-103">Powiadamia program profilujący, że Klasa jest ładowana.</span><span class="sxs-lookup"><span data-stu-id="1eecb-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eecb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1eecb-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1eecb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1eecb-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="1eecb-106">\[w] identyfikuje klasę, która jest ładowana.</span><span class="sxs-lookup"><span data-stu-id="1eecb-106">\[in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="1eecb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1eecb-107">Remarks</span></span>  
 <span data-ttu-id="1eecb-108">Wartość `classId` nie jest prawidłowa dla żądania informacji, dopóki nie zostanie wywołana metoda [ICorProfilerCallback:: ClassLoadFinished —](icorprofilercallback-classloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1eecb-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1eecb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1eecb-109">Requirements</span></span>  
 <span data-ttu-id="1eecb-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1eecb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1eecb-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1eecb-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1eecb-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1eecb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1eecb-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1eecb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eecb-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1eecb-114">See also</span></span>

- [<span data-ttu-id="1eecb-115">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1eecb-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
