---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished — metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b5ead8b5428d855b7dab81dced1de6325fd07b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455000"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="815e3-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished — metoda</span><span class="sxs-lookup"><span data-stu-id="815e3-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="815e3-103">[Obsługiwane w programie .NET Framework 4.7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="815e3-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="815e3-104">Powiadamia profilera, gdy kompilacja JIT dynamicznej metody została ukończona.</span><span class="sxs-lookup"><span data-stu-id="815e3-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="815e3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="815e3-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="815e3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="815e3-106">Parameters</span></span>  
<span data-ttu-id="815e3-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="815e3-107">[in] `functionId`</span></span>  
<span data-ttu-id="815e3-108">Identyfikator funkcji w pamięci, dla których JIT kompilacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="815e3-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="815e3-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="815e3-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="815e3-110">Wartość, która wskazuje, czy kompilacja JIT zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="815e3-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="815e3-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="815e3-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="815e3-112">`true` Aby wskazać, że blokowanie może spowodować środowiska uruchomieniowego oczekiwania na wątek wywołujący do zwrócenia z tego wywołania zwrotnego; `false` wskazująca, czy blokowanie nie wpływa na działanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="815e3-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="815e3-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="815e3-113">Remarks</span></span>  

<span data-ttu-id="815e3-114">To wywołanie zwrotne jest zawsze wyzwalane, gdy kompilacja JIT dynamicznej metody została ukończona.</span><span class="sxs-lookup"><span data-stu-id="815e3-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="815e3-115">W tym różnych klas zastępczych IL i LCG metody.</span><span class="sxs-lookup"><span data-stu-id="815e3-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="815e3-116">Jego celem jest zapewnienie autorów profilera wystarczających informacji do identyfikowania metody skompilowanej dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="815e3-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="815e3-117">`functionId` wartości nie może służyć do rozwiązania do tokenów metadanych, ponieważ metadanych nie ma metody dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="815e3-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="815e3-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="815e3-118">Requirements</span></span>  
 <span data-ttu-id="815e3-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="815e3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="815e3-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="815e3-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="815e3-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="815e3-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="815e3-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="815e3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815e3-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="815e3-123">See Also</span></span>  
 [<span data-ttu-id="815e3-124">DynamicMethodJITCompilationStarted — metoda</span><span class="sxs-lookup"><span data-stu-id="815e3-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
 [<span data-ttu-id="815e3-125">Interfejs ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="815e3-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
