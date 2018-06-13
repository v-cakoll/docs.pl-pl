---
title: ICorProfilerCallback::ModuleLoadFinished — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14f918a312031359043076be0b739f9b7e0e9f2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451646"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="1be2a-102">ICorProfilerCallback::ModuleLoadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="1be2a-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="1be2a-103">Powiadamia profilera zakończenie moduł ładowania.</span><span class="sxs-lookup"><span data-stu-id="1be2a-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1be2a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1be2a-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1be2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1be2a-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="1be2a-106">[in] Identyfikator modułu, w którym została załadowana.</span><span class="sxs-lookup"><span data-stu-id="1be2a-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="1be2a-107">[in] HRESULT, która wskazuje, czy moduł został załadowany pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1be2a-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1be2a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1be2a-108">Remarks</span></span>  
 <span data-ttu-id="1be2a-109">Wartość `moduleId` jest nieprawidłowa dla żądania informacji do `ModuleLoadFinished` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="1be2a-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="1be2a-110">Niektóre elementy podczas ładowania modułu może nadal po `ModuleLoadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1be2a-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="1be2a-111">Błąd HRESULT w `hrStatus` oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="1be2a-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="1be2a-112">Jednak Powodzenie HRESULT w `hrStatus` tylko wskazuje, że pierwsza część podczas ładowania modułu zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1be2a-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1be2a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1be2a-113">Requirements</span></span>  
 <span data-ttu-id="1be2a-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1be2a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1be2a-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1be2a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1be2a-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1be2a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1be2a-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1be2a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1be2a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1be2a-118">See Also</span></span>  
 [<span data-ttu-id="1be2a-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="1be2a-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="1be2a-120">ModuleLoadStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="1be2a-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
