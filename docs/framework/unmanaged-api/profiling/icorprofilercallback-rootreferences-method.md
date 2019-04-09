---
title: ICorProfilerCallback::RootReferences — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b616017745d7cc33d57b1626b6c27c59a0a60a32
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091177"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences — Metoda
Powiadamia program profilujący informacje na temat odwołań do katalogu głównego po wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cRootRefs`  
 [in] Liczba odwołań w `rootRefIds` tablicy.  
  
 `rootRefIds`  
 [in] Tablica identyfikatory obiektów, odwołujące się do obiektu statycznego lub obiekt na stosie.  
  
## <a name="remarks"></a>Uwagi  
 Zarówno `RootReferences` i [icorprofilercallback2::rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) są wywoływane w celu powiadomić profiler. Profilery wdroży zwykle jednej lub drugiej, ale nie oba, ponieważ informacje są przekazywane w `RootReferences2` jest nadzbiorem, przekazanej `RootReferences`.  
  
 Możliwe jest `rootRefIds` tablicy zawiera obiekt z wartością null. Na przykład wszystkie odwołania do obiektu zadeklarowany na stosie są traktowane jako elementy główne przez moduł odśmiecania pamięci i zawsze będą raportowane.  
  
 Identyfikatory obiektów są zwracane przez `RootReferences` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucania elementów bezużytecznych może być w trakcie przenoszenia obiektów z stare adresy do nowych adresów. W związku z tym, profilowania nie wolno próbować Zbadaj obiekty podczas `RootReferences` wywołania. Gdy [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) jest wywoływana, wszystkie obiekty zostały przeniesione do ich nowych lokalizacji i może być bezpiecznie kontrolowane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
