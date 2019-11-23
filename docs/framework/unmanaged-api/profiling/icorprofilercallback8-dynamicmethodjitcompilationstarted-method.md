---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 1eaf29e1c93f352facde4af2ee57910783d82e5d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136463"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="ab8d0-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span><span class="sxs-lookup"><span data-stu-id="ab8d0-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="ab8d0-103">[Obsługiwane w .NET Framework 4,7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="ab8d0-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="ab8d0-104">Powiadamia profiler za każdym razem, gdy została rozpoczęta kompilacja JIT metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="ab8d0-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab8d0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab8d0-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab8d0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab8d0-106">Parameters</span></span>  
<span data-ttu-id="ab8d0-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="ab8d0-107">[in] `functionId`</span></span>  
<span data-ttu-id="ab8d0-108">Identyfikator funkcji w pamięci, dla której uruchomiono kompilację JIT.</span><span class="sxs-lookup"><span data-stu-id="ab8d0-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="ab8d0-109">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="ab8d0-109">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="ab8d0-110">`true` wskazujący, że blokowanie może spowodować, że środowisko uruchomieniowe będzie oczekiwać na zwrócenie przez wątek wywołujący z tego wywołania zwrotnego; `false` wskazujący, że blokowanie nie ma wpływu na działanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ab8d0-110">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="ab8d0-111">[in] `pILHeader`  </span><span class="sxs-lookup"><span data-stu-id="ab8d0-111">[in] `pILHeader`  </span></span>  
<span data-ttu-id="ab8d0-112">Wskaźnik do pierwszego bajtu nagłówka IL metody.</span><span class="sxs-lookup"><span data-stu-id="ab8d0-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="ab8d0-113">[in] `cbILHeader`  </span><span class="sxs-lookup"><span data-stu-id="ab8d0-113">[in] `cbILHeader`  </span></span>  
<span data-ttu-id="ab8d0-114">Liczba bajtów w nagłówku IL.</span><span class="sxs-lookup"><span data-stu-id="ab8d0-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="ab8d0-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab8d0-115">Remarks</span></span>  

<span data-ttu-id="ab8d0-116">To wywołanie zwrotne jest wyzwalane za każdym razem, gdy metoda dynamiczna jest skompilowana w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="ab8d0-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="ab8d0-117">Obejmuje to różne metody pośredniczące IL i LCG.</span><span class="sxs-lookup"><span data-stu-id="ab8d0-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="ab8d0-118">Celem jest zapewnienie autorom profilera wystarczającej ilości informacji do zidentyfikowania skompilowanej metody dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="ab8d0-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="ab8d0-119">wartości `functionId` nie można użyć do rozpoznania swoich tokenów metadanych, ponieważ metody dynamiczne nie mają metadanych.</span><span class="sxs-lookup"><span data-stu-id="ab8d0-119">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="ab8d0-120">Wskaźnik `pILHeader` jest prawidłowy tylko podczas wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ab8d0-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="ab8d0-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab8d0-121">Requirements</span></span>  
 <span data-ttu-id="ab8d0-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab8d0-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab8d0-123">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ab8d0-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab8d0-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ab8d0-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab8d0-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ab8d0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab8d0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab8d0-126">See also</span></span>

- [<span data-ttu-id="ab8d0-127">DynamicMethodJITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="ab8d0-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="ab8d0-128">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="ab8d0-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
