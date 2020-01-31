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
ms.openlocfilehash: b96a8930c24275546b0aac9fa650cf5447ef4ef2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865418"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a>ICorProfilerCallback3::ProfilerDetachSucceeded — Metoda
Powiadamia program profilujący, że aparat plików wykonywalnych języka wspólnego (CLR) ma zwolnić plik DLL profilera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a>Wartość zwrócona  
 Wartość zwracana z tego wywołania zwrotnego jest ignorowana.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie zwrotne `ProfilerDetachSucceeded` jest emitowane po zakończeniu przez wszystkie wątki kodu profilera. Gdy ta metoda jest wywoływana, profiler powinien wykonać wszystkie ostatnie zadania, które nie są odpowiednie dla destruktora, takie jak powiadamianie jego interfejsu użytkownika lub składnika rejestrowania. Jednak Profiler nie może wywoływać funkcji w interfejsach, które są dostarczane przez środowisko CLR w trakcie tego wywołania zwrotnego (takiego jak interfejsy [ICorProfilerInfo](icorprofilerinfo-interface.md) lub `IMetaData*`).  
  
 Środowisko CLR tworzy wpis w dzienniku zdarzeń aplikacji systemu Windows, aby wskazać, że operacja odłączenia zakończyła się pomyślnie.  
  
 Po powrocie profilera z tego wywołania zwrotnego środowisko CLR zwalnia obiekt profilera i zwalnia plik Profiler DLL. W związku z tym Profiler nie może wykonywać żadnych akcji, które mogłyby spowodować wystąpienie w pliku DLL profilera po powrocie z tego wywołania zwrotnego. Na przykład nie może tworzyć wątków ani rejestrować wywołań zwrotnych czasomierza.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
