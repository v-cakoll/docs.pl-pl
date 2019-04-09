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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e3898fb836409df3b685d985d0d72ab63230a93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174177"
---
# <a name="iclrprofilingattachprofiler-method"></a>ICLRProfiling::AttachProfiler — Metoda
Dołącza określony profiler do określonego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a>Parametry  
 `dwProfileeProcessID`  
 [in] Identyfikator procesu proces, do którego program profilujący powinien być dołączony. Na komputerze 64-bitowym, bitowości PROFILOWANEGO procesu musi odpowiadać wartości bitowości proces wyzwalacza, która wywołuje `AttachProfiler`. Jeśli konto użytkownika, pod którym `AttachProfiler` jest nazywany ma uprawnienia administracyjne, proces docelowy może być dowolnym procesu w systemie. W przeciwnym razie proces docelowy musi należeć do tego samego konta użytkownika.  
  
 `dwMillisecondsMax`  
 [in] Czas trwania (w milisekundach), aby uzyskać `AttachProfiler` do ukończenia. Proces wyzwalacza powinien przekazać limitu czasu, który jest znany się wystarczająca dla konkretnego profiler, aby zakończyć proces inicjacji.  
  
 `pClsidProfiler`  
 [in] Wskaźnik do identyfikator CLSID programu profiler do załadowania. Proces wyzwalacza można ponownie użyć tej pamięci po `AttachProfiler` zwraca.  
  
 `wszProfilerPath`  
 [in] Pełna ścieżka do pliku DLL programu profilującego do załadowania. Ten ciąg może zawierać nie więcej niż 260 znaków, łącznie z terminatorem null. Jeśli `wszProfilerPath` ma wartość null lub pustym ciągiem, środowisko uruchomieniowe języka wspólnego (CLR) spróbuje znaleźć lokalizację pliku DLL profilera, wyszukując w rejestrze identyfikator CLSID, `pClsidProfiler` wskazuje.  
  
 `pvClientData`  
 [in] Wskaźnik do danych, które zostaną przekazane do profilera za [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metody. Proces wyzwalacza można ponownie użyć tej pamięci po `AttachProfiler` zwraca. Jeśli `pvClientData` ma wartość null, `cbClientData` musi mieć wartość 0 (zero).  
  
 `cbClientData`  
 [in] Rozmiar w bajtach, danych, który `pvClientData` wskazuje.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące wartości HRESULT.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Określony profiler dołączył pomyślnie do procesu docelowego.|  
|CORPROF_E_PROFILER_ALREADY_ACTIVE|Istnieje już program profilujący, aktywny lub dołączanie do procesu docelowego.|  
|CORPROF_E_PROFILER_NOT_ATTACHABLE|Określony program profilujący nie obsługuje załącznika. Proces wyzwalacza może podjąć próbę dołączenia profilera różne.|  
|CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER|Nie można żądać załącznika profiler, ponieważ wersja procesu docelowego jest niezgodna z bieżącego procesu, który wywołuje `AttachProfiler`.|  
|HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)|Użytkownik proces wyzwalacza nie ma dostępu do procesu docelowego.|  
|HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)|Użytkownik proces wyzwalacza nie ma wystarczających uprawnień do dołączania profilera do procesu docelowej. W dzienniku zdarzeń aplikacji może zawierać więcej informacji.|  
|CORPROF_E_IPC_FAILED|Wystąpił błąd podczas komunikacji z procesem docelowym. Zwykle dzieje się tak, jeśli proces docelowy został zamykanie.|  
|HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)|Proces docelowy nie istnieje lub nie jest uruchomiona CLR, która obsługuje załącznika. Może to oznaczać, że CLR został zwolniony, od wywołania do metody wyliczenia środowiska uruchomieniowego.|  
|HRESULT_FROM_WIN32(ERROR_TIMEOUT)|Upłynął limit czasu bez początku ładowanie profilera. Możesz ponowić próbę operacji dołączania. Limity czasu wystąpić, gdy finalizator w procesie docelowym działa przez dłuższy czas niż wartość limitu czasu.|  
|E_INVALIDARG|Jeden lub więcej parametrów ma nieprawidłową wartość.|  
|E_FAIL|Wystąpił błąd w niektórych innych, nieokreślone.|  
|Inne kody błędów|Jeśli profiler [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metoda zwróci wartość HRESULT, która wskazuje błąd, `AttachProfiler` zwraca takim samym HRESULT. W tym przypadku E_NOTIMPL jest konwertowany CORPROF_E_PROFILER_NOT_ATTACHABLE.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="memory-management"></a>Zarządzanie pamięcią  
 W zachowaniu z konwencjami COM, obiekt wywołujący `AttachProfiler` (na przykład, kod wyzwalacza opracowane przez Deweloper profilera) jest odpowiedzialny za przydzielanie i cofnięcia przydziału pamięci dla danych, który `pvClientData` parametr wskazuje. Gdy środowisko CLR wykonuje `AttachProfiler` wywołanie, jego tworzy kopię pamięć, `pvClientData` wskazuje i przesyła je do procesu docelowego. Gdy środowisko CLR w procesie docelowym otrzyma własną kopię `pvClientData` bloku, przekazuje bloku do profilera za pośrednictwem `InitializeForAttach` metody i następnie zwalnia jego kopię `pvClientData` blok z procesu docelowego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerInfo3 — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
