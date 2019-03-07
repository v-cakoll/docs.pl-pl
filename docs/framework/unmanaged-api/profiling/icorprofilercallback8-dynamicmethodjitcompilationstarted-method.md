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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 170d0b20069724a4e1845be0250b2897daa10dee
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501243"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="0fa0b-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span><span class="sxs-lookup"><span data-stu-id="0fa0b-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="0fa0b-103">[Obsługiwane w programie .NET Framework 4.7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="0fa0b-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="0fa0b-104">Powiadamia program profilujący, zawsze wtedy, gdy rozpoczęto kompilację JIT metodę dynamiczną.</span><span class="sxs-lookup"><span data-stu-id="0fa0b-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fa0b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fa0b-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fa0b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0fa0b-106">Parameters</span></span>  
<span data-ttu-id="0fa0b-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="0fa0b-107">[in] `functionId`</span></span>  
<span data-ttu-id="0fa0b-108">Identyfikator funkcji w pamięci, dla których JIT kompilacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="0fa0b-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="0fa0b-109">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="0fa0b-109">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="0fa0b-110">`true` Aby wskazać, że blokuje może spowodować, że środowisko uruchomieniowe oczekiwania na wątek wywołujący, zostać zwrócony przez to wywołanie zwrotne; `false` do wskazania, że blokuje nie wpłynie na funkcjonowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="0fa0b-110">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="0fa0b-111">[in] `pILHeader`  </span><span class="sxs-lookup"><span data-stu-id="0fa0b-111">[in] `pILHeader`  </span></span>  
<span data-ttu-id="0fa0b-112">Wskaźnik do pierwszego bajtu nagłówek IL metody.</span><span class="sxs-lookup"><span data-stu-id="0fa0b-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="0fa0b-113">[in] `cbILHeader`  </span><span class="sxs-lookup"><span data-stu-id="0fa0b-113">[in] `cbILHeader`  </span></span>  
<span data-ttu-id="0fa0b-114">Liczba bajtów w nagłówku IL.</span><span class="sxs-lookup"><span data-stu-id="0fa0b-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="0fa0b-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0fa0b-115">Remarks</span></span>  

<span data-ttu-id="0fa0b-116">To wywołanie zwrotne jest wywoływane zawsze wtedy, gdy metoda dynamiczna kompilowanego dokładnie na czas.</span><span class="sxs-lookup"><span data-stu-id="0fa0b-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="0fa0b-117">Obejmuje to różne wycinki kodu IL i LCG metody.</span><span class="sxs-lookup"><span data-stu-id="0fa0b-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="0fa0b-118">Jego celem jest zapewnienie autorzy profilera wystarczających informacji do identyfikowania metody skompilowanej dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="0fa0b-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="0fa0b-119">`functionId` Nie można użyć wartości do rozpoznawania tokenów metadanych, ponieważ metody dynamiczne mają Brak metadanych.</span><span class="sxs-lookup"><span data-stu-id="0fa0b-119">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="0fa0b-120">`pILHeader` Wskaźnik jest prawidłowy tylko podczas wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="0fa0b-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="0fa0b-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0fa0b-121">Requirements</span></span>  
 <span data-ttu-id="0fa0b-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fa0b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fa0b-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0fa0b-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0fa0b-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fa0b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fa0b-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0fa0b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fa0b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fa0b-126">See also</span></span>
- [<span data-ttu-id="0fa0b-127">DynamicMethodJITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="0fa0b-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="0fa0b-128">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="0fa0b-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
