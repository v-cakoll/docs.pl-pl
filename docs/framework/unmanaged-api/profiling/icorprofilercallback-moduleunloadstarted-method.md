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
ms.openlocfilehash: fcfdddbd5316c098754ea7b0d4714b050c64fe55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175151"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="9c2cb-102">ICorProfilerCallback::ModuleUnloadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="9c2cb-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="9c2cb-103">Powiadamia profiler, że moduł jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="9c2cb-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c2cb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c2cb-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a><span data-ttu-id="9c2cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c2cb-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="9c2cb-106">[w] Identyfikator modułu, który jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="9c2cb-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c2cb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c2cb-107">Remarks</span></span>  
 <span data-ttu-id="9c2cb-108">Wartość nie `moduleId` jest prawidłowa dla żądania `ModuleUnloadStarted` informacji po zwraca metodę — jest to ostatnia szansa profilera, aby uzyskać informacje o tym module.</span><span class="sxs-lookup"><span data-stu-id="9c2cb-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c2cb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9c2cb-109">Requirements</span></span>  
 <span data-ttu-id="9c2cb-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c2cb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c2cb-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9c2cb-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9c2cb-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c2cb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c2cb-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c2cb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c2cb-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c2cb-114">See also</span></span>

- [<span data-ttu-id="9c2cb-115">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9c2cb-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9c2cb-116">ModuleUnloadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="9c2cb-116">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
