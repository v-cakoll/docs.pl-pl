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
ms.openlocfilehash: d2f8d538adb965864915fb1195bf9f2b8488aac8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868411"
---
# <a name="icorprofilerinfo4requestrejit-method"></a>ICorProfilerInfo4::RequestReJIT — Metoda
Żąda ponownej kompilacji JIT wszystkich wystąpień określonych funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cFunctions`  
 podczas Liczba funkcji, które mają zostać ponownie skompilowane.  
  
 `moduleIds`  
 podczas Określa `moduleId` część par (`module`, `methodDef`), które identyfikują funkcje, które mają być ponownie skompilowane.  
  
 `methodIds`  
 podczas Określa `methodId` część par (`module`, `methodDef`), które identyfikują funkcje, które mają być ponownie skompilowane.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Podjęto próbę oznaczenia wszystkich metod ponownej kompilacji JIT. Profiler musi zaimplementować metodę [ICorProfilerCallback4:: ReJITError —](icorprofilercallback4-rejiterror-method.md) , aby określić, które metody zostały pomyślnie oznaczone do ponownej kompilacji JIT.|  
|CORPROF_E_CALLBACK4_REQUIRED|Profiler musi zaimplementować interfejs [ICorProfilerCallback4](icorprofilercallback4-interface.md) , aby można było obsługiwać to wywołanie.|  
|CORPROF_E_REJIT_NOT_ENABLED|Ponowna kompilacja JIT nie została włączona. Należy włączyć ponowną kompilację JIT podczas inicjowania przy użyciu metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) w celu ustawienia flagi `COR_PRF_ENABLE_REJIT`.|  
|E_INVALIDARG|`cFunctions` jest równa 0 lub `moduleIds` lub `methodIds` jest `NULL`.|  
|||  
|E_OUTOFMEMORY|Środowisko CLR nie mogło wykonać żądania, ponieważ zabrakło pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołaj `RequestReJIT`, aby środowisko uruchomieniowe ponownie skompiluje określony zestaw funkcji. Profiler kodu może następnie użyć interfejsu [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) , aby dostosować kod generowany podczas ponownego kompilowania funkcji. Nie ma to wpływu na aktualnie wykonywane funkcje, tylko w przyszłości wywołania funkcji. Jeśli którekolwiek z określonych funkcji zostało wcześniej ponownie skompilowane w trybie JIT, żądanie ponownej kompilacji jest równoznaczne z przywróceniem i ponownym kompilacją funkcji. Aby zachować odwracalność, gdy kompilator JIT kompiluje oryginalną wersję funkcji, bierze pod uwagę tylko oryginalne wersje wywoływane na potrzeby podejmowania decyzji dotyczących podkreślenia. Gdy kompilator JIT ponownie kompiluje funkcję, traktuje bieżące wersje (ponownie skompilowane lub oryginalnie) jego wywoływane do tworzenia konspektu.  
  
 Profiler zazwyczaj wywołuje `RequestReJIT` w odpowiedzi na dane wejściowe użytkownika z żądaniem, że instrument profilera ma jedną lub więcej metod. `RequestReJIT` zazwyczaj wstrzymuje środowisko uruchomieniowe, aby wykonać część jego pracy i może potencjalnie wyzwolić wyrzucanie elementów bezużytecznych. W związku z tym Profiler powinien wywołać `RequestReJIT` z wcześniej utworzonego wątku, a nie z wątku utworzonego przez środowisko CLR, który aktualnie wykonuje wywołanie zwrotne profilera.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo4, interfejs](icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
