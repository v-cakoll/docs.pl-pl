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
ms.openlocfilehash: 059fadc5607e76b871083682136fda542ae9bacf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462055"
---
# <a name="profiling-interfaces"></a>Interfejsy profilowania
W tej sekcji opisano niezarządzane interfejsy, które umożliwiają profilu program, który jest wykonywany przez środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ICLRProfiling, interfejs](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 Udostępnia [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metodę, która pozwala na dołączenie do uruchomionego procesu profilera.  
  
 [ICorProfilerAssemblyReferenceProvider, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 Włącza profiler do informowania CLR odwołania do zestawów, które profilera doda w [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego.  
  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 Udostępnia metody, które są używane przez środowisko CLR powiadomiono profilera kodu, w przypadku wystąpienia zdarzenia, do których subskrybowanych profilera.  
  
 [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 Rozszerza `ICorProfilerCallback` interfejsu z wywołań zwrotnych obsługiwane w programie .NET Framework 2.0 i nowszych wersjach.  
  
 [ICorProfilerCallback3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 Udostępnia metody wywołania zwrotnego, używanych do komunikacji CLR dołączania i odłączania informacje o stanie do profilera.  
  
 [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 Udostępnia metody wywołania zwrotnego, używanych do przekazywania informacji do profiler CLR.  
  
 [ICorProfilerCallback5, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 Udostępnia metody, która identyfikuje przechodnie zamknięcia odwołuje certyfikaty główne kolekcji odzyskiwanie obiektów.  
  
 [ICorProfilerCallback6, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 Udostępnia metody wywołania zwrotnego, która CLR używa powiadomiono profilera, który jest ładowany zestaw.  
  
 [ICorProfilerCallback7, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 Udostępnia metody wywołania zwrotnego, która środowisko uruchomieniowe języka wspólnego używa do powiadamiania profilera zaktualizowaniu strumienia symbol skojarzone z modułu w pamięci.  

[Interfejs ICorProfilerCallback8](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
Udostępnia metody wywołania zwrotnego, używane przez środowisko uruchomieniowe języka wspólnego powiadomiono profiler kompilacji JIT metody dynamicznej ma rozpoczęcia i zakończenia.

[Interfejs ICorProfilerCallback9](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
Udostępnia metody wywołania zwrotnego, która środowisko uruchomieniowe języka wspólnego używa powiadomiono dynamiczna metoda jest Odzyskiwanie zbierane i następnie zwalnianie profiler.

 [ICorProfilerFunctionControl, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 Udostępnia metody umożliwiające profilującego do komunikowania się z CLR, aby kontrolować sposób przy użyciu kompilatora JIT powinna generować kod ponowną kompilację określonej metody.  
  
 [ICorProfilerFunctionEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 Udostępnia metody sekwencyjnie iterowania po kolekcji funkcji środowiska CLR.  
  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 Udostępnia metody do użycia przez profilery kodu do komunikowania się z CLR do kontrolowania, monitorowanie zdarzeń i żądań informacji.  
  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 Rozszerza `ICorProfilerInfo` interfejsu z metod obsługiwanych w programie .NET Framework 2.0 i nowszych wersjach.  
  
 [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 Rozszerza `ICorProfilerInfo2` interfejsu z metod obsługiwanych w [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] i nowszych wersjach.  
  
 [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 Udostępnia metody, które profilery kodu używają do komunikacji z CLR sterować monitorowaniem zdarzenia i żądania informacji.  
  
 [ICorProfilerInfo5, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 Udostępnia metody do użycia przez profilery kodu do komunikowania się z CLR do kontrolowania monitorowania zdarzeń.  
  
 [ICorProfilerInfo6, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 Udostępnia moduł wyliczający do wszystkich metod należących do danego modułu NGen i które są wbudowane w treści danej metody.  
  
 [ICorProfilerInfo7, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 Udostępnia metody do zastosowania w nowo zdefiniowane metadanych do modułu i który zapewnia dostęp do strumienia symbol w pamięci.  
  
 [ICorProfilerModuleEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 Udostępnia metody sekwencyjnie iterowania po kolekcji moduły załadowane przez profiler lub aplikacji.  
  
 [ICorProfilerObjectEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 Udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji zablokowane obiekty, które są generowane przez [Ngen.exe (Generator obrazu natywnego)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
 [ICorProfilerThreadEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 Udostępnia metody sekwencyjnie iterowania po kolekcji wątki środowiska CLR.  
  
 [IMethodMalloc, interfejs](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 Udostępnia [alokacji](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) metody można przydzielić pamięci dla nowego treści funkcji języka pośredniego (MSIL) firmy Microsoft.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
