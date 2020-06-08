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
ms.openlocfilehash: b85a7893cf5271c65bc842bb6ea598c825225376
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495726"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="0fe0f-102">ICorProfilerInfo4::RequestRevert — Metoda</span><span class="sxs-lookup"><span data-stu-id="0fe0f-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="0fe0f-103">Przywraca oryginalne wersje wszystkich wystąpień określonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fe0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fe0f-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fe0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0fe0f-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="0fe0f-106">podczas Liczba funkcji, które mają zostać przywrócone.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="0fe0f-107">podczas Określa `moduleId` część `module` par (, `methodDef` ), które identyfikują funkcje, które mają zostać przywrócone.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="0fe0f-108">podczas Określa `methodId` część `module` par (, `methodDef` ), które identyfikują funkcje, które mają zostać przywrócone.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="0fe0f-109">określoną Tablica wartości HRESULT wymienionych w sekcji "stan HRESULT" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="0fe0f-110">Każde HRESULT wskazuje powodzenie lub niepowodzenie próby przywrócenia każdej funkcji określonej w tablicach równoległych `moduleIds` i `methodIds` .</span><span class="sxs-lookup"><span data-stu-id="0fe0f-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0fe0f-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0fe0f-111">Return Value</span></span>  
 <span data-ttu-id="0fe0f-112">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0fe0f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0fe0f-113">HRESULT</span></span>|<span data-ttu-id="0fe0f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0fe0f-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0fe0f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="0fe0f-115">S_OK</span></span>|<span data-ttu-id="0fe0f-116">Podjęto próbę przywrócenia wszystkich żądań; jednak zwracana tablica stanu musi być sprawdzona, aby określić, które funkcje zostały pomyślnie przywrócone.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="0fe0f-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="0fe0f-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="0fe0f-118">Profiler musi zaimplementować interfejs [ICorProfilerCallback4](icorprofilercallback4-interface.md) , aby można było obsługiwać to wywołanie.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-118">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="0fe0f-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="0fe0f-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="0fe0f-120">Ponowna kompilacja JIT nie została włączona.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="0fe0f-121">Należy włączyć ponowną kompilację JIT podczas inicjowania przy użyciu metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) , aby ustawić `COR_PRF_ENABLE_REJIT` flagę.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="0fe0f-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0fe0f-122">E_INVALIDARG</span></span>|<span data-ttu-id="0fe0f-123">`cFunctions`ma wartość 0 lub `moduleIds` lub `methodIds` równą `NULL` .</span><span class="sxs-lookup"><span data-stu-id="0fe0f-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="0fe0f-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0fe0f-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0fe0f-125">Środowisko CLR nie mogło wykonać żądania, ponieważ zabrakło pamięci.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="0fe0f-126">Stan HRESULT</span><span class="sxs-lookup"><span data-stu-id="0fe0f-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="0fe0f-127">Wartość HRESULT tablicy stanu</span><span class="sxs-lookup"><span data-stu-id="0fe0f-127">Status array HRESULT</span></span>|<span data-ttu-id="0fe0f-128">Opis</span><span class="sxs-lookup"><span data-stu-id="0fe0f-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="0fe0f-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="0fe0f-129">S_OK</span></span>|<span data-ttu-id="0fe0f-130">Odpowiednia funkcja została pomyślnie przywrócona.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="0fe0f-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0fe0f-131">E_INVALIDARG</span></span>|<span data-ttu-id="0fe0f-132">`moduleID`Parametr lub `methodDef` jest `NULL` .</span><span class="sxs-lookup"><span data-stu-id="0fe0f-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="0fe0f-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="0fe0f-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="0fe0f-134">Moduł nie jest jeszcze w pełni załadowany lub jest w trakcie jego zwalniania.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="0fe0f-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="0fe0f-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="0fe0f-136">Określony moduł został dynamicznie wygenerowany (na przykład przez `Reflection.Emit` ).</span><span class="sxs-lookup"><span data-stu-id="0fe0f-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="0fe0f-137">W związku z tym nie jest to obsługiwane przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="0fe0f-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="0fe0f-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="0fe0f-139">Środowisko CLR nie może przywrócić określonej funkcji, ponieważ nie znaleziono odpowiadającego jej aktywnego żądania ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="0fe0f-140">Ponowna kompilacja nigdy nie została żądana lub funkcja została już przywrócona.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="0fe0f-141">Inne</span><span class="sxs-lookup"><span data-stu-id="0fe0f-141">Other</span></span>|<span data-ttu-id="0fe0f-142">System operacyjny zwrócił błąd poza kontrolą środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="0fe0f-143">Jeśli na przykład wywołanie systemowe w celu zmiany ochrony dostępu strony pamięci zakończy się niepowodzeniem, zostanie wyświetlony komunikat o błędzie systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fe0f-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0fe0f-144">Remarks</span></span>  
 <span data-ttu-id="0fe0f-145">Przy następnym wywołaniu dowolnego wystąpienia funkcji revereted zostaną uruchomione oryginalne wersje funkcji.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="0fe0f-146">Jeśli funkcja jest już uruchomiona, zostanie zakończona wykonywanie uruchomionej wersji.</span><span class="sxs-lookup"><span data-stu-id="0fe0f-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fe0f-147">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0fe0f-147">Requirements</span></span>  
 <span data-ttu-id="0fe0f-148">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fe0f-148">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fe0f-149">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0fe0f-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0fe0f-150">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0fe0f-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fe0f-151">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fe0f-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe0f-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fe0f-152">See also</span></span>

- [<span data-ttu-id="0fe0f-153">ICorProfilerInfo4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0fe0f-153">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="0fe0f-154">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="0fe0f-154">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0fe0f-155">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="0fe0f-155">Profiling</span></span>](index.md)
