---
title: Metoda ICorProfilerCallback5::ConditionalWeakTableElementReferences
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback5.ConditionalWeakTableReferences
api_location: Mscorwks.dll
api_type: COM
f1_keywords: CondiitonalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8cfe86ac7d0cd5b4a5c6adb9f12ffe9577b6e611
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>Metoda ICorProfilerCallback5::ConditionalWeakTableElementReferences
Identyfikuje przechodnie zamknięcia odwołuje się katalogami za pomocą obu odwołania do pól bezpośrednimi elementami członkowskimi i za pomocą obiektów `ConditionalWeakTable` zależności.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ConditionalWeakTableElementReferences(     [in]                     ULONG    cRootRefs,     [in, size_is(cRootRefs)] ObjectID keyRefIds[],     [in, size_is(cRootRefs)] ObjectID valueRefIds[],     [in, size_is(cRootRefs)] GCHandleID rootIds[]);};  
```  
  
#### <a name="parameters"></a>Parametry  
 `cRootRefs`  
 [in] Liczba elementów w `keyRefIds`, `valueRefIds`, i `rootIds` tablic.  
  
 `keyRefIds`  
 [in] Tablica wartości identyfikatorów obiektów, z których każdy zawiera `ObjectID` podstawowego elementu w parze dojścia zależnych.  
  
 `valueRefIds`  
 [in] Tablica wartości identyfikatorów obiektów, z których każdy zawiera `ObjectID` dla elementu pomocniczego w parze dojścia zależnych. (`keyRefIds[i]` przechowuje `valueRefIds[i]` aktywności.)  
  
 `rootIds`  
 [in] Tablica `GCHandleID` wartości, które wskazują liczba całkowita, która zawiera dodatkowe informacje dotyczące głównego kolekcji pamięci.  
  
 Żadna z `ObjectID` wartości zwracanych przez `ConditionalWeakTableElementReferences` — metoda są prawidłowe podczas wywołania zwrotnego, ponieważ moduł garbage collector może znajdować się w trakcie przenoszenia obiektów ze starej do nowej lokalizacji. W związku z tym profilery nie powinny podejmować próby sprawdź obiekty podczas `ConditionalWeakTableElementReferences` wywołania. W `GarbageCollectionFinished`, wszystkie obiekty zostały przeniesione do nowej lokalizacji i można przeprowadzić inspekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak wdrożyć [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) i użyć tej metody.  
  
```  
HRESULT Callback5Impl::ConditionalWeakTableElementReferences(  
    ULONG      cRootRefs,  
    ObjectID   keyRefIds[],  
    ObjectID   valueRefIds[],  
    GCHandleID rootIds[])  
{  
    printf("Callback5Impl::ConditionalWeakTableElementReferences called\n");  
    for (unsigned int i = 0; i < cRootRefs; ++i)  
    {  
        // Save dependency to XML for later retrieval  
        PersistDependencyToXml(rootIds[i], keyRefIds[i], valueRefIds[i]);  
        // or store dependency to an internal map  
        m_cwt_deps->add_dep(rootIds[i], keyRefIds[i], valueRefIds[i]);  
        // or add arc to object graph  
        m_obj_graph->add_arc(keyRefIds[i], valueRefIds[i], rootIds[i]);  
    }  
    return S_OK;  
}  
```  
  
## <a name="remarks"></a>Uwagi  
 Profilera dla [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] lub nowsze wersje implementuje [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) interfejsu i rejestruje zależności określony przez `ConditionalWeakTableElementReferences` metody. `ICorProfilerCallback5`zapewnia pełny zestaw zależności między obiektami na żywo reprezentowany przez `ConditionalWeakTable` wpisów. Te zależności i element członkowski odwołania określony przez pole [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) metoda włączyć zarządzany profiler do generowania wykresu obiektu pełne obiektów na żywo.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback5, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)
