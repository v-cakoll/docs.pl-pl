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
ms.openlocfilehash: 1abc4dd209581c9f7c8e950ea1addc74c611d248
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787949"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="a702b-102">ICorProfilerCallback::JITCompilationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="a702b-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="a702b-103">Powiadamia program profilujący, że kompilator just-in-time (JIT) została zakończona, kompilowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="a702b-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a702b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a702b-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a702b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a702b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a702b-106">[in] Identyfikator funkcji, który został skompilowany.</span><span class="sxs-lookup"><span data-stu-id="a702b-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="a702b-107">[in] Wartość wskazująca, czy kompilacja zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="a702b-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="a702b-108">[in] Wartość do programu profilującego wskazującą, czy blokowanie wpłynie na funkcjonowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a702b-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="a702b-109">Wartość jest `true` Jeśli blokowanie może spowodować, że środowisko uruchomieniowe oczekiwania na wątek wywołujący, zostać zwrócony przez to wywołanie zwrotne; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="a702b-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="a702b-110">Mimo, że wartość `true` nie uszkodzi środowiska uruchomieniowego, jego pochylanie wyniki profilowania.</span><span class="sxs-lookup"><span data-stu-id="a702b-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a702b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a702b-111">Requirements</span></span>  
 <span data-ttu-id="a702b-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a702b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a702b-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a702b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a702b-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a702b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a702b-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a702b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a702b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a702b-116">See also</span></span>

- [<span data-ttu-id="a702b-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="a702b-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a702b-118">JITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="a702b-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
