---
title: Interfejsy profilowania
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d97960a43e1d7ce625d96755a7c597a0425d0911
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457462"
---
# <a name="profiling-interfaces"></a>Interfejsy profilowania
W tej sekcji opisano niezarządzane interfejsy, które umożliwiają profilowanie program, który jest wykonywany przez środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ICLRProfiling, interfejs](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 Udostępnia [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metody, która umożliwia programowi profilującemu dołączanie do uruchomionego procesu.  
  
 [ICorProfilerAssemblyReferenceProvider, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 Włącza program profilujący do informowania CLR odwołania do zestawów, które doda profilera w [icorprofilercallback::moduleloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego.  
  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 Udostępnia metody, które są używane przez środowisko CLR, aby powiadomić profiler kodu po wystąpieniu zdarzenia, dla których zostały zasubskrybowane przez profiler.  
  
 [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 Rozszerza `ICorProfilerCallback` interfejs za pomocą wywołania zwrotne obsługiwane w programie .NET Framework 2.0 i nowszych wersjach.  
  
 [ICorProfilerCallback3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 Udostępnia metody wywołania zwrotnego, które środowisko CLR używa do komunikowania się dołączania i odłączania informacje o stanie do programu profilującego.  
  
 [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 Udostępnia metody wywołania zwrotnego, które środowisko CLR używa do przekazywania informacji do programu profilującego.  
  
 [ICorProfilerCallback5, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 Dostarcza metodę, która identyfikuje przechodnie zamknięcia obiektów, które odwołują się obiekty główne kolekcji wyrzucania elementów.  
  
 [ICorProfilerCallback6, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 Zapewnia metodę wywołania zwrotnego, która używa środowiska CLR, aby powiadomić profiler, która jest ładowana zestawu.  
  
 [ICorProfilerCallback7, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 Zapewnia metodę wywołania zwrotnego, która środowiska uruchomieniowego języka wspólnego używa powiadomić profiler, że strumień symbol skojarzone z modułem w pamięci jest aktualizowana.  

[ICorProfilerCallback8, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
Udostępnia metody wywołania zwrotnego, używanych przez środowisko uruchomieniowe języka wspólnego powiadomić profiler, który kompilację JIT metoda dynamiczna ma rozpoczęcia i zakończenia.

[ICorProfilerCallback9, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
Zapewnia metodę wywołania zwrotnego, który środowiska uruchomieniowego języka wspólnego używa powiadomić profiler, która metoda dynamiczna jest pamięci zbierane i następnie zwolnione.

 [ICorProfilerFunctionControl, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 Udostępnia metody, które umożliwiają programowi profilującemu kodu komunikować się z CLR do kontrolowania, jak kompilator JIT ma generować kod ponownej kompilacji określonej metody.  
  
 [ICorProfilerFunctionEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 Udostępnia metody do sekwencyjnie iteracji przez kolekcję funkcji środowiska CLR.  
  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 Udostępnia metody do użycia przez profilery kodu do komunikowania się z CLR do kontrolowania, monitorowanie zdarzeń i zażądać informacji.  
  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 Rozszerza `ICorProfilerInfo` interfejs za pomocą metod obsługiwanych w programie .NET Framework 2.0 i nowszych wersjach.  
  
 [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 Rozszerza `ICorProfilerInfo2` interfejs za pomocą metod obsługiwanych w programie .NET Framework 4 i nowszych wersjach.  
  
 [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 Zawiera metody, które profilery kodu używają do komunikacji z CLR do kontrolowania, monitorowanie zdarzeń i żądania informacji.  
  
 [ICorProfilerInfo5, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 Udostępnia metody do użycia przez profilery kodu do komunikowania się z CLR do kontrolowania, monitorowanie zdarzeń.  
  
 [ICorProfilerInfo6, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 Dostarcza moduł wyliczający dla wszystkich metod należących do danego modułu NGen i są śródwierszowe w treści danej metody.  
  
 [ICorProfilerInfo7, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 Zapewnia metody do stosowania w nowo zdefiniowane metadane do modułu i który zapewnia dostęp do strumienia symboli w pamięci.  
  
 [ICorProfilerModuleEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 Udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji moduły załadowane przez program profilujący lub aplikacji.  
  
 [ICorProfilerObjectEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 Udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji zamrożone obiekty, które są generowane przez [Ngen.exe (Generator obrazu natywnego)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
 [ICorProfilerThreadEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 Udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji wątków w CLR.  
  
 [IMethodMalloc, interfejs](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 Udostępnia [alokacji](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) metoda można przydzielić pamięci dla nowej treści funkcji Microsoft intermediate language (MSIL).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
