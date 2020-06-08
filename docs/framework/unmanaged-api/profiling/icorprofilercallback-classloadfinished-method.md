---
title: ICorProfilerCallback::ClassLoadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: 4be2a50664b001e865b5ecdd9aabe8ba727b8c26
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500393"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="895b1-102">ICorProfilerCallback::ClassLoadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="895b1-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="895b1-103">Powiadamia profiler o zakończeniu ładowania klasy.</span><span class="sxs-lookup"><span data-stu-id="895b1-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="895b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="895b1-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="895b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="895b1-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="895b1-106">\[w] identyfikuje klasę, która została załadowana.</span><span class="sxs-lookup"><span data-stu-id="895b1-106">\[in] Identifies the class that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="895b1-107">\[w] wynik HRESULT wskazujący, czy klasa została pomyślnie załadowana.</span><span class="sxs-lookup"><span data-stu-id="895b1-107">\[in] An HRESULT that indicates whether the class loaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="895b1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="895b1-108">Remarks</span></span>  
 <span data-ttu-id="895b1-109">Wartość `classId` nie jest prawidłowa dla żądania informacji, dopóki `ClassLoadFinished` Metoda nie zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="895b1-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="895b1-110">Niektóre części ładowania klasy mogą być kontynuowane po `ClassLoadFinished` wywołaniu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="895b1-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="895b1-111">Błąd HRESULT w elemencie `hrStatus` wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="895b1-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="895b1-112">Jednak powodzenie HRESULT w programie `hrStatus` wskazuje tylko, że pierwsza część ładowania klasy zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="895b1-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="895b1-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="895b1-113">Requirements</span></span>  
 <span data-ttu-id="895b1-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="895b1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="895b1-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="895b1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="895b1-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="895b1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="895b1-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="895b1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="895b1-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="895b1-118">See also</span></span>

- [<span data-ttu-id="895b1-119">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="895b1-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="895b1-120">ClassLoadStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="895b1-120">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
