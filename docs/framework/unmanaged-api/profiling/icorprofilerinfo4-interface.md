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
ms.openlocfilehash: 58d11e9084f53c69f2656b4f0ee6bc7d2cc4ae21
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495869"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="422ea-102">ICorProfilerInfo4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="422ea-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="422ea-103">Zapewnia metody, które są używane przez program codeer do komunikowania się ze środowiskiem uruchomieniowym języka wspólnego (CLR) w celu kontrolowania informacji o monitorowaniu zdarzeń i żądaniach.</span><span class="sxs-lookup"><span data-stu-id="422ea-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="422ea-104">.</span><span class="sxs-lookup"><span data-stu-id="422ea-104">.</span></span> <span data-ttu-id="422ea-105">`ICorProfilerInfo4`Interfejs jest rozszerzeniem innych `ICorProfilerInfo` interfejsów.</span><span class="sxs-lookup"><span data-stu-id="422ea-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="422ea-106">Udostępnia nowe metody obsługi ponownej kompilacji just-in-Time (JIT), dodane w .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="422ea-106">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="422ea-107">Metody</span><span class="sxs-lookup"><span data-stu-id="422ea-107">Methods</span></span>  
  
|<span data-ttu-id="422ea-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="422ea-108">Method</span></span>|<span data-ttu-id="422ea-109">Opis</span><span class="sxs-lookup"><span data-stu-id="422ea-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="422ea-110">EnumJITedFunctions2, metoda</span><span class="sxs-lookup"><span data-stu-id="422ea-110">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="422ea-111">Zwraca moduł wyliczający dla wszystkich funkcji, które były poprzednio skompilowane JIT i ponownie skompilowane w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="422ea-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="422ea-112">EnumThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="422ea-112">EnumThreads Method</span></span>](icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="422ea-113">Pobiera moduł wyliczający, który dostarcza metody sekwencyjnie iteracji przez kolekcję wszystkich zarządzanych wątków w profilowanym procesie.</span><span class="sxs-lookup"><span data-stu-id="422ea-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="422ea-114">GetCodeInfo3, metoda</span><span class="sxs-lookup"><span data-stu-id="422ea-114">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="422ea-115">Pobiera zakresy kodu natywnego skojarzone z rekompilowaną ponownie wersją określonej funkcji JIT.</span><span class="sxs-lookup"><span data-stu-id="422ea-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="422ea-116">GetFunctionFromIP2, metoda</span><span class="sxs-lookup"><span data-stu-id="422ea-116">GetFunctionFromIP2 Method</span></span>](icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="422ea-117">Mapuje wskaźnik zarządzanej instrukcji kodu do wersji z ponowną kompilacją JIT dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="422ea-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="422ea-118">GetILToNativeMapping2, metoda</span><span class="sxs-lookup"><span data-stu-id="422ea-118">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="422ea-119">Pobiera mapę z przesunięcia języka pośredniego firmy Microsoft (MSIL) do natywnych przesunięć dla kodu zawartego w ponownej kompilacji JIT w wersji określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="422ea-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="422ea-120">GetObjectSize2, metoda</span><span class="sxs-lookup"><span data-stu-id="422ea-120">GetObjectSize2 Method</span></span>](icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="422ea-121">Zwraca rozmiar określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="422ea-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="422ea-122">GetReJITIDs, metoda</span><span class="sxs-lookup"><span data-stu-id="422ea-122">GetReJITIDs Method</span></span>](icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="422ea-123">Zwraca tablicę identyfikatorów, które identyfikują wszystkie wersje JIT-ponownie skompilowane określonej funkcji, które są nadal przydzieleni.</span><span class="sxs-lookup"><span data-stu-id="422ea-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="422ea-124">InitializeCurrentThread, metoda</span><span class="sxs-lookup"><span data-stu-id="422ea-124">InitializeCurrentThread Method</span></span>](icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="422ea-125">Inicjuje bieżący wątek przed kolejnymi wywołaniami interfejsu API profilera w tym samym wątku, aby można było uniknąć zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="422ea-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="422ea-126">RequestReJIT, metoda</span><span class="sxs-lookup"><span data-stu-id="422ea-126">RequestReJIT Method</span></span>](icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="422ea-127">Żąda ponownej kompilacji JIT wszystkich wystąpień określonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="422ea-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="422ea-128">RequestRevert, metoda</span><span class="sxs-lookup"><span data-stu-id="422ea-128">RequestRevert Method</span></span>](icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="422ea-129">Przywraca oryginalne wersje wszystkich wystąpień określonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="422ea-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="422ea-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="422ea-130">Remarks</span></span>  
 <span data-ttu-id="422ea-131">Środowisko CLR implementuje metody `ICorProfilerInfo4` interfejsu przy użyciu modelu typu "wolny-wątek".</span><span class="sxs-lookup"><span data-stu-id="422ea-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="422ea-132">Każda metoda zwraca wynik HRESULT wskazujący powodzenie lub niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="422ea-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="422ea-133">Aby uzyskać listę możliwych kodów powrotu, zobacz plik CorError. h.</span><span class="sxs-lookup"><span data-stu-id="422ea-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="422ea-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="422ea-134">Requirements</span></span>  
 <span data-ttu-id="422ea-135">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="422ea-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="422ea-136">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="422ea-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="422ea-137">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="422ea-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="422ea-138">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="422ea-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="422ea-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="422ea-139">See also</span></span>

- [<span data-ttu-id="422ea-140">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="422ea-140">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="422ea-141">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="422ea-141">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
