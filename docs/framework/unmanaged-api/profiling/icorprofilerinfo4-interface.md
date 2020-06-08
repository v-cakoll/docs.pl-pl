---
title: ICorProfilerInfo4 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
ms.openlocfilehash: 58d11e9084f53c69f2656b4f0ee6bc7d2cc4ae21
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495869"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 — Interfejs
Zapewnia metody, które są używane przez program codeer do komunikowania się ze środowiskiem uruchomieniowym języka wspólnego (CLR) w celu kontrolowania informacji o monitorowaniu zdarzeń i żądaniach. . `ICorProfilerInfo4`Interfejs jest rozszerzeniem innych `ICorProfilerInfo` interfejsów. Udostępnia nowe metody obsługi ponownej kompilacji just-in-Time (JIT), dodane w .NET Framework 4,5.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumJITedFunctions2, metoda](icorprofilerinfo4-enumjitedfunctions2-method.md)|Zwraca moduł wyliczający dla wszystkich funkcji, które były poprzednio skompilowane JIT i ponownie skompilowane w trybie JIT.|  
|[EnumThreads, metoda](icorprofilerinfo4-enumthreads-method.md)|Pobiera moduł wyliczający, który dostarcza metody sekwencyjnie iteracji przez kolekcję wszystkich zarządzanych wątków w profilowanym procesie.|  
|[GetCodeInfo3, metoda](icorprofilerinfo4-getcodeinfo3-method.md)|Pobiera zakresy kodu natywnego skojarzone z rekompilowaną ponownie wersją określonej funkcji JIT.|  
|[GetFunctionFromIP2, metoda](icorprofilerinfo4-getfunctionfromip2-method.md)|Mapuje wskaźnik zarządzanej instrukcji kodu do wersji z ponowną kompilacją JIT dla określonej funkcji.|  
|[GetILToNativeMapping2, metoda](icorprofilerinfo4-getiltonativemapping2-method.md)|Pobiera mapę z przesunięcia języka pośredniego firmy Microsoft (MSIL) do natywnych przesunięć dla kodu zawartego w ponownej kompilacji JIT w wersji określonej funkcji.|  
|[GetObjectSize2, metoda](icorprofilerinfo4-getobjectsize2-method.md)|Zwraca rozmiar określonego obiektu.|  
|[GetReJITIDs, metoda](icorprofilerinfo4-getrejitids-method.md)|Zwraca tablicę identyfikatorów, które identyfikują wszystkie wersje JIT-ponownie skompilowane określonej funkcji, które są nadal przydzieleni.|  
|[InitializeCurrentThread, metoda](icorprofilerinfo4-initializecurrentthread-method.md)|Inicjuje bieżący wątek przed kolejnymi wywołaniami interfejsu API profilera w tym samym wątku, aby można było uniknąć zakleszczenia.|  
|[RequestReJIT, metoda](icorprofilerinfo4-requestrejit-method.md)|Żąda ponownej kompilacji JIT wszystkich wystąpień określonych funkcji.|  
|[RequestRevert, metoda](icorprofilerinfo4-requestrevert-method.md)|Przywraca oryginalne wersje wszystkich wystąpień określonych funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR implementuje metody `ICorProfilerInfo4` interfejsu przy użyciu modelu typu "wolny-wątek". Każda metoda zwraca wynik HRESULT wskazujący powodzenie lub niepowodzenie. Aby uzyskać listę możliwych kodów powrotu, zobacz plik CorError. h.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
