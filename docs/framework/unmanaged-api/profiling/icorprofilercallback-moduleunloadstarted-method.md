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
ms.openlocfilehash: f0000e9b063022e828e52b9b940ec6f4e0ce4165
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445902"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="29e65-102">ICorProfilerCallback::ModuleUnloadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="29e65-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="29e65-103">Powiadamia program profilujący, że moduł jest zwolniony.</span><span class="sxs-lookup"><span data-stu-id="29e65-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29e65-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29e65-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="29e65-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29e65-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="29e65-106">podczas Identyfikator modułu, który jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="29e65-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29e65-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29e65-107">Remarks</span></span>  
 <span data-ttu-id="29e65-108">Wartość `moduleId` nie jest prawidłowa dla żądania informacji po powrocie metody `ModuleUnloadStarted` — jest to Ostatnia szansa dla profilera, aby uzyskać informacje na temat tego modułu.</span><span class="sxs-lookup"><span data-stu-id="29e65-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29e65-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29e65-109">Requirements</span></span>  
 <span data-ttu-id="29e65-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29e65-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29e65-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="29e65-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29e65-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="29e65-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29e65-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29e65-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e65-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29e65-114">See also</span></span>

- [<span data-ttu-id="29e65-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="29e65-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="29e65-116">ModuleUnloadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="29e65-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
