---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67ae413ae8944757fc90bcde752b9a5fe53cc68f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948528"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="8f4d2-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="8f4d2-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="8f4d2-103">Zwraca moduł wyliczający do metod, które są zdefiniowane w danym module NGen i wbudowane danej metody.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-103">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="8f4d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f4d2-104">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="8f4d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f4d2-105">Parameters</span></span>

`inlinersModuleId`\
<span data-ttu-id="8f4d2-106">[in] Identyfikator modułu NGen.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-106">[in] The identifier of an NGen module.</span></span>

`inlineeModuleId`\
<span data-ttu-id="8f4d2-107">[in] Identyfikator modułu, który definiuje `inlineeMethodId`.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-107">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="8f4d2-108">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-108">See the Remarks section for more information.</span></span>

`inlineeMethodId`\
<span data-ttu-id="8f4d2-109">[in] Identyfikator śródwierszowych metody.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-109">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="8f4d2-110">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-110">See the Remarks section for more information.</span></span>

`incompleteData`\
<span data-ttu-id="8f4d2-111">[out] Flaga, która wskazuje, czy `ppEnum` zawiera wszystkie metody wbudowanie danej metody.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-111">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="8f4d2-112">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-112">See the Remarks section for more information.</span></span>

`ppEnum`\
<span data-ttu-id="8f4d2-113">[out] Wskaźnik na adres modułu wyliczającego</span><span class="sxs-lookup"><span data-stu-id="8f4d2-113">[out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="8f4d2-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f4d2-114">Remarks</span></span>

<span data-ttu-id="8f4d2-115">`inlineeModuleId` i `inlineeMethodId` razem tworzą pełny identyfikator metodę, która może być śródwierszowa.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-115">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="8f4d2-116">Załóżmy na przykład moduł `A` definiuje metodę `Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="8f4d2-116">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="8f4d2-117">i definiuje moduł B `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="8f4d2-117">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="8f4d2-118">Umożliwia także przyjęto założenie, że `Fancy.AddTwice` inlines wywołanie do `SimpleAdd`.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-118">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="8f4d2-119">Program profilujący można użyć tego modułu wyliczającego można znaleźć wszystkie metody zdefiniowanego w module B, której wbudowane `Simple.Add`, i wynik będzie wyliczanie `AddTwice`.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-119">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="8f4d2-120">`inlineeModuleId` Identyfikator modułu `A`, i `inlineeMethodId` jest identyfikatorem `Simple.Add(int a, int b)`.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-120">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="8f4d2-121">Jeśli `incompleteData` ma wartość true po funkcji zwraca wartość modułu wyliczającego nie zawiera wszystkich metod wbudowanie danej metody.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-121">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="8f4d2-122">Może się to zdarzyć, gdy dla jednego lub więcej bezpośrednich lub pośrednich zależności inliners moduł nie został jeszcze załadowany.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-122">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="8f4d2-123">Jeśli program profilujący musi dokładnych danych, należy ponowić próbę później podczas więcej są załadowane moduły, najlepiej podczas każdego ładowania modułu.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-123">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="8f4d2-124">`EnumNgenModuleMethodsInliningThisMethod` Metoda może służyć do obejścia ograniczeń na wbudowanie dla ReJIT.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-124">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="8f4d2-125">ReJIT informuje program profilujący Zmień implementację metody, a następnie utwórz nowy kod go na bieżąco.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-125">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="8f4d2-126">Na przykład można zmienić `Simple.Add` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8f4d2-126">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="8f4d2-127">Jednak ponieważ `Fancy.AddTwice` ma już śródwierszowych `Simple.Add`, będzie nadal mają takie samo zachowanie, tak jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-127">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="8f4d2-128">W celu obejścia tego ograniczenia, obiekt wywołujący ma wyszukiwać wszystkie metody we wszystkich modułach tym miejscu `Simple.Add` i użyj `ICorProfilerInfo5::RequestRejit` na każdym z tych metod.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-128">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="8f4d2-129">Gdy metody są ponownie skompilowany, muszą nowe zachowanie `Simple.Add` zamiast stare zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8f4d2-129">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="8f4d2-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f4d2-130">Requirements</span></span>

<span data-ttu-id="8f4d2-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f4d2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="8f4d2-132">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8f4d2-132">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="8f4d2-133">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f4d2-133">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="8f4d2-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f4d2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8f4d2-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f4d2-135">See also</span></span>

- [<span data-ttu-id="8f4d2-136">ICorProfilerInfo6, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f4d2-136">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)