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
ms.openlocfilehash: 4480fefa51eec2f2751bd71910db87b72a1c32cf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496731"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 — Interfejs
Zapewnia metody, które są używane przez program codeer do komunikowania się ze środowiskiem uruchomieniowym języka wspólnego (CLR) w celu kontrolowania informacji o monitorowaniu zdarzeń i żądaniach. `ICorProfilerInfo2`Interfejs jest rozszerzeniem interfejsu [ICorProfilerInfo](icorprofilerinfo-interface.md) . Oznacza to, że udostępnia nowe metody obsługiwane w .NET Framework wersji 2,0 i nowszych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DoStackSnapshot, metoda](icorprofilerinfo2-dostacksnapshot-method.md)|Przeprowadzi stos określonego wątku, aby raportować zarządzane ramki wywołań do profilera.|  
|[EnumModuleFrozenObjects, metoda](icorprofilerinfo2-enummodulefrozenobjects-method.md)|Pobiera moduł wyliczający, który umożliwia iterację w odniesieniu do zablokowanych obiektów w określonym module.|  
|[GetAppDomainStaticAddress, metoda](icorprofilerinfo2-getappdomainstaticaddress-method.md)|Pobiera adres wskazanej domeny aplikacji — pole statyczne należące do zakresu określonej domeny aplikacji.|  
|[GetArrayObjectInfo, metoda](icorprofilerinfo2-getarrayobjectinfo-method.md)|Pobiera szczegółowe informacje o obiekcie array.|  
|[GetBoxClassLayout, metoda](icorprofilerinfo2-getboxclasslayout-method.md)|Pobiera informacje o układzie klasy dla określonego typu wartości, który jest opakowany.|  
|[GetClassFromTokenAndTypeArgs, metoda](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Pobiera `ClassID` Typ przy użyciu określonego tokenu metadanych i `ClassID` wartości dowolnego argumentu typu.|  
|[GetClassIDInfo2, metoda](icorprofilerinfo2-getclassidinfo2-method.md)|Pobiera moduł nadrzędny określonej klasy generycznej, token metadanych klasy, `ClassID` klasy nadrzędnej i `ClassID` dla każdego argumentu typu, jeśli istnieje, klasy.|  
|[GetClassLayout — Metoda](icorprofilerinfo2-getclasslayout-method.md)|Pobiera informacje o układzie, w pamięci, pól zdefiniowanych przez określoną klasę. Oznacza to, że ta metoda pobiera przesunięcia pól klasy.|  
|[GetCodeInfo2, metoda](icorprofilerinfo2-getcodeinfo2-method.md)|Pobiera zakresy kodu natywnego skojarzonego z określonym `FunctionID` .|  
|[GetContextStaticAddress, metoda](icorprofilerinfo2-getcontextstaticaddress-method.md)|Pobiera adres określonego pola statycznego kontekstu, które znajduje się w zakresie określonego kontekstu.|  
|[GetFunctionFromTokenAndTypeArgs, metoda](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Pobiera `FunctionID` funkcję przy użyciu określonego tokenu metadanych, zawierającego klasę i `ClassID` wartości dowolnego argumentu typu.|  
|[GetFunctionInfo2, metoda](icorprofilerinfo2-getfunctioninfo2-method.md)|Pobiera klasę nadrzędną, token metadanych i `ClassID` dla każdego argumentu typu, jeśli istnieje, funkcji.|  
|[GetGenerationBounds, metoda](icorprofilerinfo2-getgenerationbounds-method.md)|Pobiera regiony pamięci (segmenty sterty), które tworzą generacji sterty zebranych elementów bezużytecznych.|  
|[GetNotifiedExceptionClauseInfo, metoda](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Pobiera natywne informacje o adresie i ramce dla klauzuli wyjątku ( `catch` / `finally` / `filter` ), która ma zostać uruchomiona lub właśnie została uruchomiona.|  
|[GetObjectGeneration, metoda](icorprofilerinfo2-getobjectgeneration-method.md)|Pobiera segment sterty, która zawiera określony obiekt.|  
|[GetRVAStaticAddress, metoda](icorprofilerinfo2-getrvastaticaddress-method.md)|Pobiera adres określonego względnego adresu wirtualnego (RVA) — statycznego pola.|  
|[GetStaticFieldInfo, metoda](icorprofilerinfo2-getstaticfieldinfo-method.md)|Pobiera zakres, w którym określone pole jest statyczne.|  
|[GetStringLayout, metoda](icorprofilerinfo2-getstringlayout-method.md)|Pobiera informacje o układzie obiektu ciągu.|  
|[GetThreadAppDomain, metoda](icorprofilerinfo2-getthreadappdomain-method.md)|Pobiera identyfikator domeny aplikacji, w której określony wątek aktualnie wykonuje kod.|  
|[GetThreadStaticAddress, metoda](icorprofilerinfo2-getthreadstaticaddress-method.md)|Pobiera adres określonego wątku-static pola, które znajduje się w zakresie określonego wątku.|  
|[SetEnterLeaveFunctionHooks2, metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Określa funkcje zaimplementowane przez profiler, które mają być wywoływane w podpunktach "Enter", "urlop" i "tailcall" punktów zarządzanych funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Profiler wywołuje metodę w `ICorProfilerInfo2` interfejsie, aby komunikować się z środowiskiem CLR w celu sterowania monitorowaniem zdarzeń i informacjami o żądaniu.  
  
 Metody `ICorProfilerInfo2` interfejsu są implementowane przez środowisko CLR przy użyciu modelu dowolnego wątku. Każda metoda zwraca wynik HRESULT wskazujący powodzenie lub niepowodzenie. Aby uzyskać listę możliwych kodów powrotu, zobacz plik CorError. h.  
  
 Środowisko CLR przekazuje `ICorProfilerInfo2` interfejs do każdego profilera kodu podczas inicjowania przy użyciu implementacji profilera [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md). Profiler kodu może następnie wywołać metody `ICorProfilerInfo2` interfejsu, aby uzyskać informacje o kodzie zarządzanym wykonywanym pod kontrolą środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
