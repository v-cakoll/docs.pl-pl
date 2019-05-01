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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b979b5f4ee849b96cd29b6c8e2e6a8932e88c182
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049560"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo — Interfejs
Udostępnia metody do użycia przez profilery kodu do komunikowania się z środowisko uruchomieniowe języka wspólnego (CLR) do kontrolowania, monitorowanie zdarzeń i zażądać informacji.  
  
> [!NOTE]
>  Każda metoda w `ICorProfilerInfo` interfejsu zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia. Aby uzyskać listę możliwych kodów powrotnych, zobacz CorError.h.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginInprocDebugging, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|Inicjuje obsługę debugowania w procesie. Ta metoda jest przestarzała w programie .NET Framework 2.0.|  
|[EndInprocDebugging, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|Zamyka w trakcie sesji debugowania. Ta metoda jest przestarzała w programie .NET Framework 2.0.|  
|[ForceGC, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|Wymusza wyrzucanie elementów bezużytecznych w obrębie środowiska uruchomieniowego.|  
|[GetAppDomainInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|Pobiera informacje o domenie określonej aplikacji.|  
|[GetAssemblyInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|Pobiera informacje o określonym zestawie.|  
|[GetClassFromObject, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|Pobiera `ClassID` programu<br /><br /> obiekt, na podstawie jego `ObjectID`.|  
|[GetClassFromToken, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|Pobiera identyfikator klasy, biorąc pod uwagę token metadanych. Ta metoda jest przestarzała w programie .NET Framework 2.0. Użyj [icorprofilerinfo2::getclassfromtokenandtypeargs —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) metody zamiast tego.|  
|[GetClassIDInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|Pobiera element nadrzędny, modułu oraz tokenie metadanych dla określonej klasy.|  
|[GetCodeInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|Pobiera zakres kodu natywnego skojarzony z identyfikatorem określonej funkcji. Ta metoda jest przestarzała. Użyj [icorprofilerinfo2::getcodeinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) metody zamiast tego.|  
|[GetCurrentThreadID, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|Pobiera identyfikator bieżącego wątku, jeśli jest wątków zarządzanych.|  
|[GetEventMask, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|Pobiera bieżący kategorie zdarzeń, dla których program profilujący chce otrzymywać powiadomienia o zdarzeniach, ze środowiska CLR.|  
|[GetFunctionFromIP, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|Mapy kodu zarządzanego wskaźnik instrukcji do `FunctionID`.|  
|[GetFunctionFromToken, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|Pobiera identyfikator funkcji. Ta metoda jest przestarzała w programie .NET Framework 2.0. Użyj [icorprofilerinfo2::getfunctionfromtokenandtypeargs —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) metody zamiast tego.|  
|[GetFunctionInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|Pobiera klasy nadrzędnej i metadane token dla określonej funkcji.|  
|[GetHandleFromThread, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|Identyfikator wątku jest mapowany na dojście wątku Win32.|  
|[GetILFunctionBody, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|Pobiera wskaźnik do treści metody w kodzie języka intermediate language (MSIL) firmy Microsoft, zaczynając od jej nagłówek.|  
|[GetILFunctionBodyAllocator, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|Pobiera interfejs, który udostępnia metody, można przydzielić pamięci, które ma być używany dla zastępowaniu treści metody w kodzie MSIL.|  
|[GetILToNativeMapping, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|Pobiera mapę z MSIL przesunięcia do macierzystych przesunięciach kodu zawartych w określonej funkcji.|  
|[GetInprocInspectionInterface, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|Pobiera obiekt, który może być odpytywany icordebugprocess — interfejs. Ta metoda jest przestarzała w programie .NET Framework 2.0.|  
|[GetInprocInspectionIThisThread, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|Pobiera obiekt, który może być odpytywany icordebugthread — interfejs. Ta metoda jest przestarzała w programie .NET Framework 2.0.|  
|[GetModuleInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|Podany identyfikator modułu zwraca nazwę pliku modułu i identyfikator zestawu nadrzędnego modułu.|  
|[GetModuleMetaData, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|Pobiera wystąpienie interfejsu metadanych, który jest mapowany do określonego modułu.|  
|[GetObjectSize, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|Pobiera rozmiar określonego obiektu.|  
|[GetThreadContext, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|Pobiera tożsamość kontekstu aktualnie skojarzone z określonego wątku.|  
|[GetThreadInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|Pobiera bieżącą tożsamość wątku Win32 dla określonego wątku.|  
|[GetTokenAndMetadataFromFunction, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|Pobiera token metadanych i wystąpienie interfejsu metadanych, który może zostać użyty dla tokenu dla określonej funkcji.|  
|[IsArrayClass, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|Określa, czy określona klasa jest klasą tablicy.|  
|[SetEnterLeaveFunctionHooks, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|Określa funkcje implementowane przez profiler ma być wywołane na "enter", "Opuść" i "rekurencja ogonowa" hooks zarządzanej funkcji.|  
|[SetEventMask, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|Ustawia wartość, która określa typy zdarzeń, dla których program profilujący chce otrzymywać powiadomienia ze środowiska CLR.|  
|[SetFunctionIDMapper, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|Określa funkcję implementowany przez program profilujący zostanie wywołana w celu mapowania `FunctionID` wartości alternatywne wartości, które są przekazywane do programu profilującego funkcji punktów zaczepienia wejścia/wyjścia.|  
|[SetFunctionReJIT, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|Nie zaimplementowano. Nie używać.|  
|[SetILFunctionBody, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|Zastępuje treść określonej funkcji w określonym module.|  
|[SetILInstrumentedCodeMap, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|Określa sposób mapowania przesunięcia MSIL oryginalnego określonej funkcji do nowych przesunięcia MSIL zmodyfikowane przez profiler funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Program profilujący wywołuje metodę `ICorProfilerInfo` interfejs do komunikacji przy użyciu środowiska CLR do kontrolowania, monitorowanie zdarzeń i zażądać informacji.  
  
 Metody `ICorProfilerInfo` interfejsu są implementowane przez środowisko CLR, przy użyciu modelu bezwątkowy. Każda metoda zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia. Aby uzyskać listę możliwych kodów powrotnych, zobacz CorError.h.  
  
 Przekazuje środowisko CLR, za pomocą implementacji programu profilującego [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md), `ICorProfilerInfo` interfejs do każdej profilującego podczas inicjowania. Program profilujący kodu może wywoływać metody `ICorProfilerInfo` interfejsu, aby uzyskać informacje na temat kodu zarządzanego, wykonywana jest pod kontrolą środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
