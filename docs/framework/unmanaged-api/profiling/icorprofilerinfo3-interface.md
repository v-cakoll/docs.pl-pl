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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b523c5819994e6da0332188311b4b631e3f9072
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178766"
---
# <a name="icorprofilerinfo3-interface"></a>ICorProfilerInfo3 — Interfejs
Zawiera metody, które profilery kodu używają do komunikacji z środowisko uruchomieniowe języka wspólnego (CLR) do kontrolowania, monitorowanie zdarzeń i żądania informacji. `ICorProfilerInfo3` Interfejs jest rozszerzeniem [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) interfejsu. Zapewnia nowe metody obsługiwane w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] i nowszych wersjach.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumJITedFunctions, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)|Zwraca moduł wyliczający dla wszystkich funkcji wcześniej skompilowany JIT.|  
|[EnumModules, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)|Zwraca moduł wyliczający, który udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji modułów zarządzanych, które są ładowane do aplikacji.|  
|[GetAppDomainsContainingModule, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|Pobiera identyfikatory domen aplikacji, w których dany moduł został załadowany.|  
|[GetFunctionEnter3Info, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)|Zawiera informacje stosu ramki i argument funkcji, która jest zgłaszany do profilera za [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkcji; może być wywoływana tylko w trakcie `FunctionEnter3WithInfo` wywołania zwrotnego.|  
|[GetFunctionLeave3Info, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)|Udostępnia ramki stosu i wartość zwracana przez funkcję, która jest zgłaszany do profilera za [functionleave3withinfo — funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkcji; może być wywoływana tylko w trakcie `FunctionLeave3WithInfo` wywołania zwrotnego.|  
|[GetFunctionTailcall3Info, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)|Udostępnia ramki stosu funkcji, która jest zgłaszany do profilera za [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) funkcji; może być wywoływana tylko w trakcie `FunctionTailcall3WithInfo` wywołania zwrotnego.|  
|[GetModuleInfo2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)|Podany identyfikator modułu zwraca nazwę pliku modułu, identyfikator elementu nadrzędnego modułu zestawu i masek bitowych, który opisuje właściwości modułu.|  
|[GetRuntimeInformation, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getruntimeinformation-method.md)|Zawiera informacje o wersji dotyczące środowiska uruchomieniowego, która jest profilowana.|  
|[GetStringLayout2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)|Pobiera informacje o układ obiektu ciągu.|  
|[GetThreadStaticAddress2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getthreadstaticaddress2-method.md)|Pobiera adres określone pole statyczne wątku, który znajduje się w zakresie określonego wątku i domeny aplikacji.|  
|[RequestProfilerDetach, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)|Powoduje, że środowisko uruchomieniowe, aby odłączyć profiler.|  
|[SetEnterLeaveFunctionHooks3, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|Określa funkcje implementowane przez program profilujący zostanie wywołana na [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) funkcji.|  
|[SetEnterLeaveFunctionHooks3WithInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|Określa funkcje implementowane przez program profilujący zostanie wywołana na [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) punkty zaczepienia funkcji zarządzanej.|  
|[SetFunctionIDMapper2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)|Określa funkcję implementowany przez program profilujący zostanie wywołana w celu mapowania `FunctionID` wartości alternatywne wartości, które są przekazywane do programu profilującego funkcji punktów zaczepienia wejścia/wyjścia. Ta metoda jest rozszerzeniem [icorprofilerinfo::setfunctionidmapper —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) z parametrem profilery może używać w celu rozróżniać wśród modułów wykonawczych.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR implementuje metody `ICorProfilerInfo3` interfejsu przy użyciu modelu bezwątkowy. Każda metoda zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia. Aby uzyskać listę możliwych kodów powrotnych zobacz plik CorError.h.  
  
 Przekazuje środowisko CLR `ICorProfilerInfo3` interfejs do każdej profilującego podczas inicjowania przy użyciu implementacji programu profilującego [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) lub [ICorProfilerCallback3::I nitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metody. Program profilujący kodu może wywoływać `ICorProfilerInfo3` metody, aby uzyskać informacje na zarządzanego kodu, który jest wykonywana pod kontrolą środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
