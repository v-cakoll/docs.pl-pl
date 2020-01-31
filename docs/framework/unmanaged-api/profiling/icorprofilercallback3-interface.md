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
ms.openlocfilehash: ad9c5445cbef0be7919570db64b027556d923752
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865574"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="0f57e-102">ICorProfilerCallback3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0f57e-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="0f57e-103">Zapewnia metody wywołania zwrotnego, które są używane przez środowisko uruchomieniowe języka wspólnego (CLR) do przekazywania informacji o stanie dołączania i odłączania do profilera.</span><span class="sxs-lookup"><span data-stu-id="0f57e-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f57e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0f57e-104">Methods</span></span>  
  
|<span data-ttu-id="0f57e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0f57e-105">Method</span></span>|<span data-ttu-id="0f57e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0f57e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f57e-107">InitializeForAttach, metoda</span><span class="sxs-lookup"><span data-stu-id="0f57e-107">InitializeForAttach Method</span></span>](icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="0f57e-108">Wywoływane przez środowisko CLR, aby dać profilerowi możliwość zainicjowania stanu po operacji Attach.</span><span class="sxs-lookup"><span data-stu-id="0f57e-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="0f57e-109">ProfilerAttachComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="0f57e-109">ProfilerAttachComplete Method</span></span>](icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="0f57e-110">Wywoływane przez środowisko CLR, aby wskazać, że profiler może teraz wywoływać metody przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="0f57e-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="0f57e-111">ProfilerDetachSucceeded, metoda</span><span class="sxs-lookup"><span data-stu-id="0f57e-111">ProfilerDetachSucceeded Method</span></span>](icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="0f57e-112">Powiadamia program profilujący, że aparat plików wykonywalnych języka wspólnego (CLR) ma zwolnić plik DLL profilera.</span><span class="sxs-lookup"><span data-stu-id="0f57e-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f57e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f57e-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f57e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0f57e-114">Requirements</span></span>  
 <span data-ttu-id="0f57e-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f57e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f57e-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0f57e-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0f57e-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0f57e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f57e-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f57e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f57e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f57e-119">See also</span></span>

- [<span data-ttu-id="0f57e-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="0f57e-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0f57e-121">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f57e-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="0f57e-122">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f57e-122">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="0f57e-123">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f57e-123">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
