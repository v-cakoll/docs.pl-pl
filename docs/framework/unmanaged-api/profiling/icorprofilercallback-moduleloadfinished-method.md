---
title: "ICorProfilerCallback::ModuleLoadFinished — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 360c14ccdd67cb7609ffe2f9c49914fdda163389
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="ffa91-102">ICorProfilerCallback::ModuleLoadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="ffa91-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="ffa91-103">Powiadamia profilera zakończenie moduł ładowania.</span><span class="sxs-lookup"><span data-stu-id="ffa91-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffa91-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffa91-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffa91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffa91-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="ffa91-106">[in] Identyfikator modułu, w którym została załadowana.</span><span class="sxs-lookup"><span data-stu-id="ffa91-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="ffa91-107">[in] HRESULT, która wskazuje, czy moduł został załadowany pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ffa91-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffa91-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ffa91-108">Remarks</span></span>  
 <span data-ttu-id="ffa91-109">Wartość `moduleId` jest nieprawidłowa dla żądania informacji do `ModuleLoadFinished` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="ffa91-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="ffa91-110">Niektóre elementy podczas ładowania modułu może nadal po `ModuleLoadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ffa91-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="ffa91-111">Błąd HRESULT w `hrStatus` oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="ffa91-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="ffa91-112">Jednak Powodzenie HRESULT w `hrStatus` tylko wskazuje, że pierwsza część podczas ładowania modułu zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ffa91-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffa91-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ffa91-113">Requirements</span></span>  
 <span data-ttu-id="ffa91-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffa91-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffa91-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ffa91-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ffa91-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffa91-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffa91-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffa91-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa91-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ffa91-118">See Also</span></span>  
 [<span data-ttu-id="ffa91-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ffa91-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="ffa91-120">ModuleLoadStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="ffa91-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
