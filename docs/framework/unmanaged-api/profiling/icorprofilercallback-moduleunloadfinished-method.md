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
ms.openlocfilehash: b13573d19ab4d8bb655c1e153530dc70173abe82
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866146"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="b78a5-102">ICorProfilerCallback::ModuleUnloadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="b78a5-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="b78a5-103">Powiadamia program profilujący o zakończeniu ładowania modułu.</span><span class="sxs-lookup"><span data-stu-id="b78a5-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b78a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b78a5-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b78a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b78a5-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="b78a5-106">podczas Identyfikator modułu, który został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="b78a5-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="b78a5-107">podczas WYNIK HRESULT wskazujący, czy moduł został zwolniony pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b78a5-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b78a5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b78a5-108">Remarks</span></span>  
 <span data-ttu-id="b78a5-109">Wartość `moduleId` nie jest prawidłowa dla żądania informacji po powrocie metody [ICorProfilerCallback:: ModuleUnloadStarted —](icorprofilercallback-moduleunloadstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b78a5-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="b78a5-110">Niektóre części zwalniania klasy mogą być kontynuowane po wywołaniu wywołania zwrotnego `ModuleUnloadFinished`.</span><span class="sxs-lookup"><span data-stu-id="b78a5-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="b78a5-111">Błąd HRESULT w `hrStatus` wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="b78a5-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="b78a5-112">Jednak wynik HRESULT w `hrStatus` wskazuje tylko, że pierwsza część zwalniania modułu zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="b78a5-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b78a5-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b78a5-113">Requirements</span></span>  
 <span data-ttu-id="b78a5-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b78a5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b78a5-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b78a5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b78a5-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b78a5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b78a5-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b78a5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b78a5-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b78a5-118">See also</span></span>

- [<span data-ttu-id="b78a5-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="b78a5-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
