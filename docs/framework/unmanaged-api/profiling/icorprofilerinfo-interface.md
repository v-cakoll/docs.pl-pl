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
ms.openlocfilehash: da5a041e8a18420b4cf9962e4315683be8857711
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo — Interfejs
Udostępnia metody do użycia przez profilery kodu do komunikowania się z środowisko uruchomieniowe języka wspólnego (CLR) do kontrolowania, monitorowanie zdarzeń i żądań informacji.  
  
> [!NOTE]
>  Każda metoda w `ICorProfilerInfo` interfejsu zwraca HRESULT do wskazania powodzenia lub niepowodzenia. Zobacz CorError.h listę możliwych kody powrotu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginInprocDebugging, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|Inicjuje obsługę debugowania w procesie. Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.|  
|[EndInprocDebugging, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|Zamyka w trakcie sesji debugowania. Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.|  
|[ForceGC, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|Wymusza wyrzucanie elementów bezużytecznych w czasie wykonywania.|  
|[GetAppDomainInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|Pobiera informacje o domenie określonej aplikacji.|  
|[GetAssemblyInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|Pobiera informacje o określonym zestawie.|  
|[GetClassFromObject, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|Pobiera `ClassID` z<br /><br /> obiekt, na podstawie jego `ObjectID`.|  
|[GetClassFromToken, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|Pobiera identyfikator klasy, podany token metadanych. Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0. Użyj [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) metody zamiast tego.|  
|[GetClassIDInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|Pobiera element nadrzędny Moduł i token metadanych dla określonej klasy.|  
|[GetCodeInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|Pobiera zakres skojarzony z identyfikatorem. określona funkcja kodu natywnego Ta metoda jest przestarzała. Użyj [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) metody zamiast tego.|  
|[GetCurrentThreadID, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|Pobiera identyfikator bieżącego wątku, jeśli jest zarządzanego wątku.|  
|[GetEventMask, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|Pobiera bieżący kategorii zdarzeń, dla których chce otrzymywać powiadomienia o zdarzeniach środowiska CLR profilera.|  
|[GetFunctionFromIP, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|Mapuje wskaźnik instrukcji kodu zarządzanego do `FunctionID`.|  
|[GetFunctionFromToken, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|Pobiera identyfikator funkcji. Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0. Użyj [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) metody zamiast tego.|  
|[GetFunctionInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|Pobiera klasy nadrzędnej i metadanych token dla określonej funkcji.|  
|[GetHandleFromThread, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|Identyfikator wątku jest mapowany na dojście wątku Win32.|  
|[GetILFunctionBody, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|Pobiera wskaźnik do treści metody w kodzie języka pośredniego (MSIL) firmy Microsoft, zaczynając od jej nagłówek.|  
|[GetILFunctionBodyAllocator, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|Pobiera interfejs, który udostępnia metody można przydzielić pamięci do zastosowania w przypadku zastępowaniu treści metody w kodzie MSIL.|  
|[GetILToNativeMapping, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|Pobiera mapy z przesunięcia MSIL do natywnej przesunięć kod źródłowy znajdujący się w podanej funkcji.|  
|[GetInprocInspectionInterface, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|Pobiera obiekt, który może być badana ICorDebugProcess — interfejs. Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.|  
|[GetInprocInspectionIThisThread, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|Pobiera obiekt, który można wykonać zapytania interfejsu ICorDebugThread. Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.|  
|[GetModuleInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|Podany identyfikator modułu zwraca nazwę modułu i identyfikator zestawu nadrzędnego modułu.|  
|[GetModuleMetaData, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|Pobiera wystąpienie interfejsu metadanych, który jest mapowany na określony moduł.|  
|[GetObjectSize, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|Pobiera rozmiar określonego obiektu.|  
|[GetThreadContext, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|Pobiera tożsamość kontekst, w obecnie skojarzony z określonego wątku.|  
|[GetThreadInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|Pobiera tożsamość bieżącego wątku Win32 dla określonego wątku.|  
|[GetTokenAndMetadataFromFunction, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|Pobiera token metadanych i wystąpienie interfejsu metadanych, który może służyć przed token dla określonej funkcji.|  
|[IsArrayClass, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|Określa, czy określona klasa jest klasą tablicy.|  
|[SetEnterLeaveFunctionHooks, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|Określa zaimplementowana profilera funkcji do wywołania "Wprowadź", "Pozostaw" i "tailcall" punkty zaczepienia w funkcji zarządzanych.|  
|[SetEventMask, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|Ustawia wartość, która określa typy zdarzeń, dla których chce otrzymywać powiadomienia ze środowiska CLR profilera.|  
|[SetFunctionIDMapper, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|Określa zaimplementowana profilera funkcję, która będzie wywoływana w celu mapowania `FunctionID` wartości alternatywne wartości, które są przekazywane do profilera działać punkty zaczepienia wejścia/wyjścia.|  
|[SetFunctionReJIT, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|Nie jest zaimplementowana. Nie używać.|  
|[SetILFunctionBody, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|Zastępuje treści określonej funkcji w określonym module.|  
|[SetILInstrumentedCodeMap, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|Określa sposobu przesunięcia MSIL oryginalnego określona funkcja mapowania przesunięcia nowych funkcji modyfikacji profilera MSIL.|  
  
## <a name="remarks"></a>Uwagi  
 Profiler wywołuje metodę `ICorProfilerInfo` interfejs do komunikacji z CLR do kontrolowania, monitorowanie zdarzeń i żądań informacji.  
  
 Metody `ICorProfilerInfo` interfejsu są implementowane przez środowisko CLR za pomocą modelu bezwątkowy. Każda metoda zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia. Zobacz CorError.h listę możliwych kody powrotu.  
  
 Przekazuje środowisko CLR, przy użyciu profilera stosowania [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md), `ICorProfilerInfo` interfejs do każdego profilującego podczas inicjowania. Profiler kodu można wywoływać metody `ICorProfilerInfo` interfejsu, aby uzyskać informacje na temat kodu zarządzanego wykonywana pod kontrolą środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
