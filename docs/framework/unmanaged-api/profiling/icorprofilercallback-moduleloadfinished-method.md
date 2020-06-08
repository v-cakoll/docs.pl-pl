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
ms.openlocfilehash: 481fc2c40331e31f6a018d012fb2b2543d4fd9b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503370"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="ac123-102">ICorProfilerCallback::ModuleLoadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="ac123-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="ac123-103">Powiadamia profiler o zakończeniu ładowania modułu.</span><span class="sxs-lookup"><span data-stu-id="ac123-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac123-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac123-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac123-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac123-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="ac123-106">podczas Identyfikator modułu, który zakończył ładowanie.</span><span class="sxs-lookup"><span data-stu-id="ac123-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="ac123-107">podczas WYNIK HRESULT wskazujący, czy moduł został załadowany pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ac123-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac123-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac123-108">Remarks</span></span>  
 <span data-ttu-id="ac123-109">Wartość `moduleId` nie jest prawidłowa dla żądania informacji, dopóki `ModuleLoadFinished` Metoda nie zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="ac123-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="ac123-110">Niektóre części ładowania modułu mogą być kontynuowane po `ModuleLoadFinished` wywołaniu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ac123-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="ac123-111">Błąd HRESULT w elemencie `hrStatus` wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="ac123-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="ac123-112">Jednak powodzenie HRESULT w programie `hrStatus` wskazuje tylko, że pierwsza część ładowania modułu zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="ac123-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac123-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac123-113">Requirements</span></span>  
 <span data-ttu-id="ac123-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac123-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac123-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ac123-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac123-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ac123-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac123-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac123-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac123-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac123-118">See also</span></span>

- [<span data-ttu-id="ac123-119">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ac123-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ac123-120">ModuleLoadStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="ac123-120">ModuleLoadStarted Method</span></span>](icorprofilercallback-moduleloadstarted-method.md)
