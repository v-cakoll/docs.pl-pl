---
title: ICorProfilerInfo3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3
helpviewer_keywords:
- ICorProfilerInfo3 interface [.NET Framework profiling]
ms.assetid: 044a262f-0fa7-485d-b0c1-64cdc359c654
topic_type:
- apiref
ms.openlocfilehash: 0a474719935ba763cbd15dc6e18fe5ba99c14ebc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496311"
---
# <a name="icorprofilerinfo3-interface"></a>ICorProfilerInfo3 — Interfejs
Zapewnia metody, które są używane przez program codeer do komunikowania się ze środowiskiem uruchomieniowym języka wspólnego (CLR) w celu kontrolowania monitorowania zdarzeń oraz żądania informacji. `ICorProfilerInfo3`Interfejs jest rozszerzeniem interfejsu [ICorProfilerInfo2](icorprofilerinfo2-interface.md) . Dostępne są nowe metody obsługiwane w .NET Framework 4 i nowszych wersjach.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumJITedFunctions, metoda](icorprofilerinfo3-enumjitedfunctions-method.md)|Zwraca moduł wyliczający dla wszystkich poprzednio skompilowanych funkcji JIT.|  
|[EnumModules, metoda](icorprofilerinfo3-enummodules-method.md)|Zwraca moduł wyliczający, który dostarcza metody sekwencyjnie iteracji przez kolekcję modułów zarządzanych, które są ładowane do aplikacji.|  
|[GetAppDomainsContainingModule, metoda](icorprofilerinfo3-getappdomainscontainingmodule-method.md)|Pobiera identyfikatory domen aplikacji, w których dany moduł został załadowany.|  
|[GetFunctionEnter3Info, metoda](icorprofilerinfo3-getfunctionenter3info-method.md)|Zapewnia ramkę stosu i informacje o argumentach funkcji raportowanej przez profiler przez funkcję [FunctionEnter3WithInfo](functionenter3withinfo-function.md) ; może być wywoływana tylko podczas `FunctionEnter3WithInfo` wywołania zwrotnego.|  
|[GetFunctionLeave3Info, metoda](icorprofilerinfo3-getfunctionleave3info-method.md)|Udostępnia ramkę stosu i zwracaną wartość funkcji raportowanej do profilera przez funkcję [funkcji FunctionLeave3WithInfo](functionleave3withinfo-function.md) . może być wywoływana tylko podczas `FunctionLeave3WithInfo` wywołania zwrotnego.|  
|[GetFunctionTailcall3Info, metoda](icorprofilerinfo3-getfunctiontailcall3info-method.md)|Udostępnia ramkę stosu funkcji, która jest raportowana do profilera przez funkcję [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) ; może być wywoływana tylko podczas `FunctionTailcall3WithInfo` wywołania zwrotnego.|  
|[GetModuleInfo2, metoda](icorprofilerinfo3-getmoduleinfo2-method.md)|Podano identyfikator modułu, zwraca nazwę pliku modułu, identyfikator zestawu nadrzędnego modułu i maskę bitów opisującą właściwości modułu.|  
|[GetRuntimeInformation, metoda](icorprofilerinfo3-getruntimeinformation-method.md)|Zawiera informacje o wersji dotyczące plików środowiska uruchomieniowego, które są profilowane.|  
|[GetStringLayout2, metoda](icorprofilerinfo3-getstringlayout2-method.md)|Pobiera informacje o układzie obiektu ciągu.|  
|[GetThreadStaticAddress2, metoda](icorprofilerinfo3-getthreadstaticaddress2-method.md)|Pobiera adres określonego wątku-static pola, które znajduje się w zakresie określonego wątku i domeny aplikacji.|  
|[RequestProfilerDetach, metoda](icorprofilerinfo3-requestprofilerdetach-method.md)|Nakazuje programowi uruchomieniowemu odłączenie profilera.|  
|[SetEnterLeaveFunctionHooks3, metoda](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|Określa funkcje zaimplementowane przez profiler, które będą wywoływane w funkcjach [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)i [FunctionTailcall3](functiontailcall3-function.md) .|  
|[SetEnterLeaveFunctionHooks3WithInfo, metoda](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|Określa funkcje zaimplementowane przez profiler, które będą wywoływane w podpunktach [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)i [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) funkcji zarządzanych.|  
|[SetFunctionIDMapper2, metoda](icorprofilerinfo3-setfunctionidmapper2-method.md)|Określa funkcję zaimplementowaną przez profiler, która zostanie wywołana w celu mapowania `FunctionID` wartości na wartości alternatywne, które są przesyłane do punktów zaczepienia wejścia/wyjścia profilera. Ta metoda rozszerza [ICorProfilerInfo:: SetFunctionIDMapper —](icorprofilerinfo-setfunctionidmapper-method.md) z parametrem, który może być używany przez program do rozróżniania między środowiskami uruchomieniowymi.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR implementuje metody `ICorProfilerInfo3` interfejsu przy użyciu modelu typu "wolny-wątek". Każda metoda zwraca wynik HRESULT wskazujący powodzenie lub niepowodzenie. Aby uzyskać listę możliwych kodów powrotu, zobacz plik CorError. h.  
  
 Środowisko CLR przekazuje `ICorProfilerInfo3` interfejs do każdego profilera kodu podczas inicjowania przy użyciu implementacji profilera [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) lub [ICorProfilerCallback3:: InitializeForAttach —](icorprofilercallback3-initializeforattach-method.md) . Program Code profiler może następnie wywołać `ICorProfilerInfo3` metody, aby uzyskać informacje o zarządzanym kodzie, który jest wykonywany pod kontrolą środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
