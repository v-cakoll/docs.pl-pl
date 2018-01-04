---
title: "ICorProfilerCallback3::ProfilerDetachSucceeded — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d06671917094752287836800ebc492d5f0a5b595
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="cadca-102">ICorProfilerCallback3::ProfilerDetachSucceeded — Metoda</span><span class="sxs-lookup"><span data-stu-id="cadca-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="cadca-103">Powiadamia profilera środowisko uruchomieniowe języka wspólnego (CLR) o zbliżającym się zwolnienia biblioteki DLL profilera.</span><span class="sxs-lookup"><span data-stu-id="cadca-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cadca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cadca-104">Syntax</span></span>  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cadca-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cadca-105">Return Value</span></span>  
 <span data-ttu-id="cadca-106">Wartość zwracana z tego wywołania zwrotnego jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="cadca-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cadca-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cadca-107">Remarks</span></span>  
 <span data-ttu-id="cadca-108">`ProfilerDetachSucceeded` Wywołania zwrotnego jest wystawianym po zamknięciu kodu profilera wszystkie wątki.</span><span class="sxs-lookup"><span data-stu-id="cadca-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="cadca-109">Gdy ta metoda jest wywoływana, profilera, należy wykonać wszystkie zadania ostatniej minuty, które nie są odpowiednie do jego destruktor, takich jak powiadamiania jego interfejsu użytkownika lub rejestrowania składnika.</span><span class="sxs-lookup"><span data-stu-id="cadca-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="cadca-110">Jednak profilera nie mogą wywoływać funkcje na interfejsy, które są udostępniane przez środowisko CLR Podczas tego wywołania zwrotnego (takich jak [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) lub `IMetaData*` interfejsów).</span><span class="sxs-lookup"><span data-stu-id="cadca-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="cadca-111">Środowisko CLR tworzy wpis w dzienniku zdarzeń aplikacji systemu Windows, aby wskazać, czy operacja odłączenia zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cadca-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="cadca-112">Po powrocie profilera z tego wywołania zwrotnego, CLR zwalnia obiektu profilera i zwalnia biblioteki DLL profilera.</span><span class="sxs-lookup"><span data-stu-id="cadca-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="cadca-113">W związku z tym profilera nie musi wykonywać wszystkie akcje, które mogłoby spowodować wykonanie wystąpienia wewnątrz biblioteki DLL profilera zwraca to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="cadca-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="cadca-114">Na przykład nie musi utworzyć wątków lub rejestrowania wywołań zwrotnych czasomierza.</span><span class="sxs-lookup"><span data-stu-id="cadca-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cadca-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cadca-115">Requirements</span></span>  
 <span data-ttu-id="cadca-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cadca-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cadca-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cadca-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cadca-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cadca-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cadca-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cadca-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cadca-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cadca-120">See Also</span></span>  
 [<span data-ttu-id="cadca-121">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="cadca-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="cadca-122">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="cadca-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="cadca-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="cadca-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="cadca-124">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="cadca-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
