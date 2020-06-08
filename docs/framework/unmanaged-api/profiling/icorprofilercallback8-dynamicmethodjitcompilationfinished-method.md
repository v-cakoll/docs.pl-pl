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
ms.openlocfilehash: 554cc93de934061e87322c7557e05545e5e7bc62
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499080"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="e1ab0-102">ICorProfilerCallback8::D ynamicMethodJITCompilationFinished Metoda</span><span class="sxs-lookup"><span data-stu-id="e1ab0-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="e1ab0-103">[Obsługiwane w .NET Framework 4,7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="e1ab0-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="e1ab0-104">Powiadamia profiler za każdym razem, gdy kompilacja JIT metody dynamicznej została ukończona.</span><span class="sxs-lookup"><span data-stu-id="e1ab0-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1ab0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1ab0-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1ab0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1ab0-106">Parameters</span></span>  
<span data-ttu-id="e1ab0-107">podczas`functionId`</span><span class="sxs-lookup"><span data-stu-id="e1ab0-107">[in] `functionId`</span></span>  
<span data-ttu-id="e1ab0-108">Identyfikator funkcji w pamięci, dla której uruchomiono kompilację JIT.</span><span class="sxs-lookup"><span data-stu-id="e1ab0-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="e1ab0-109">[w] `hrStatus` Wartość wskazująca, czy kompilacja JIT zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e1ab0-109">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="e1ab0-110">[w] `fIsSafeToBlock` 
 `true` Aby wskazać, że blokowanie może spowodować, że środowisko uruchomieniowe będzie oczekiwać na zwrócenie przez wątek wywołujący z tego wywołania zwrotnego; `false`, aby wskazać, że blokowanie nie wpłynie na działanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e1ab0-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="e1ab0-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1ab0-111">Remarks</span></span>  

<span data-ttu-id="e1ab0-112">To wywołanie zwrotne jest wyzwalane za każdym razem, gdy kompilacja JIT metody dynamicznej została zakończona.</span><span class="sxs-lookup"><span data-stu-id="e1ab0-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="e1ab0-113">Obejmuje to różne metody pośredniczące IL i LCG.</span><span class="sxs-lookup"><span data-stu-id="e1ab0-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="e1ab0-114">Celem jest zapewnienie autorom profilera wystarczającej ilości informacji do zidentyfikowania skompilowanej metody dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="e1ab0-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="e1ab0-115">`functionId`wartości nie można użyć do rozpoznania ich tokenów metadanych, ponieważ metody dynamiczne nie mają metadanych.</span><span class="sxs-lookup"><span data-stu-id="e1ab0-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="e1ab0-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1ab0-116">Requirements</span></span>  
 <span data-ttu-id="e1ab0-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1ab0-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1ab0-118">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e1ab0-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1ab0-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e1ab0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1ab0-120">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e1ab0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1ab0-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1ab0-121">See also</span></span>

- [<span data-ttu-id="e1ab0-122">DynamicMethodJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="e1ab0-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="e1ab0-123">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1ab0-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
