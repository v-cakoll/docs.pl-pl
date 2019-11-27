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
ms.openlocfilehash: c7ced05692e3030bace10dab9a6793a29fac6c26
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444837"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="15ee2-102">ICorProfilerInfo4::RequestRevert — Metoda</span><span class="sxs-lookup"><span data-stu-id="15ee2-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="15ee2-103">Przywraca oryginalne wersje wszystkich wystąpień określonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="15ee2-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15ee2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="15ee2-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15ee2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15ee2-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="15ee2-106">podczas Liczba funkcji, które mają zostać przywrócone.</span><span class="sxs-lookup"><span data-stu-id="15ee2-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="15ee2-107">podczas Określa `moduleId` część par (`module`, `methodDef`), które identyfikują funkcje, które mają zostać przywrócone.</span><span class="sxs-lookup"><span data-stu-id="15ee2-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="15ee2-108">podczas Określa `methodId` część par (`module`, `methodDef`), które identyfikują funkcje, które mają zostać przywrócone.</span><span class="sxs-lookup"><span data-stu-id="15ee2-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="15ee2-109">określoną Tablica wartości HRESULT wymienionych w sekcji "stan HRESULT" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="15ee2-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="15ee2-110">Każde HRESULT wskazuje powodzenie lub niepowodzenie próby przywrócenia każdej funkcji określonej w tablicach równoległych `moduleIds` i `methodIds`.</span><span class="sxs-lookup"><span data-stu-id="15ee2-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15ee2-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="15ee2-111">Return Value</span></span>  
 <span data-ttu-id="15ee2-112">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="15ee2-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="15ee2-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15ee2-113">HRESULT</span></span>|<span data-ttu-id="15ee2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="15ee2-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15ee2-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="15ee2-115">S_OK</span></span>|<span data-ttu-id="15ee2-116">Podjęto próbę przywrócenia wszystkich żądań; jednak zwracana tablica stanu musi być sprawdzona, aby określić, które funkcje zostały pomyślnie przywrócone.</span><span class="sxs-lookup"><span data-stu-id="15ee2-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="15ee2-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="15ee2-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="15ee2-118">Profiler musi zaimplementować interfejs [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) , aby można było obsługiwać to wywołanie.</span><span class="sxs-lookup"><span data-stu-id="15ee2-118">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="15ee2-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="15ee2-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="15ee2-120">Ponowna kompilacja JIT nie została włączona.</span><span class="sxs-lookup"><span data-stu-id="15ee2-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="15ee2-121">Należy włączyć ponowną kompilację JIT podczas inicjowania przy użyciu metody [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) w celu ustawienia flagi `COR_PRF_ENABLE_REJIT`.</span><span class="sxs-lookup"><span data-stu-id="15ee2-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="15ee2-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="15ee2-122">E_INVALIDARG</span></span>|<span data-ttu-id="15ee2-123">`cFunctions` jest równa 0 lub `moduleIds` lub `methodIds` jest `NULL`.</span><span class="sxs-lookup"><span data-stu-id="15ee2-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="15ee2-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="15ee2-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="15ee2-125">Środowisko CLR nie mogło wykonać żądania, ponieważ zabrakło pamięci.</span><span class="sxs-lookup"><span data-stu-id="15ee2-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="15ee2-126">Stan HRESULT</span><span class="sxs-lookup"><span data-stu-id="15ee2-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="15ee2-127">Wartość HRESULT tablicy stanu</span><span class="sxs-lookup"><span data-stu-id="15ee2-127">Status array HRESULT</span></span>|<span data-ttu-id="15ee2-128">Opis</span><span class="sxs-lookup"><span data-stu-id="15ee2-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="15ee2-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="15ee2-129">S_OK</span></span>|<span data-ttu-id="15ee2-130">Odpowiednia funkcja została pomyślnie przywrócona.</span><span class="sxs-lookup"><span data-stu-id="15ee2-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="15ee2-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="15ee2-131">E_INVALIDARG</span></span>|<span data-ttu-id="15ee2-132">Parametr `moduleID` lub `methodDef` ma wartość `NULL`.</span><span class="sxs-lookup"><span data-stu-id="15ee2-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="15ee2-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="15ee2-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="15ee2-134">Moduł nie jest jeszcze w pełni załadowany lub jest w trakcie jego zwalniania.</span><span class="sxs-lookup"><span data-stu-id="15ee2-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="15ee2-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="15ee2-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="15ee2-136">Określony moduł został dynamicznie wygenerowany (na przykład przez `Reflection.Emit`).</span><span class="sxs-lookup"><span data-stu-id="15ee2-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="15ee2-137">W związku z tym nie jest to obsługiwane przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="15ee2-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="15ee2-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="15ee2-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="15ee2-139">Środowisko CLR nie może przywrócić określonej funkcji, ponieważ nie znaleziono odpowiadającego jej aktywnego żądania ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="15ee2-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="15ee2-140">Ponowna kompilacja nigdy nie została żądana lub funkcja została już przywrócona.</span><span class="sxs-lookup"><span data-stu-id="15ee2-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="15ee2-141">Inne</span><span class="sxs-lookup"><span data-stu-id="15ee2-141">Other</span></span>|<span data-ttu-id="15ee2-142">System operacyjny zwrócił błąd poza kontrolą środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="15ee2-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="15ee2-143">Jeśli na przykład wywołanie systemowe w celu zmiany ochrony dostępu strony pamięci zakończy się niepowodzeniem, zostanie wyświetlony komunikat o błędzie systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="15ee2-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15ee2-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15ee2-144">Remarks</span></span>  
 <span data-ttu-id="15ee2-145">Przy następnym wywołaniu dowolnego wystąpienia funkcji revereted zostaną uruchomione oryginalne wersje funkcji.</span><span class="sxs-lookup"><span data-stu-id="15ee2-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="15ee2-146">Jeśli funkcja jest już uruchomiona, zostanie zakończona wykonywanie uruchomionej wersji.</span><span class="sxs-lookup"><span data-stu-id="15ee2-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15ee2-147">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15ee2-147">Requirements</span></span>  
 <span data-ttu-id="15ee2-148">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15ee2-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15ee2-149">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="15ee2-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15ee2-150">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="15ee2-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15ee2-151">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15ee2-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15ee2-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15ee2-152">See also</span></span>

- [<span data-ttu-id="15ee2-153">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="15ee2-153">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="15ee2-154">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="15ee2-154">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="15ee2-155">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="15ee2-155">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
