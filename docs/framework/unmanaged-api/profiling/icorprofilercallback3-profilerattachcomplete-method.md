---
title: "ICorProfilerCallback3::ProfilerAttachComplete — Metoda"
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
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1472658fb5d2d68b14574b233bd5950d0a7abe5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="60195-102">ICorProfilerCallback3::ProfilerAttachComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="60195-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="60195-103">Wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR), aby wskazać, że profiler można teraz wywołać [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) i [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) wyrównującej metody.</span><span class="sxs-lookup"><span data-stu-id="60195-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60195-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="60195-104">Syntax</span></span>  
  
```  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="60195-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60195-105">Remarks</span></span>  
 <span data-ttu-id="60195-106">`ProfilerAttachComplete` Wywołanie zwrotne zostało wydane po [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="60195-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="60195-107">Wskazuje on następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="60195-107">It indicates the following:</span></span>  
  
-   <span data-ttu-id="60195-108">Wywołania zwrotne, zażądanych przez profiler w `InitializeForAttach` został aktywowany.</span><span class="sxs-lookup"><span data-stu-id="60195-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
-   <span data-ttu-id="60195-109">Profiler może teraz wykonywać przechwycenie na skojarzonych identyfikatorów bez konieczności zajmującym się brak powiadomień.</span><span class="sxs-lookup"><span data-stu-id="60195-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="60195-110">Środowisko CLR ignoruje wartość zwracana z tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="60195-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60195-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60195-111">Requirements</span></span>  
 <span data-ttu-id="60195-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60195-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60195-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="60195-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60195-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60195-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60195-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60195-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60195-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60195-116">See Also</span></span>  
 [<span data-ttu-id="60195-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="60195-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="60195-118">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="60195-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="60195-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="60195-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="60195-120">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="60195-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
