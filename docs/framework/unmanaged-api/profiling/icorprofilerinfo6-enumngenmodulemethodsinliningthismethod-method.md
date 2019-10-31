---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, metoda
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 103fe1b6845edfe0a364db979557db63511f6ee3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130386"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="b2a3e-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="b2a3e-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="b2a3e-103">Zwraca moduł wyliczający do wszystkich metod, które są zdefiniowane w danym module NGen i wbudowana daną metodę.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-103">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2a3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2a3e-104">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="b2a3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2a3e-105">Parameters</span></span>

`inlinersModuleId`\
<span data-ttu-id="b2a3e-106">podczas Identyfikator modułu NGen.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-106">[in] The identifier of an NGen module.</span></span>

`inlineeModuleId`\
<span data-ttu-id="b2a3e-107">podczas Identyfikator modułu, który definiuje `inlineeMethodId`.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-107">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="b2a3e-108">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-108">See the Remarks section for more information.</span></span>

`inlineeMethodId`\
<span data-ttu-id="b2a3e-109">podczas Identyfikator metody wbudowanej.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-109">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="b2a3e-110">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-110">See the Remarks section for more information.</span></span>

`incompleteData`\
<span data-ttu-id="b2a3e-111">określoną Flaga wskazująca, czy `ppEnum` zawiera wszystkie metody podkreślające daną metodę.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-111">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="b2a3e-112">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-112">See the Remarks section for more information.</span></span>

`ppEnum`\
<span data-ttu-id="b2a3e-113">określoną Wskaźnik do adresu modułu wyliczającego</span><span class="sxs-lookup"><span data-stu-id="b2a3e-113">[out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="b2a3e-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2a3e-114">Remarks</span></span>

<span data-ttu-id="b2a3e-115">`inlineeModuleId` i `inlineeMethodId` razem tworzą pełny identyfikator dla metody, która może być wbudowana.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-115">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="b2a3e-116">Załóżmy na przykład, że moduł `A` definiuje `Simple.Add`metody:</span><span class="sxs-lookup"><span data-stu-id="b2a3e-116">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="b2a3e-117">i moduł B definiuje `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="b2a3e-117">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="b2a3e-118">Umożliwia również założenie, że `Fancy.AddTwice` rozliczanie wywołania `SimpleAdd`.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-118">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="b2a3e-119">Profiler może użyć tego modułu wyliczającego, aby znaleźć wszystkie metody zdefiniowane w module B, które są wbudowane `Simple.Add`, a wynikiem będzie Wyliczenie `AddTwice`.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-119">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="b2a3e-120">`inlineeModuleId` jest identyfikatorem `A`modułu, a `inlineeMethodId` jest identyfikatorem `Simple.Add(int a, int b)`.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-120">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="b2a3e-121">Jeśli `incompleteData` ma wartość true po powrocie funkcji, moduł wyliczający nie zawiera wszystkich metod, które podkreślają daną metodę.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-121">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="b2a3e-122">Może to być spowodowane tym, że co najmniej jedna bezpośrednia lub pośrednia zależność modułu modułów nie została jeszcze załadowana.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-122">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="b2a3e-123">Jeśli Profiler wymaga dokładnej ilości danych, powinien ponowić próbę później, gdy więcej modułów zostanie załadowanych, najlepiej przy każdym załadowaniu modułu.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-123">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="b2a3e-124">Za pomocą metody `EnumNgenModuleMethodsInliningThisMethod` można obejść ograniczenia dotyczące deReJIT.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-124">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="b2a3e-125">ReJIT umożliwia usłudze Profiler zmianę implementacji metody, a następnie utworzenie nowego kodu na bieżąco.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-125">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="b2a3e-126">Można na przykład zmienić `Simple.Add` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b2a3e-126">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="b2a3e-127">Ponieważ jednak `Fancy.AddTwice` ma już wbudowaną `Simple.Add`, nadal ma takie samo zachowanie jak wcześniej.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-127">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="b2a3e-128">Aby obejść to ograniczenie, obiekt wywołujący musi wyszukać wszystkie metody we wszystkich modułach, które są wbudowane `Simple.Add` i używają `ICorProfilerInfo5::RequestRejit` dla każdej z tych metod.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-128">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="b2a3e-129">Po ponownym skompilowaniu metod będą one miały nowe zachowanie `Simple.Add` zamiast starego zachowania.</span><span class="sxs-lookup"><span data-stu-id="b2a3e-129">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="b2a3e-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2a3e-130">Requirements</span></span>

<span data-ttu-id="b2a3e-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2a3e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="b2a3e-132">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b2a3e-132">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="b2a3e-133">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b2a3e-133">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b2a3e-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2a3e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b2a3e-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2a3e-135">See also</span></span>

- [<span data-ttu-id="b2a3e-136">ICorProfilerInfo6, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2a3e-136">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)
