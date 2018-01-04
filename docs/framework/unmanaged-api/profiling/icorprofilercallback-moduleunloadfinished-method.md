---
title: "ICorProfilerCallback::ModuleUnloadFinished — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f9f048d60d2d463e3d846fadda91932a9a2a091
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="cd1a7-102">ICorProfilerCallback::ModuleUnloadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="cd1a7-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="cd1a7-103">Powiadamia profilera modułu zakończenie zwalnianie.</span><span class="sxs-lookup"><span data-stu-id="cd1a7-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd1a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd1a7-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd1a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd1a7-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="cd1a7-106">[in] Identyfikator modułu, który został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="cd1a7-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="cd1a7-107">[in] HRESULT, która wskazuje, czy moduł został pomyślnie usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="cd1a7-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd1a7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd1a7-108">Remarks</span></span>  
 <span data-ttu-id="cd1a7-109">Wartość `moduleId` jest nieprawidłowa dla żądania informacji po [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) zwraca metody.</span><span class="sxs-lookup"><span data-stu-id="cd1a7-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="cd1a7-110">Niektóre elementy zwalnianie klasy mogą nadal po `ModuleUnloadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="cd1a7-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="cd1a7-111">Błąd HRESULT w `hrStatus` oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="cd1a7-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="cd1a7-112">Jednak Powodzenie HRESULT w `hrStatus` tylko wskazuje, że pierwsza część zwalnianie modułu zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cd1a7-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd1a7-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd1a7-113">Requirements</span></span>  
 <span data-ttu-id="cd1a7-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd1a7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd1a7-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd1a7-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd1a7-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd1a7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd1a7-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd1a7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd1a7-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd1a7-118">See Also</span></span>  
 [<span data-ttu-id="cd1a7-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd1a7-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
