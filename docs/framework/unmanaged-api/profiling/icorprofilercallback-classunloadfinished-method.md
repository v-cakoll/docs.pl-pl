---
title: "ICorProfilerCallback::ClassUnloadFinished — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ClassUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 920fa36edcc49c12f8f73644cc4e6551a0e954ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="b8864-102">ICorProfilerCallback::ClassUnloadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="b8864-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="b8864-103">Powiadamia profilera klasy zakończenie zwalnianie.</span><span class="sxs-lookup"><span data-stu-id="b8864-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8864-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8864-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8864-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8864-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="b8864-106">[in] Określa klasę, która została zwolniona.</span><span class="sxs-lookup"><span data-stu-id="b8864-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="b8864-107">[in] HRESULT, która wskazuje, czy klasa został pomyślnie usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="b8864-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8864-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8864-108">Remarks</span></span>  
 <span data-ttu-id="b8864-109">Niektóre elementy zwalnianie klasy mogą nadal po `ClassUnloadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b8864-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="b8864-110">Błąd HRESULT w `hrStatus` oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="b8864-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="b8864-111">Jednak Powodzenie HRESULT w `hrStatus` tylko wskazuje, że pierwsza część zwalnianie klasie zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b8864-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8864-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8864-112">Requirements</span></span>  
 <span data-ttu-id="b8864-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8864-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8864-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b8864-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b8864-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8864-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8864-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8864-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8864-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8864-117">See Also</span></span>  
 [<span data-ttu-id="b8864-118">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="b8864-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="b8864-119">ClassUnloadStarted — metoda</span><span class="sxs-lookup"><span data-stu-id="b8864-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
