---
title: ICorProfilerCallback::ObjectReferences — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1142b33f029708d93cc3b808dc6be2b2df5b0ee3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119252"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences — Metoda
Powiadamia program profilujący dotyczących obiektów w pamięci, przywoływane przez określony obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 [in] Identyfikator obiektu, który odwołuje się do obiektów.  
  
 `classId`  
 [in] Identyfikator klasy określony obiekt jest wystąpieniem.  
  
 `cObjectRefs`  
 [in] Liczba obiektów, odwołuje się określony obiekt (oznacza to, że liczba elementów w `objectRefIds` tablicy).  
  
 `objectRefIds`  
 [in] Tablica identyfikatorów obiektów, które odwołują się `objectId`.  
  
## <a name="remarks"></a>Uwagi  
 `ObjectReferences` Metoda jest wywoływana dla każdego obiektu, pozostałe w stercie po zakończeniu wyrzucania elementów bezużytecznych. Jeśli program profilujący zwraca błąd z to wywołanie zwrotne, profilowania services zostanie wycofana, wywoływania to wywołanie zwrotne aż do następnego wyrzucania elementów bezużytecznych.  
  
 `ObjectReferences` Wywołania zwrotnego mogą być używane w połączeniu z [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) wywołania zwrotnego, aby utworzyć obiekt kompletny wykres odwołań dla środowiska uruchomieniowego. Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia, że każde odwołanie obiektu jest raportowane tylko raz przez `ObjectReferences` metody.  
  
 Identyfikatory obiektów są zwracane przez `ObjectReferences` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucania elementów bezużytecznych może być w trakcie przenoszenia obiektów. W związku z tym, profilowania nie wolno próbować Zbadaj obiekty podczas `ObjectReferences` wywołania. Gdy [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) jest wywoływana, wyrzucanie elementów zakończeniu zbierania i inspekcji można bezpiecznie wykonać.  
  
 Wartość null `ClassId` wskazuje, że `objectId` ma typ, który jest zwolnienie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
