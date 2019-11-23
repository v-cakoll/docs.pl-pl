---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationFinished Metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0e04459614ca697908fb9b71ecc3931ac305a838
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136583"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="4915f-102">ICorProfilerCallback8::D ynamicMethodJITCompilationFinished Metoda</span><span class="sxs-lookup"><span data-stu-id="4915f-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="4915f-103">[Obsługiwane w .NET Framework 4,7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="4915f-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="4915f-104">Powiadamia profiler za każdym razem, gdy kompilacja JIT metody dynamicznej została ukończona.</span><span class="sxs-lookup"><span data-stu-id="4915f-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4915f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4915f-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4915f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4915f-106">Parameters</span></span>  
<span data-ttu-id="4915f-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="4915f-107">[in] `functionId`</span></span>  
<span data-ttu-id="4915f-108">Identyfikator funkcji w pamięci, dla której uruchomiono kompilację JIT.</span><span class="sxs-lookup"><span data-stu-id="4915f-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="4915f-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="4915f-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="4915f-110">Wartość wskazująca, czy kompilacja JIT zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4915f-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="4915f-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="4915f-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="4915f-112">`true` wskazujący, że blokowanie może spowodować, że środowisko uruchomieniowe będzie oczekiwać na zwrócenie przez wątek wywołujący z tego wywołania zwrotnego; `false` wskazujący, że blokowanie nie ma wpływu na działanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="4915f-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="4915f-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4915f-113">Remarks</span></span>  

<span data-ttu-id="4915f-114">To wywołanie zwrotne jest wyzwalane za każdym razem, gdy kompilacja JIT metody dynamicznej została zakończona.</span><span class="sxs-lookup"><span data-stu-id="4915f-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="4915f-115">Obejmuje to różne metody pośredniczące IL i LCG.</span><span class="sxs-lookup"><span data-stu-id="4915f-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="4915f-116">Celem jest zapewnienie autorom profilera wystarczającej ilości informacji do zidentyfikowania skompilowanej metody dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="4915f-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="4915f-117">wartości `functionId` nie można użyć do rozpoznania swoich tokenów metadanych, ponieważ metody dynamiczne nie mają metadanych.</span><span class="sxs-lookup"><span data-stu-id="4915f-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="4915f-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4915f-118">Requirements</span></span>  
 <span data-ttu-id="4915f-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4915f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4915f-120">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4915f-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4915f-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4915f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4915f-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4915f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4915f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4915f-123">See also</span></span>

- [<span data-ttu-id="4915f-124">DynamicMethodJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="4915f-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="4915f-125">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="4915f-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
