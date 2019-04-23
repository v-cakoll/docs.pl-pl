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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3476a338191a4af9cc01b7e44456f1bd20f52a10
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179013"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 — Interfejs
Udostępnia metody, które profilery kodu używać do komunikowania się za pomocą środowiska uruchomieniowego języka wspólnego (CLR) do kontrolowania, monitorowanie zdarzeń i informacje o żądaniu. `ICorProfilerInfo2` Interfejs jest rozszerzeniem [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interfejsu. Oznacza to, że zapewnia nowe metody obsługiwane w programie .NET Framework w wersji 2.0 i nowszych wersjach.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DoStackSnapshot, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|Przedstawia stos określonego wątku do zgłaszania ramki zarządzane wywołania do programu profilującego.|  
|[EnumModuleFrozenObjects, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|Pobiera moduł wyliczający, który pozwala iteracji przez zamrożone obiekty w określonym module.|  
|[GetAppDomainStaticAddress, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|Pobiera adres pola statyczne domeny określonej aplikacji, które znajduje się w zakresie domeny określonej aplikacji.|  
|[GetArrayObjectInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|Pobiera szczegółowe informacje dotyczące obiektu array.|  
|[GetBoxClassLayout, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|Pobiera informacje o układ klasy dla typu określonej wartości, który jest spakowany.|  
|[GetClassFromTokenAndTypeArgs, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Pobiera `ClassID` typu przy użyciu tokenu określonych metadanych i `ClassID` wartości wszelkich argumentów typu.|  
|[GetClassIDInfo2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|Pobiera moduł nadrzędnej określonej klasy ogólnej token metadanych dla tej klasy, `ClassID` klasy nadrzędnej, a `ClassID` dla każdego typu argumentu, jeśli jest obecny, klasy.|  
|[GetClassLayout, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|Pobiera informacje o układu, w pamięci, pól zdefiniowanych przez określonej klasy. Oznacza to, że ta metoda pobiera przesunięcia pól tej klasy.|  
|[GetCodeInfo2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|Pobiera zakres kodu natywnego skojarzonego z określonym `FunctionID`.|  
|[GetContextStaticAddress, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|Pobiera adres określone pole statyczne kontekstu, który znajduje się w zakresie określonego kontekstu.|  
|[GetFunctionFromTokenAndTypeArgs, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Pobiera `FunctionID` funkcji przy użyciu tokenu określonych metadanych, klasą, i `ClassID` wartości wszelkich argumentów typu.|  
|[GetFunctionInfo2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|Pobiera klasy nadrzędnej, token metadanych i `ClassID` każdego argumentu typu, jeśli jest obecny w funkcji.|  
|[GetGenerationBounds, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|Pobiera regiony pamięci (segmenty stosu), które tworzą generacje stercie zebranych elementów bezużytecznych.|  
|[GetNotifiedExceptionClauseInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Pobiera natywne informacje dotyczące adresów i ramki dla klauzuli wyjątek (`catch`/`finally`/`filter`) który ma być uruchomiona lub została uruchomiona.|  
|[GetObjectGeneration, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|Pobiera segment stosu, który zawiera dany obiekt.|  
|[GetRVAStaticAddress, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|Pobiera adres określonej względnych adresów wirtualnych (RVA) — pole statyczne.|  
|[GetStaticFieldInfo, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|Pobiera zakres, w którym określone pole jest statyczne.|  
|[GetStringLayout, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|Pobiera informacje o układ obiektu ciągu.|  
|[GetThreadAppDomain, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|Pobiera identyfikator domeny aplikacji, w którym określony wątek jest w trakcie wykonywania kodu.|  
|[GetThreadStaticAddress, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|Pobiera adres określone pole statyczne wątku, który znajduje się w zakresie określonego wątku.|  
|[SetEnterLeaveFunctionHooks2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Określa funkcje implementowane przez profiler ma być wywołane na "enter", "Opuść" i "rekurencja ogonowa" hooks zarządzanej funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Program profilujący wywołuje metodę `ICorProfilerInfo2` interfejs do komunikacji przy użyciu środowiska CLR do kontrolowania, monitorowanie zdarzeń i zażądać informacji.  
  
 Metody `ICorProfilerInfo2` interfejsu są implementowane przez środowisko CLR, przy użyciu modelu bezwątkowy. Każda metoda zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia. Aby uzyskać listę możliwych kodów powrotnych zobacz plik CorError.h.  
  
 Przekazuje środowisko CLR `ICorProfilerInfo2` interfejs do każdej profilującego podczas inicjowania przy użyciu implementacji programu profilującego [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Program profilujący kodu może wywoływać metody `ICorProfilerInfo2` interfejsu, aby uzyskać informacje na temat kodu zarządzanego, wykonywana jest pod kontrolą środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
