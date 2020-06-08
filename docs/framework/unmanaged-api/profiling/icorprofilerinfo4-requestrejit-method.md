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
ms.openlocfilehash: 7dd82f2dfab885070df4789fe5efc16a49d50e06
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495804"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="4af47-102">ICorProfilerInfo4::RequestReJIT — Metoda</span><span class="sxs-lookup"><span data-stu-id="4af47-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="4af47-103">Żąda ponownej kompilacji JIT wszystkich wystąpień określonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="4af47-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af47-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4af47-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4af47-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4af47-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="4af47-106">podczas Liczba funkcji, które mają zostać ponownie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="4af47-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="4af47-107">podczas Określa `moduleId` część `module` par (, `methodDef` ), które identyfikują funkcje, które mają być ponownie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="4af47-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="4af47-108">podczas Określa `methodId` część `module` par (, `methodDef` ), które identyfikują funkcje, które mają być ponownie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="4af47-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4af47-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4af47-109">Return Value</span></span>  
 <span data-ttu-id="4af47-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="4af47-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4af47-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4af47-111">HRESULT</span></span>|<span data-ttu-id="4af47-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4af47-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4af47-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="4af47-113">S_OK</span></span>|<span data-ttu-id="4af47-114">Podjęto próbę oznaczenia wszystkich metod ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="4af47-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="4af47-115">Profiler musi zaimplementować metodę [ICorProfilerCallback4:: ReJITError —](icorprofilercallback4-rejiterror-method.md) , aby określić, które metody zostały pomyślnie oznaczone do ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="4af47-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="4af47-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="4af47-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="4af47-117">Profiler musi zaimplementować interfejs [ICorProfilerCallback4](icorprofilercallback4-interface.md) , aby można było obsługiwać to wywołanie.</span><span class="sxs-lookup"><span data-stu-id="4af47-117">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="4af47-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="4af47-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="4af47-119">Ponowna kompilacja JIT nie została włączona.</span><span class="sxs-lookup"><span data-stu-id="4af47-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="4af47-120">Należy włączyć ponowną kompilację JIT podczas inicjowania przy użyciu metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) , aby ustawić `COR_PRF_ENABLE_REJIT` flagę.</span><span class="sxs-lookup"><span data-stu-id="4af47-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="4af47-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4af47-121">E_INVALIDARG</span></span>|<span data-ttu-id="4af47-122">`cFunctions`ma wartość 0 lub `moduleIds` lub `methodIds` równą `NULL` .</span><span class="sxs-lookup"><span data-stu-id="4af47-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="4af47-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4af47-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4af47-124">Środowisko CLR nie mogło wykonać żądania, ponieważ zabrakło pamięci.</span><span class="sxs-lookup"><span data-stu-id="4af47-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4af47-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4af47-125">Remarks</span></span>  
 <span data-ttu-id="4af47-126">Wywołaj `RequestReJIT` , aby środowisko uruchomieniowe ponownie skompiluje określony zestaw funkcji.</span><span class="sxs-lookup"><span data-stu-id="4af47-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="4af47-127">Profiler kodu może następnie użyć interfejsu [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) , aby dostosować kod generowany podczas ponownego kompilowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="4af47-127">A code profiler can then use the [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="4af47-128">Nie ma to wpływu na aktualnie wykonywane funkcje, tylko w przyszłości wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="4af47-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="4af47-129">Jeśli którekolwiek z określonych funkcji zostało wcześniej ponownie skompilowane w trybie JIT, żądanie ponownej kompilacji jest równoznaczne z przywróceniem i ponownym kompilacją funkcji.</span><span class="sxs-lookup"><span data-stu-id="4af47-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="4af47-130">Aby zachować odwracalność, gdy kompilator JIT kompiluje oryginalną wersję funkcji, bierze pod uwagę tylko oryginalne wersje wywoływane na potrzeby podejmowania decyzji dotyczących podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="4af47-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="4af47-131">Gdy kompilator JIT ponownie kompiluje funkcję, traktuje bieżące wersje (ponownie skompilowane lub oryginalnie) jego wywoływane do tworzenia konspektu.</span><span class="sxs-lookup"><span data-stu-id="4af47-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="4af47-132">Profiler zazwyczaj wywołuje `RequestReJIT` w odpowiedzi na dane wejściowe użytkownika z żądaniem, że instrument profilera ma jedną lub więcej metod.</span><span class="sxs-lookup"><span data-stu-id="4af47-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="4af47-133">`RequestReJIT`zazwyczaj wstrzymuje środowisko uruchomieniowe, aby wykonać część jego pracy i może potencjalnie wyzwolić wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4af47-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="4af47-134">W związku z tym Profiler powinien wywołać `RequestReJIT` z wcześniej utworzonego wątku, a nie z wątku utworzonego przez środowisko CLR, który aktualnie wykonuje wywołanie zwrotne profilera.</span><span class="sxs-lookup"><span data-stu-id="4af47-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4af47-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4af47-135">Requirements</span></span>  
 <span data-ttu-id="4af47-136">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4af47-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4af47-137">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4af47-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4af47-138">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4af47-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4af47-139">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4af47-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af47-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4af47-140">See also</span></span>

- [<span data-ttu-id="4af47-141">ICorProfilerInfo4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4af47-141">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="4af47-142">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="4af47-142">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4af47-143">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="4af47-143">Profiling</span></span>](index.md)
