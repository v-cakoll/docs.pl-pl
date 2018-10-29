---
title: ICorProfilerInfo4 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27cce8a77d4236829124b45650d5d0ac32a5150c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198006"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="efcfb-102">ICorProfilerInfo4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="efcfb-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="efcfb-103">Udostępnia metody, które profilery kodu używać do komunikowania się za pomocą środowiska uruchomieniowego języka wspólnego (CLR) do kontrolowania, monitorowanie zdarzeń i informacje o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="efcfb-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="efcfb-104">.</span><span class="sxs-lookup"><span data-stu-id="efcfb-104">.</span></span> <span data-ttu-id="efcfb-105">`ICorProfilerInfo4` Interfejs jest rozszerzeniem innych `ICorProfilerInfo` interfejsów.</span><span class="sxs-lookup"><span data-stu-id="efcfb-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="efcfb-106">Zapewnia nowe metody obsługi ponownej kompilacji just-in-time (JIT), dodane w [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="efcfb-106">It provides new methods to support just-in-time (JIT) recompilation, added in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="methods"></a><span data-ttu-id="efcfb-107">Metody</span><span class="sxs-lookup"><span data-stu-id="efcfb-107">Methods</span></span>  
  
|<span data-ttu-id="efcfb-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="efcfb-108">Method</span></span>|<span data-ttu-id="efcfb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="efcfb-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="efcfb-110">EnumJITedFunctions2, metoda</span><span class="sxs-lookup"><span data-stu-id="efcfb-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="efcfb-111">Zwraca moduł wyliczający dla wszystkich funkcji, które wcześniej były skompilowane JIT i ponownie skompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="efcfb-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="efcfb-112">EnumThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="efcfb-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="efcfb-113">Pobiera moduł wyliczający, który udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji wszystkie zarządzane wątki w profilowanym procesie.</span><span class="sxs-lookup"><span data-stu-id="efcfb-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="efcfb-114">GetCodeInfo3, metoda</span><span class="sxs-lookup"><span data-stu-id="efcfb-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="efcfb-115">Pobiera zakres skojarzony z wersją określoną funkcję ponownie skompilowana JIT kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="efcfb-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="efcfb-116">GetFunctionFromIP2, metoda</span><span class="sxs-lookup"><span data-stu-id="efcfb-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="efcfb-117">Mapuje wskaźnik instrukcji kodu zarządzanego do wersji ponownie skompilowana JIT określoną funkcję.</span><span class="sxs-lookup"><span data-stu-id="efcfb-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="efcfb-118">GetILToNativeMapping2, metoda</span><span class="sxs-lookup"><span data-stu-id="efcfb-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="efcfb-119">Pobiera mapę od firmy Microsoft intermediate language (MSIL) przesuwa się do macierzystych przesunięciach kod zawarty w wersji ponownie skompilowana JIT określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="efcfb-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="efcfb-120">GetObjectSize2, metoda</span><span class="sxs-lookup"><span data-stu-id="efcfb-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="efcfb-121">Zwraca rozmiar określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="efcfb-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="efcfb-122">GetReJITIDs, metoda</span><span class="sxs-lookup"><span data-stu-id="efcfb-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="efcfb-123">Zwraca tablicę identyfikatorów, które identyfikują wszystkie ponownie skompilowana JIT wersje określonej funkcji, które nadal są przydzielane.</span><span class="sxs-lookup"><span data-stu-id="efcfb-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="efcfb-124">InitializeCurrentThread, metoda</span><span class="sxs-lookup"><span data-stu-id="efcfb-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="efcfb-125">Inicjuje bieżący wątek ewentualnej profilującym kolejnych wywołań interfejsu API w tym samym wątku, dzięki czemu można uniknąć tego zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="efcfb-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="efcfb-126">RequestReJIT, metoda</span><span class="sxs-lookup"><span data-stu-id="efcfb-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="efcfb-127">Żąda JIT — rekompilacja wszystkich wystąpień określonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="efcfb-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="efcfb-128">RequestRevert, metoda</span><span class="sxs-lookup"><span data-stu-id="efcfb-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="efcfb-129">Przywraca wszystkie wystąpienia określonych funkcji do ich oryginalnej wersji.</span><span class="sxs-lookup"><span data-stu-id="efcfb-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efcfb-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="efcfb-130">Remarks</span></span>  
 <span data-ttu-id="efcfb-131">Środowisko CLR implementuje metody `ICorProfilerInfo4` interfejsu przy użyciu modelu bezwątkowy.</span><span class="sxs-lookup"><span data-stu-id="efcfb-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="efcfb-132">Każda metoda zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="efcfb-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="efcfb-133">Aby uzyskać listę możliwych kodów powrotnych zobacz plik CorError.h.</span><span class="sxs-lookup"><span data-stu-id="efcfb-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efcfb-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="efcfb-134">Requirements</span></span>  
 <span data-ttu-id="efcfb-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efcfb-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efcfb-136">**Nagłówek:** } CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="efcfb-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="efcfb-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efcfb-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efcfb-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efcfb-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efcfb-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efcfb-139">See Also</span></span>  
 [<span data-ttu-id="efcfb-140">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="efcfb-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="efcfb-141">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="efcfb-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
