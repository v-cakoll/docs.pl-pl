---
title: ICorProfilerCallback3::ProfilerDetachSucceeded — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8cff277179be761bb0dc78b02702e7d35ad4b6a9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779248"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a>ICorProfilerCallback3::ProfilerDetachSucceeded — Metoda
Powiadamia program profilujący, że środowisko uruchomieniowe języka wspólnego (CLR) zostanie zwolnienia biblioteki DLL profilera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwrócona przez to wywołanie zwrotne jest ignorowany.  
  
## <a name="remarks"></a>Uwagi  
 `ProfilerDetachSucceeded` Wywołanie zwrotne zostało wydane po zamknięciu wszystkich wątków programu profilującego kodu. Gdy ta metoda jest wywoływana, program profilujący, należy wykonać wszelkie zadania ostatniej chwili, które nie są odpowiednie dla jego destruktor, takie jak jego interfejsu użytkownika lub składnik rejestrowania zgłaszające. Jednakże program profilujący nie mogą wywoływać funkcje dla interfejsów, które są dostarczane przez środowisko CLR Podczas tego wywołania zwrotnego (takie jak [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) lub `IMetaData*` interfejsów).  
  
 Środowisko CLR tworzy wpis w dzienniku zdarzeń aplikacji Windows, aby wskazać, czy operacja odłączenia powiodła się.  
  
 Po profiler zwraca z to wywołanie zwrotne, środowisko CLR zwalnia obiekt profilera i wyładowuje profiler DLL. W związku z tym program profilujący nie musi wykonywać wszystkie akcje, które mogłoby spowodować wykonanie zapytania wewnątrz biblioteki DLL profilera po zwraca od to wywołanie zwrotne. Na przykład nie musi tworzyć wątków lub rejestrowanie wywołań zwrotnych czasomierza.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
