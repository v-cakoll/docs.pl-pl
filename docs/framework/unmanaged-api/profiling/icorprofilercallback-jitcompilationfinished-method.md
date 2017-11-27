---
title: "ICorProfilerCallback::JITCompilationFinished — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCompilationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9719ce1474c2111692c6176655b75bd2d7edf923
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="81a2b-102">ICorProfilerCallback::JITCompilationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="81a2b-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="81a2b-103">Powiadamia profilera przy użyciu kompilatora just in time (JIT) zostało zakończone, kompilowanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="81a2b-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81a2b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81a2b-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81a2b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81a2b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="81a2b-106">[in] Identyfikator funkcji, która została skompilowana.</span><span class="sxs-lookup"><span data-stu-id="81a2b-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="81a2b-107">[in] Wartość wskazująca, czy kompilacja zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="81a2b-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="81a2b-108">[in] Wartość wskazującą profilera, czy blokowanie będzie miało wpływ na działanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="81a2b-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="81a2b-109">Wartość jest `true` Jeśli blokuje może spowodować środowiska uruchomieniowego oczekiwania na wątek wywołujący do zwrócenia z tego wywołania zwrotnego; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="81a2b-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="81a2b-110">Chociaż wartość `true` nie będzie uszkodzić środowiska uruchomieniowego, jego pochylanie wyniki profilowania.</span><span class="sxs-lookup"><span data-stu-id="81a2b-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81a2b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81a2b-111">Requirements</span></span>  
 <span data-ttu-id="81a2b-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81a2b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81a2b-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="81a2b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="81a2b-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81a2b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81a2b-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81a2b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a2b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81a2b-116">See Also</span></span>  
 [<span data-ttu-id="81a2b-117">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="81a2b-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="81a2b-118">JITCompilationStarted — metoda</span><span class="sxs-lookup"><span data-stu-id="81a2b-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
