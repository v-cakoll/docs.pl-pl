---
title: Metoda ICorProfilerCallback5::ConditionalWeakTableElementReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5.ConditionalWeakTableReferences
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- CondiitonalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad192f753cd1977c9ca68e147d23375ce092b66f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708236"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>Metoda ICorProfilerCallback5::ConditionalWeakTableElementReferences
Identyfikuje przechodnie zamknięcia obiektów, odwołuje się katalogami, za pomocą odwołania do obu pól bezpośrednim członkiem i za pomocą `ConditionalWeakTable` zależności.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ConditionalWeakTableElementReferences(     [in]                     ULONG    cRootRefs,     [in, size_is(cRootRefs)] ObjectID keyRefIds[],     [in, size_is(cRootRefs)] ObjectID valueRefIds[],     [in, size_is(cRootRefs)] GCHandleID rootIds[]);};  
```  
  
#### <a name="parameters"></a>Parametry  
 `cRootRefs`  
 [in] Liczba elementów w `keyRefIds`, `valueRefIds`, i `rootIds` tablic.  
  
 `keyRefIds`  
 [in] Tablica identyfikatory obiektów, z których każdy zawiera `ObjectID` dla podstawowego elementu w parze dojście zależne.  
  
 `valueRefIds`  
 [in] Tablica identyfikatory obiektów, z których każdy zawiera `ObjectID` dla elementu pomocniczego w parze dojście zależne. (`keyRefIds[i]` utrzymuje `valueRefIds[i]` podtrzymywania połączenia.)  
  
 `rootIds`  
 [in] Tablica `GCHandleID` wartości, które wskazują na liczbę całkowitą, która zawiera dodatkowe informacje na temat głównych kolekcji wyrzucania elementów.  
  
 Żaden z `ObjectID` wartości zwracanych przez `ConditionalWeakTableElementReferences` metody są prawidłowe podczas wywołania zwrotnego, ponieważ moduł odśmiecania pamięci może być w trakcie przenoszenia obiektów ze starej do nowej lokalizacji. W związku z tym, profilowania nie należy próbować Zbadaj obiekty podczas `ConditionalWeakTableElementReferences` wywołania. W `GarbageCollectionFinished`, wszystkie obiekty zostały przeniesione do ich nowych lokalizacji i może zostać przeprowadzona inspekcja.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób implementacji [icorprofilercallback5 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) i używania tej metody.  
  
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
 Profiler dla [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] lub nowsze wersje implementuje [icorprofilercallback5 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) interfejsu i rekordy zależności, określony przez `ConditionalWeakTableElementReferences` metody. `ICorProfilerCallback5` zawiera pełen zestaw zależności między obiektami na żywo, reprezentowane przez `ConditionalWeakTable` wpisów. Te zależności i element członkowski pola odwołania do określonego przez [icorprofilercallback::objectreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) metoda włączyć zarządzany profiler można wygenerować wykresu obiektu pełną obiektów na żywo.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerCallback5, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)
