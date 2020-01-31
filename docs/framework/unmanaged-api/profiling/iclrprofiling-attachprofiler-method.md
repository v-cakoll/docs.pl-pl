---
title: ICLRProfiling::AttachProfiler — Metoda
ms.date: 03/30/2017
api_name:
- IClrProfiling.AttachProfiler Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- IClrProfiling::AttachProfiler
helpviewer_keywords:
- AttachProfiler method [.NET Framework profiling]
- IClrProfiling::AttachProfiler method [.NET Framework profiling]
ms.assetid: 535a6839-c443-405b-a6f4-e2af90725d5b
topic_type:
- apiref
ms.openlocfilehash: 29aecd530d18b931420467e9127bcbf96d3a4a5f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866767"
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="c6870-102">ICLRProfiling::AttachProfiler — Metoda</span><span class="sxs-lookup"><span data-stu-id="c6870-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="c6870-103">Dołącza określony Profiler do określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="c6870-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6870-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6870-104">Syntax</span></span>  
  
```cpp  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6870-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6870-105">Parameters</span></span>

- `dwProfileeProcessID`

  <span data-ttu-id="c6870-106">\[] Identyfikator procesu, do którego ma zostać dołączony Profiler.</span><span class="sxs-lookup"><span data-stu-id="c6870-106">\[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="c6870-107">Na komputerze 64-bitowym profilowana liczba bitów procesu PROFILOWANEGO musi być zgodna z bitową procesu wyzwalacza, który wywołuje `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="c6870-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="c6870-108">Jeśli konto użytkownika, pod którym jest wywoływane `AttachProfiler` ma uprawnienia administracyjne, proces docelowy może być dowolnym procesem w systemie.</span><span class="sxs-lookup"><span data-stu-id="c6870-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="c6870-109">W przeciwnym razie proces docelowy musi należeć do tego samego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c6870-109">Otherwise, the target process must be owned by the same user account.</span></span>

- `dwMillisecondsMax`

  <span data-ttu-id="c6870-110">\[] czas trwania (w milisekundach) dla `AttachProfiler` do ukończenia.</span><span class="sxs-lookup"><span data-stu-id="c6870-110">\[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="c6870-111">Proces wyzwalacza powinien przekroczyć limit czasu, który jest znany jako wystarczający dla danego profilera, aby zakończyć jego inicjalizację.</span><span class="sxs-lookup"><span data-stu-id="c6870-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>
  
- `pClsidProfiler`

  <span data-ttu-id="c6870-112">\[w] wskaźnik do identyfikatora CLSID profilera do załadowania.</span><span class="sxs-lookup"><span data-stu-id="c6870-112">\[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="c6870-113">Proces wyzwalacza może ponownie użyć tej pamięci po powrocie `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="c6870-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>

- `wszProfilerPath`

  <span data-ttu-id="c6870-114">\[w] pełna ścieżka do pliku DLL profilera do załadowania.</span><span class="sxs-lookup"><span data-stu-id="c6870-114">\[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="c6870-115">Ten ciąg nie może zawierać więcej niż 260 znaków, łącznie z terminatorem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="c6870-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="c6870-116">Jeśli `wszProfilerPath` ma wartość null lub jest pustym ciągiem, środowisko uruchomieniowe języka wspólnego (CLR) spróbuje znaleźć lokalizację pliku DLL profilera, przeglądając rejestr dla identyfikatora CLSID, do którego `pClsidProfiler` wskazują.</span><span class="sxs-lookup"><span data-stu-id="c6870-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>

- `pvClientData`

  <span data-ttu-id="c6870-117">\[] wskaźnik do danych, które mają zostać przesłane do profilera przez metodę [ICorProfilerCallback3:: InitializeForAttach —](icorprofilercallback3-initializeforattach-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c6870-117">\[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="c6870-118">Proces wyzwalacza może ponownie użyć tej pamięci po powrocie `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="c6870-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="c6870-119">Jeśli `pvClientData` ma wartość null, `cbClientData` musi mieć wartość 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="c6870-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>

- `cbClientData`

  <span data-ttu-id="c6870-120">\[] rozmiar (w bajtach) danych, do których `pvClientData` wskazują.</span><span class="sxs-lookup"><span data-stu-id="c6870-120">\[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>

## <a name="return-value"></a><span data-ttu-id="c6870-121">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="c6870-121">Return Value</span></span>  
 <span data-ttu-id="c6870-122">Ta metoda zwraca następujące HRESULTs.</span><span class="sxs-lookup"><span data-stu-id="c6870-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="c6870-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6870-123">HRESULT</span></span>|<span data-ttu-id="c6870-124">Opis</span><span class="sxs-lookup"><span data-stu-id="c6870-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6870-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6870-125">S_OK</span></span>|<span data-ttu-id="c6870-126">Określony profiler został pomyślnie dołączony do procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="c6870-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="c6870-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="c6870-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="c6870-128">Istnieje już Profiler aktywny lub dołączany do procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="c6870-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="c6870-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="c6870-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="c6870-130">Określony Profiler nie obsługuje załącznika.</span><span class="sxs-lookup"><span data-stu-id="c6870-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="c6870-131">Proces wyzwalacza może próbować dołączyć inny Profiler.</span><span class="sxs-lookup"><span data-stu-id="c6870-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="c6870-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="c6870-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="c6870-133">Nie można zażądać załącznika profilera, ponieważ wersja procesu docelowego jest niezgodna z bieżącym procesem wywołującym `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="c6870-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="c6870-134">HRESULT_FROM_WIN32 (ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="c6870-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="c6870-135">Użytkownik procesu wyzwalacza nie ma dostępu do procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="c6870-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="c6870-136">HRESULT_FROM_WIN32 (ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="c6870-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="c6870-137">Użytkownik procesu wyzwalacza nie ma uprawnień niezbędnych do dołączenia profilera do danego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="c6870-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="c6870-138">Dziennik zdarzeń aplikacji może zawierać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="c6870-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="c6870-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="c6870-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="c6870-140">Wystąpił błąd podczas komunikacji z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="c6870-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="c6870-141">Zwykle zdarza się to, gdy proces docelowy został zamknięty.</span><span class="sxs-lookup"><span data-stu-id="c6870-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="c6870-142">HRESULT_FROM_WIN32 (ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="c6870-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="c6870-143">Proces docelowy nie istnieje lub nie działa z nim środowisko CLR obsługujące załącznik.</span><span class="sxs-lookup"><span data-stu-id="c6870-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="c6870-144">Może to wskazywać, że środowisko CLR zostało zwolnione od czasu wywołania metody wyliczania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c6870-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="c6870-145">HRESULT_FROM_WIN32 (ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="c6870-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="c6870-146">Upłynął limit czasu bez rozpoczęcia ładowania profilera.</span><span class="sxs-lookup"><span data-stu-id="c6870-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="c6870-147">Można ponowić próbę wykonania operacji Attach.</span><span class="sxs-lookup"><span data-stu-id="c6870-147">You can retry the attach operation.</span></span> <span data-ttu-id="c6870-148">Limity czasu są wykonywane, gdy finalizator w procesie docelowym jest uruchamiany przez dłuższy czas niż wartość limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="c6870-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="c6870-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c6870-149">E_INVALIDARG</span></span>|<span data-ttu-id="c6870-150">Co najmniej jeden parametr ma nieprawidłowe wartości.</span><span class="sxs-lookup"><span data-stu-id="c6870-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="c6870-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c6870-151">E_FAIL</span></span>|<span data-ttu-id="c6870-152">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="c6870-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="c6870-153">Inne kody błędów</span><span class="sxs-lookup"><span data-stu-id="c6870-153">Other error codes</span></span>|<span data-ttu-id="c6870-154">Jeśli metoda [ICorProfilerCallback3:: InitializeForAttach —](icorprofilercallback3-initializeforattach-method.md) profilera zwraca wartość HRESULT, która wskazuje błąd, `AttachProfiler` zwraca ten sam wynik HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c6870-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="c6870-155">W tym przypadku E_NOTIMPL jest konwertowany na CORPROF_E_PROFILER_NOT_ATTACHABLE.</span><span class="sxs-lookup"><span data-stu-id="c6870-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6870-156">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6870-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="c6870-157">Zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="c6870-157">Memory Management</span></span>  
 <span data-ttu-id="c6870-158">W zakresie utrzymywania z konwencjami COM wywołujący `AttachProfiler` (na przykład kod wyzwalacza utworzony przez twórcę profilera) jest odpowiedzialny za przydzielanie i cofanie przydziału pamięci dla danych, do których wskazuje parametr `pvClientData`.</span><span class="sxs-lookup"><span data-stu-id="c6870-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="c6870-159">Gdy środowisko CLR wykonuje wywołanie `AttachProfiler`, tworzy kopię pamięci, która `pvClientData` wskazuje i przesyła ją do procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="c6870-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="c6870-160">Gdy środowisko CLR wewnątrz procesu docelowego otrzymuje własną kopię bloku `pvClientData`, przekazuje blok do profilera za pośrednictwem metody `InitializeForAttach`, a następnie rozdziela jego kopię bloku `pvClientData` z procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="c6870-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6870-161">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6870-161">Requirements</span></span>  
 <span data-ttu-id="c6870-162">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6870-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6870-163">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c6870-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6870-164">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c6870-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6870-165">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6870-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6870-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6870-166">See also</span></span>

- [<span data-ttu-id="c6870-167">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="c6870-167">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c6870-168">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="c6870-168">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="c6870-169">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="c6870-169">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c6870-170">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="c6870-170">Profiling</span></span>](index.md)
