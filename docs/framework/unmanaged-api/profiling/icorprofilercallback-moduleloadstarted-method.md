---
title: ICorProfilerCallback::ModuleLoadStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5b847cbbdf1bfccd91ca212dadd1fcd82cc12c82
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768201"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="e160c-102">ICorProfilerCallback::ModuleLoadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="e160c-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="e160c-103">Powiadamia program profilujący, że moduł jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="e160c-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e160c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e160c-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e160c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e160c-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="e160c-106">[in] Identyfikator modułu, który jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="e160c-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e160c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e160c-107">Remarks</span></span>  
 <span data-ttu-id="e160c-108">Wartość `moduleId` jest nieprawidłowa dla żądania informacje do momentu [icorprofilercallback::moduleloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="e160c-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e160c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e160c-109">Requirements</span></span>  
 <span data-ttu-id="e160c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e160c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e160c-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e160c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e160c-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e160c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e160c-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e160c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e160c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e160c-114">See also</span></span>

- [<span data-ttu-id="e160c-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="e160c-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
