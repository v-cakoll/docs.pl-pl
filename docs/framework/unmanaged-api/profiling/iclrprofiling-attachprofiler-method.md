---
title: "ICLRProfiling::AttachProfiler — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IClrProfiling.AttachProfiler Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: IClrProfiling::AttachProfiler
helpviewer_keywords:
- AttachProfiler method [.NET Framework profiling]
- IClrProfiling::AttachProfiler method [.NET Framework profiling]
ms.assetid: 535a6839-c443-405b-a6f4-e2af90725d5b
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b364ab407294b20ac2f2f830e3f875169a18b7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="a58ab-102">ICLRProfiling::AttachProfiler — Metoda</span><span class="sxs-lookup"><span data-stu-id="a58ab-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="a58ab-103">Dołącza określony profiler do określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="a58ab-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a58ab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a58ab-104">Syntax</span></span>  
  
```  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a58ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a58ab-105">Parameters</span></span>  
 `dwProfileeProcessID`  
 <span data-ttu-id="a58ab-106">[in] Identyfikator procesu procesu, do której należy dołączyć profilera.</span><span class="sxs-lookup"><span data-stu-id="a58ab-106">[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="a58ab-107">Na komputerze 64-bitowych bitowości PROFILOWANEGO procesu musi pasuje do liczby bitów procesu wyzwalacz, który wywołuje `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="a58ab-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="a58ab-108">Jeśli konto użytkownika, w którym `AttachProfiler` jest nazywany ma uprawnienia administracyjne, proces docelowy może być dowolnym procesu w systemie.</span><span class="sxs-lookup"><span data-stu-id="a58ab-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="a58ab-109">W przeciwnym razie proces docelowy musi należeć do tego samego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a58ab-109">Otherwise, the target process must be owned by the same user account.</span></span>  
  
 `dwMillisecondsMax`  
 <span data-ttu-id="a58ab-110">[in] Czas trwania (w milisekundach), aby uzyskać `AttachProfiler` do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a58ab-110">[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="a58ab-111">Proces wyzwalacza należy przekazać przekroczenie limitu czasu jest znany wystarczający dla konkretnego profiler w celu wykonania inicjowania.</span><span class="sxs-lookup"><span data-stu-id="a58ab-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>  
  
 `pClsidProfiler`  
 <span data-ttu-id="a58ab-112">[in] Wskaźnik do identyfikator CLSID profilera do załadowania.</span><span class="sxs-lookup"><span data-stu-id="a58ab-112">[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="a58ab-113">Proces wyzwalacza można ponownie użyć tej pamięci po `AttachProfiler` zwraca.</span><span class="sxs-lookup"><span data-stu-id="a58ab-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>  
  
 `wszProfilerPath`  
 <span data-ttu-id="a58ab-114">[in] Pełna ścieżka do pliku DLL profilera do załadowania.</span><span class="sxs-lookup"><span data-stu-id="a58ab-114">[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="a58ab-115">Ten ciąg powinien zawierać nie więcej niż 260 znaków, włącznie z terminatorem null.</span><span class="sxs-lookup"><span data-stu-id="a58ab-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="a58ab-116">Jeśli `wszProfilerPath` ma wartość null lub pusty ciąg, środowisko uruchomieniowe języka wspólnego (CLR) próbuje znaleźć lokalizację pliku biblioteki DLL profilera, wyszukując identyfikator CLSID w rejestrze który `pClsidProfiler` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="a58ab-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="a58ab-117">[in] Wskaźnik do danych do przekazania do profilera przez [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a58ab-117">[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="a58ab-118">Proces wyzwalacza można ponownie użyć tej pamięci po `AttachProfiler` zwraca.</span><span class="sxs-lookup"><span data-stu-id="a58ab-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="a58ab-119">Jeśli `pvClientData` ma wartość null, `cbClientData` musi być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="a58ab-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="a58ab-120">[in] Rozmiar w bajtach danych który `pvClientData` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="a58ab-120">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a58ab-121">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a58ab-121">Return Value</span></span>  
 <span data-ttu-id="a58ab-122">Ta metoda zwraca następujące wyników HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a58ab-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="a58ab-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a58ab-123">HRESULT</span></span>|<span data-ttu-id="a58ab-124">Opis</span><span class="sxs-lookup"><span data-stu-id="a58ab-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a58ab-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="a58ab-125">S_OK</span></span>|<span data-ttu-id="a58ab-126">Określony profilera pomyślnie został dołączony do procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a58ab-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="a58ab-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="a58ab-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="a58ab-128">Jest już profilera aktywnego lub dołączenia do procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a58ab-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="a58ab-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="a58ab-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="a58ab-130">Określony profiler nie obsługuje załącznika.</span><span class="sxs-lookup"><span data-stu-id="a58ab-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="a58ab-131">Proces wyzwalacz może podjąć próbę dołączenia innego profilera.</span><span class="sxs-lookup"><span data-stu-id="a58ab-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="a58ab-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="a58ab-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="a58ab-133">Nie można zażądać załącznika profilera, ponieważ wersja procesu docelowego jest niezgodna z bieżącego procesu, który wywołuje `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="a58ab-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="a58ab-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="a58ab-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="a58ab-135">Użytkownik procesu wyzwalacz nie ma dostępu do procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a58ab-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="a58ab-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="a58ab-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="a58ab-137">Użytkownik procesu wyzwalacz nie ma wystarczających uprawnień do Dołącz profiler do procesu docelowego podanego.</span><span class="sxs-lookup"><span data-stu-id="a58ab-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="a58ab-138">W dzienniku zdarzeń aplikacji może zawierać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="a58ab-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="a58ab-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="a58ab-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="a58ab-140">Wystąpił błąd podczas komunikacji z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="a58ab-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="a58ab-141">Najczęściej dzieje się tak, jeśli proces docelowy była zamknięta.</span><span class="sxs-lookup"><span data-stu-id="a58ab-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="a58ab-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="a58ab-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="a58ab-143">Proces docelowy nie istnieje lub nie jest uruchomiona CLR, która obsługuje załącznika.</span><span class="sxs-lookup"><span data-stu-id="a58ab-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="a58ab-144">Może to wskazywać środowiska CLR został zwolniony od wywołania metody wyliczania środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="a58ab-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="a58ab-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="a58ab-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="a58ab-146">Upłynął limit czasu bez początku można załadować profilera.</span><span class="sxs-lookup"><span data-stu-id="a58ab-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="a58ab-147">Możesz ponowić próbę operacji dołączania.</span><span class="sxs-lookup"><span data-stu-id="a58ab-147">You can retry the attach operation.</span></span> <span data-ttu-id="a58ab-148">Limity czasu występują, jeśli finalizator w procesie docelowym jest uruchomione dłużej niż wartość limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="a58ab-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="a58ab-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a58ab-149">E_INVALIDARG</span></span>|<span data-ttu-id="a58ab-150">Co najmniej jeden parametr ma nieprawidłową wartość.</span><span class="sxs-lookup"><span data-stu-id="a58ab-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="a58ab-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a58ab-151">E_FAIL</span></span>|<span data-ttu-id="a58ab-152">Niektóre inne, nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="a58ab-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="a58ab-153">Inne kody błędów</span><span class="sxs-lookup"><span data-stu-id="a58ab-153">Other error codes</span></span>|<span data-ttu-id="a58ab-154">Jeśli profilera [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metoda zwróci wartość HRESULT, która wskazuje niepowodzenie, `AttachProfiler` zwraca takim samym HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a58ab-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="a58ab-155">W takim przypadku E_NOTIMPL jest konwertowana na CORPROF_E_PROFILER_NOT_ATTACHABLE.</span><span class="sxs-lookup"><span data-stu-id="a58ab-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a58ab-156">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a58ab-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="a58ab-157">Zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="a58ab-157">Memory Management</span></span>  
 <span data-ttu-id="a58ab-158">W zapewnieniu z konwencjami COM, funkcji wywołującej `AttachProfiler` (na przykład kod wyzwalacza utworzone przez dewelopera profilera) jest odpowiedzialny za przydzielanie i cofnąć alokacji pamięci dla danych, który `pvClientData` parametr wskazuje.</span><span class="sxs-lookup"><span data-stu-id="a58ab-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="a58ab-159">Gdy wykonuje CLR `AttachProfiler` wywołanie, ułatwia kopię pamięć który `pvClientData` wskazuje i przesyła ją do procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a58ab-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="a58ab-160">Kiedy CLR w procesie docelowym otrzyma własną kopię `pvClientData` bloku, przekazaniem bloku do profilera za pośrednictwem `InitializeForAttach` metody, a następnie zwalnia jego kopii `pvClientData` blokowanie w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="a58ab-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a58ab-161">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a58ab-161">Requirements</span></span>  
 <span data-ttu-id="a58ab-162">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a58ab-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a58ab-163">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a58ab-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a58ab-164">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a58ab-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a58ab-165">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a58ab-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a58ab-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a58ab-166">See Also</span></span>  
 [<span data-ttu-id="a58ab-167">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="a58ab-167">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="a58ab-168">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="a58ab-168">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="a58ab-169">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="a58ab-169">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="a58ab-170">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="a58ab-170">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
