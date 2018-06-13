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
ms.openlocfilehash: be7184e07815ebe222b8ff8736c26fd3879c8777
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460711"
---
# <a name="icorprofilerinfo4requestrejit-method"></a>ICorProfilerInfo4::RequestReJIT — Metoda
Żądania kompilacji JIT, wszystkich wystąpień określonych funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cFunctions`  
 [in] Liczba funkcji ponowną kompilację.  
  
 `moduleIds`  
 [in] Określa `moduleId` część (`module`, `methodDef`) pary, które identyfikują funkcje do ponownej kompilacji.  
  
 `methodIds`  
 [in] Określa `methodId` część (`module`, `methodDef`) pary, które identyfikują funkcje do ponownej kompilacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Nastąpiła próba można oznaczyć wszystkie metody na potrzeby ponownej kompilacji JIT. Profiler musi implementować [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) metodę, aby określić, które metody pomyślnie zostały oznaczona do ponownej kompilacji JIT.|  
|CORPROF_E_CALLBACK4_REQUIRED|Profiler musi implementować [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejs dla tego wywołania do obsługi.|  
|CORPROF_E_REJIT_NOT_ENABLED|Nie włączono ponownej kompilacji JIT. Należy włączyć ponownej kompilacji JIT podczas inicjowania przy użyciu [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby ustawić `COR_PRF_ENABLE_REJIT` flagi.|  
|E_INVALIDARG|`cFunctions` ma wartość 0, lub `moduleIds` lub `methodIds` jest `NULL`.|  
|||  
|E_OUTOFMEMORY|Środowisko CLR nie może wykonać żądania, ponieważ zabrakło pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie `RequestReJIT` Aby ponownie skompilować określony zestaw funkcji środowiska uruchomieniowego. Profiler kodu można następnie użyć [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interfejsu, aby dopasować kod, który jest generowany, gdy te funkcje są ponownie kompilowana. Nie dotyczy to aktualnie wykonywane funkcje, wywołania funkcji tylko w przyszłości. Jeśli określona funkcje poprzednio JIT ponownie skompilowana, żądanie ponownej jest odpowiednikiem przywrócenie i ponownie funkcji. Aby zachować stosownie, kiedy przy użyciu kompilatora JIT kompiluje z oryginalną wersją funkcji, traktuje oryginalnej wersji jego callees ze śródwierszowaniem decyzji. Kompilator JIT rekompiluje funkcję, traktuje bieżące wersje jego callees dla (ponownej kompilacji lub oryginalnego) ze śródwierszowaniem.  
  
 Profiler zwykle wymaga `RequestReJIT` w odpowiedzi na żądanie, że profiler Instrumentacja co najmniej jedną metodę wprowadzania danych przez użytkownika. `RequestReJIT` zwykle wstrzymuje środowiska uruchomieniowego w celu wykonania określonej prac i może potencjalnie wyzwalacza wyrzucania elementów bezużytecznych. W efekcie powinny wywoływać profilera `RequestReJIT` wprowadzanych przez wątek on wcześniej utworzony, a nie z wątku utworzone CLR który jest obecnie wykonywane wywołanie zwrotne profilera.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
