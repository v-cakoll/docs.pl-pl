---
title: ICorProfilerCallback8::DynamicMethodJITKomunikacjaKończa metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c2e9489654a0fe5fa65ec638ed0f991a6c01415a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175112"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="f2b55-102">ICorProfilerCallback8::DynamicMethodJITKomunikacjaKończa metoda</span><span class="sxs-lookup"><span data-stu-id="f2b55-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="f2b55-103">[Obsługiwane w .NET Framework 4.7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="f2b55-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="f2b55-104">Powiadamia profiler po zakończeniu kompilacji JIT metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="f2b55-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2b55-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2b55-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2b55-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2b55-106">Parameters</span></span>  
<span data-ttu-id="f2b55-107">[w]`functionId`</span><span class="sxs-lookup"><span data-stu-id="f2b55-107">[in] `functionId`</span></span>  
<span data-ttu-id="f2b55-108">Identyfikator funkcji w pamięci, dla której jest uruchomiona kompilacja JIT.</span><span class="sxs-lookup"><span data-stu-id="f2b55-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="f2b55-109">[w] `hrStatus` Wartość, która wskazuje, czy kompilacja JIT zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f2b55-109">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="f2b55-110">[w] `fIsSafeToBlock` aby wskazać, że blokowanie może spowodować, że środowisko uruchomieniowe czekać na wątek wywołujący do powrotu z tego wywołania zwrotnego; 
 `true` `false` , aby wskazać, że blokowanie nie wpłynie na działanie środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="f2b55-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="f2b55-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2b55-111">Remarks</span></span>  

<span data-ttu-id="f2b55-112">To wywołanie zwrotne jest wyzwalane po zakończeniu kompilacji JIT metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="f2b55-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="f2b55-113">Obejmuje to różne wycinki IL i metody LCG.</span><span class="sxs-lookup"><span data-stu-id="f2b55-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="f2b55-114">Jego celem jest dostarczenie pisarzom profilerów wystarczającej ilości informacji, aby zidentyfikować skompilowaną metodę dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="f2b55-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="f2b55-115">`functionId`wartości nie mogą być używane do rozpoznawania ich tokenów metadanych, ponieważ metody dynamiczne nie mają metadanych.</span><span class="sxs-lookup"><span data-stu-id="f2b55-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="f2b55-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2b55-116">Requirements</span></span>  
 <span data-ttu-id="f2b55-117">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2b55-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2b55-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2b55-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2b55-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2b55-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2b55-120">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f2b55-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b55-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2b55-121">See also</span></span>

- [<span data-ttu-id="f2b55-122">DynamicMethodJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="f2b55-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="f2b55-123">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="f2b55-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
