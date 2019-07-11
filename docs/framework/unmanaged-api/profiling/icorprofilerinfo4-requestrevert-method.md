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
ms.openlocfilehash: 5e74cb663f968cc9b1b04a912307e3b4a12e86d4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748664"
---
# <a name="icorprofilerinfo4requestrevert-method"></a>ICorProfilerInfo4::RequestRevert — Metoda
Przywraca wszystkie wystąpienia określonych funkcji do ich oryginalnej wersji.  
  
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
 [in] Liczba funkcji do przywrócenia.  
  
 `moduleIds`  
 [in] Określa `moduleId` część (`module`, `methodDef`) pary, które identyfikują funkcji, które mają zostać przywrócone.  
  
 `methodIds`  
 [in] Określa `methodId` część (`module`, `methodDef`) pary, które identyfikują funkcji, które mają zostać przywrócone.  
  
 `status`  
 [out] Tablica wartości HRESULT wymienionych w sekcji "Wartości HRESULT stanu" w dalszej części tego tematu. Każda wartość HRESULT wskazuje powodzenie lub niepowodzenie próbę przywrócenia każdej funkcji, które określono w tablicach równoległe `moduleIds` i `methodIds`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Próbowano przywrócić wszystkie żądania; Jednak tablica zwrócona stanu musi być zaznaczone do określenia, które funkcje zostały pomyślnie przywrócone.|  
|CORPROF_E_CALLBACK4_REQUIRED|Program profilujący musi zaimplementować [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsu dla tego wywołania są obsługiwane.|  
|CORPROF_E_REJIT_NOT_ENABLED|JIT — rekompilacja nie została włączona. JIT — rekompilacja podczas inicjowania należy włączyć, używając [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby ustawić `COR_PRF_ENABLE_REJIT` flagi.|  
|E_INVALIDARG|`cFunctions` ma wartość 0, lub `moduleIds` lub `methodIds` jest `NULL`.|  
|E_OUTOFMEMORY|Nie można ukończyć żądania, ponieważ zabrakło jej pamięci CLR.|  
  
## <a name="status-hresults"></a>Stan HRESULTS  
  
|Stan macierzy HRESULT|Opis|  
|--------------------------|-----------------|  
|S_OK|Odpowiednich funkcji została pomyślnie przywrócona.|  
|E_INVALIDARG|`moduleID` Lub `methodDef` parametr `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Moduł nie jest jeszcze w pełni załadowany lub jest właśnie Trwa zwalnianie.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Określony moduł dynamicznie został wygenerowany (np. przez `Reflection.Emit`). W związku z tym nie jest obsługiwane przez tę metodę.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|Środowisko CLR nie można przywrócić określonej funkcji, ponieważ nie znaleziono odpowiedniego żądania active ponownej kompilacji. Nigdy nie zażądano ponowną kompilację albo funkcja została już przywrócona.|  
|Inne|System operacyjny zwrócił błąd poza kontrolą środowiska CLR. Na przykład jeśli wywołanie systemowe, aby zmienić ustawienia ochrony dostępu do strony pamięci nie powiedzie się, zostanie wyświetlony błąd systemu operacyjnego.|  
  
## <a name="remarks"></a>Uwagi  
 Przy następnym noszą nazwę wszystkich wystąpień funkcji revereted, oryginalnym wersje funkcji zostanie uruchomiony. Funkcja jest już uruchomiona, zostanie ono ukończone, wykonywanie wersję, która jest uruchomiona.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
