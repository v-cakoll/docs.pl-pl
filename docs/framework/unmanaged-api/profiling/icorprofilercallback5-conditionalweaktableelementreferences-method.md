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
- ConditionalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
ms.openlocfilehash: 17fbc99b30921f795c1f7ff882ec73432aade8c6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499249"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>Metoda ICorProfilerCallback5::ConditionalWeakTableElementReferences

Identyfikuje przechodnie zamknięcie obiektów, do których odwołują się te elementy główne za pośrednictwem bezpośrednich odwołań do pól składowych i za pośrednictwem `ConditionalWeakTable` zależności.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a>Parametry

`cRootRefs`\
podczas Liczba elementów w `keyRefIds` `valueRefIds` `rootIds` tablicach, i.

`keyRefIds`\
podczas Tablica identyfikatorów obiektów, z których każdy zawiera `ObjectID` element dla elementu podstawowego w parze uchwytów zależnych.

`valueRefIds`\
podczas Tablica identyfikatorów obiektów, z których każdy zawiera `ObjectID` element dla elementu pomocniczego w parze zależnych uchwytów. ( `keyRefIds[i]` utrzymuje `valueRefIds[i]` aktywność).

`rootIds`\
podczas Tablica `GCHandleID` wartości, która wskazuje liczbę całkowitą, która zawiera dodatkowe informacje o katalogu głównym wyrzucania elementów bezużytecznych.

Żadna z `ObjectID` wartości zwracanych przez `ConditionalWeakTableElementReferences` metodę nie jest prawidłowa podczas wywołania zwrotnego, ponieważ moduł wyrzucania elementów bezużytecznych może być w trakcie przechodzenia obiektów ze starych do nowych lokalizacji. W związku z tym nie należy próbować kontrolować obiektów podczas `ConditionalWeakTableElementReferences` wywołania. W programie `GarbageCollectionFinished` wszystkie obiekty zostały przeniesione do nowych lokalizacji i można przeprowadzić inspekcję.

## <a name="example"></a>Przykład

Poniższy przykład kodu demonstruje sposób implementacji [ICorProfilerCallback5](icorprofilercallback5-interface.md) i używania tej metody.

```cpp
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

Profiler dla .NET Framework 4,5 lub nowszych wersji implementuje interfejs [ICorProfilerCallback5](icorprofilercallback5-interface.md) i rejestruje zależności określone przez `ConditionalWeakTableElementReferences` metodę. `ICorProfilerCallback5`zapewnia pełen zestaw zależności między obiektami na żywo reprezentowane przez `ConditionalWeakTable` wpisy. Te zależności i odwołania do pól elementu członkowskiego określone przez metodę [ICorProfilerCallback:: ObjectReferences —](icorprofilercallback-objectreferences-method.md) umożliwiają zarządzanemu profilerowi generowanie grafu pełnego obiektu na żywo obiektów.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** CorProf. idl, CorProf. h

**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback5, interfejs](icorprofilercallback5-interface.md)
