---
title: ICorProfilerCallback::ModuleUnloadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7759b0815946301932ca60edaf731313d04a245
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743468"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="38576-102">ICorProfilerCallback::ModuleUnloadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="38576-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="38576-103">Powiadamia program profilujący, moduł zakończenie zwolnienie.</span><span class="sxs-lookup"><span data-stu-id="38576-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38576-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38576-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38576-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38576-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="38576-106">[in] Identyfikator modułu, który został usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="38576-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="38576-107">[in] Wartość HRESULT, która wskazuje, czy moduł został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="38576-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38576-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38576-108">Remarks</span></span>  
 <span data-ttu-id="38576-109">Wartość `moduleId` jest nieprawidłowa dla żądania informacji po [icorprofilercallback::moduleunloadstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="38576-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="38576-110">Niektóre części zwolnienie tej klasy może kontynuować po `ModuleUnloadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="38576-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="38576-111">Błąd HRESULT w `hrStatus` wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="38576-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="38576-112">Jednak sukcesów wartość HRESULT w `hrStatus` tylko wskazuje, czy zakończyła się pomyślnie w pierwszej części zwalnianie modułu.</span><span class="sxs-lookup"><span data-stu-id="38576-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38576-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38576-113">Requirements</span></span>  
 <span data-ttu-id="38576-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38576-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38576-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="38576-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="38576-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38576-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38576-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38576-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38576-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38576-118">See also</span></span>
- [<span data-ttu-id="38576-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="38576-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
