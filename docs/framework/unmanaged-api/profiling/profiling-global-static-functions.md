---
title: Profilowanie statycznych funkcji globalnych
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ea65c06871d9762fa6daac229a568594b4c4479
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457473"
---
# <a name="profiling-global-static-functions"></a>Profilowanie statycznych funkcji globalnych
W tej sekcji opisano niezarządzane funkcje interfejsu API, których używa interfejs profilowania API.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
## <a name="net-framework-version-1-profiling-functions"></a>Profilowanie funkcje programu .NET framework w wersji 1  
 [FunctionEnter, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Powiadamia program profilujący, że formant jest przekazywany do funkcji. Przestarzałe w programie .NET Framework 2.0.  
  
 [FunctionLeave, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Powiadamia program profilujący, że funkcja jest około, aby powrócić do obiektu wywołującego. Przestarzałe w programie .NET Framework 2.0.  
  
 [FunctionTailcall, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Powiadamia program profilujący, że aktualnie wykonywanej funkcji zostanie wykonywać wywołania tail do innej funkcji. Przestarzałe w programie .NET Framework 2.0.  
  
## <a name="net-framework-version-2-profiling-functions"></a>Profilowanie funkcje programu .NET framework w wersji 2  
 [FunctionIDMapper, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Powiadamia program profilujący, że identyfikator danej funkcji może być ponownie mapowany do alternatywnego Identyfikatora do użycia w [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), i [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) wywołań zwrotnych tej funkcji. Umożliwia także profilującemu wskazanie, czy chce odbierać wywołania zwrotne do tej funkcji  
  
 [FunctionEnter2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Powiadamia program profilujący, że kontroli jest przekazywany do funkcji i zawiera informacje o stosie argumenty ramki i funkcji. Przestarzałe w programie .NET Framework 4.  
  
 [FunctionLeave2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Powiadamia program profilujący, że funkcji ma zwrócić do elementu wywołującego i zawiera informacje dotyczące stosu ramki i funkcja wartość zwracaną. Przestarzałe w programie .NET Framework 4.  
  
 [FunctionTailcall2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Powiadamia program profilujący, że aktualnie wykonywanej funkcji ma wykonywać wywołania tail do innej funkcji oraz informacje o ramki stosu. Przestarzałe w programie .NET Framework 4.  
  
 [StackSnapshotCallback, funkcja](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Dostarcza informacji na temat każdej zarządzanej ramki i każde uruchomienie niezarządzanych ramek na stosie podczas przeszukiwania stosu jest inicjowane przez profiler [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.  
  
## <a name="net-framework-version-4-profiling-functions"></a>Profilowanie funkcje programu .NET framework w wersji 4  
 [FunctionIDMapper2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Powiadamia program profilujący, że identyfikator danej funkcji może być ponownie mapowany do alternatywnego Identyfikatora do użycia w [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), lub[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) wywołań zwrotnych tej funkcji. Umożliwia także profilującemu wskazanie, czy chce odbierać wywołania zwrotne do tej funkcji.  
  
 `FunctionIDMapper2` Rozszerza [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkcją `clientData` parametr, który profilery może używać w celu rozróżniać wśród modułów wykonawczych.  
  
 [FunctionEnter3, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Powiadamia program profilujący, że formant jest przekazywany do funkcji.  
  
 [FunctionEnter3WithInfo, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Powiadamia program profilujący, że formant jest przekazywany do funkcji, a także uchwyt, który może być przekazywany do [icorprofilerinfo3::getfunctionenter3info —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) można pobrać argumenty ramki i funkcję stosu.  
  
 [FunctionLeave3, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Powiadamia program profilujący, że kontrolki zwracana przez funkcję.  
  
 [FunctionLeave3WithInfo, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Powiadamia program profilujący, że kontrolki zwracana przez funkcję, a także uchwyt, który może być przekazywany do [icorprofilerinfo3::getfunctionleave3info —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) pobieranie ramki stosu i wartość zwracaną.  
  
 [FunctionTailcall3, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Powiadamia program profilujący, że aktualnie wykonywanej funkcji zostanie wykonywać wywołania tail do innej funkcji.  
  
 [FunctionTailcall3WithInfo, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Powiadamia program profilujący, które ma wykonywać wywołania tail do innej funkcji aktualnie wykonywanej funkcji i zapewnia uchwyt, który może być przekazywany do [icorprofilerinfo3::getfunctiontailcall3info —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) można pobrać ramki stosu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
