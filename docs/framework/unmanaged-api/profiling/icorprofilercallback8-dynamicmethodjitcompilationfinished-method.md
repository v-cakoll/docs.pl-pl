---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method
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
ms.openlocfilehash: 9dbe8d4f7050b93ffb34280be6d63367ef294ae8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049716"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="19cdb-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span><span class="sxs-lookup"><span data-stu-id="19cdb-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="19cdb-103">[Obsługiwane w programie .NET Framework 4.7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="19cdb-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="19cdb-104">Powiadamia program profilujący, zawsze wtedy, gdy kompilacja JIT dynamicznej metody została ukończona.</span><span class="sxs-lookup"><span data-stu-id="19cdb-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19cdb-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="19cdb-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19cdb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="19cdb-106">Parameters</span></span>  
<span data-ttu-id="19cdb-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="19cdb-107">[in] `functionId`</span></span>  
<span data-ttu-id="19cdb-108">Identyfikator funkcji w pamięci, dla których JIT kompilacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="19cdb-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="19cdb-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="19cdb-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="19cdb-110">Wartość, która wskazuje, czy kompilacja JIT zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="19cdb-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="19cdb-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="19cdb-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="19cdb-112">`true` Aby wskazać, że blokuje może spowodować, że środowisko uruchomieniowe oczekiwania na wątek wywołujący, zostać zwrócony przez to wywołanie zwrotne; `false` do wskazania, że blokuje nie wpłynie na funkcjonowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="19cdb-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="19cdb-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19cdb-113">Remarks</span></span>  

<span data-ttu-id="19cdb-114">To wywołanie zwrotne jest zawsze wyzwalane, gdy kompilacja JIT dynamicznej metody zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="19cdb-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="19cdb-115">Obejmuje to różne wycinki kodu IL i LCG metody.</span><span class="sxs-lookup"><span data-stu-id="19cdb-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="19cdb-116">Jego celem jest zapewnienie autorzy profilera wystarczających informacji do identyfikowania metody skompilowanej dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="19cdb-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="19cdb-117">`functionId` Nie można użyć wartości do rozpoznawania tokenów metadanych, ponieważ metody dynamiczne mają Brak metadanych.</span><span class="sxs-lookup"><span data-stu-id="19cdb-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="19cdb-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19cdb-118">Requirements</span></span>  
 <span data-ttu-id="19cdb-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19cdb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19cdb-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="19cdb-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="19cdb-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19cdb-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19cdb-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="19cdb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19cdb-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19cdb-123">See also</span></span>

- [<span data-ttu-id="19cdb-124">DynamicMethodJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="19cdb-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="19cdb-125">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="19cdb-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
