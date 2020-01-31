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
ms.openlocfilehash: 8168f6f1079ec34b9fb53a485da0f32175446719
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865431"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="a9295-102">ICorProfilerCallback3::ProfilerAttachComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="a9295-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="a9295-103">Wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR), aby wskazać, że profiler może teraz wywołać metody przechwytywania [ICorProfilerInfo3:: EnumJITedFunctions —](icorprofilerinfo3-enumjitedfunctions-method.md) i [ICorProfilerInfo3:: EnumModules —](icorprofilerinfo3-enummodules-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9295-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9295-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9295-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a9295-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9295-105">Remarks</span></span>  
 <span data-ttu-id="a9295-106">Wywołanie zwrotne `ProfilerAttachComplete` jest wydawane po wywołaniu metody [ICorProfilerCallback3:: InitializeForAttach —](icorprofilercallback3-initializeforattach-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9295-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="a9295-107">Wskazuje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="a9295-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="a9295-108">Wywołania zwrotne, które zażądały Profiler w `InitializeForAttach`, zostały aktywowane.</span><span class="sxs-lookup"><span data-stu-id="a9295-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="a9295-109">Profiler może teraz przechwycić odpowiednie identyfikatory bez konieczności powiadamiania o brakujących powiadomieniach.</span><span class="sxs-lookup"><span data-stu-id="a9295-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="a9295-110">Środowisko CLR ignoruje wartość zwracaną z tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="a9295-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9295-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9295-111">Requirements</span></span>  
 <span data-ttu-id="a9295-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9295-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9295-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a9295-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a9295-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a9295-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9295-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9295-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9295-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9295-116">See also</span></span>

- [<span data-ttu-id="a9295-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9295-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="a9295-118">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9295-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="a9295-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="a9295-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a9295-120">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="a9295-120">Profiling</span></span>](index.md)
