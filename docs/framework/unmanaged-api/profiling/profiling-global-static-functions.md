---
title: Profilowanie statycznych funkcji globalnych
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: d1d9b0a4c61ce7c3f8f9792046fb4bddf0fdfa05
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447429"
---
# <a name="profiling-global-static-functions"></a>Profilowanie statycznych funkcji globalnych
W tej sekcji opisano niezarządzane funkcje API, które są używane przez interfejs API profilowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
## <a name="net-framework-version-1-profiling-functions"></a>Funkcje profilowania .NET Framework w wersji 1  
 [FunctionEnter, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Powiadamia profiler, że sterowanie jest przesyłane do funkcji. Przestarzałe w .NET Framework 2,0.  
  
 [FunctionLeave, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Powiadamia profiler, że funkcja ma zwrócić do obiektu wywołującego. Przestarzałe w .NET Framework 2,0.  
  
 [FunctionTailcall, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Powiadamia profiler, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji. Przestarzałe w .NET Framework 2,0.  
  
## <a name="net-framework-version-2-profiling-functions"></a>Funkcje profilowania .NET Framework w wersji 2  
 [FunctionIDMapper, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Powiadamia program profilujący, że dany identyfikator funkcji może zostać ponownie zmapowany na alternatywny identyfikator, który ma być używany w wywołaniach zwrotnych [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)i [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) dla tej funkcji. Umożliwia również profilerowi wskazanie, czy chce otrzymywać wywołania zwrotne dla tej funkcji  
  
 [FunctionEnter2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Powiadamia profiler, że sterowanie jest przesyłane do funkcji i zawiera informacje na temat ramki stosu i argumentów funkcji. Przestarzałe w .NET Framework 4.  
  
 [FunctionLeave2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Powiadamia program profilujący, że funkcja ma zwrócić do obiektu wywołującego i zawiera informacje na temat ramki stosu i wartości zwracanej przez funkcję. Przestarzałe w .NET Framework 4.  
  
 [FunctionTailcall2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Powiadamia profiler, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji i zawiera informacje na temat ramki stosu. Przestarzałe w .NET Framework 4.  
  
 [StackSnapshotCallback, funkcja](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Zapewnia profilerowi informacje o każdej zarządzanej ramce i każdym uruchomieniu niezarządzanych ramek na stosie podczas przechodzenia stosu, który jest inicjowany przez [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="net-framework-version-4-profiling-functions"></a>Funkcje profilowania .NET Framework w wersji 4  
 [FunctionIDMapper2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Powiadamia program profilujący, że dany identyfikator funkcji może zostać ponownie zmapowany na alternatywny identyfikator, który ma być używany w wywołaniach zwrotnych [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), lub[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) dla tej funkcji. Umożliwia również profilerowi określenie, czy chce otrzymywać wywołania zwrotne dla tej funkcji.  
  
 `FunctionIDMapper2` rozszerza funkcję [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) z parametrem `clientData`, którego mogą używać pliki do rozróżniania między środowiskami uruchomieniowymi.  
  
 [FunctionEnter3, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Powiadamia profiler, że sterowanie jest przesyłane do funkcji.  
  
 [FunctionEnter3WithInfo, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Powiadamia program profilujący, że formant jest przesyłany do funkcji i udostępnia dojście, które może być przekazane do [ICorProfilerInfo3:: GetFunctionEnter3Info —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) w celu pobrania ramki stosu i argumentów funkcji.  
  
 [FunctionLeave3, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Powiadamia profiler, że formant jest zwracany przez funkcję.  
  
 [FunctionLeave3WithInfo, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Powiadamia profiler, że formant jest zwracany przez funkcję i udostępnia dojście, które można przesłać do [ICorProfilerInfo3:: GetFunctionLeave3Info —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) , aby pobrać ramkę stosu i wartość zwracaną.  
  
 [FunctionTailcall3, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Powiadamia profiler, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji.  
  
 [FunctionTailcall3WithInfo, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Powiadamia program profilujący, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji i udostępnia dojście, które może zostać przesłane do [ICorProfilerInfo3:: GetFunctionTailcall3Info —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) w celu pobrania ramki stosu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
