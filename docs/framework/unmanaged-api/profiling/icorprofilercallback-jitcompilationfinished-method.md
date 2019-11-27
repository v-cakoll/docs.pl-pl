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
ms.openlocfilehash: 1bbdfa93913b9fdf8aa164c8ca6c35cd33a228df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449918"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="b3735-102">ICorProfilerCallback::JITCompilationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="b3735-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="b3735-103">Powiadamia profiler, że kompilator just-in-Time (JIT) zakończył Kompilowanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="b3735-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3735-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3735-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3735-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3735-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b3735-106">podczas Identyfikator funkcji, która została skompilowana.</span><span class="sxs-lookup"><span data-stu-id="b3735-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="b3735-107">podczas Wartość wskazująca, czy kompilacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b3735-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="b3735-108">podczas Wartość wskazująca, czy blokowanie będzie miało wpływ na działanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b3735-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="b3735-109">Wartość jest `true`, jeśli blokowanie może spowodować, że środowisko uruchomieniowe będzie oczekiwać na zwrócenie przez wątek wywołujący z tego wywołania zwrotnego; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="b3735-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="b3735-110">Mimo że wartość `true` nie będzie szkodliwe dla środowiska uruchomieniowego, może pochylić wyniki profilowania.</span><span class="sxs-lookup"><span data-stu-id="b3735-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3735-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b3735-111">Requirements</span></span>  
 <span data-ttu-id="b3735-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3735-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3735-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b3735-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3735-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b3735-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3735-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3735-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3735-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3735-116">See also</span></span>

- [<span data-ttu-id="b3735-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="b3735-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b3735-118">JITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="b3735-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
