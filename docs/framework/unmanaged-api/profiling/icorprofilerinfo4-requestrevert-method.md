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
# <a name="icorprofilerinfo4requestrevert-method"></a>ICorProfilerInfo4::RequestRevert — Metoda
Przywraca oryginalne wersje wszystkich wystąpień określonych funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cFunctions`  
 podczas Liczba funkcji, które mają zostać przywrócone.  
  
 `moduleIds`  
 podczas Określa `moduleId` część `module` par (, `methodDef` ), które identyfikują funkcje, które mają zostać przywrócone.  
  
 `methodIds`  
 podczas Określa `methodId` część `module` par (, `methodDef` ), które identyfikują funkcje, które mają zostać przywrócone.  
  
 `status`  
 określoną Tablica wartości HRESULT wymienionych w sekcji "stan HRESULT" w dalszej części tego tematu. Każde HRESULT wskazuje powodzenie lub niepowodzenie próby przywrócenia każdej funkcji określonej w tablicach równoległych `moduleIds` i `methodIds` .  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Podjęto próbę przywrócenia wszystkich żądań; jednak zwracana tablica stanu musi być sprawdzona, aby określić, które funkcje zostały pomyślnie przywrócone.|  
|CORPROF_E_CALLBACK4_REQUIRED|Profiler musi zaimplementować interfejs [ICorProfilerCallback4](icorprofilercallback4-interface.md) , aby można było obsługiwać to wywołanie.|  
|CORPROF_E_REJIT_NOT_ENABLED|Ponowna kompilacja JIT nie została włączona. Należy włączyć ponowną kompilację JIT podczas inicjowania przy użyciu metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) , aby ustawić `COR_PRF_ENABLE_REJIT` flagę.|  
|E_INVALIDARG|`cFunctions`ma wartość 0 lub `moduleIds` lub `methodIds` równą `NULL` .|  
|E_OUTOFMEMORY|Środowisko CLR nie mogło wykonać żądania, ponieważ zabrakło pamięci.|  
  
## <a name="status-hresults"></a>Stan HRESULT  
  
|Wartość HRESULT tablicy stanu|Opis|  
|--------------------------|-----------------|  
|S_OK|Odpowiednia funkcja została pomyślnie przywrócona.|  
|E_INVALIDARG|`moduleID`Parametr lub `methodDef` jest `NULL` .|  
|CORPROF_E_DATAINCOMPLETE|Moduł nie jest jeszcze w pełni załadowany lub jest w trakcie jego zwalniania.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Określony moduł został dynamicznie wygenerowany (na przykład przez `Reflection.Emit` ). W związku z tym nie jest to obsługiwane przez tę metodę.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|Środowisko CLR nie może przywrócić określonej funkcji, ponieważ nie znaleziono odpowiadającego jej aktywnego żądania ponownej kompilacji. Ponowna kompilacja nigdy nie została żądana lub funkcja została już przywrócona.|  
|Inne|System operacyjny zwrócił błąd poza kontrolą środowiska CLR. Jeśli na przykład wywołanie systemowe w celu zmiany ochrony dostępu strony pamięci zakończy się niepowodzeniem, zostanie wyświetlony komunikat o błędzie systemu operacyjnego.|  
  
## <a name="remarks"></a>Uwagi  
 Przy następnym wywołaniu dowolnego wystąpienia funkcji revereted zostaną uruchomione oryginalne wersje funkcji. Jeśli funkcja jest już uruchomiona, zostanie zakończona wykonywanie uruchomionej wersji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo4 — Interfejs](icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
