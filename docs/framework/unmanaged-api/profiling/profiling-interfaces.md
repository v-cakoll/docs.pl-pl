---
title: Interfejsy profilowania
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: adc47417265d32d79508af949c118c4d31a83365
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124195"
---
# <a name="profiling-interfaces"></a>Interfejsy profilowania
W tej sekcji opisano niezarządzane interfejsy, które umożliwiają profilowanie programu wykonywanego przez środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ICLRProfiling, interfejs](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 Udostępnia metodę [AttachProfiler —](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) , która umożliwia profilerowi dołączenie do uruchomionego procesu.  
  
 [ICorProfilerAssemblyReferenceProvider, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 Umożliwia programowi Profiler informowanie CLR o odwołaniach do zestawów, które Profiler doda do wywołania zwrotnego [ICorProfilerCallback:: ModuleLoadFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) .  
  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 Dostarcza metody, które są używane przez środowisko CLR do powiadamiania profilera kodu o wystąpieniu zdarzeń subskrybowanych przez profiler.  
  
 [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 Rozszerza interfejs `ICorProfilerCallback` z wywołaniami zwrotnymi obsługiwanymi w .NET Framework 2,0 i nowszymi wersjami.  
  
 [ICorProfilerCallback3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 Zapewnia metody wywołania zwrotnego używane przez środowisko CLR do przekazywania informacji o stanie dołączania i odłączania do profilera.  
  
 [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 Zapewnia metody wywołania zwrotnego używane przez środowisko CLR do przekazywania informacji do profilera.  
  
 [ICorProfilerCallback5, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 Zapewnia metodę, która identyfikuje przechodnie zamknięcie obiektów, do których odwołują się katalogi główne wyrzucania elementów bezużytecznych.  
  
 [ICorProfilerCallback6, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 Zapewnia metodę wywołania zwrotnego używaną przez środowisko CLR do powiadomienia profilera o ładowaniu zestawu.  
  
 [ICorProfilerCallback7, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 Zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o aktualizowaniu strumienia symboli skojarzonego z modułem w pamięci.  

[ICorProfilerCallback8, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
Zapewnia metody wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o rozpoczęciu i zakończeniu kompilacji JIT metody dynamicznej.

[ICorProfilerCallback9, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
Zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadomienia profilera, że metoda dynamiczna jest odzyskiwana, a następnie zwolniona.

 [ICorProfilerFunctionControl, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 Dostarcza metody, które umożliwiają profilerowi kodu komunikowanie się z środowiskiem CLR w celu kontrolowania sposobu generowania kodu przez kompilator JIT podczas ponownego kompilowania określonej metody.  
  
 [ICorProfilerFunctionEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 Zapewnia metody sekwencyjnej iteracji przez kolekcję funkcji w środowisku CLR.  
  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 Zapewnia metody do użycia przez program Code profilowas do komunikowania się z środowiskiem CLR w celu kontrolowania informacji o monitorowaniu zdarzeń i żądaniu.  
  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 Rozszerza interfejs `ICorProfilerInfo` z metodami obsługiwanymi w .NET Framework 2,0 i nowszymi wersjami.  
  
 [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 Rozszerza interfejs `ICorProfilerInfo2` z metodami obsługiwanymi w .NET Framework 4 i nowszych wersjach.  
  
 [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 Dostarcza metody, których program codeer używa do komunikacji z środowiskiem CLR w celu kontrolowania monitorowania zdarzeń oraz żądania informacji.  
  
 [ICorProfilerInfo5, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 Zapewnia metody do użycia przez program Code profilowas do komunikowania się z środowiskiem CLR w celu kontrolowania monitorowania zdarzeń.  
  
 [ICorProfilerInfo6, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 Dostarcza moduł wyliczający do wszystkich metod, które należą do danego modułu NGen i są zawarte w treści danej metody.  
  
 [ICorProfilerInfo7, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 Zapewnia metodę zastosowania nowo zdefiniowanych metadanych do modułu, który zapewnia dostęp do strumienia symboli w pamięci.  
  
 [ICorProfilerModuleEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 Dostarcza metody sekwencyjnie iteracji przez kolekcję modułów ładowanych przez aplikację lub profiler.  
  
 [ICorProfilerObjectEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 Zapewnia metody sekwencyjnej iteracji przez kolekcję zamrożonych obiektów, które są generowane przez program [Ngen. exe (Generator obrazu natywnego)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
 [ICorProfilerThreadEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 Zapewnia metody sekwencyjnej iteracji przez kolekcję wątków w środowisku CLR.  
  
 [IMethodMalloc, interfejs](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 Udostępnia metodę [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) do przydzielania pamięci dla nowej treści funkcji języka pośredniego (MSIL) firmy Microsoft.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
