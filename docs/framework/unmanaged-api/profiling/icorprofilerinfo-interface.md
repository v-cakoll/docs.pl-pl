---
title: ICorProfilerInfo — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo
helpviewer_keywords:
- ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: eb4e4ce0-06e7-4469-bbc4-edc2eb5da4b1
topic_type:
- apiref
ms.openlocfilehash: 0af990930e8c30307e9da3b586621ca8ddb95d0c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438750"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo — Interfejs
Zapewnia metody do użycia przez program Code profilowas do komunikowania się ze środowiskiem uruchomieniowym języka wspólnego (CLR) w celu kontrolowania informacji o monitorowaniu zdarzeń i żądaniach.  
  
> [!NOTE]
> Każda metoda w interfejsie `ICorProfilerInfo` zwraca wynik HRESULT wskazujący powodzenie lub niepowodzenie. Zobacz CorError. h, aby uzyskać listę możliwych kodów powrotu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginInprocDebugging, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|Inicjuje obsługę debugowania w procesie. Ta metoda jest przestarzała w .NET Framework w wersji 2,0.|  
|[EndInprocDebugging, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|Zamyka sesję debugowania w procesie. Ta metoda jest przestarzała w .NET Framework w wersji 2,0.|  
|[ForceGC, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|Wymusza wyrzucanie elementów bezużytecznych w czasie wykonywania.|  
|[GetAppDomainInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|Pobiera informacje o określonej domenie aplikacji.|  
|[GetAssemblyInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|Pobiera informacje o określonym zestawie.|  
|[GetClassFromObject, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|Pobiera `ClassID`<br /><br /> Obiekt, pod którym `ObjectID`.|  
|[GetClassFromToken, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|Pobiera identyfikator klasy, z uwzględnieniem tokenu metadanych. Ta metoda jest przestarzała w .NET Framework w wersji 2,0. Zamiast tego użyj metody [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) .|  
|[GetClassIDInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|Pobiera moduł nadrzędny i token metadanych dla określonej klasy.|  
|[GetCodeInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|Pobiera zakres kodu natywnego skojarzonego z określonym IDENTYFIKATORem funkcji. Ta metoda jest przestarzała. Zamiast tego użyj metody [ICorProfilerInfo2:: GetCodeInfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) .|  
|[GetCurrentThreadID, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|Pobiera identyfikator bieżącego wątku, jeśli jest to wątek zarządzany.|  
|[GetEventMask, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|Pobiera bieżące kategorie zdarzeń, dla których profiler chce otrzymywać powiadomienia o zdarzeniach z środowiska CLR.|  
|[GetFunctionFromIP, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|Mapuje wskaźnik zarządzanej instrukcji kodu na `FunctionID`.|  
|[GetFunctionFromToken, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|Pobiera identyfikator funkcji. Ta metoda jest przestarzała w .NET Framework w wersji 2,0. Zamiast tego użyj metody [ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) .|  
|[GetFunctionInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|Pobiera klasę nadrzędną i token metadanych dla określonej funkcji.|  
|[GetHandleFromThread, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|Mapuje identyfikator wątku na dojście wątku Win32.|  
|[GetILFunctionBody, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|Pobiera wskaźnik do treści metody w kodzie języka pośredniego firmy Microsoft (MSIL), rozpoczynając od jego nagłówka.|  
|[GetILFunctionBodyAllocator, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|Pobiera interfejs, który zapewnia metodę przydzielenia pamięci do użycia podczas wymiany treści metody w kodzie MSIL.|  
|[GetILToNativeMapping, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|Pobiera mapę z przesunięcia MSIL do natywnych przesunięć dla kodu zawartego w określonej funkcji.|  
|[GetInprocInspectionInterface, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|Pobiera obiekt, który może być badany dla interfejsu ICorDebugProcess. Ta metoda jest przestarzała w .NET Framework w wersji 2,0.|  
|[GetInprocInspectionIThisThread, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|Pobiera obiekt, który może być badany dla interfejsu ICorDebugThread. Ta metoda jest przestarzała w .NET Framework w wersji 2,0.|  
|[GetModuleInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|Podanym IDENTYFIKATORem modułu zwraca nazwę pliku modułu i identyfikator zestawu nadrzędnego modułu.|  
|[GetModuleMetaData, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|Pobiera wystąpienie interfejsu metadanych, które mapuje do określonego modułu.|  
|[GetObjectSize, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|Pobiera rozmiar określonego obiektu.|  
|[GetThreadContext, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|Pobiera tożsamość kontekstu aktualnie skojarzoną z określonym wątkiem.|  
|[GetThreadInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|Pobiera bieżącą tożsamość wątku Win32 dla określonego wątku.|  
|[GetTokenAndMetadataFromFunction, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|Pobiera token metadanych i wystąpienie interfejsu metadanych, które mogą być używane w odniesieniu do tokenu określonej funkcji.|  
|[IsArrayClass, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|Określa, czy określona Klasa jest klasą Array.|  
|[SetEnterLeaveFunctionHooks, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|Określa funkcje zaimplementowane przez profiler, które mają być wywoływane w podpunktach "Enter", "urlop" i "tailcall" punktów zarządzanych funkcji.|  
|[SetEventMask, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|Ustawia wartość określającą typy zdarzeń, dla których profiler chce otrzymywać powiadomienia z aparatu CLR.|  
|[SetFunctionIDMapper, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|Określa funkcję zaimplementowaną przez profiler, która zostanie wywołana w celu mapowania wartości `FunctionID` na wartości alternatywne, które są przesyłane do punktów zaczepienia wejścia/wyjścia profilera.|  
|[SetFunctionReJIT, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|Nie zaimplementowane. Nie używać.|  
|[SetILFunctionBody, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|Zastępuje treść określonej funkcji w określonym module.|  
|[SetILInstrumentedCodeMap, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|Określa sposób, w jaki przesunięcia oryginalnej mapy MSIL określonej funkcji są mapowane na nowe przesunięcia narzędzia MSIL modyfikowanego przez profiler funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Profiler wywołuje metodę w interfejsie `ICorProfilerInfo`, aby komunikować się z środowiskiem CLR w celu kontrolowania informacji o monitorowaniu zdarzeń i żądaniu.  
  
 Metody interfejsu `ICorProfilerInfo` są implementowane przez środowisko CLR przy użyciu modelu dowolnego wątku. Każda metoda zwraca wynik HRESULT wskazujący powodzenie lub niepowodzenie. Zobacz CorError. h, aby uzyskać listę możliwych kodów powrotu.  
  
 Środowisko CLR przechodzi przez implementację profilera [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md), interfejs `ICorProfilerInfo` do każdego profilera kodu podczas inicjalizacji. Profiler kodu może następnie wywołać metody interfejsu `ICorProfilerInfo`, aby uzyskać informacje o kodzie zarządzanym wykonywanym w ramach kontroli środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
