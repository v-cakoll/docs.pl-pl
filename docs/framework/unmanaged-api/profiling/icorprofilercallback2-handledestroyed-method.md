---
title: ICorProfilerCallback2::HandleDestroyed — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleDestroyed
helpviewer_keywords:
- ICorProfilerCallback2::HandleDestroyed method [.NET Framework profiling]
- HandleDestroyed method [.NET Framework profiling]
ms.assetid: ab4f4bbd-40c7-4667-bfde-60cd73803110
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d666b01ae202831df38e0537221e238b9e2bf35e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484410"
---
# <a name="icorprofilercallback2handledestroyed-method"></a><span data-ttu-id="59faa-102">ICorProfilerCallback2::HandleDestroyed — Metoda</span><span class="sxs-lookup"><span data-stu-id="59faa-102">ICorProfilerCallback2::HandleDestroyed Method</span></span>
<span data-ttu-id="59faa-103">Powiadamia program profilujący kodu zniszczono uchwyt kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="59faa-103">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59faa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="59faa-104">Syntax</span></span>  
  
```  
HRESULT HandleDestroyed(  
    [in] GCHandleID handleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59faa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="59faa-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="59faa-106">[in] Identyfikator dojścia do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="59faa-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59faa-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59faa-107">Requirements</span></span>  
 <span data-ttu-id="59faa-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59faa-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59faa-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="59faa-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="59faa-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59faa-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59faa-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59faa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59faa-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59faa-112">See also</span></span>
- [<span data-ttu-id="59faa-113">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="59faa-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="59faa-114">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="59faa-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
