---
title: ICorProfilerCallback::ModuleLoadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 354d2f278bcb0618b823b7300079278fc4c3315c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157355"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="3cb6c-102">ICorProfilerCallback::ModuleLoadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="3cb6c-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="3cb6c-103">Powiadamia program profilujący, że moduł zakończeniu ładowania.</span><span class="sxs-lookup"><span data-stu-id="3cb6c-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cb6c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3cb6c-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cb6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cb6c-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="3cb6c-106">[in] Identyfikator modułu, który zakończy ładowanie.</span><span class="sxs-lookup"><span data-stu-id="3cb6c-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="3cb6c-107">[in] Wartość HRESULT, która wskazuje, czy moduł został załadowany pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3cb6c-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cb6c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3cb6c-108">Remarks</span></span>  
 <span data-ttu-id="3cb6c-109">Wartość `moduleId` jest nieprawidłowa dla żądania informacje do momentu `ModuleLoadFinished` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="3cb6c-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="3cb6c-110">Niektóre części podczas ładowania modułu może nadal po `ModuleLoadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3cb6c-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="3cb6c-111">Błąd HRESULT w `hrStatus` wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="3cb6c-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="3cb6c-112">Jednak sukcesów wartość HRESULT w `hrStatus` wskazuje tylko, powiodło się w pierwszej części podczas ładowania modułu.</span><span class="sxs-lookup"><span data-stu-id="3cb6c-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cb6c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3cb6c-113">Requirements</span></span>  
 <span data-ttu-id="3cb6c-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cb6c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cb6c-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3cb6c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3cb6c-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3cb6c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cb6c-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cb6c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb6c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3cb6c-118">See also</span></span>

- [<span data-ttu-id="3cb6c-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="3cb6c-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="3cb6c-120">ModuleLoadStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="3cb6c-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
