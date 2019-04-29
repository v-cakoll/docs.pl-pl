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
ms.openlocfilehash: 66e6a67ce022365fa8c9e1005dfecbe4b23abd10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598886"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="05a3d-102">ICorProfilerCallback3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="05a3d-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="05a3d-103">Udostępnia metody wywołania zwrotnego, używanych przez środowisko uruchomieniowe języka wspólnego (CLR) do komunikacji dołączania i odłączania informacje o stanie do programu profilującego.</span><span class="sxs-lookup"><span data-stu-id="05a3d-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05a3d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="05a3d-104">Methods</span></span>  
  
|<span data-ttu-id="05a3d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="05a3d-105">Method</span></span>|<span data-ttu-id="05a3d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="05a3d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05a3d-107">InitializeForAttach, metoda</span><span class="sxs-lookup"><span data-stu-id="05a3d-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="05a3d-108">Metoda wywoływana przez środowisko CLR, aby dać profilerowi możliwość zainicjowania jego stanu po operacji dołączania.</span><span class="sxs-lookup"><span data-stu-id="05a3d-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="05a3d-109">ProfilerAttachComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="05a3d-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="05a3d-110">Metoda wywoływana przez środowisko CLR, aby wskazać, że profiler teraz można wywołać metody zapoznać się ze zmianami.</span><span class="sxs-lookup"><span data-stu-id="05a3d-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="05a3d-111">ProfilerDetachSucceeded, metoda</span><span class="sxs-lookup"><span data-stu-id="05a3d-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="05a3d-112">Powiadamia program profilujący, że środowisko uruchomieniowe języka wspólnego (CLR) zostanie zwolnienia biblioteki DLL profilera.</span><span class="sxs-lookup"><span data-stu-id="05a3d-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05a3d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05a3d-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05a3d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05a3d-114">Requirements</span></span>  
 <span data-ttu-id="05a3d-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05a3d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05a3d-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="05a3d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05a3d-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05a3d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05a3d-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05a3d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05a3d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05a3d-119">See also</span></span>

- [<span data-ttu-id="05a3d-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="05a3d-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="05a3d-121">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="05a3d-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="05a3d-122">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="05a3d-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="05a3d-123">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="05a3d-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
