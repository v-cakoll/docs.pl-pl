---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationStarted Metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: a4c434c5d458602db8a4d582b239d6e57def6ace
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499002"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="b0232-102">ICorProfilerCallback8::D ynamicMethodJITCompilationStarted Metoda</span><span class="sxs-lookup"><span data-stu-id="b0232-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="b0232-103">[Obsługiwane w .NET Framework 4,7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="b0232-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="b0232-104">Powiadamia profiler za każdym razem, gdy została rozpoczęta kompilacja JIT metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="b0232-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0232-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0232-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0232-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0232-106">Parameters</span></span>  
<span data-ttu-id="b0232-107">podczas`functionId`</span><span class="sxs-lookup"><span data-stu-id="b0232-107">[in] `functionId`</span></span>  
<span data-ttu-id="b0232-108">Identyfikator funkcji w pamięci, dla której uruchomiono kompilację JIT.</span><span class="sxs-lookup"><span data-stu-id="b0232-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="b0232-109">[w] `fIsSafeToBlock` 
 `true` Aby wskazać, że blokowanie może spowodować, że środowisko uruchomieniowe będzie oczekiwać na zwrócenie przez wątek wywołujący z tego wywołania zwrotnego; `false`, aby wskazać, że blokowanie nie wpłynie na działanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b0232-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="b0232-110">[w] `pILHeader` Wskaźnik do pierwszego bajtu nagłówka IL metody.</span><span class="sxs-lookup"><span data-stu-id="b0232-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="b0232-111">[w] `cbILHeader` Liczba bajtów w nagłówku IL.</span><span class="sxs-lookup"><span data-stu-id="b0232-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0232-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0232-112">Remarks</span></span>  

<span data-ttu-id="b0232-113">To wywołanie zwrotne jest wyzwalane za każdym razem, gdy metoda dynamiczna jest skompilowana w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="b0232-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="b0232-114">Obejmuje to różne metody pośredniczące IL i LCG.</span><span class="sxs-lookup"><span data-stu-id="b0232-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="b0232-115">Celem jest zapewnienie autorom profilera wystarczającej ilości informacji do zidentyfikowania skompilowanej metody dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="b0232-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="b0232-116">`functionId`wartości nie można użyć do rozpoznania ich tokenów metadanych, ponieważ metody dynamiczne nie mają metadanych.</span><span class="sxs-lookup"><span data-stu-id="b0232-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="b0232-117">`pILHeader`Wskaźnik jest prawidłowy tylko podczas wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b0232-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0232-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0232-118">Requirements</span></span>  
 <span data-ttu-id="b0232-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0232-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0232-120">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b0232-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0232-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b0232-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0232-122">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b0232-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0232-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0232-123">See also</span></span>

- [<span data-ttu-id="b0232-124">DynamicMethodJITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="b0232-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="b0232-125">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0232-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
