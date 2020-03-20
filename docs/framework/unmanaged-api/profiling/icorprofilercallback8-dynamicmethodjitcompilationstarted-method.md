---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted Metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: e8b1a243b691d8d5eb364fd16821fd9156505c60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177049"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="372c4-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Metoda</span><span class="sxs-lookup"><span data-stu-id="372c4-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="372c4-103">[Obsługiwane w .NET Framework 4.7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="372c4-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="372c4-104">Powiadamia profiler przy każdym uruchomieniu kompilacji JIT metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="372c4-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="372c4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="372c4-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="372c4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="372c4-106">Parameters</span></span>  
<span data-ttu-id="372c4-107">[w]`functionId`</span><span class="sxs-lookup"><span data-stu-id="372c4-107">[in] `functionId`</span></span>  
<span data-ttu-id="372c4-108">Identyfikator funkcji w pamięci, dla której jest uruchomiona kompilacja JIT.</span><span class="sxs-lookup"><span data-stu-id="372c4-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="372c4-109">[w] `fIsSafeToBlock` aby wskazać, że blokowanie może spowodować, że środowisko uruchomieniowe czekać na wątek wywołujący do powrotu z tego wywołania zwrotnego; 
 `true` `false` , aby wskazać, że blokowanie nie wpłynie na działanie środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="372c4-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="372c4-110">[w] `pILHeader` Wskaźnik do pierwszego bajtu nagłówka IL metody.</span><span class="sxs-lookup"><span data-stu-id="372c4-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="372c4-111">[w] `cbILHeader` Liczba bajtów w nagłówku IL.</span><span class="sxs-lookup"><span data-stu-id="372c4-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="372c4-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="372c4-112">Remarks</span></span>  

<span data-ttu-id="372c4-113">To wywołanie zwrotne jest wyzwalane, gdy metoda dynamiczna jest skompilowana przez JIT.</span><span class="sxs-lookup"><span data-stu-id="372c4-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="372c4-114">Obejmuje to różne wycinki IL i metody LCG.</span><span class="sxs-lookup"><span data-stu-id="372c4-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="372c4-115">Jego celem jest dostarczenie pisarzom profilerów wystarczającej ilości informacji, aby zidentyfikować skompilowaną metodę dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="372c4-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="372c4-116">`functionId`wartości nie mogą być używane do rozpoznawania ich tokenów metadanych, ponieważ metody dynamiczne nie mają metadanych.</span><span class="sxs-lookup"><span data-stu-id="372c4-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="372c4-117">Wskaźnik `pILHeader` jest prawidłowy tylko podczas wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="372c4-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="372c4-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="372c4-118">Requirements</span></span>  
 <span data-ttu-id="372c4-119">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="372c4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="372c4-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="372c4-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="372c4-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="372c4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="372c4-122">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="372c4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="372c4-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="372c4-123">See also</span></span>

- [<span data-ttu-id="372c4-124">DynamicMethodJITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="372c4-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="372c4-125">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="372c4-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
