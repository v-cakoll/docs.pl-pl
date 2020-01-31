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
ms.openlocfilehash: c287b630aee58c6795ef405cc1801149e220fd51
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868424"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="dadcd-102">ICorProfilerInfo4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dadcd-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="dadcd-103">Zapewnia metody, które są używane przez program codeer do komunikowania się ze środowiskiem uruchomieniowym języka wspólnego (CLR) w celu kontrolowania informacji o monitorowaniu zdarzeń i żądaniach.</span><span class="sxs-lookup"><span data-stu-id="dadcd-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="dadcd-104">.</span><span class="sxs-lookup"><span data-stu-id="dadcd-104">.</span></span> <span data-ttu-id="dadcd-105">Interfejs `ICorProfilerInfo4` jest rozszerzeniem innych interfejsów `ICorProfilerInfo`.</span><span class="sxs-lookup"><span data-stu-id="dadcd-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="dadcd-106">Udostępnia nowe metody obsługi ponownej kompilacji just-in-Time (JIT), dodane w .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="dadcd-106">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dadcd-107">Metody</span><span class="sxs-lookup"><span data-stu-id="dadcd-107">Methods</span></span>  
  
|<span data-ttu-id="dadcd-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="dadcd-108">Method</span></span>|<span data-ttu-id="dadcd-109">Opis</span><span class="sxs-lookup"><span data-stu-id="dadcd-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dadcd-110">EnumJITedFunctions2, metoda</span><span class="sxs-lookup"><span data-stu-id="dadcd-110">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="dadcd-111">Zwraca moduł wyliczający dla wszystkich funkcji, które były poprzednio skompilowane JIT i ponownie skompilowane w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="dadcd-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="dadcd-112">EnumThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="dadcd-112">EnumThreads Method</span></span>](icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="dadcd-113">Pobiera moduł wyliczający, który dostarcza metody sekwencyjnie iteracji przez kolekcję wszystkich zarządzanych wątków w profilowanym procesie.</span><span class="sxs-lookup"><span data-stu-id="dadcd-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="dadcd-114">GetCodeInfo3, metoda</span><span class="sxs-lookup"><span data-stu-id="dadcd-114">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="dadcd-115">Pobiera zakresy kodu natywnego skojarzone z rekompilowaną ponownie wersją określonej funkcji JIT.</span><span class="sxs-lookup"><span data-stu-id="dadcd-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="dadcd-116">GetFunctionFromIP2, metoda</span><span class="sxs-lookup"><span data-stu-id="dadcd-116">GetFunctionFromIP2 Method</span></span>](icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="dadcd-117">Mapuje wskaźnik zarządzanej instrukcji kodu do wersji z ponowną kompilacją JIT dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="dadcd-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="dadcd-118">GetILToNativeMapping2, metoda</span><span class="sxs-lookup"><span data-stu-id="dadcd-118">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="dadcd-119">Pobiera mapę z przesunięcia języka pośredniego firmy Microsoft (MSIL) do natywnych przesunięć dla kodu zawartego w ponownej kompilacji JIT w wersji określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="dadcd-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="dadcd-120">GetObjectSize2, metoda</span><span class="sxs-lookup"><span data-stu-id="dadcd-120">GetObjectSize2 Method</span></span>](icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="dadcd-121">Zwraca rozmiar określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="dadcd-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="dadcd-122">GetReJITIDs, metoda</span><span class="sxs-lookup"><span data-stu-id="dadcd-122">GetReJITIDs Method</span></span>](icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="dadcd-123">Zwraca tablicę identyfikatorów, które identyfikują wszystkie wersje JIT-ponownie skompilowane określonej funkcji, które są nadal przydzieleni.</span><span class="sxs-lookup"><span data-stu-id="dadcd-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="dadcd-124">InitializeCurrentThread, metoda</span><span class="sxs-lookup"><span data-stu-id="dadcd-124">InitializeCurrentThread Method</span></span>](icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="dadcd-125">Inicjuje bieżący wątek przed kolejnymi wywołaniami interfejsu API profilera w tym samym wątku, aby można było uniknąć zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="dadcd-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="dadcd-126">RequestReJIT, metoda</span><span class="sxs-lookup"><span data-stu-id="dadcd-126">RequestReJIT Method</span></span>](icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="dadcd-127">Żąda ponownej kompilacji JIT wszystkich wystąpień określonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="dadcd-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="dadcd-128">RequestRevert, metoda</span><span class="sxs-lookup"><span data-stu-id="dadcd-128">RequestRevert Method</span></span>](icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="dadcd-129">Przywraca oryginalne wersje wszystkich wystąpień określonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="dadcd-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dadcd-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dadcd-130">Remarks</span></span>  
 <span data-ttu-id="dadcd-131">Środowisko CLR implementuje metody interfejsu `ICorProfilerInfo4` przy użyciu modelu typu wolny-wątek.</span><span class="sxs-lookup"><span data-stu-id="dadcd-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="dadcd-132">Każda metoda zwraca wynik HRESULT wskazujący powodzenie lub niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="dadcd-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="dadcd-133">Aby uzyskać listę możliwych kodów powrotu, zobacz plik CorError. h.</span><span class="sxs-lookup"><span data-stu-id="dadcd-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dadcd-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dadcd-134">Requirements</span></span>  
 <span data-ttu-id="dadcd-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dadcd-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dadcd-136">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dadcd-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dadcd-137">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dadcd-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dadcd-138">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dadcd-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dadcd-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dadcd-139">See also</span></span>

- [<span data-ttu-id="dadcd-140">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="dadcd-140">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="dadcd-141">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="dadcd-141">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
