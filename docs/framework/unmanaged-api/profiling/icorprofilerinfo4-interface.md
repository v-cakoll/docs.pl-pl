---
title: ICorProfilerInfo4 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27cce8a77d4236829124b45650d5d0ac32a5150c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198006"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 — Interfejs
Udostępnia metody, które profilery kodu używać do komunikowania się za pomocą środowiska uruchomieniowego języka wspólnego (CLR) do kontrolowania, monitorowanie zdarzeń i informacje o żądaniu. . `ICorProfilerInfo4` Interfejs jest rozszerzeniem innych `ICorProfilerInfo` interfejsów. Zapewnia nowe metody obsługi ponownej kompilacji just-in-time (JIT), dodane w [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumJITedFunctions2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|Zwraca moduł wyliczający dla wszystkich funkcji, które wcześniej były skompilowane JIT i ponownie skompilowana JIT.|  
|[EnumThreads, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|Pobiera moduł wyliczający, który udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji wszystkie zarządzane wątki w profilowanym procesie.|  
|[GetCodeInfo3, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|Pobiera zakres skojarzony z wersją określoną funkcję ponownie skompilowana JIT kodu natywnego.|  
|[GetFunctionFromIP2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|Mapuje wskaźnik instrukcji kodu zarządzanego do wersji ponownie skompilowana JIT określoną funkcję.|  
|[GetILToNativeMapping2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Pobiera mapę od firmy Microsoft intermediate language (MSIL) przesuwa się do macierzystych przesunięciach kod zawarty w wersji ponownie skompilowana JIT określonej funkcji.|  
|[GetObjectSize2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|Zwraca rozmiar określonego obiektu.|  
|[GetReJITIDs, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|Zwraca tablicę identyfikatorów, które identyfikują wszystkie ponownie skompilowana JIT wersje określonej funkcji, które nadal są przydzielane.|  
|[InitializeCurrentThread, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|Inicjuje bieżący wątek ewentualnej profilującym kolejnych wywołań interfejsu API w tym samym wątku, dzięki czemu można uniknąć tego zakleszczenia.|  
|[RequestReJIT, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|Żąda JIT — rekompilacja wszystkich wystąpień określonych funkcji.|  
|[RequestRevert, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|Przywraca wszystkie wystąpienia określonych funkcji do ich oryginalnej wersji.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR implementuje metody `ICorProfilerInfo4` interfejsu przy użyciu modelu bezwątkowy. Każda metoda zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia. Aby uzyskać listę możliwych kodów powrotnych zobacz plik CorError.h.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** } CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
