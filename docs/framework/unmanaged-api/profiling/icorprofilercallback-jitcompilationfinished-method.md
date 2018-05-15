---
title: ICorProfilerCallback::JITCompilationFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dbf447e1325b4acaa26c9bb16d7d1a736eb20a29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="f76a8-102">ICorProfilerCallback::JITCompilationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="f76a8-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="f76a8-103">Powiadamia profilera przy użyciu kompilatora just in time (JIT) zostało zakończone, kompilowanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="f76a8-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f76a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f76a8-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f76a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f76a8-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f76a8-106">[in] Identyfikator funkcji, która została skompilowana.</span><span class="sxs-lookup"><span data-stu-id="f76a8-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="f76a8-107">[in] Wartość wskazująca, czy kompilacja zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f76a8-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="f76a8-108">[in] Wartość wskazującą profilera, czy blokowanie będzie miało wpływ na działanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f76a8-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="f76a8-109">Wartość jest `true` Jeśli blokuje może spowodować środowiska uruchomieniowego oczekiwania na wątek wywołujący do zwrócenia z tego wywołania zwrotnego; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="f76a8-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="f76a8-110">Chociaż wartość `true` nie będzie uszkodzić środowiska uruchomieniowego, jego pochylanie wyniki profilowania.</span><span class="sxs-lookup"><span data-stu-id="f76a8-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f76a8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f76a8-111">Requirements</span></span>  
 <span data-ttu-id="f76a8-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f76a8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f76a8-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f76a8-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f76a8-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f76a8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f76a8-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f76a8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f76a8-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f76a8-116">See Also</span></span>  
 [<span data-ttu-id="f76a8-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="f76a8-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="f76a8-118">JITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="f76a8-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
