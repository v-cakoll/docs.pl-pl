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
ms.openlocfilehash: 08fbf49e6944de4934a9fe7a960405ee96a7d8e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445940"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="05e9f-102">ICorProfilerCallback::ModuleLoadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="05e9f-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="05e9f-103">Powiadamia profiler o zakończeniu ładowania modułu.</span><span class="sxs-lookup"><span data-stu-id="05e9f-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05e9f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05e9f-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05e9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05e9f-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="05e9f-106">podczas Identyfikator modułu, który zakończył ładowanie.</span><span class="sxs-lookup"><span data-stu-id="05e9f-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="05e9f-107">podczas WYNIK HRESULT wskazujący, czy moduł został załadowany pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="05e9f-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05e9f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05e9f-108">Remarks</span></span>  
 <span data-ttu-id="05e9f-109">Wartość `moduleId` nie jest prawidłowa dla żądania informacji, dopóki nie zostanie wywołana metoda `ModuleLoadFinished`.</span><span class="sxs-lookup"><span data-stu-id="05e9f-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="05e9f-110">Niektóre części ładowania modułu mogą być kontynuowane po wywołaniu wywołania zwrotnego `ModuleLoadFinished`.</span><span class="sxs-lookup"><span data-stu-id="05e9f-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="05e9f-111">Błąd HRESULT w `hrStatus` wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="05e9f-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="05e9f-112">Jednak wynik HRESULT w `hrStatus` wskazuje tylko, że pierwsza część ładowania modułu zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="05e9f-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05e9f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05e9f-113">Requirements</span></span>  
 <span data-ttu-id="05e9f-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05e9f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05e9f-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="05e9f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05e9f-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="05e9f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05e9f-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05e9f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05e9f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05e9f-118">See also</span></span>

- [<span data-ttu-id="05e9f-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="05e9f-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="05e9f-120">ModuleLoadStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="05e9f-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
