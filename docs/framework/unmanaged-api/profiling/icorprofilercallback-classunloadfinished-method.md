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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9bb7e31f3bff9bfc2cb44259f29b6a7293193371
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623217"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="27bc2-102">ICorProfilerCallback::ClassUnloadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="27bc2-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="27bc2-103">Powiadamia program profilujący, klasa zakończenie zwolnienie.</span><span class="sxs-lookup"><span data-stu-id="27bc2-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27bc2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="27bc2-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27bc2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27bc2-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="27bc2-106">[in] Określa klasę, która został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="27bc2-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="27bc2-107">[in] Wartość HRESULT, która wskazuje, czy klasa został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="27bc2-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27bc2-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27bc2-108">Remarks</span></span>  
 <span data-ttu-id="27bc2-109">Niektóre części zwolnienie tej klasy może kontynuować po `ClassUnloadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="27bc2-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="27bc2-110">Błąd HRESULT w `hrStatus` wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="27bc2-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="27bc2-111">Jednak sukcesów wartość HRESULT w `hrStatus` wskazuje tylko, pierwsza część zwalnianie klasy zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="27bc2-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27bc2-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27bc2-112">Requirements</span></span>  
 <span data-ttu-id="27bc2-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27bc2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27bc2-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27bc2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27bc2-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27bc2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27bc2-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27bc2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27bc2-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27bc2-117">See also</span></span>
- [<span data-ttu-id="27bc2-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="27bc2-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="27bc2-119">ClassUnloadStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="27bc2-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
