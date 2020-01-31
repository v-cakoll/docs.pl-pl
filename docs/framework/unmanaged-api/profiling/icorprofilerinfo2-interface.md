---
title: ICorProfilerInfo2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2
helpviewer_keywords:
- ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type:
- apiref
ms.openlocfilehash: 23fd44a6865b0487296f3ade37c1219e8feba288
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862584"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 — Interfejs
Zapewnia metody, które są używane przez program codeer do komunikowania się ze środowiskiem uruchomieniowym języka wspólnego (CLR) w celu kontrolowania informacji o monitorowaniu zdarzeń i żądaniach. Interfejs `ICorProfilerInfo2` jest rozszerzeniem interfejsu [ICorProfilerInfo](icorprofilerinfo-interface.md) . Oznacza to, że udostępnia nowe metody obsługiwane w .NET Framework wersji 2,0 i nowszych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DoStackSnapshot, metoda](icorprofilerinfo2-dostacksnapshot-method.md)|Przeprowadzi stos określonego wątku, aby raportować zarządzane ramki wywołań do profilera.|  
|[EnumModuleFrozenObjects, metoda](icorprofilerinfo2-enummodulefrozenobjects-method.md)|Pobiera moduł wyliczający, który umożliwia iterację w odniesieniu do zablokowanych obiektów w określonym module.|  
|[GetAppDomainStaticAddress, metoda](icorprofilerinfo2-getappdomainstaticaddress-method.md)|Pobiera adres wskazanej domeny aplikacji — pole statyczne należące do zakresu określonej domeny aplikacji.|  
|[GetArrayObjectInfo, metoda](icorprofilerinfo2-getarrayobjectinfo-method.md)|Pobiera szczegółowe informacje o obiekcie array.|  
|[GetBoxClassLayout, metoda](icorprofilerinfo2-getboxclasslayout-method.md)|Pobiera informacje o układzie klasy dla określonego typu wartości, który jest opakowany.|  
|[GetClassFromTokenAndTypeArgs, metoda](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Pobiera `ClassID` typu przy użyciu określonego tokenu metadanych i wartości `ClassID` dowolnego argumentu typu.|  
|[GetClassIDInfo2, metoda](icorprofilerinfo2-getclassidinfo2-method.md)|Pobiera moduł nadrzędny określonej klasy generycznej, token metadanych dla klasy, `ClassID` jej klasy nadrzędnej i `ClassID` dla każdego argumentu typu, jeśli istnieje, klasy.|  
|[GetClassLayout, metoda](icorprofilerinfo2-getclasslayout-method.md)|Pobiera informacje o układzie, w pamięci, pól zdefiniowanych przez określoną klasę. Oznacza to, że ta metoda pobiera przesunięcia pól klasy.|  
|[GetCodeInfo2, metoda](icorprofilerinfo2-getcodeinfo2-method.md)|Pobiera zakresy kodu natywnego powiązane z określonym `FunctionID`.|  
|[GetContextStaticAddress, metoda](icorprofilerinfo2-getcontextstaticaddress-method.md)|Pobiera adres określonego pola statycznego kontekstu, które znajduje się w zakresie określonego kontekstu.|  
|[GetFunctionFromTokenAndTypeArgs, metoda](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Pobiera `FunctionID` funkcji przy użyciu określonego tokenu metadanych, zawierającego klasę i `ClassID` wartości dowolnego argumentu typu.|  
|[GetFunctionInfo2, metoda](icorprofilerinfo2-getfunctioninfo2-method.md)|Pobiera klasę nadrzędną, token metadanych i `ClassID` każdego argumentu typu, jeśli istnieje, funkcji.|  
|[GetGenerationBounds, metoda](icorprofilerinfo2-getgenerationbounds-method.md)|Pobiera regiony pamięci (segmenty sterty), które tworzą generacji sterty zebranych elementów bezużytecznych.|  
|[GetNotifiedExceptionClauseInfo, metoda](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Pobiera natywne informacje o adresie i ramce dla klauzuli wyjątku (`catch`/`finally`/`filter`), które mają zostać uruchomione lub właśnie uruchomione.|  
|[GetObjectGeneration, metoda](icorprofilerinfo2-getobjectgeneration-method.md)|Pobiera segment sterty, która zawiera określony obiekt.|  
|[GetRVAStaticAddress, metoda](icorprofilerinfo2-getrvastaticaddress-method.md)|Pobiera adres określonego względnego adresu wirtualnego (RVA) — statycznego pola.|  
|[GetStaticFieldInfo, metoda](icorprofilerinfo2-getstaticfieldinfo-method.md)|Pobiera zakres, w którym określone pole jest statyczne.|  
|[GetStringLayout, metoda](icorprofilerinfo2-getstringlayout-method.md)|Pobiera informacje o układzie obiektu ciągu.|  
|[GetThreadAppDomain, metoda](icorprofilerinfo2-getthreadappdomain-method.md)|Pobiera identyfikator domeny aplikacji, w której określony wątek aktualnie wykonuje kod.|  
|[GetThreadStaticAddress, metoda](icorprofilerinfo2-getthreadstaticaddress-method.md)|Pobiera adres określonego wątku-static pola, które znajduje się w zakresie określonego wątku.|  
|[SetEnterLeaveFunctionHooks2, metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Określa funkcje zaimplementowane przez profiler, które mają być wywoływane w podpunktach "Enter", "urlop" i "tailcall" punktów zarządzanych funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Profiler wywołuje metodę w interfejsie `ICorProfilerInfo2`, aby komunikować się z środowiskiem CLR w celu kontrolowania informacji o monitorowaniu zdarzeń i żądaniu.  
  
 Metody interfejsu `ICorProfilerInfo2` są implementowane przez środowisko CLR przy użyciu modelu dowolnego wątku. Każda metoda zwraca wynik HRESULT wskazujący powodzenie lub niepowodzenie. Aby uzyskać listę możliwych kodów powrotu, zobacz plik CorError. h.  
  
 Środowisko CLR przekazuje interfejs `ICorProfilerInfo2` do każdego profilera kodu podczas inicjowania przy użyciu implementacji profilera [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md). Profiler kodu może następnie wywołać metody interfejsu `ICorProfilerInfo2`, aby uzyskać informacje o kodzie zarządzanym wykonywanym w ramach kontroli środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
