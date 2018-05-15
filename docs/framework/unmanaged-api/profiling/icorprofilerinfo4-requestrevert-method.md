---
title: ICorProfilerInfo4::RequestRevert — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43a1954d75d37f68eb967eb714070a097573100a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="d4a18-102">ICorProfilerInfo4::RequestRevert — Metoda</span><span class="sxs-lookup"><span data-stu-id="d4a18-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="d4a18-103">Przywraca wszystkie wystąpienia określonych funkcji, do ich oryginalnej wersji.</span><span class="sxs-lookup"><span data-stu-id="d4a18-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4a18-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4a18-104">Syntax</span></span>  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4a18-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4a18-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="d4a18-106">[in] Liczbę funkcji do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="d4a18-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="d4a18-107">[in] Określa `moduleId` część (`module`, `methodDef`) pary, które identyfikują funkcje przywrócenie.</span><span class="sxs-lookup"><span data-stu-id="d4a18-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="d4a18-108">[in] Określa `methodId` część (`module`, `methodDef`) pary, które identyfikują funkcje przywrócenie.</span><span class="sxs-lookup"><span data-stu-id="d4a18-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="d4a18-109">[out] Tablica wyników HRESULT wymienionych w sekcji "Wyników HRESULT stan" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d4a18-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="d4a18-110">Każdy HRESULT wskazuje powodzenie lub niepowodzenie próbę przywrócenia każdej funkcji określony w tablicach równoległych `moduleIds` i `methodIds`.</span><span class="sxs-lookup"><span data-stu-id="d4a18-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4a18-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d4a18-111">Return Value</span></span>  
 <span data-ttu-id="d4a18-112">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="d4a18-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d4a18-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4a18-113">HRESULT</span></span>|<span data-ttu-id="d4a18-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d4a18-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4a18-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4a18-115">S_OK</span></span>|<span data-ttu-id="d4a18-116">Podjęto próbę przywrócenia wszystkich żądań; jednak zwrócony stan tablicy musi być zaznaczone do określenia, jakie funkcje zostały pomyślnie przywrócone.</span><span class="sxs-lookup"><span data-stu-id="d4a18-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="d4a18-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="d4a18-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="d4a18-118">Profiler musi implementować [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejs dla tego wywołania do obsługi.</span><span class="sxs-lookup"><span data-stu-id="d4a18-118">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="d4a18-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="d4a18-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="d4a18-120">Nie włączono ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="d4a18-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="d4a18-121">Należy włączyć ponownej kompilacji JIT podczas inicjowania przy użyciu [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby ustawić `COR_PRF_ENABLE_REJIT` flagi.</span><span class="sxs-lookup"><span data-stu-id="d4a18-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="d4a18-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d4a18-122">E_INVALIDARG</span></span>|<span data-ttu-id="d4a18-123">`cFunctions` ma wartość 0, lub `moduleIds` lub `methodIds` jest `NULL`.</span><span class="sxs-lookup"><span data-stu-id="d4a18-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="d4a18-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d4a18-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d4a18-125">Środowisko CLR nie może wykonać żądania, ponieważ zabrakło pamięci.</span><span class="sxs-lookup"><span data-stu-id="d4a18-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="d4a18-126">Stan wyników HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4a18-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="d4a18-127">Stan tablicy HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4a18-127">Status array HRESULT</span></span>|<span data-ttu-id="d4a18-128">Opis</span><span class="sxs-lookup"><span data-stu-id="d4a18-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="d4a18-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4a18-129">S_OK</span></span>|<span data-ttu-id="d4a18-130">Odpowiednich funkcji została pomyślnie przywrócona.</span><span class="sxs-lookup"><span data-stu-id="d4a18-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="d4a18-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d4a18-131">E_INVALIDARG</span></span>|<span data-ttu-id="d4a18-132">`moduleID` Lub `methodDef` parametr jest `NULL`.</span><span class="sxs-lookup"><span data-stu-id="d4a18-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="d4a18-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="d4a18-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="d4a18-134">Moduł nie został jeszcze całkowicie załadowany lub Trwa zwalnianie modułu.</span><span class="sxs-lookup"><span data-stu-id="d4a18-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="d4a18-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="d4a18-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="d4a18-136">Określony moduł został generowane dynamicznie (np. przez `Reflection.Emit`).</span><span class="sxs-lookup"><span data-stu-id="d4a18-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="d4a18-137">W związku z tym jest nieobsługiwany przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="d4a18-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="d4a18-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="d4a18-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="d4a18-139">Środowisko CLR nie można przywrócić określonej funkcji, ponieważ nie znaleziono odpowiedniego żądania active ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d4a18-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="d4a18-140">Nigdy nie odebrał żądanie ponownej kompilacji albo funkcję już została przywrócona.</span><span class="sxs-lookup"><span data-stu-id="d4a18-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="d4a18-141">Inne</span><span class="sxs-lookup"><span data-stu-id="d4a18-141">Other</span></span>|<span data-ttu-id="d4a18-142">System operacyjny zwrócił błąd poza kontrolą środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d4a18-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="d4a18-143">Na przykład jeśli wystąpi błąd wywołania systemu, aby zmienić ustawienia ochrony dostępu do strony pamięci, zostanie wyświetlony błąd systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d4a18-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4a18-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4a18-144">Remarks</span></span>  
 <span data-ttu-id="d4a18-145">Przy następnym wszystkich wystąpień funkcji revereted są nazywane, oryginalnej wersji funkcji zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="d4a18-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="d4a18-146">Jeśli funkcja jest już uruchomiona, zostanie zakończony, wykonywania wersję, do której jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="d4a18-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4a18-147">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d4a18-147">Requirements</span></span>  
 <span data-ttu-id="d4a18-148">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4a18-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4a18-149">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d4a18-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d4a18-150">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4a18-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4a18-151">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4a18-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4a18-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4a18-152">See Also</span></span>  
 [<span data-ttu-id="d4a18-153">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="d4a18-153">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="d4a18-154">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="d4a18-154">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="d4a18-155">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="d4a18-155">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
