---
title: "ICorProfilerCallback::ClassUnloadFinished — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9801113e23474fa0aae461d356e4aa57a203bd6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="27197-102">ICorProfilerCallback::ClassUnloadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="27197-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="27197-103">Powiadamia profilera klasy zakończenie zwalnianie.</span><span class="sxs-lookup"><span data-stu-id="27197-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27197-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="27197-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27197-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27197-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="27197-106">[in] Określa klasę, która została zwolniona.</span><span class="sxs-lookup"><span data-stu-id="27197-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="27197-107">[in] HRESULT, która wskazuje, czy klasa został pomyślnie usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="27197-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27197-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27197-108">Remarks</span></span>  
 <span data-ttu-id="27197-109">Niektóre elementy zwalnianie klasy mogą nadal po `ClassUnloadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="27197-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="27197-110">Błąd HRESULT w `hrStatus` oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="27197-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="27197-111">Jednak Powodzenie HRESULT w `hrStatus` tylko wskazuje, że pierwsza część zwalnianie klasie zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="27197-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27197-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27197-112">Requirements</span></span>  
 <span data-ttu-id="27197-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27197-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27197-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27197-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27197-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27197-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27197-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27197-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27197-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27197-117">See Also</span></span>  
 [<span data-ttu-id="27197-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="27197-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="27197-119">ClassUnloadStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="27197-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
