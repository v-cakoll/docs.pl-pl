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
ms.openlocfilehash: 1a0f1e41f7d59074f997a5812da61fdbcd692770
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
  
#### <a name="parameters"></a>Parametry  
 `dwProfileeProcessID`  
 [in] Identyfikator procesu procesu, do której należy dołączyć profilera. Na komputerze 64-bitowych bitowości PROFILOWANEGO procesu musi pasuje do liczby bitów procesu wyzwalacz, który wywołuje `AttachProfiler`. Jeśli konto użytkownika, w którym `AttachProfiler` jest nazywany ma uprawnienia administracyjne, proces docelowy może być dowolnym procesu w systemie. W przeciwnym razie proces docelowy musi należeć do tego samego konta użytkownika.  
  
 `dwMillisecondsMax`  
 [in] Czas trwania (w milisekundach), aby uzyskać `AttachProfiler` do wykonania. Proces wyzwalacza należy przekazać przekroczenie limitu czasu jest znany wystarczający dla konkretnego profiler w celu wykonania inicjowania.  
  
 `pClsidProfiler`  
 [in] Wskaźnik do identyfikator CLSID profilera do załadowania. Proces wyzwalacza można ponownie użyć tej pamięci po `AttachProfiler` zwraca.  
  
 `wszProfilerPath`  
 [in] Pełna ścieżka do pliku DLL profilera do załadowania. Ten ciąg powinien zawierać nie więcej niż 260 znaków, włącznie z terminatorem null. Jeśli `wszProfilerPath` ma wartość null lub pusty ciąg, środowisko uruchomieniowe języka wspólnego (CLR) próbuje znaleźć lokalizację pliku biblioteki DLL profilera, wyszukując identyfikator CLSID w rejestrze który `pClsidProfiler` wskazuje.  
  
 `pvClientData`  
 [in] Wskaźnik do danych do przekazania do profilera przez [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metody. Proces wyzwalacza można ponownie użyć tej pamięci po `AttachProfiler` zwraca. Jeśli `pvClientData` ma wartość null, `cbClientData` musi być równa 0 (zero).  
  
 `cbClientData`  
 [in] Rozmiar w bajtach danych który `pvClientData` wskazuje.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące wyników HRESULT.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Określony profilera pomyślnie został dołączony do procesu docelowego.|  
|CORPROF_E_PROFILER_ALREADY_ACTIVE|Jest już profilera aktywnego lub dołączenia do procesu docelowego.|  
|CORPROF_E_PROFILER_NOT_ATTACHABLE|Określony profiler nie obsługuje załącznika. Proces wyzwalacz może podjąć próbę dołączenia innego profilera.|  
|CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER|Nie można zażądać załącznika profilera, ponieważ wersja procesu docelowego jest niezgodna z bieżącego procesu, który wywołuje `AttachProfiler`.|  
|HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)|Użytkownik procesu wyzwalacz nie ma dostępu do procesu docelowego.|  
|HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)|Użytkownik procesu wyzwalacz nie ma wystarczających uprawnień do Dołącz profiler do procesu docelowego podanego. W dzienniku zdarzeń aplikacji może zawierać więcej informacji.|  
|CORPROF_E_IPC_FAILED|Wystąpił błąd podczas komunikacji z procesem docelowym. Najczęściej dzieje się tak, jeśli proces docelowy była zamknięta.|  
|HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)|Proces docelowy nie istnieje lub nie jest uruchomiona CLR, która obsługuje załącznika. Może to wskazywać środowiska CLR został zwolniony od wywołania metody wyliczania środowiska wykonawczego.|  
|HRESULT_FROM_WIN32(ERROR_TIMEOUT)|Upłynął limit czasu bez początku można załadować profilera. Możesz ponowić próbę operacji dołączania. Limity czasu występują, jeśli finalizator w procesie docelowym jest uruchomione dłużej niż wartość limitu czasu.|  
|E_INVALIDARG|Co najmniej jeden parametr ma nieprawidłową wartość.|  
|E_FAIL|Niektóre inne, nieokreślony błąd.|  
|Inne kody błędów|Jeśli profilera [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metoda zwróci wartość HRESULT, która wskazuje niepowodzenie, `AttachProfiler` zwraca takim samym HRESULT. W takim przypadku E_NOTIMPL jest konwertowana na CORPROF_E_PROFILER_NOT_ATTACHABLE.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="memory-management"></a>Zarządzanie pamięcią  
 W zapewnieniu z konwencjami COM, funkcji wywołującej `AttachProfiler` (na przykład kod wyzwalacza utworzone przez dewelopera profilera) jest odpowiedzialny za przydzielanie i cofnąć alokacji pamięci dla danych, który `pvClientData` parametr wskazuje. Gdy wykonuje CLR `AttachProfiler` wywołanie, ułatwia kopię pamięć który `pvClientData` wskazuje i przesyła ją do procesu docelowego. Kiedy CLR w procesie docelowym otrzyma własną kopię `pvClientData` bloku, przekazaniem bloku do profilera za pośrednictwem `InitializeForAttach` metody, a następnie zwalnia jego kopii `pvClientData` blokowanie w procesie docelowym.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerInfo3 — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
