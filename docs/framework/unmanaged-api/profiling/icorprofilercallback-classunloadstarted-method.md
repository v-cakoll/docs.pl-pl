---
title: "ICorProfilerCallback::ClassUnloadStarted — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ClassUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0056d97e7cf8286291292f27e942b7a846efb3f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="2cf51-102">ICorProfilerCallback::ClassUnloadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="2cf51-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="2cf51-103">Powiadamia profiler jest zwalniany klasy.</span><span class="sxs-lookup"><span data-stu-id="2cf51-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cf51-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2cf51-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2cf51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2cf51-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="2cf51-106">[in] Określa klasę, która jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="2cf51-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cf51-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2cf51-107">Remarks</span></span>  
 <span data-ttu-id="2cf51-108">Wartość `classId` jest nieprawidłowa dla żądania informacji po `ClassUnloadStarted` metoda zwraca — jest to profilera ostatnia możliwość uzyskania informacji na temat tej klasy.</span><span class="sxs-lookup"><span data-stu-id="2cf51-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cf51-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2cf51-109">Requirements</span></span>  
 <span data-ttu-id="2cf51-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cf51-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cf51-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2cf51-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2cf51-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cf51-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cf51-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cf51-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf51-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2cf51-114">See Also</span></span>  
 [<span data-ttu-id="2cf51-115">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="2cf51-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="2cf51-116">ClassUnloadFinished — metoda</span><span class="sxs-lookup"><span data-stu-id="2cf51-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
