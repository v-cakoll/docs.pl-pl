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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 39ce72451f3a375f0cd3adb67a431162fc421a93
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352207"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="e7755-102">Metoda ICorProfilerCallback5::ConditionalWeakTableElementReferences</span><span class="sxs-lookup"><span data-stu-id="e7755-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>

<span data-ttu-id="e7755-103">Identyfikuje przechodnie zamknięcia obiektów, odwołuje się katalogami, za pomocą odwołania do obu pól bezpośrednim członkiem i za pomocą `ConditionalWeakTable` zależności.</span><span class="sxs-lookup"><span data-stu-id="e7755-103">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>

## <a name="syntax"></a><span data-ttu-id="e7755-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7755-104">Syntax</span></span>

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a><span data-ttu-id="e7755-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7755-105">Parameters</span></span>

`cRootRefs`\
<span data-ttu-id="e7755-106">[in] Liczba elementów w `keyRefIds`, `valueRefIds`, i `rootIds` tablic.</span><span class="sxs-lookup"><span data-stu-id="e7755-106">[in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>

`keyRefIds`\
<span data-ttu-id="e7755-107">[in] Tablica identyfikatory obiektów, z których każdy zawiera `ObjectID` dla podstawowego elementu w parze dojście zależne.</span><span class="sxs-lookup"><span data-stu-id="e7755-107">[in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>

`valueRefIds`\
<span data-ttu-id="e7755-108">[in] Tablica identyfikatory obiektów, z których każdy zawiera `ObjectID` dla elementu pomocniczego w parze dojście zależne.</span><span class="sxs-lookup"><span data-stu-id="e7755-108">[in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="e7755-109">(`keyRefIds[i]` utrzymuje `valueRefIds[i]` podtrzymywania połączenia.)</span><span class="sxs-lookup"><span data-stu-id="e7755-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>

`rootIds`\
<span data-ttu-id="e7755-110">[in] Tablica `GCHandleID` wartości, które wskazują na liczbę całkowitą, która zawiera dodatkowe informacje na temat głównych kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="e7755-110">[in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>

<span data-ttu-id="e7755-111">Żaden z `ObjectID` wartości zwracanych przez `ConditionalWeakTableElementReferences` metody są prawidłowe podczas wywołania zwrotnego, ponieważ moduł odśmiecania pamięci może być w trakcie przenoszenia obiektów ze starej do nowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e7755-111">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="e7755-112">W związku z tym, profilowania nie należy próbować Zbadaj obiekty podczas `ConditionalWeakTableElementReferences` wywołania.</span><span class="sxs-lookup"><span data-stu-id="e7755-112">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="e7755-113">W `GarbageCollectionFinished`, wszystkie obiekty zostały przeniesione do ich nowych lokalizacji i może zostać przeprowadzona inspekcja.</span><span class="sxs-lookup"><span data-stu-id="e7755-113">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>

## <a name="example"></a><span data-ttu-id="e7755-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7755-114">Example</span></span>

<span data-ttu-id="e7755-115">Poniższy przykład kodu demonstruje sposób implementacji [icorprofilercallback5 —](icorprofilercallback5-interface.md) i używania tej metody.</span><span class="sxs-lookup"><span data-stu-id="e7755-115">The following code example demonstrates how to implement [ICorProfilerCallback5](icorprofilercallback5-interface.md) and use this method.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="e7755-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7755-116">Remarks</span></span>

<span data-ttu-id="e7755-117">Profiler dla [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] lub nowsze wersje implementuje [icorprofilercallback5 —](icorprofilercallback5-interface.md) interfejsu i rekordy zależności, określony przez `ConditionalWeakTableElementReferences` metody.</span><span class="sxs-lookup"><span data-stu-id="e7755-117">A profiler for the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] or later versions implements the [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="e7755-118">`ICorProfilerCallback5` zawiera pełen zestaw zależności między obiektami na żywo, reprezentowane przez `ConditionalWeakTable` wpisów.</span><span class="sxs-lookup"><span data-stu-id="e7755-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="e7755-119">Te zależności i element członkowski pola odwołania do określonego przez [icorprofilercallback::objectreferences —](icorprofilercallback-objectreferences-method.md) metoda włączyć zarządzany profiler można wygenerować wykresu obiektu pełną obiektów na żywo.</span><span class="sxs-lookup"><span data-stu-id="e7755-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7755-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7755-120">Requirements</span></span>

<span data-ttu-id="e7755-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7755-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="e7755-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e7755-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="e7755-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7755-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e7755-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7755-124">See also</span></span>

- [<span data-ttu-id="e7755-125">ICorProfilerCallback5, interfejs</span><span class="sxs-lookup"><span data-stu-id="e7755-125">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)