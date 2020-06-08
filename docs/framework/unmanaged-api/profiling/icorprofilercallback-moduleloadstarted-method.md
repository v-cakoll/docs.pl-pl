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
ms.openlocfilehash: a04f72fff9a88c8689821131b08b35500c23b3d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503357"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="1a577-102">ICorProfilerCallback::ModuleLoadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="1a577-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="1a577-103">Powiadamia program profilujący, że moduł jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="1a577-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a577-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a577-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a577-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a577-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="1a577-106">podczas Identyfikator modułu, który jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="1a577-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a577-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a577-107">Remarks</span></span>  
 <span data-ttu-id="1a577-108">Wartość `moduleId` nie jest prawidłowa dla żądania informacji, dopóki nie zostanie wywołana metoda [ICorProfilerCallback:: ModuleLoadFinished —](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1a577-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a577-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a577-109">Requirements</span></span>  
 <span data-ttu-id="1a577-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a577-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a577-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1a577-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1a577-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1a577-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a577-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a577-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a577-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a577-114">See also</span></span>

- [<span data-ttu-id="1a577-115">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1a577-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
