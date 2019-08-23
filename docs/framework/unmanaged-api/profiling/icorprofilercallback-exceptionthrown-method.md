---
title: ICorProfilerCallback::ExceptionThrown — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 01e407b726ce4426f3b58bc29854b30bd6add257
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953879"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a>ICorProfilerCallback::ExceptionThrown — Metoda
Powiadamia profiler o zgłoszonym wyjątku.  
  
> [!NOTE]
> Ta funkcja jest wywoływana tylko wtedy, gdy wyjątek osiągnie kod zarządzany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a>Parametry  
 `thrownObjectId`  
 podczas Identyfikator obiektu, który spowodował wyjątek.  
  
## <a name="remarks"></a>Uwagi  
 Profiler nie powinien blokować swojej implementacji tej metody, ponieważ stos może nie znajdować się w stanie, który zezwala na wyrzucanie elementów bezużytecznych i dlatego nie można włączyć zastępujący elementów bezużytecznych. Jeśli profiler blokuje tutaj i zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu wywołania zwrotnego.  
  
 Implementacja profilera nie powinna być wywoływana w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorProf. idl, CorProf. h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
