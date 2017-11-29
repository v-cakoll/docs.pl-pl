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
ms.openlocfilehash: d4413e5c475bce6d6f2eea1f7a968c946237f47a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="58154-102">ICorProfilerCallback3::ProfilerDetachSucceeded — Metoda</span><span class="sxs-lookup"><span data-stu-id="58154-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="58154-103">Powiadamia profilera środowisko uruchomieniowe języka wspólnego (CLR) o zbliżającym się zwolnienia biblioteki DLL profilera.</span><span class="sxs-lookup"><span data-stu-id="58154-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58154-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58154-104">Syntax</span></span>  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="58154-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="58154-105">Return Value</span></span>  
 <span data-ttu-id="58154-106">Wartość zwracana z tego wywołania zwrotnego jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="58154-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58154-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58154-107">Remarks</span></span>  
 <span data-ttu-id="58154-108">`ProfilerDetachSucceeded` Wywołania zwrotnego jest wystawianym po zamknięciu kodu profilera wszystkie wątki.</span><span class="sxs-lookup"><span data-stu-id="58154-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="58154-109">Gdy ta metoda jest wywoływana, profilera, należy wykonać wszystkie zadania ostatniej minuty, które nie są odpowiednie do jego destruktor, takich jak powiadamiania jego interfejsu użytkownika lub rejestrowania składnika.</span><span class="sxs-lookup"><span data-stu-id="58154-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="58154-110">Jednak profilera nie mogą wywoływać funkcje na interfejsy, które są udostępniane przez środowisko CLR Podczas tego wywołania zwrotnego (takich jak [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) lub `IMetaData*` interfejsów).</span><span class="sxs-lookup"><span data-stu-id="58154-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="58154-111">Środowisko CLR tworzy wpis w dzienniku zdarzeń aplikacji systemu Windows, aby wskazać, czy operacja odłączenia zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="58154-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="58154-112">Po powrocie profilera z tego wywołania zwrotnego, CLR zwalnia obiektu profilera i zwalnia biblioteki DLL profilera.</span><span class="sxs-lookup"><span data-stu-id="58154-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="58154-113">W związku z tym profilera nie musi wykonywać wszystkie akcje, które mogłoby spowodować wykonanie wystąpienia wewnątrz biblioteki DLL profilera zwraca to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="58154-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="58154-114">Na przykład nie musi utworzyć wątków lub rejestrowania wywołań zwrotnych czasomierza.</span><span class="sxs-lookup"><span data-stu-id="58154-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58154-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="58154-115">Requirements</span></span>  
 <span data-ttu-id="58154-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58154-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58154-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="58154-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="58154-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58154-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58154-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58154-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58154-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58154-120">See Also</span></span>  
 [<span data-ttu-id="58154-121">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="58154-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="58154-122">ICorProfilerInfo3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="58154-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="58154-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="58154-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="58154-124">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="58154-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
