---
title: ICorProfilerInfo4::RequestReJIT — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ddad2497f18aa510ade41f58ba20c9de1a46ce5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135099"
---
# <a name="icorprofilerinfo4requestrejit-method"></a>ICorProfilerInfo4::RequestReJIT — Metoda
Żąda JIT — rekompilacja wszystkich wystąpień określonych funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cFunctions`  
 [in] Liczba funkcji ponownej kompilacji.  
  
 `moduleIds`  
 [in] Określa `moduleId` część (`module`, `methodDef`) pary, które identyfikują funkcji, które mają być ponownie kompilowane.  
  
 `methodIds`  
 [in] Określa `methodId` część (`module`, `methodDef`) pary, które identyfikują funkcji, które mają być ponownie kompilowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Aby oznaczyć wszystkie metody JIT — rekompilacja nastąpiła próba. Program profilujący musi zaimplementować [icorprofilercallback4::rejiterror —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) metodę pozwala ustalić metody, które zostały pomyślnie oznaczona do ponownej kompilacji JIT.|  
|CORPROF_E_CALLBACK4_REQUIRED|Program profilujący musi zaimplementować [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsu dla tego wywołania są obsługiwane.|  
|CORPROF_E_REJIT_NOT_ENABLED|JIT — rekompilacja nie została włączona. JIT — rekompilacja podczas inicjowania należy włączyć, używając [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby ustawić `COR_PRF_ENABLE_REJIT` flagi.|  
|E_INVALIDARG|`cFunctions` ma wartość 0, lub `moduleIds` lub `methodIds` jest `NULL`.|  
|||  
|E_OUTOFMEMORY|Nie można ukończyć żądania, ponieważ zabrakło jej pamięci CLR.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołaj `RequestReJIT` do środowiska uruchomieniowego określony zestaw funkcji, należy ponownie skompilować. Profiler kodu może używać [icorprofilerfunctioncontrol —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interfejsu, aby dopasować kod, który jest generowany, gdy funkcje są ponownie kompilowane. To nie wpływa na aktualnie wykonywanej funkcji, wywołania tylko przyszłych funkcji. Jeśli dowolny z określonych funkcji poprzednio ponownie skompilowana JIT, żądanie ponownej kompilacji jest odpowiednikiem Przywracanie i konieczności ponownego kompilowania funkcji. Aby zachować stosownie, kiedy kompilator JIT kompiluje oryginalnej wersji funkcji, traktuje oryginalnej wersji jego wywoływane dla wbudowanie decyzji. Gdy kompilator JIT, następuje rekompilacja funkcji, uzna aktualne wersje (oryginalna lub ponownie skompilowanymi) jej wywoływane dla wbudowanie.  
  
 Program profilujący zazwyczaj wywołuje `RequestReJIT` w odpowiedzi na żądanie, czy programu profilującego Instrumentację co najmniej jedną metodę wprowadzania danych przez użytkownika. `RequestReJIT` Zazwyczaj wstrzymuje działanie środowiska uruchomieniowego w celu wykonania niektórych prac i może potencjalnie wyzwalacza wyrzucania elementów bezużytecznych. W efekcie program profilujący powinien wywoływać `RequestReJIT` z wątku on wcześniej utworzony, a nie z utworzonego przez CLR wątku, jest w trakcie wykonywania zwrotnym profilera.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo4 — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
