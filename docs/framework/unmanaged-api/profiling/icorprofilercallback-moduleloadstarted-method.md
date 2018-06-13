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
ms.openlocfilehash: e9d6c322d82b34af908065106ef03ccf5ff846e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451733"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="78fe4-102">ICorProfilerCallback::ModuleLoadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="78fe4-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="78fe4-103">Powiadamia profilera, czy moduł jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="78fe4-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78fe4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78fe4-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78fe4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78fe4-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="78fe4-106">[in] Identyfikator modułu, który jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="78fe4-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78fe4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78fe4-107">Remarks</span></span>  
 <span data-ttu-id="78fe4-108">Wartość `moduleId` jest nieprawidłowa dla żądania informacji do [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="78fe4-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78fe4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78fe4-109">Requirements</span></span>  
 <span data-ttu-id="78fe4-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78fe4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78fe4-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="78fe4-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78fe4-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78fe4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78fe4-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78fe4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78fe4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78fe4-114">See Also</span></span>  
 [<span data-ttu-id="78fe4-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="78fe4-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
