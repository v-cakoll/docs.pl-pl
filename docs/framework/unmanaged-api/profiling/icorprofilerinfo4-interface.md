---
title: "ICorProfilerInfo4 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4
helpviewer_keywords: ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: db91347ad2c951c28ea7b653336450929d37bdcb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 — Interfejs
Udostępnia metody, które używają profilery kodu do komunikacji z środowisko uruchomieniowe języka wspólnego (CLR) w celu kontrolowania, monitorowanie zdarzeń i informacje o żądaniu. . `ICorProfilerInfo4` Interfejsu jest rozszerzeniem innym `ICorProfilerInfo` interfejsów. Zapewnia nowych metod do obsługi kompilację just-in-time (JIT), dodane w [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumJITedFunctions2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|Zwraca moduł wyliczający dla wszystkich funkcji, które były wcześniej kompilacji JIT i ponownie kompilowana JIT.|  
|[EnumThreads — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|Pobiera moduł wyliczający, który, który udostępnia metody do sekwencyjnie iteracji kolekcji wszystkie wątki zarządzane PROFILOWANEGO procesu.|  
|[GetCodeInfo3 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|Pobiera zakres skojarzone z ponownie kompilowana JIT wersja określona funkcja kodu natywnego.|  
|[GetFunctionFromIP2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|Mapuje wskaźnik instrukcji kodu zarządzanego do wersji ponownie kompilowana JIT określona funkcja.|  
|[GetILToNativeMapping2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Pobiera mapy firmy Microsoft do natywnej przesunięć kod źródłowy znajdujący się w wersji ponownie kompilowana JIT określona funkcja powoduje przesunięcie język pośredni (MSIL).|  
|[GetObjectSize2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|Zwraca rozmiar określonego obiektu.|  
|[GetReJITIDs — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|Zwraca tablicę identyfikatorów, które identyfikują wszystkie ponownie kompilowana JIT wersje określona funkcja nadal przydzielonych.|  
|[InitializeCurrentThread — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|Inicjuje bieżący wątek klienta z wyprzedzeniem kolejnych profilera, który wywołania interfejsu API w tym samym wątku, aby uniknąć tego zakleszczenia.|  
|[RequestReJIT — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|Żądania kompilacji JIT, wszystkich wystąpień określonych funkcji.|  
|[RequestRevert — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|Przywraca wszystkie wystąpienia określonych funkcji, do ich oryginalnej wersji.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR implementuje metody `ICorProfilerInfo4` interfejsu za pomocą modelu bezwątkowy. Każda metoda zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia. Aby uzyskać listę możliwych kody powrotu zobacz plik CorError.h.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
