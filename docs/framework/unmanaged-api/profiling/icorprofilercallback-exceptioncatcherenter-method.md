---
title: ICorProfilerCallback::ExceptionCatcherEnter — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9b47e1d1bfa1d8f6c970e95fe25f62a690d3b91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143874"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a>ICorProfilerCallback::ExceptionCatcherEnter — Metoda
Powiadamia program profilujący, że formant jest przekazywany do odpowiedniego `catch` bloku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji zawierającego `catch` bloku.  
  
 `objectId`  
 [in] Identyfikator obsługiwanie wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 `ExceptionCatcherEnter` Metoda jest wywoływana tylko wtedy, gdy punkt catch w kodzie skompilowanym za pomocą kompilatora just-in-time (JIT). Wyjątek, który zostanie przechwycony w niezarządzanym kodzie lub w kodzie wewnętrznego środowiska uruchomieniowego nie wywoła to powiadomienie. `objectId` Wartość jest przekazywana ponownie, ponieważ wyrzucania elementów bezużytecznych można przenieść obiektu, ponieważ `ExceptionThrown` powiadomień.  
  
 Program profilujący nie powinna blokować w jego implementacja tej metody, ponieważ stos może nie być w stanie umożliwiającym wyrzucania elementów bezużytecznych, a w związku z tym nie można włączyć preemptive wyrzucania elementów bezużytecznych. Jeśli program profilujący blokuje tutaj i wyrzucania elementów bezużytecznych jest podejmowana próba, środowisko uruchomieniowe spowoduje zablokowanie, dopóki nie zwróci to wywołanie zwrotne.  
  
 Implementacja tej metody program profilujący nie powinien wywoływać wywołanie kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ExceptionCatcherLeave, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
