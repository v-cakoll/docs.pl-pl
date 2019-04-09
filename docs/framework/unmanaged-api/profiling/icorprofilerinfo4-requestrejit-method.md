---
title: ICorProfilerInfo4::RequestReJIT — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ddad2497f18aa510ade41f58ba20c9de1a46ce5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135099"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="360b1-102">ICorProfilerInfo4::RequestReJIT — Metoda</span><span class="sxs-lookup"><span data-stu-id="360b1-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="360b1-103">Żąda JIT — rekompilacja wszystkich wystąpień określonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="360b1-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="360b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="360b1-104">Syntax</span></span>  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="360b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="360b1-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="360b1-106">[in] Liczba funkcji ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="360b1-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="360b1-107">[in] Określa `moduleId` część (`module`, `methodDef`) pary, które identyfikują funkcji, które mają być ponownie kompilowane.</span><span class="sxs-lookup"><span data-stu-id="360b1-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="360b1-108">[in] Określa `methodId` część (`module`, `methodDef`) pary, które identyfikują funkcji, które mają być ponownie kompilowane.</span><span class="sxs-lookup"><span data-stu-id="360b1-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="360b1-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="360b1-109">Return Value</span></span>  
 <span data-ttu-id="360b1-110">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="360b1-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="360b1-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="360b1-111">HRESULT</span></span>|<span data-ttu-id="360b1-112">Opis</span><span class="sxs-lookup"><span data-stu-id="360b1-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="360b1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="360b1-113">S_OK</span></span>|<span data-ttu-id="360b1-114">Aby oznaczyć wszystkie metody JIT — rekompilacja nastąpiła próba.</span><span class="sxs-lookup"><span data-stu-id="360b1-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="360b1-115">Program profilujący musi zaimplementować [icorprofilercallback4::rejiterror —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) metodę pozwala ustalić metody, które zostały pomyślnie oznaczona do ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="360b1-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="360b1-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="360b1-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="360b1-117">Program profilujący musi zaimplementować [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsu dla tego wywołania są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="360b1-117">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="360b1-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="360b1-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="360b1-119">JIT — rekompilacja nie została włączona.</span><span class="sxs-lookup"><span data-stu-id="360b1-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="360b1-120">JIT — rekompilacja podczas inicjowania należy włączyć, używając [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby ustawić `COR_PRF_ENABLE_REJIT` flagi.</span><span class="sxs-lookup"><span data-stu-id="360b1-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="360b1-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="360b1-121">E_INVALIDARG</span></span>|`cFunctions` <span data-ttu-id="360b1-122">ma wartość 0, lub `moduleIds` lub `methodIds` jest `NULL`.</span><span class="sxs-lookup"><span data-stu-id="360b1-122">is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="360b1-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="360b1-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="360b1-124">Nie można ukończyć żądania, ponieważ zabrakło jej pamięci CLR.</span><span class="sxs-lookup"><span data-stu-id="360b1-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="360b1-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="360b1-125">Remarks</span></span>  
 <span data-ttu-id="360b1-126">Wywołaj `RequestReJIT` do środowiska uruchomieniowego określony zestaw funkcji, należy ponownie skompilować.</span><span class="sxs-lookup"><span data-stu-id="360b1-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="360b1-127">Profiler kodu może używać [icorprofilerfunctioncontrol —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interfejsu, aby dopasować kod, który jest generowany, gdy funkcje są ponownie kompilowane.</span><span class="sxs-lookup"><span data-stu-id="360b1-127">A code profiler can then use the [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="360b1-128">To nie wpływa na aktualnie wykonywanej funkcji, wywołania tylko przyszłych funkcji.</span><span class="sxs-lookup"><span data-stu-id="360b1-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="360b1-129">Jeśli dowolny z określonych funkcji poprzednio ponownie skompilowana JIT, żądanie ponownej kompilacji jest odpowiednikiem Przywracanie i konieczności ponownego kompilowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="360b1-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="360b1-130">Aby zachować stosownie, kiedy kompilator JIT kompiluje oryginalnej wersji funkcji, traktuje oryginalnej wersji jego wywoływane dla wbudowanie decyzji.</span><span class="sxs-lookup"><span data-stu-id="360b1-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="360b1-131">Gdy kompilator JIT, następuje rekompilacja funkcji, uzna aktualne wersje (oryginalna lub ponownie skompilowanymi) jej wywoływane dla wbudowanie.</span><span class="sxs-lookup"><span data-stu-id="360b1-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="360b1-132">Program profilujący zazwyczaj wywołuje `RequestReJIT` w odpowiedzi na żądanie, czy programu profilującego Instrumentację co najmniej jedną metodę wprowadzania danych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="360b1-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> `RequestReJIT` <span data-ttu-id="360b1-133">Zazwyczaj wstrzymuje działanie środowiska uruchomieniowego w celu wykonania niektórych prac i może potencjalnie wyzwalacza wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="360b1-133">typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="360b1-134">W efekcie program profilujący powinien wywoływać `RequestReJIT` z wątku on wcześniej utworzony, a nie z utworzonego przez CLR wątku, jest w trakcie wykonywania zwrotnym profilera.</span><span class="sxs-lookup"><span data-stu-id="360b1-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="360b1-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="360b1-135">Requirements</span></span>  
 <span data-ttu-id="360b1-136">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="360b1-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="360b1-137">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="360b1-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="360b1-138">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="360b1-138">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="360b1-139">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="360b1-139">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="360b1-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="360b1-140">See also</span></span>

- [<span data-ttu-id="360b1-141">ICorProfilerInfo4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="360b1-141">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="360b1-142">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="360b1-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="360b1-143">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="360b1-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
