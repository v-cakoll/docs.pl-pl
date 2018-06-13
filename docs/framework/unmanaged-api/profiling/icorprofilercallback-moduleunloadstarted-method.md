---
title: ICorProfilerCallback::ModuleUnloadStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c509606995a0ddb00a8b586ce8b8cd54b7694cd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452513"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="76391-102">ICorProfilerCallback::ModuleUnloadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="76391-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="76391-103">Powiadamia profilera, że Trwa zwalnianie modułu.</span><span class="sxs-lookup"><span data-stu-id="76391-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76391-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76391-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="76391-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76391-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="76391-106">[in] Identyfikator modułu, w którym jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="76391-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76391-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76391-107">Remarks</span></span>  
 <span data-ttu-id="76391-108">Wartość `moduleId` jest nieprawidłowa dla żądania informacji po `ModuleUnloadStarted` metoda zwraca — jest to profilera ostatnia możliwość uzyskania informacji na temat tego modułu.</span><span class="sxs-lookup"><span data-stu-id="76391-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76391-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76391-109">Requirements</span></span>  
 <span data-ttu-id="76391-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76391-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76391-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="76391-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="76391-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76391-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76391-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76391-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76391-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76391-114">See Also</span></span>  
 [<span data-ttu-id="76391-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="76391-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="76391-116">ModuleUnloadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="76391-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
