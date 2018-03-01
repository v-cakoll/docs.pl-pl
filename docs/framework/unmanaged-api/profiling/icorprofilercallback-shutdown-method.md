---
title: "ICorProfilerCallback::Shutdown — Metoda"
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
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 42c9abc3c255f7ddda5e7934c495b073a7b1f6fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="24312-102">ICorProfilerCallback::Shutdown — Metoda</span><span class="sxs-lookup"><span data-stu-id="24312-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="24312-103">Powiadamia profilera, że aplikacja jest zamykana.</span><span class="sxs-lookup"><span data-stu-id="24312-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24312-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24312-104">Syntax</span></span>  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="24312-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24312-105">Remarks</span></span>  
 <span data-ttu-id="24312-106">Kod profilera bezpiecznie nie można wywołać metody [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interfejsu po `Shutdown` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="24312-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="24312-107">Wszelkie wywołania `ICorProfilerInfo` metod spowodować niezdefiniowane zachowanie po `Shutdown` zwraca metody.</span><span class="sxs-lookup"><span data-stu-id="24312-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="24312-108">Określone zdarzenia niezmienne nadal może wystąpić po zamknięciu; profilera należy zwrócić uwagę, aby zwrócić natychmiast w takiej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="24312-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="24312-109">`Shutdown` Metoda zostanie wywołana tylko wtedy, gdy aplikacja zarządzana, który jest poddawany profilowaniu uruchomiona jako kodu zarządzanego (to znaczy początkowej ramek na stosie proces odbywa się).</span><span class="sxs-lookup"><span data-stu-id="24312-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="24312-110">Jeśli aplikacja uruchomiona jako kodu niezarządzanego, ale później przeskoki do kodu zarządzanego, tworząc wystąpienia środowisko uruchomieniowe języka wspólnego (CLR), następnie `Shutdown` nie zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="24312-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="24312-111">W tych przypadkach profilera, należy uwzględnić w jego biblioteki `DllMain` procedury, która używa komunikat DLL_PROCESS_DETACH wartość, aby zwolnić wszystkie zasoby i przetwarzania oczyszczania jej dane, takie jak opróżnianie ślady na dysku i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="24312-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="24312-112">Ogólnie rzecz biorąc profilera musi sprostać zamknięć.</span><span class="sxs-lookup"><span data-stu-id="24312-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="24312-113">Na przykład proces może być zatrzymana przez Win32 w `TerminateProcess` — metoda (deklaracja w Winbase.h).</span><span class="sxs-lookup"><span data-stu-id="24312-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="24312-114">W innych przypadkach CLR spowoduje zatrzymanie niektórych zarządzanych wątków (tła) bez dostarczanie wiadomości uporządkowany zniszczenie dla nich.</span><span class="sxs-lookup"><span data-stu-id="24312-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24312-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24312-115">Requirements</span></span>  
 <span data-ttu-id="24312-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24312-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24312-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24312-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24312-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24312-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24312-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24312-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24312-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24312-120">See Also</span></span>  
 [<span data-ttu-id="24312-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="24312-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="24312-122">Initialize, metoda</span><span class="sxs-lookup"><span data-stu-id="24312-122">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
