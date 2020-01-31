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
# <a name="iclrprofilingattachprofiler-method"></a>ICLRProfiling::AttachProfiler — Metoda
Dołącza określony Profiler do określonego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a>Parametry

- `dwProfileeProcessID`

  \[] Identyfikator procesu, do którego ma zostać dołączony Profiler. Na komputerze 64-bitowym profilowana liczba bitów procesu PROFILOWANEGO musi być zgodna z bitową procesu wyzwalacza, który wywołuje `AttachProfiler`. Jeśli konto użytkownika, pod którym jest wywoływane `AttachProfiler` ma uprawnienia administracyjne, proces docelowy może być dowolnym procesem w systemie. W przeciwnym razie proces docelowy musi należeć do tego samego konta użytkownika.

- `dwMillisecondsMax`

  \[] czas trwania (w milisekundach) dla `AttachProfiler` do ukończenia. Proces wyzwalacza powinien przekroczyć limit czasu, który jest znany jako wystarczający dla danego profilera, aby zakończyć jego inicjalizację.
  
- `pClsidProfiler`

  \[w] wskaźnik do identyfikatora CLSID profilera do załadowania. Proces wyzwalacza może ponownie użyć tej pamięci po powrocie `AttachProfiler`.

- `wszProfilerPath`

  \[w] pełna ścieżka do pliku DLL profilera do załadowania. Ten ciąg nie może zawierać więcej niż 260 znaków, łącznie z terminatorem o wartości null. Jeśli `wszProfilerPath` ma wartość null lub jest pustym ciągiem, środowisko uruchomieniowe języka wspólnego (CLR) spróbuje znaleźć lokalizację pliku DLL profilera, przeglądając rejestr dla identyfikatora CLSID, do którego `pClsidProfiler` wskazują.

- `pvClientData`

  \[] wskaźnik do danych, które mają zostać przesłane do profilera przez metodę [ICorProfilerCallback3:: InitializeForAttach —](icorprofilercallback3-initializeforattach-method.md) . Proces wyzwalacza może ponownie użyć tej pamięci po powrocie `AttachProfiler`. Jeśli `pvClientData` ma wartość null, `cbClientData` musi mieć wartość 0 (zero).

- `cbClientData`

  \[] rozmiar (w bajtach) danych, do których `pvClientData` wskazują.

## <a name="return-value"></a>Wartość zwrócona  
 Ta metoda zwraca następujące HRESULTs.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Określony profiler został pomyślnie dołączony do procesu docelowego.|  
|CORPROF_E_PROFILER_ALREADY_ACTIVE|Istnieje już Profiler aktywny lub dołączany do procesu docelowego.|  
|CORPROF_E_PROFILER_NOT_ATTACHABLE|Określony Profiler nie obsługuje załącznika. Proces wyzwalacza może próbować dołączyć inny Profiler.|  
|CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER|Nie można zażądać załącznika profilera, ponieważ wersja procesu docelowego jest niezgodna z bieżącym procesem wywołującym `AttachProfiler`.|  
|HRESULT_FROM_WIN32 (ERROR_ACCESS_DENIED)|Użytkownik procesu wyzwalacza nie ma dostępu do procesu docelowego.|  
|HRESULT_FROM_WIN32 (ERROR_PRIVILEGE_NOT_HELD)|Użytkownik procesu wyzwalacza nie ma uprawnień niezbędnych do dołączenia profilera do danego procesu docelowego. Dziennik zdarzeń aplikacji może zawierać więcej informacji.|  
|CORPROF_E_IPC_FAILED|Wystąpił błąd podczas komunikacji z procesem docelowym. Zwykle zdarza się to, gdy proces docelowy został zamknięty.|  
|HRESULT_FROM_WIN32 (ERROR_FILE_NOT_FOUND)|Proces docelowy nie istnieje lub nie działa z nim środowisko CLR obsługujące załącznik. Może to wskazywać, że środowisko CLR zostało zwolnione od czasu wywołania metody wyliczania środowiska uruchomieniowego.|  
|HRESULT_FROM_WIN32 (ERROR_TIMEOUT)|Upłynął limit czasu bez rozpoczęcia ładowania profilera. Można ponowić próbę wykonania operacji Attach. Limity czasu są wykonywane, gdy finalizator w procesie docelowym jest uruchamiany przez dłuższy czas niż wartość limitu czasu.|  
|E_INVALIDARG|Co najmniej jeden parametr ma nieprawidłowe wartości.|  
|E_FAIL|Wystąpił nieokreślony błąd.|  
|Inne kody błędów|Jeśli metoda [ICorProfilerCallback3:: InitializeForAttach —](icorprofilercallback3-initializeforattach-method.md) profilera zwraca wartość HRESULT, która wskazuje błąd, `AttachProfiler` zwraca ten sam wynik HRESULT. W tym przypadku E_NOTIMPL jest konwertowany na CORPROF_E_PROFILER_NOT_ATTACHABLE.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="memory-management"></a>Zarządzanie pamięcią  
 W zakresie utrzymywania z konwencjami COM wywołujący `AttachProfiler` (na przykład kod wyzwalacza utworzony przez twórcę profilera) jest odpowiedzialny za przydzielanie i cofanie przydziału pamięci dla danych, do których wskazuje parametr `pvClientData`. Gdy środowisko CLR wykonuje wywołanie `AttachProfiler`, tworzy kopię pamięci, która `pvClientData` wskazuje i przesyła ją do procesu docelowego. Gdy środowisko CLR wewnątrz procesu docelowego otrzymuje własną kopię bloku `pvClientData`, przekazuje blok do profilera za pośrednictwem metody `InitializeForAttach`, a następnie rozdziela jego kopię bloku `pvClientData` z procesu docelowego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
- [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
