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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d19814b0c663310e977ef148ad37eb74129fd4d2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466508"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="7920d-102">ICorProfilerCallback::ClassLoadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="7920d-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="7920d-103">Powiadamia program profilujący, że klasa jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="7920d-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7920d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7920d-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7920d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7920d-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="7920d-106">[in] Określa klasę, która jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="7920d-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7920d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7920d-107">Remarks</span></span>  
 <span data-ttu-id="7920d-108">Wartość `classId` jest nieprawidłowa dla żądania informacje do momentu [icorprofilercallback::classloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="7920d-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7920d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7920d-109">Requirements</span></span>  
 <span data-ttu-id="7920d-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7920d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7920d-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7920d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7920d-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7920d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7920d-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7920d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7920d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7920d-114">See also</span></span>
- [<span data-ttu-id="7920d-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="7920d-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
