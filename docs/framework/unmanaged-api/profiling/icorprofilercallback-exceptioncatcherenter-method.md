---
title: "ICorProfilerCallback::ExceptionCatcherEnter — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCatcherEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a72b2e75ee622bab357046ff29fac4aa9223d7a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a>ICorProfilerCallback::ExceptionCatcherEnter — Metoda
Powiadamia profiler kontrola jest przekazywana do odpowiedniego `catch` bloku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator zawierający funkcja `catch` bloku.  
  
 `objectId`  
 [in] Identyfikator obsługiwanie wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 `ExceptionCatcherEnter` Metoda jest wywoływana tylko wtedy, gdy punkt catch w kodzie skompilowanym z kompilatora just-in-time (JIT). Wyjątek zostanie przechwycony za pomocą kodu niezarządzanego lub w kodzie wewnętrzny środowiska uruchomieniowego nie wywoła tego powiadomienia. `objectId` Została przekazana wartość ponownie ponieważ wyrzucania elementów bezużytecznych można przenieść obiektu, ponieważ `ExceptionThrown` powiadomień.  
  
 Profilera nie należy zablokować w jej implementacja tej metody, ponieważ stos nie może być w stanie, który umożliwia odzyskiwanie pamięci i dlatego nie można włączyć cenią sobie wcześniejsze wyrzucanie elementów bezużytecznych. Jeśli profilera blokuje tutaj i nastąpiła wyrzucanie elementów bezużytecznych, środowisko uruchomieniowe zablokuje dopóki zwraca tego wywołania zwrotnego.  
  
 Profiler implementacja tej metody nie powinny wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ExceptionCatcherLeave, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
