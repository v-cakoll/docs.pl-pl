---
title: "ICorProfilerInfo3 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3
helpviewer_keywords: ICorProfilerInfo3 interface [.NET Framework profiling]
ms.assetid: 044a262f-0fa7-485d-b0c1-64cdc359c654
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 471fbae929723fb47dd6bc2a65196de1800717bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3-interface"></a>ICorProfilerInfo3 — Interfejs
Udostępnia metody, które profilery kodu używają do komunikacji z środowisko uruchomieniowe języka wspólnego (CLR) do sterowania monitorowanie zdarzeń oraz żądań informacji. `ICorProfilerInfo3` Interfejsu jest rozszerzeniem [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) interfejsu. Zapewnia nowych metod obsługiwanych w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] i nowszych wersjach.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumJITedFunctions — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)|Zwraca moduł wyliczający dla wszystkich funkcji wcześniej kompilacji JIT.|  
|[EnumModules — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)|Zwraca moduł wyliczający, który udostępnia metody do sekwencyjnie iteracji to zbiór modułów zarządzanych, które są ładowane do aplikacji.|  
|[GetAppDomainsContainingModule — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|Pobiera identyfikatory domeny aplikacji, w których dany moduł został załadowany.|  
|[GetFunctionEnter3Info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)|Zawiera informacje ramki i argument stosu funkcji, która jest raportowany przez profiler [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkcji; można wywołać tylko podczas `FunctionEnter3WithInfo` wywołania zwrotnego.|  
|[GetFunctionLeave3Info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)|Zapewnia ramki stosu oraz wartości zwracanej przez funkcję, która jest raportowany przez profiler [functionleave3withinfo — funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkcji; można wywołać tylko podczas `FunctionLeave3WithInfo` wywołania zwrotnego.|  
|[GetFunctionTailcall3Info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)|Udostępnia ramki stosu funkcji, która jest raportowany przez profiler [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) funkcji; można wywołać tylko podczas `FunctionTailcall3WithInfo` wywołania zwrotnego.|  
|[GetModuleInfo2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)|Podany identyfikator modułu zwraca nazwę modułu, identyfikator elementu nadrzędnego modułu zestawu i maski, który opisuje właściwości modułu.|  
|[GetRuntimeInformation — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getruntimeinformation-method.md)|Zawiera informacje o wersji dotyczące środowiska uruchomieniowego, który jest poddawany profilowaniu.|  
|[GetStringLayout2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)|Pobiera informacje o układzie z obiektem ciągu.|  
|[GetThreadStaticAddress2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getthreadstaticaddress2-method.md)|Pobiera adres określonego pola statyczne dla wątku, który znajduje się w zakresie określonego wątku i domeny aplikacji.|  
|[RequestProfilerDetach — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)|Powoduje, że środowisko uruchomieniowe można odłączyć profilera.|  
|[SetEnterLeaveFunctionHooks3 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|Określa zaimplementowana profilera funkcje, które będą wywoływane na [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) funkcji.|  
|[SetEnterLeaveFunctionHooks3WithInfo — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|Określa zaimplementowana profilera funkcje, które będą wywoływane na [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) punkty zaczepienia zarządzanego funkcji.|  
|[SetFunctionIDMapper2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)|Określa zaimplementowana profilera funkcję, która będzie wywoływana w celu mapowania `FunctionID` wartości alternatywne wartości, które są przekazywane do profilera działać punkty zaczepienia wejścia/wyjścia. Ta metoda jest rozszerzeniem [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) z parametrem, który może używać profilowania, aby usunąć Niejednoznaczność między środowisk uruchomieniowych.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR implementuje metody `ICorProfilerInfo3` interfejsu za pomocą modelu bezwątkowy. Każda metoda zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia. Aby uzyskać listę możliwych kody powrotu zobacz plik CorError.h.  
  
 Przekazuje CLR `ICorProfilerInfo3` interfejs do każdego profilującego podczas inicjowania przy użyciu profilera stosowania [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) lub [ICorProfilerCallback3::I nitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metody. Profiler kod może wywoływać `ICorProfilerInfo3` metody w celu uzyskania informacji zarządzanego kodu, który jest wykonywany pod kontrolą środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
