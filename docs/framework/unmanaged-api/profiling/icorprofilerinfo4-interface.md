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
ms.openlocfilehash: f452a3324365fb23e1affc11dbdb2ede15346010
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="5ed68-102">ICorProfilerInfo4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5ed68-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="5ed68-103">Udostępnia metody, które używają profilery kodu do komunikacji z środowisko uruchomieniowe języka wspólnego (CLR) w celu kontrolowania, monitorowanie zdarzeń i informacje o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="5ed68-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="5ed68-104">.</span><span class="sxs-lookup"><span data-stu-id="5ed68-104">.</span></span> <span data-ttu-id="5ed68-105">`ICorProfilerInfo4` Interfejsu jest rozszerzeniem innym `ICorProfilerInfo` interfejsów.</span><span class="sxs-lookup"><span data-stu-id="5ed68-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="5ed68-106">Zapewnia nowych metod do obsługi kompilację just-in-time (JIT), dodane w [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5ed68-106">It provides new methods to support just-in-time (JIT) recompilation, added in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ed68-107">Metody</span><span class="sxs-lookup"><span data-stu-id="5ed68-107">Methods</span></span>  
  
|<span data-ttu-id="5ed68-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="5ed68-108">Method</span></span>|<span data-ttu-id="5ed68-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5ed68-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ed68-110">EnumJITedFunctions2, metoda</span><span class="sxs-lookup"><span data-stu-id="5ed68-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="5ed68-111">Zwraca moduł wyliczający dla wszystkich funkcji, które były wcześniej kompilacji JIT i ponownie kompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="5ed68-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="5ed68-112">EnumThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="5ed68-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="5ed68-113">Pobiera moduł wyliczający, który, który udostępnia metody do sekwencyjnie iteracji kolekcji wszystkie wątki zarządzane PROFILOWANEGO procesu.</span><span class="sxs-lookup"><span data-stu-id="5ed68-113">Gets an enumerator that that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="5ed68-114">GetCodeInfo3, metoda</span><span class="sxs-lookup"><span data-stu-id="5ed68-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="5ed68-115">Pobiera zakres skojarzone z ponownie kompilowana JIT wersja określona funkcja kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="5ed68-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="5ed68-116">GetFunctionFromIP2, metoda</span><span class="sxs-lookup"><span data-stu-id="5ed68-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="5ed68-117">Mapuje wskaźnik instrukcji kodu zarządzanego do wersji ponownie kompilowana JIT określona funkcja.</span><span class="sxs-lookup"><span data-stu-id="5ed68-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="5ed68-118">GetILToNativeMapping2, metoda</span><span class="sxs-lookup"><span data-stu-id="5ed68-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="5ed68-119">Pobiera mapy firmy Microsoft do natywnej przesunięć kod źródłowy znajdujący się w wersji ponownie kompilowana JIT określona funkcja powoduje przesunięcie język pośredni (MSIL).</span><span class="sxs-lookup"><span data-stu-id="5ed68-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="5ed68-120">GetObjectSize2, metoda</span><span class="sxs-lookup"><span data-stu-id="5ed68-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="5ed68-121">Zwraca rozmiar określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5ed68-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="5ed68-122">GetReJITIDs, metoda</span><span class="sxs-lookup"><span data-stu-id="5ed68-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="5ed68-123">Zwraca tablicę identyfikatorów, które identyfikują wszystkie ponownie kompilowana JIT wersje określona funkcja nadal przydzielonych.</span><span class="sxs-lookup"><span data-stu-id="5ed68-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="5ed68-124">InitializeCurrentThread, metoda</span><span class="sxs-lookup"><span data-stu-id="5ed68-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="5ed68-125">Inicjuje bieżący wątek klienta z wyprzedzeniem kolejnych profilera, który wywołania interfejsu API w tym samym wątku, aby uniknąć tego zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="5ed68-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="5ed68-126">RequestReJIT, metoda</span><span class="sxs-lookup"><span data-stu-id="5ed68-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="5ed68-127">Żądania kompilacji JIT, wszystkich wystąpień określonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="5ed68-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="5ed68-128">RequestRevert, metoda</span><span class="sxs-lookup"><span data-stu-id="5ed68-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="5ed68-129">Przywraca wszystkie wystąpienia określonych funkcji, do ich oryginalnej wersji.</span><span class="sxs-lookup"><span data-stu-id="5ed68-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ed68-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ed68-130">Remarks</span></span>  
 <span data-ttu-id="5ed68-131">Środowisko CLR implementuje metody `ICorProfilerInfo4` interfejsu za pomocą modelu bezwątkowy.</span><span class="sxs-lookup"><span data-stu-id="5ed68-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="5ed68-132">Każda metoda zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="5ed68-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="5ed68-133">Aby uzyskać listę możliwych kody powrotu zobacz plik CorError.h.</span><span class="sxs-lookup"><span data-stu-id="5ed68-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ed68-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5ed68-134">Requirements</span></span>  
 <span data-ttu-id="5ed68-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ed68-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ed68-136">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ed68-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ed68-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ed68-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ed68-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ed68-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed68-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ed68-139">See Also</span></span>  
 [<span data-ttu-id="5ed68-140">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="5ed68-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="5ed68-141">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ed68-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
