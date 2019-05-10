---
title: ICorProfilerCallback3::ProfilerAttachComplete — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a181ca2da8385107d63cd94ea832846c4211ad5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650383"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="df64e-102">ICorProfilerCallback3::ProfilerAttachComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="df64e-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="df64e-103">Wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR), aby wskazać, że teraz można wywołać program profilujący [icorprofilerinfo3::enumjitedfunctions —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) i [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) wyrównującej metody.</span><span class="sxs-lookup"><span data-stu-id="df64e-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df64e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df64e-104">Syntax</span></span>  
  
```  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="df64e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df64e-105">Remarks</span></span>  
 <span data-ttu-id="df64e-106">`ProfilerAttachComplete` Wywołanie zwrotne zostało wydane po [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="df64e-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="df64e-107">Oznacza to, że:</span><span class="sxs-lookup"><span data-stu-id="df64e-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="df64e-108">Wywołania zwrotne, których zażądał profiler w `InitializeForAttach` został aktywowany.</span><span class="sxs-lookup"><span data-stu-id="df64e-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="df64e-109">Profiler może teraz wykonywać wyrównanie na skojarzonych identyfikatorach bez danych o ominięcie powiadomień.</span><span class="sxs-lookup"><span data-stu-id="df64e-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="df64e-110">Środowisko CLR ignoruje wartość zwracaną z to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="df64e-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df64e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df64e-111">Requirements</span></span>  
 <span data-ttu-id="df64e-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df64e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df64e-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="df64e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="df64e-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df64e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df64e-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df64e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df64e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df64e-116">See also</span></span>

- [<span data-ttu-id="df64e-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="df64e-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="df64e-118">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="df64e-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="df64e-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="df64e-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="df64e-120">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="df64e-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
