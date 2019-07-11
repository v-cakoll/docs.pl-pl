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
ms.openlocfilehash: c99ddc66cca0a0d0083cfa19cfca34a1e557d4e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769150"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="94859-102">ICorProfilerCallback::ModuleUnloadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="94859-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="94859-103">Powiadamia program profilujący, że Trwa zwalnianie modułu.</span><span class="sxs-lookup"><span data-stu-id="94859-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94859-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94859-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="94859-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94859-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="94859-106">[in] Identyfikator modułu, który jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="94859-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94859-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94859-107">Remarks</span></span>  
 <span data-ttu-id="94859-108">Wartość `moduleId` jest nieprawidłowa dla żądania informacji po `ModuleUnloadStarted` metoda zwraca — jest to programu profilującego ostatniego masz szansę, aby uzyskać informacje na temat tego modułu.</span><span class="sxs-lookup"><span data-stu-id="94859-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94859-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94859-109">Requirements</span></span>  
 <span data-ttu-id="94859-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94859-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94859-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="94859-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="94859-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94859-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94859-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94859-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94859-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94859-114">See also</span></span>

- [<span data-ttu-id="94859-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="94859-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="94859-116">ModuleUnloadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="94859-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
