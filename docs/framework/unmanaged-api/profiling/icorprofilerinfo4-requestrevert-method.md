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
ms.locfileid: "33460327"
---
# <a name="icorprofilerinfo4requestrevert-method"></a>ICorProfilerInfo4::RequestRevert — Metoda
Przywraca wszystkie wystąpienia określonych funkcji, do ich oryginalnej wersji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cFunctions`  
 [in] Liczbę funkcji do przywrócenia.  
  
 `moduleIds`  
 [in] Określa `moduleId` część (`module`, `methodDef`) pary, które identyfikują funkcje przywrócenie.  
  
 `methodIds`  
 [in] Określa `methodId` część (`module`, `methodDef`) pary, które identyfikują funkcje przywrócenie.  
  
 `status`  
 [out] Tablica wyników HRESULT wymienionych w sekcji "Wyników HRESULT stan" w dalszej części tego tematu. Każdy HRESULT wskazuje powodzenie lub niepowodzenie próbę przywrócenia każdej funkcji określony w tablicach równoległych `moduleIds` i `methodIds`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Podjęto próbę przywrócenia wszystkich żądań; jednak zwrócony stan tablicy musi być zaznaczone do określenia, jakie funkcje zostały pomyślnie przywrócone.|  
|CORPROF_E_CALLBACK4_REQUIRED|Profiler musi implementować [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejs dla tego wywołania do obsługi.|  
|CORPROF_E_REJIT_NOT_ENABLED|Nie włączono ponownej kompilacji JIT. Należy włączyć ponownej kompilacji JIT podczas inicjowania przy użyciu [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby ustawić `COR_PRF_ENABLE_REJIT` flagi.|  
|E_INVALIDARG|`cFunctions` ma wartość 0, lub `moduleIds` lub `methodIds` jest `NULL`.|  
|E_OUTOFMEMORY|Środowisko CLR nie może wykonać żądania, ponieważ zabrakło pamięci.|  
  
## <a name="status-hresults"></a>Stan wyników HRESULT  
  
|Stan tablicy HRESULT|Opis|  
|--------------------------|-----------------|  
|S_OK|Odpowiednich funkcji została pomyślnie przywrócona.|  
|E_INVALIDARG|`moduleID` Lub `methodDef` parametr jest `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Moduł nie został jeszcze całkowicie załadowany lub Trwa zwalnianie modułu.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Określony moduł został generowane dynamicznie (np. przez `Reflection.Emit`). W związku z tym jest nieobsługiwany przez tę metodę.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|Środowisko CLR nie można przywrócić określonej funkcji, ponieważ nie znaleziono odpowiedniego żądania active ponownej kompilacji. Nigdy nie odebrał żądanie ponownej kompilacji albo funkcję już została przywrócona.|  
|Inne|System operacyjny zwrócił błąd poza kontrolą środowiska CLR. Na przykład jeśli wystąpi błąd wywołania systemu, aby zmienić ustawienia ochrony dostępu do strony pamięci, zostanie wyświetlony błąd systemu operacyjnego.|  
  
## <a name="remarks"></a>Uwagi  
 Przy następnym wszystkich wystąpień funkcji revereted są nazywane, oryginalnej wersji funkcji zostanie uruchomiony. Jeśli funkcja jest już uruchomiona, zostanie zakończony, wykonywania wersję, do której jest uruchomiony.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
