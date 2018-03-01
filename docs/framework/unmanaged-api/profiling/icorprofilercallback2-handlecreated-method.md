---
title: "ICorProfilerCallback2::HandleCreated — Metoda"
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
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9d920f2e33a43e36c7bf27b4e1a88d6bc4a23600
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="cfa86-102">ICorProfilerCallback2::HandleCreated — Metoda</span><span class="sxs-lookup"><span data-stu-id="cfa86-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="cfa86-103">Powiadamia profilera kodu utworzono uchwyt kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="cfa86-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfa86-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfa86-104">Syntax</span></span>  
  
```  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfa86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cfa86-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="cfa86-106">[in] Identyfikator obsługę wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cfa86-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="cfa86-107">[in] Identyfikator obiektu, dla którego utworzono uchwyt kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="cfa86-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfa86-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cfa86-108">Requirements</span></span>  
 <span data-ttu-id="cfa86-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfa86-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfa86-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cfa86-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cfa86-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfa86-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfa86-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfa86-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfa86-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfa86-113">See Also</span></span>  
 [<span data-ttu-id="cfa86-114">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="cfa86-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="cfa86-115">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cfa86-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
