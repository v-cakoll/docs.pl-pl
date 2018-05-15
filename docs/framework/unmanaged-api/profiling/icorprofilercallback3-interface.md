---
title: ICorProfilerCallback3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cc63a0a42c1da11daa5d38ecce505296a893616b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="7059a-102">ICorProfilerCallback3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7059a-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="7059a-103">Udostępnia metody wywołania zwrotnego, środowisko uruchomieniowe języka wspólnego (CLR) używanych do komunikacji dołączania i odłączania informacje o stanie do profilera.</span><span class="sxs-lookup"><span data-stu-id="7059a-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7059a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7059a-104">Methods</span></span>  
  
|<span data-ttu-id="7059a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7059a-105">Method</span></span>|<span data-ttu-id="7059a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7059a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7059a-107">InitializeForAttach, metoda</span><span class="sxs-lookup"><span data-stu-id="7059a-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="7059a-108">Wywoływane przez środowisko CLR, które umożliwia profilera zainicjować stanu po operacji dołączania.</span><span class="sxs-lookup"><span data-stu-id="7059a-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="7059a-109">ProfilerAttachComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="7059a-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="7059a-110">Wywoływane przez środowisko CLR, aby wskazać, że profilera można teraz wywołać metody wyrównującej.</span><span class="sxs-lookup"><span data-stu-id="7059a-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="7059a-111">ProfilerDetachSucceeded, metoda</span><span class="sxs-lookup"><span data-stu-id="7059a-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="7059a-112">Powiadamia profilera środowisko uruchomieniowe języka wspólnego (CLR) o zbliżającym się zwolnienia biblioteki DLL profilera.</span><span class="sxs-lookup"><span data-stu-id="7059a-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7059a-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7059a-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7059a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7059a-114">Requirements</span></span>  
 <span data-ttu-id="7059a-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7059a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7059a-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7059a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7059a-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7059a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7059a-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7059a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7059a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7059a-119">See Also</span></span>  
 [<span data-ttu-id="7059a-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="7059a-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="7059a-121">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="7059a-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="7059a-122">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7059a-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="7059a-123">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="7059a-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
