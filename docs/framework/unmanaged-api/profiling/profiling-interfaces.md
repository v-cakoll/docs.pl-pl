---
title: Interfejsy profilowania
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: 8b6b9acff2945e2d8fd684bfa31e4af086ea5ab9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868151"
---
# <a name="profiling-interfaces"></a>Interfejsy profilowania
W tej sekcji opisano niezarządzane interfejsy, które umożliwiają profilowanie programu wykonywanego przez środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ICLRProfiling, interfejs](iclrprofiling-interface.md)  
 Udostępnia metodę [AttachProfiler —](iclrprofiling-attachprofiler-method.md) , która umożliwia profilerowi dołączenie do uruchomionego procesu.  
  
 [ICorProfilerAssemblyReferenceProvider, interfejs](icorprofilerassemblyreferenceprovider-interface.md)  
 Umożliwia programowi Profiler informowanie CLR o odwołaniach do zestawów, które Profiler doda do wywołania zwrotnego [ICorProfilerCallback:: ModuleLoadFinished —](icorprofilercallback-moduleloadfinished-method.md) .  
  
 [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)  
 Dostarcza metody, które są używane przez środowisko CLR do powiadamiania profilera kodu o wystąpieniu zdarzeń subskrybowanych przez profiler.  
  
 [ICorProfilerCallback2, interfejs](icorprofilercallback2-interface.md)  
 Rozszerza interfejs `ICorProfilerCallback` z wywołaniami zwrotnymi obsługiwanymi w .NET Framework 2,0 i nowszymi wersjami.  
  
 [ICorProfilerCallback3, interfejs](icorprofilercallback3-interface.md)  
 Zapewnia metody wywołania zwrotnego używane przez środowisko CLR do przekazywania informacji o stanie dołączania i odłączania do profilera.  
  
 [ICorProfilerCallback4, interfejs](icorprofilercallback4-interface.md)  
 Zapewnia metody wywołania zwrotnego używane przez środowisko CLR do przekazywania informacji do profilera.  
  
 [ICorProfilerCallback5, interfejs](icorprofilercallback5-interface.md)  
 Zapewnia metodę, która identyfikuje przechodnie zamknięcie obiektów, do których odwołują się katalogi główne wyrzucania elementów bezużytecznych.  
  
 [ICorProfilerCallback6, interfejs](icorprofilercallback6-interface.md)  
 Zapewnia metodę wywołania zwrotnego używaną przez środowisko CLR do powiadomienia profilera o ładowaniu zestawu.  
  
 [ICorProfilerCallback7, interfejs](icorprofilercallback7-interface.md)  
 Zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o aktualizowaniu strumienia symboli skojarzonego z modułem w pamięci.  

[ICorProfilerCallback8, interfejs](icorprofilercallback8-interface.md)  
Zapewnia metody wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o rozpoczęciu i zakończeniu kompilacji JIT metody dynamicznej.

[ICorProfilerCallback9, interfejs](icorprofilercallback9-interface.md)  
Zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadomienia profilera, że metoda dynamiczna jest odzyskiwana, a następnie zwolniona.

 [ICorProfilerFunctionControl, interfejs](icorprofilerfunctioncontrol-interface.md)  
 Dostarcza metody, które umożliwiają profilerowi kodu komunikowanie się z środowiskiem CLR w celu kontrolowania sposobu generowania kodu przez kompilator JIT podczas ponownego kompilowania określonej metody.  
  
 [ICorProfilerFunctionEnum, interfejs](icorprofilerfunctionenum-interface.md)  
 Zapewnia metody sekwencyjnej iteracji przez kolekcję funkcji w środowisku CLR.  
  
 [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)  
 Zapewnia metody do użycia przez program Code profilowas do komunikowania się z środowiskiem CLR w celu kontrolowania informacji o monitorowaniu zdarzeń i żądaniu.  
  
 [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)  
 Rozszerza interfejs `ICorProfilerInfo` z metodami obsługiwanymi w .NET Framework 2,0 i nowszymi wersjami.  
  
 [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)  
 Rozszerza interfejs `ICorProfilerInfo2` z metodami obsługiwanymi w .NET Framework 4 i nowszych wersjach.  
  
 [ICorProfilerInfo4, interfejs](icorprofilerinfo4-interface.md)  
 Dostarcza metody, których program codeer używa do komunikacji z środowiskiem CLR w celu kontrolowania monitorowania zdarzeń oraz żądania informacji.  
  
 [ICorProfilerInfo5, interfejs](icorprofilerinfo5-interface.md)  
 Zapewnia metody do użycia przez program Code profilowas do komunikowania się z środowiskiem CLR w celu kontrolowania monitorowania zdarzeń.  
  
 [ICorProfilerInfo6, interfejs](icorprofilerinfo6-interface.md)  
 Dostarcza moduł wyliczający do wszystkich metod, które należą do danego modułu NGen i są zawarte w treści danej metody.  
  
 [ICorProfilerInfo7, interfejs](icorprofilerinfo7-interface.md)  
 Zapewnia metodę zastosowania nowo zdefiniowanych metadanych do modułu, który zapewnia dostęp do strumienia symboli w pamięci.  
  
 [ICorProfilerModuleEnum, interfejs](icorprofilermoduleenum-interface.md)  
 Dostarcza metody sekwencyjnie iteracji przez kolekcję modułów ładowanych przez aplikację lub profiler.  
  
 [ICorProfilerObjectEnum, interfejs](icorprofilerobjectenum-interface.md)  
 Zapewnia metody sekwencyjnej iteracji przez kolekcję zamrożonych obiektów, które są generowane przez program [Ngen. exe (Generator obrazu natywnego)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
 [ICorProfilerThreadEnum, interfejs](icorprofilerthreadenum-interface.md)  
 Zapewnia metody sekwencyjnej iteracji przez kolekcję wątków w środowisku CLR.  
  
 [IMethodMalloc, interfejs](imethodmalloc-interface.md)  
 Udostępnia metodę [Alloc](imethodmalloc-alloc-method.md) do przydzielania pamięci dla nowej treści funkcji języka pośredniego (MSIL) firmy Microsoft.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie profilowania](profiling-overview.md)  
  
 [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)  
  
 [Profilowanie — wyliczenia](profiling-enumerations.md)  
  
 [Profiling — struktury](profiling-structures.md)
