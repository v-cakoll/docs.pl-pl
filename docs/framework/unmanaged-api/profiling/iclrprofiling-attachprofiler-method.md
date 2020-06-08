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
ms.openlocfilehash: 48ac09e1862ae58e79707235e891f72920de1251
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500562"
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

  \[in] Identyfikator procesu, do którego ma zostać dołączony Profiler. Na komputerze 64-bitowym profilowana liczba bitów procesu PROFILOWANEGO musi być zgodna z bitową wywoływanym przez proces wyzwalacza `AttachProfiler` . Jeśli konto użytkownika, pod którym `AttachProfiler` jest wywoływane, ma uprawnienia administracyjne, proces docelowy może być dowolnym procesem w systemie. W przeciwnym razie proces docelowy musi należeć do tego samego konta użytkownika.

- `dwMillisecondsMax`

  \[w] czas trwania w milisekundach do `AttachProfiler` ukończenia. Proces wyzwalacza powinien przekroczyć limit czasu, który jest znany jako wystarczający dla danego profilera, aby zakończyć jego inicjalizację.
  
- `pClsidProfiler`

  \[w] wskaźnik do identyfikatora CLSID profilera do załadowania. Proces wyzwalacza może ponownie użyć tej pamięci po `AttachProfiler` powrocie.

- `wszProfilerPath`

  \[w] pełna ścieżka do pliku DLL profilera do załadowania. Ten ciąg nie może zawierać więcej niż 260 znaków, łącznie z terminatorem o wartości null. Jeśli `wszProfilerPath` parametr ma wartość null lub jest pustym ciągiem, środowisko uruchomieniowe języka wspólnego (CLR) spróbuje znaleźć lokalizację pliku DLL profilera, przeglądając rejestr dla identyfikatora CLSID wskazującego `pClsidProfiler` na.

- `pvClientData`

  \[w] wskaźnik do danych, które mają zostać przesłane do profilera przez metodę [ICorProfilerCallback3:: InitializeForAttach —](icorprofilercallback3-initializeforattach-method.md) . Proces wyzwalacza może ponownie użyć tej pamięci po `AttachProfiler` powrocie. Jeśli `pvClientData` ma wartość null, `cbClientData` musi mieć wartość 0 (zero).

- `cbClientData`

  \[w] rozmiar, w bajtach, danych, które `pvClientData` wskazują.

## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące HRESULTs.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Określony profiler został pomyślnie dołączony do procesu docelowego.|  
|CORPROF_E_PROFILER_ALREADY_ACTIVE|Istnieje już Profiler aktywny lub dołączany do procesu docelowego.|  
|CORPROF_E_PROFILER_NOT_ATTACHABLE|Określony Profiler nie obsługuje załącznika. Proces wyzwalacza może próbować dołączyć inny Profiler.|  
|CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER|Nie można zażądać załącznika profilera, ponieważ wersja procesu docelowego jest niezgodna z bieżącym procesem wywołującym `AttachProfiler` .|  
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
 W zakresie utrzymywania z konwencjami COM obiekt wywołujący `AttachProfiler` (na przykład kod wyzwalacza utworzony przez twórcę profilera) jest odpowiedzialny za przydzielanie i cofanie przydziału pamięci dla danych, `pvClientData` do których wskazuje parametr. Gdy środowisko CLR wykonuje `AttachProfiler` wywołanie, tworzy kopię pamięci, która `pvClientData` wskazuje na i przesyła ją do procesu docelowego. Gdy środowisko CLR wewnątrz procesu docelowego otrzymuje własną kopię `pvClientData` bloku, przekazuje blok do profilera za pośrednictwem `InitializeForAttach` metody, a następnie cofa alokację kopii `pvClientData` bloku z procesu docelowego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
