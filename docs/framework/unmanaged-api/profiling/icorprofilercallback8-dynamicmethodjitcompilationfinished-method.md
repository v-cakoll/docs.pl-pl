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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206593"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="09385-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span><span class="sxs-lookup"><span data-stu-id="09385-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="09385-103">[Obsługiwane w programie .NET Framework 4.7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="09385-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="09385-104">Powiadamia program profilujący, zawsze wtedy, gdy kompilacja JIT dynamicznej metody została ukończona.</span><span class="sxs-lookup"><span data-stu-id="09385-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09385-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="09385-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09385-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="09385-106">Parameters</span></span>  
<span data-ttu-id="09385-107">[in]</span><span class="sxs-lookup"><span data-stu-id="09385-107">[in]</span></span> `functionId`  
<span data-ttu-id="09385-108">Identyfikator funkcji w pamięci, dla których JIT kompilacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="09385-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="09385-109">[in]</span><span class="sxs-lookup"><span data-stu-id="09385-109">[in]</span></span> `hrStatus`   
<span data-ttu-id="09385-110">Wartość, która wskazuje, czy kompilacja JIT zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="09385-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="09385-111">[in]</span><span class="sxs-lookup"><span data-stu-id="09385-111">[in]</span></span> `fIsSafeToBlock`   
`true` <span data-ttu-id="09385-112">Aby wskazać, że blokuje może spowodować, że środowisko uruchomieniowe oczekiwania na wątek wywołujący, zostać zwrócony przez to wywołanie zwrotne; `false` do wskazania, że blokuje nie wpłynie na funkcjonowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="09385-112">to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="09385-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09385-113">Remarks</span></span>  

<span data-ttu-id="09385-114">To wywołanie zwrotne jest zawsze wyzwalane, gdy kompilacja JIT dynamicznej metody zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="09385-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="09385-115">Obejmuje to różne wycinki kodu IL i LCG metody.</span><span class="sxs-lookup"><span data-stu-id="09385-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="09385-116">Jego celem jest zapewnienie autorzy profilera wystarczających informacji do identyfikowania metody skompilowanej dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="09385-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> `functionId` <span data-ttu-id="09385-117">Nie można użyć wartości do rozpoznawania tokenów metadanych, ponieważ metody dynamiczne mają Brak metadanych.</span><span class="sxs-lookup"><span data-stu-id="09385-117">values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="09385-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09385-118">Requirements</span></span>  
 <span data-ttu-id="09385-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09385-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09385-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="09385-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="09385-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09385-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="09385-122">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="09385-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="09385-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09385-123">See also</span></span>

- [<span data-ttu-id="09385-124">DynamicMethodJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="09385-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="09385-125">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="09385-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
