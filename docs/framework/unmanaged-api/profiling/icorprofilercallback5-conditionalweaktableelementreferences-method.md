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
ms.openlocfilehash: ad721d28f6a7dc6ae0370ce10178990cb02fb9f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430052"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>Metoda ICorProfilerCallback5::ConditionalWeakTableElementReferences

Identyfikuje przechodnie zamknięcie obiektów, do których odwołują się te elementy główne za pośrednictwem bezpośrednich odwołań do pól składowych i za pośrednictwem zależności `ConditionalWeakTable`.

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
podczas Liczba elementów w tablicach `keyRefIds`, `valueRefIds`i `rootIds`.

`keyRefIds`\
podczas Tablica identyfikatorów obiektów, z których każdy zawiera `ObjectID` dla elementu podstawowego w parze uchwytów zależnych.

`valueRefIds`\
podczas Tablica identyfikatorów obiektów, z których każdy zawiera `ObjectID` dla elementu pomocniczego w parze uchwytów zależnych. (`keyRefIds[i]` utrzymuje `valueRefIds[i]` aktywności).

`rootIds`\
podczas Tablica wartości `GCHandleID`, która wskazuje liczbę całkowitą, która zawiera dodatkowe informacje o katalogu głównym wyrzucania elementów bezużytecznych.

Żadna z wartości `ObjectID` zwróconych przez metodę `ConditionalWeakTableElementReferences` nie jest prawidłowa podczas wywołania zwrotnego, ponieważ moduł wyrzucania elementów bezużytecznych może znajdować się w procesie przeniesienia obiektów ze starych do nowych lokalizacji. W związku z tym nie należy próbować kontrolować obiektów podczas wywołania `ConditionalWeakTableElementReferences`. W `GarbageCollectionFinished`wszystkie obiekty zostały przeniesione do nowej lokalizacji, a inspekcja może zostać wykonana.

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

Profiler dla .NET Framework 4,5 lub nowszych wersji implementuje interfejs [ICorProfilerCallback5](icorprofilercallback5-interface.md) i rejestruje zależności określone przez metodę `ConditionalWeakTableElementReferences`. `ICorProfilerCallback5` zapewnia pełen zestaw zależności między obiektami na żywo reprezentowanymi przez `ConditionalWeakTable` wpisy. Te zależności i odwołania do pól elementu członkowskiego określone przez metodę [ICorProfilerCallback:: ObjectReferences —](icorprofilercallback-objectreferences-method.md) umożliwiają zarządzanemu profilerowi generowanie grafu pełnego obiektu na żywo obiektów.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** CorProf. idl, CorProf. h

**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback5, interfejs](icorprofilercallback5-interface.md)
