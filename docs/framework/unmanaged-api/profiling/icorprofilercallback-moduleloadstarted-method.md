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
ms.openlocfilehash: aa5ca8871ab284d2a46e6777b226f5a9b155e566
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502472"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="86dc8-102">ICorProfilerCallback::ModuleLoadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="86dc8-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="86dc8-103">Powiadamia program profilujący, że moduł jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="86dc8-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86dc8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86dc8-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86dc8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86dc8-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="86dc8-106">[in] Identyfikator modułu, który jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="86dc8-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86dc8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86dc8-107">Remarks</span></span>  
 <span data-ttu-id="86dc8-108">Wartość `moduleId` jest nieprawidłowa dla żądania informacje do momentu [icorprofilercallback::moduleloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="86dc8-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86dc8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86dc8-109">Requirements</span></span>  
 <span data-ttu-id="86dc8-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86dc8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86dc8-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="86dc8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="86dc8-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86dc8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86dc8-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86dc8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86dc8-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86dc8-114">See also</span></span>
- [<span data-ttu-id="86dc8-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="86dc8-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
