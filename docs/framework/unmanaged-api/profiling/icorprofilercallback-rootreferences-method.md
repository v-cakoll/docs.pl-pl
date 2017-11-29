---
title: "ICorProfilerCallback::RootReferences — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RootReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a12dec1ed0fecad235090592def9689f60e50193
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences — Metoda
Powiadamia profilera z informacji o odwołaniach głównego po wyrzucanie elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
#### <a name="parameters"></a>Parametry  
 `cRootRefs`  
 [in] Liczba odwołań w `rootRefIds` tablicy.  
  
 `rootRefIds`  
 [in] Tablica identyfikatory obiektów, które odwołują się do statycznego obiektu albo obiekt na stosie.  
  
## <a name="remarks"></a>Uwagi  
 Zarówno `RootReferences` i [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) są wywoływane w celu powiadomienia profilera. Profilery będzie zwykle implementowany jednej lub drugiej, ale nie obu, ponieważ informacje przekazano `RootReferences2` jest nadzbiorem tego przekazano `RootReferences`.  
  
 Istnieje możliwość `rootRefIds` tablica zawiera obiekt zerowy. Na przykład wszystkie odwołania do obiektów zadeklarowane na stosie są traktowane jako katalogów głównych przez moduł garbage collector i zawsze będą zgłaszane.  
  
 Identyfikatory obiektów zwrócona przez `RootReferences` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może znajdować się w środku przenoszenie obiektów z stare adresy do nowych adresów. W związku z tym profilowania nie wolno próbować sprawdzić obiekty podczas `RootReferences` wywołania. Gdy [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) jest wywoływana, wszystkie obiekty zostały przeniesione do nowej lokalizacji i może być bezpiecznie kontrolowane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
