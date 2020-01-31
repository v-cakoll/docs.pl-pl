---
title: ICorProfilerCallback::ClassUnloadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: 5d9474f78dd8b999a37f60e0698cfd04240b897a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866575"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="9951d-102">ICorProfilerCallback::ClassUnloadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="9951d-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="9951d-103">Powiadamia profiler o zakończeniu zwalniania klasy.</span><span class="sxs-lookup"><span data-stu-id="9951d-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9951d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9951d-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9951d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9951d-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="9951d-106">\[in] określa klasę, która została zwolniona.</span><span class="sxs-lookup"><span data-stu-id="9951d-106">\[in] Identifies the class that was unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="9951d-107">\[in] wynik HRESULT wskazujący, czy klasa została zwolniona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9951d-107">\[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="9951d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9951d-108">Remarks</span></span>  
 <span data-ttu-id="9951d-109">Niektóre części zwalniania klasy mogą być kontynuowane po wywołaniu wywołania zwrotnego `ClassUnloadFinished`.</span><span class="sxs-lookup"><span data-stu-id="9951d-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="9951d-110">Błąd HRESULT w `hrStatus` wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="9951d-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="9951d-111">Jednak wynik HRESULT w `hrStatus` wskazuje tylko, że pierwsza część zwalniania klasy zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="9951d-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9951d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9951d-112">Requirements</span></span>  
 <span data-ttu-id="9951d-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9951d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9951d-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9951d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9951d-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9951d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9951d-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9951d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9951d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9951d-117">See also</span></span>

- [<span data-ttu-id="9951d-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="9951d-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9951d-119">ClassUnloadStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="9951d-119">ClassUnloadStarted Method</span></span>](icorprofilercallback-classunloadstarted-method.md)
