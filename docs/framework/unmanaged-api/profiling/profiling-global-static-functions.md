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
ms.openlocfilehash: 8bb5d93c91de857ebbee63009cad73fba7e1d284
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461838"
---
# <a name="profiling-global-static-functions"></a>Profilowanie statycznych funkcji globalnych
W tej sekcji opisano niezarządzanych funkcji interfejsu API, które używa interfejsu API profilowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
## <a name="net-framework-version-1-profiling-functions"></a>Profilowanie funkcje programu .NET framework w wersji 1  
 [FunctionEnter, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Powiadamia profilera, czy formant jest przekazywany do funkcji. Przestarzałe w programie .NET Framework 2.0.  
  
 [FunctionLeave, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Powiadamia profilera funkcji o zbliżającym się zwrócić do obiektu wywołującego. Przestarzałe w programie .NET Framework 2.0.  
  
 [FunctionTailcall, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Powiadamia profilera aktualnie wykonywane funkcja o zbliżającym się wykonywać wywołania tail na inną funkcję. Przestarzałe w programie .NET Framework 2.0.  
  
## <a name="net-framework-version-2-profiling-functions"></a>Profilowanie funkcji programu .NET framework w wersji 2  
 [FunctionIDMapper, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Powiadamia profilera, że danym identyfikatorem funkcji mogą być mapowane ponownie do alternatywny identyfikator ma być używany w [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), i [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) wywołań zwrotnych dla tej funkcji. Umożliwia również profilera wskazać, czy chce odbierać wywołań zwrotnych dla tej funkcji  
  
 [FunctionEnter2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Powiadamia profilera, czy formant jest przekazywany do funkcji i zawiera informacje o stosie argumenty ramki i funkcji. Przestarzałe w [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [FunctionLeave2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Powiadamia profilera, że funkcja ma zwrócić do obiektu wywołującego i zawiera informacje o stosu ramki i funkcja wartość zwracaną. Przestarzałe w [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [FunctionTailcall2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Powiadamia profilera, że funkcja aktualnie wykonywane ma wykonywać wywołania tail do innej funkcji i zawiera informacje o ramki stosu. Przestarzałe w [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StackSnapshotCallback, funkcja](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Zawiera informacje o każdej ramce zarządzanych i każdym uruchomieniu niezarządzane ramek na stosie podczas przeszukiwania stosu, który jest inicjowane przez profiler [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.  
  
## <a name="net-framework-version-4-profiling-functions"></a>Profilowanie funkcji programu .NET framework w wersji 4  
 [FunctionIDMapper2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Powiadamia profilera, że danym identyfikatorem funkcji mogą być mapowane ponownie do alternatywny identyfikator ma być używany w [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), lub[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) wywołań zwrotnych dla tej funkcji. Umożliwia również profilera wskazać, czy chce odbierać wywołań zwrotnych dla tej funkcji.  
  
 `FunctionIDMapper2` Rozszerza [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) działać z `clientData` parametr, który może używać profilowania, aby usunąć Niejednoznaczność między środowisk uruchomieniowych.  
  
 [FunctionEnter3, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Powiadamia profilera, czy formant jest przekazywany do funkcji.  
  
 [FunctionEnter3WithInfo, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Powiadamia profilera, czy formant jest przekazywany do funkcji, a także uchwytu, które mogą zostać przekazane do [ICorProfilerInfo3::GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) można pobrać argumenty ramki i funkcja stosu.  
  
 [FunctionLeave3, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Powiadamia profilera, że formant zostały zwrócone z funkcji.  
  
 [FunctionLeave3WithInfo, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Powiadamia profilera, że formant zostały zwrócone z funkcji, a także uchwytu, które mogą zostać przekazane do [ICorProfilerInfo3::GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) można pobrać ramki stosu oraz wartości zwracanej.  
  
 [FunctionTailcall3, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Powiadamia profilera aktualnie wykonywane funkcja o zbliżającym się wykonywać wywołania tail na inną funkcję.  
  
 [FunctionTailcall3WithInfo, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Powiadamia profilera, który aktualnie wykonywane funkcji ma wykonywać wywołania tail do innej funkcji, a także uchwytu, które mogą zostać przekazane do [ICorProfilerInfo3::GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) można pobrać ramki stosu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
