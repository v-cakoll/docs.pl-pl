---
title: "ICorProfilerInfo2 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2
helpviewer_keywords: ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cbc0b4ad46c6a49313a42c4c232873988e7f4e99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 — Interfejs
Udostępnia metody, które używają profilery kodu do komunikacji z środowisko uruchomieniowe języka wspólnego (CLR) w celu kontrolowania, monitorowanie zdarzeń i informacje o żądaniu. `ICorProfilerInfo2` Interfejsu jest rozszerzeniem [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interfejsu. Oznacza to, że zapewnia nowych metod obsługiwanych w programie .NET Framework w wersji 2.0 i nowszych wersjach.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DoStackSnapshot — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|Zawiera opis stosu określonego wątku zgłosić ramki wywołanie zarządzanego profilera.|  
|[EnumModuleFrozenObjects — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|Pobiera moduł wyliczający, który umożliwia iteracji za pośrednictwem zablokowane obiekty w ramach określonego modułu.|  
|[GetAppDomainStaticAddress — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|Pobiera adres pola statyczne domeny określonej aplikacji, która znajduje się w zakresie domeny określonej aplikacji.|  
|[GetArrayObjectInfo — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|Pobiera szczegółowe informacje o tablicy obiektów.|  
|[GetBoxClassLayout — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|Pobiera informacje o układzie klasy dla określonej wartości typu, który jest opakowany.|  
|[GetClassFromTokenAndTypeArgs — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Pobiera `ClassID` typu przy użyciu tokenu określonych metadanych i `ClassID` wartości dowolnego argumentów typu.|  
|[GetClassIDInfo2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|Pobiera moduł nadrzędnej określonej klasy rodzajowe token metadanych dla tej klasy, `ClassID` jego klasy nadrzędnej i `ClassID` dla każdego typu argumentu, jeśli jest obecny, klasy.|  
|[GetClassLayout — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|Pobiera informacje o układzie, w pamięci, pól zdefiniowanych przez określonej klasy. Oznacza to, że ta metoda pobiera przesunięcia pól tej klasy.|  
|[GetCodeInfo2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|Pobiera zakres kodu natywnego skojarzonego z określonym `FunctionID`.|  
|[GetContextStaticAddress — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|Pobiera adres określonego pola statyczne kontekstu, które znajduje się w zakresie określonego kontekstu.|  
|[GetFunctionFromTokenAndTypeArgs — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Pobiera `FunctionID` funkcji przy użyciu tokenu określonych metadanych, klasą, i `ClassID` wartości dowolnego argumentów typu.|  
|[GetFunctionInfo2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|Pobiera klasy nadrzędnej, token metadanych i `ClassID` argumentu typu, jeśli jest obecny, funkcji.|  
|[GetGenerationBounds — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|Pobiera regiony pamięci (segmenty sterty) tworzące generacje stosu zebranego przez pamięci.|  
|[GetNotifiedExceptionClauseInfo — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Pobiera natywnego adresu i ramki informacje dla klauzuli wyjątek (`catch`/`finally`/`filter`) ma być uruchomiona albo został uruchomiony.|  
|[GetObjectGeneration — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|Pobiera segment stosu, który zawiera określony obiekt.|  
|[GetRVAStaticAddress — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|Pobiera adres określony wirtualny adres względny (RVA)-pola statycznego.|  
|[GetStaticFieldInfo — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|Pobiera zakres, w którym określone pole jest statyczne.|  
|[GetStringLayout — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|Pobiera informacje o układzie z obiektem ciągu.|  
|[GetThreadAppDomain — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|Pobiera identyfikator domeny aplikacji, w którym określony wątek jest w trakcie wykonywania kodu.|  
|[GetThreadStaticAddress — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|Pobiera adres określonego pola statyczne dla wątku, który znajduje się w zakresie określonego wątku.|  
|[SetEnterLeaveFunctionHooks2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Określa zaimplementowana profilera funkcji do wywołania "Wprowadź", "Pozostaw" i "tailcall" punkty zaczepienia w funkcji zarządzanych.|  
  
## <a name="remarks"></a>Uwagi  
 Profiler wywołuje metodę `ICorProfilerInfo2` interfejs do komunikacji z CLR do kontrolowania, monitorowanie zdarzeń i żądań informacji.  
  
 Metody `ICorProfilerInfo2` interfejsu są implementowane przez środowisko CLR za pomocą modelu bezwątkowy. Każda metoda zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia. Aby uzyskać listę możliwych kody powrotu zobacz plik CorError.h.  
  
 Przekazuje CLR `ICorProfilerInfo2` interfejs do każdego profilującego podczas inicjowania przy użyciu profilera stosowania [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Profiler kodu można wywoływać metody `ICorProfilerInfo2` interfejsu, aby uzyskać informacje na temat kodu zarządzanego wykonywana pod kontrolą środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
