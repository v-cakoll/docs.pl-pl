---
title: "ICorProfilerCallback3 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback3
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback3
helpviewer_keywords: ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1419dfff7005b33fd1f8a545d168a410e7a88a76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="3185e-102">ICorProfilerCallback3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3185e-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="3185e-103">Udostępnia metody wywołania zwrotnego, środowisko uruchomieniowe języka wspólnego (CLR) używanych do komunikacji dołączania i odłączania informacje o stanie do profilera.</span><span class="sxs-lookup"><span data-stu-id="3185e-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3185e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3185e-104">Methods</span></span>  
  
|<span data-ttu-id="3185e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3185e-105">Method</span></span>|<span data-ttu-id="3185e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3185e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3185e-107">InitializeForAttach, metoda</span><span class="sxs-lookup"><span data-stu-id="3185e-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="3185e-108">Wywoływane przez środowisko CLR, które umożliwia profilera zainicjować stanu po operacji dołączania.</span><span class="sxs-lookup"><span data-stu-id="3185e-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="3185e-109">ProfilerAttachComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="3185e-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="3185e-110">Wywoływane przez środowisko CLR, aby wskazać, że profilera można teraz wywołać metody wyrównującej.</span><span class="sxs-lookup"><span data-stu-id="3185e-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="3185e-111">ProfilerDetachSucceeded, metoda</span><span class="sxs-lookup"><span data-stu-id="3185e-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="3185e-112">Powiadamia profilera środowisko uruchomieniowe języka wspólnego (CLR) o zbliżającym się zwolnienia biblioteki DLL profilera.</span><span class="sxs-lookup"><span data-stu-id="3185e-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3185e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3185e-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3185e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3185e-114">Requirements</span></span>  
 <span data-ttu-id="3185e-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3185e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3185e-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3185e-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3185e-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3185e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3185e-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3185e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3185e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3185e-119">See Also</span></span>  
 [<span data-ttu-id="3185e-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="3185e-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="3185e-121">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="3185e-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="3185e-122">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3185e-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="3185e-123">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="3185e-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
