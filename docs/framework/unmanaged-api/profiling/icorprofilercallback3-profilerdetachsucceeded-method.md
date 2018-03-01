---
title: "ICorProfilerCallback3::ProfilerDetachSucceeded — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d06671917094752287836800ebc492d5f0a5b595
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a>ICorProfilerCallback3::ProfilerDetachSucceeded — Metoda
Powiadamia profilera środowisko uruchomieniowe języka wspólnego (CLR) o zbliżającym się zwolnienia biblioteki DLL profilera.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana z tego wywołania zwrotnego jest ignorowana.  
  
## <a name="remarks"></a>Uwagi  
 `ProfilerDetachSucceeded` Wywołania zwrotnego jest wystawianym po zamknięciu kodu profilera wszystkie wątki. Gdy ta metoda jest wywoływana, profilera, należy wykonać wszystkie zadania ostatniej minuty, które nie są odpowiednie do jego destruktor, takich jak powiadamiania jego interfejsu użytkownika lub rejestrowania składnika. Jednak profilera nie mogą wywoływać funkcje na interfejsy, które są udostępniane przez środowisko CLR Podczas tego wywołania zwrotnego (takich jak [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) lub `IMetaData*` interfejsów).  
  
 Środowisko CLR tworzy wpis w dzienniku zdarzeń aplikacji systemu Windows, aby wskazać, czy operacja odłączenia zakończy się pomyślnie.  
  
 Po powrocie profilera z tego wywołania zwrotnego, CLR zwalnia obiektu profilera i zwalnia biblioteki DLL profilera. W związku z tym profilera nie musi wykonywać wszystkie akcje, które mogłoby spowodować wykonanie wystąpienia wewnątrz biblioteki DLL profilera zwraca to wywołanie zwrotne. Na przykład nie musi utworzyć wątków lub rejestrowania wywołań zwrotnych czasomierza.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
