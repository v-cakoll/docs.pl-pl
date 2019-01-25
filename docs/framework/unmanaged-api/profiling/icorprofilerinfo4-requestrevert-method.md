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
ms.openlocfilehash: 9578b8148efed1cac2ee25c86054c3507b84b254
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718757"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="b2470-102">ICorProfilerInfo4::RequestRevert — Metoda</span><span class="sxs-lookup"><span data-stu-id="b2470-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="b2470-103">Przywraca wszystkie wystąpienia określonych funkcji do ich oryginalnej wersji.</span><span class="sxs-lookup"><span data-stu-id="b2470-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2470-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2470-104">Syntax</span></span>  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2470-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2470-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="b2470-106">[in] Liczba funkcji do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="b2470-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="b2470-107">[in] Określa `moduleId` część (`module`, `methodDef`) pary, które identyfikują funkcji, które mają zostać przywrócone.</span><span class="sxs-lookup"><span data-stu-id="b2470-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="b2470-108">[in] Określa `methodId` część (`module`, `methodDef`) pary, które identyfikują funkcji, które mają zostać przywrócone.</span><span class="sxs-lookup"><span data-stu-id="b2470-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="b2470-109">[out] Tablica wartości HRESULT wymienionych w sekcji "Wartości HRESULT stanu" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b2470-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="b2470-110">Każda wartość HRESULT wskazuje powodzenie lub niepowodzenie próbę przywrócenia każdej funkcji, które określono w tablicach równoległe `moduleIds` i `methodIds`.</span><span class="sxs-lookup"><span data-stu-id="b2470-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2470-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b2470-111">Return Value</span></span>  
 <span data-ttu-id="b2470-112">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="b2470-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b2470-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2470-113">HRESULT</span></span>|<span data-ttu-id="b2470-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b2470-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2470-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2470-115">S_OK</span></span>|<span data-ttu-id="b2470-116">Próbowano przywrócić wszystkie żądania; Jednak tablica zwrócona stanu musi być zaznaczone do określenia, które funkcje zostały pomyślnie przywrócone.</span><span class="sxs-lookup"><span data-stu-id="b2470-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="b2470-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="b2470-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="b2470-118">Program profilujący musi zaimplementować [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsu dla tego wywołania są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b2470-118">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="b2470-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="b2470-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="b2470-120">JIT — rekompilacja nie została włączona.</span><span class="sxs-lookup"><span data-stu-id="b2470-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="b2470-121">JIT — rekompilacja podczas inicjowania należy włączyć, używając [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby ustawić `COR_PRF_ENABLE_REJIT` flagi.</span><span class="sxs-lookup"><span data-stu-id="b2470-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="b2470-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b2470-122">E_INVALIDARG</span></span>|<span data-ttu-id="b2470-123">`cFunctions` ma wartość 0, lub `moduleIds` lub `methodIds` jest `NULL`.</span><span class="sxs-lookup"><span data-stu-id="b2470-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="b2470-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b2470-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b2470-125">Nie można ukończyć żądania, ponieważ zabrakło jej pamięci CLR.</span><span class="sxs-lookup"><span data-stu-id="b2470-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="b2470-126">Stan HRESULTS</span><span class="sxs-lookup"><span data-stu-id="b2470-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="b2470-127">Stan macierzy HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2470-127">Status array HRESULT</span></span>|<span data-ttu-id="b2470-128">Opis</span><span class="sxs-lookup"><span data-stu-id="b2470-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="b2470-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2470-129">S_OK</span></span>|<span data-ttu-id="b2470-130">Odpowiednich funkcji została pomyślnie przywrócona.</span><span class="sxs-lookup"><span data-stu-id="b2470-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="b2470-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b2470-131">E_INVALIDARG</span></span>|<span data-ttu-id="b2470-132">`moduleID` Lub `methodDef` parametr `NULL`.</span><span class="sxs-lookup"><span data-stu-id="b2470-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="b2470-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="b2470-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="b2470-134">Moduł nie jest jeszcze w pełni załadowany lub jest właśnie Trwa zwalnianie.</span><span class="sxs-lookup"><span data-stu-id="b2470-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="b2470-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="b2470-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="b2470-136">Określony moduł dynamicznie został wygenerowany (np. przez `Reflection.Emit`).</span><span class="sxs-lookup"><span data-stu-id="b2470-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="b2470-137">W związku z tym nie jest obsługiwane przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="b2470-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="b2470-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="b2470-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="b2470-139">Środowisko CLR nie można przywrócić określonej funkcji, ponieważ nie znaleziono odpowiedniego żądania active ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b2470-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="b2470-140">Nigdy nie zażądano ponowną kompilację albo funkcja została już przywrócona.</span><span class="sxs-lookup"><span data-stu-id="b2470-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="b2470-141">Inne</span><span class="sxs-lookup"><span data-stu-id="b2470-141">Other</span></span>|<span data-ttu-id="b2470-142">System operacyjny zwrócił błąd poza kontrolą środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="b2470-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="b2470-143">Na przykład jeśli wywołanie systemowe, aby zmienić ustawienia ochrony dostępu do strony pamięci nie powiedzie się, zostanie wyświetlony błąd systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b2470-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2470-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2470-144">Remarks</span></span>  
 <span data-ttu-id="b2470-145">Przy następnym noszą nazwę wszystkich wystąpień funkcji revereted, oryginalnym wersje funkcji zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="b2470-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="b2470-146">Funkcja jest już uruchomiona, zostanie ono ukończone, wykonywanie wersję, która jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="b2470-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2470-147">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2470-147">Requirements</span></span>  
 <span data-ttu-id="b2470-148">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2470-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2470-149">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b2470-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b2470-150">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2470-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2470-151">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2470-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2470-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2470-152">See also</span></span>
- [<span data-ttu-id="b2470-153">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2470-153">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="b2470-154">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="b2470-154">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b2470-155">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="b2470-155">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
