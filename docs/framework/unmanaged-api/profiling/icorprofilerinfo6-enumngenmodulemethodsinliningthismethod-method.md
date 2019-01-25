---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07b1c905e587708336ce690bbf3d187b2d21e5b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568156"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="d0ee1-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span><span class="sxs-lookup"><span data-stu-id="d0ee1-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>
<span data-ttu-id="d0ee1-103">[Obsługiwane w programie .NET Framework 4.6 lub nowszy]</span><span class="sxs-lookup"><span data-stu-id="d0ee1-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="d0ee1-104">Zwraca moduł wyliczający do metod, które są zdefiniowane w danym module NGen i wbudowane danej metody.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-104">Returns an enumerator to all the methods that          are defined in  a given NGen module and          inline a given method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0ee1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0ee1-105">Syntax</span></span>  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0ee1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0ee1-106">Parameters</span></span>  
 `inlinersModuleId`  
 <span data-ttu-id="d0ee1-107">[in] Identyfikator modułu NGen.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-107">[in] The identifier of an NGen module.</span></span>  
  
 `inlineeModuleId`  
 <span data-ttu-id="d0ee1-108">[in] Identyfikator modułu, który definiuje `inlineeMethodId`.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-108">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="d0ee1-109">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-109">See the Remarks section for more information.</span></span>  
  
 `inlineeMethodId`  
 <span data-ttu-id="d0ee1-110">[in] Identyfikator śródwierszowych metody.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-110">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="d0ee1-111">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-111">See the Remarks section for more information.</span></span>  
  
 `incompleteData`  
 <span data-ttu-id="d0ee1-112">[out] Flaga, która wskazuje, czy `ppEnum` zawiera wszystkie metody wbudowanie danej metody.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-112">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="d0ee1-113">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-113">See the Remarks section for more information.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="d0ee1-114">[out] Wskaźnik na adres modułu wyliczającego</span><span class="sxs-lookup"><span data-stu-id="d0ee1-114">[out] A pointer to the address of an enumerator</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0ee1-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d0ee1-115">Remarks</span></span>  
 <span data-ttu-id="d0ee1-116">`inlineeModuleId` i `inlineeMethodId` razem tworzą pełny identyfikator metodę, która może być śródwierszowa.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="d0ee1-117">Załóżmy na przykład moduł `A` definiuje metodę `Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="d0ee1-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 <span data-ttu-id="d0ee1-118">Moduł Bdefines i `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="d0ee1-118">and module Bdefines `Fancy.AddTwice`:</span></span>  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 <span data-ttu-id="d0ee1-119">Umożliwia także przyjęto założenie, że `Fancy.AddTwice` inlines wywołanie do `SimpleAdd`.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="d0ee1-120">Program profilujący można użyć tego modułu wyliczającego można znaleźć wszystkie metody zdefiniowanego w module B, której wbudowane `Simple.Add`, i wynik będzie wyliczanie `AddTwice`.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="d0ee1-121">`inlineeModuleId` Identyfikator modułu `A`, i `inlineeeMethodId` jest identyfikatorem `Simple.Add(int a, int b)`.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-121">`inlineeModuleId` is the identifier of module `A`,   and `inlineeeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>  
  
 <span data-ttu-id="d0ee1-122">Jeśli `incompleteData` ma wartość true po funkcji zwraca wartość modułu wyliczającego nie zawiera wszystkich metod wbudowanie danej metody.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="d0ee1-123">Może się to zdarzyć, gdy dla jednego lub więcej bezpośrednich lub pośrednich zależności inliners moduł nie został jeszcze załadowany.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="d0ee1-124">Jeśli program profilujący musi dokładnych danych, należy ponowić próbę później podczas więcej są załadowane moduły, najlepiej podczas każdego ładowania modułu.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>  
  
 <span data-ttu-id="d0ee1-125">`EnumNgenModuleMethodsInliningThisMethod` Metoda może służyć do obejścia ograniczeń na wbudowanie dla ReJIT.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="d0ee1-126">ReJIT informuje program profilujący Zmień implementację metody, a następnie utwórz nowy kod go na bieżąco.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="d0ee1-127">Na przykład można zmienić `Simple.Add` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d0ee1-127">For example, we could change `Simple.Add` as follows:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 <span data-ttu-id="d0ee1-128">Jednak ponieważ `Fancy.AddTwice` ma już śródwierszowych `Simple.Add`, będzie nadal mają takie samo zachowanie, tak jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="d0ee1-129">W celu obejścia tego ograniczenia, obiekt wywołujący ma wyszukiwać wszystkie metody we wszystkich modułach tym miejscu `Simple.Add` i użyj `ICorProfilerInfo5::RequestRejit` na każdym z tych metod.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="d0ee1-130">Gdy metody są ponownie skompilowany, muszą nowe zachowanie `Simple.Add` zamiast stare zachowanie.</span><span class="sxs-lookup"><span data-stu-id="d0ee1-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0ee1-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0ee1-131">Requirements</span></span>  
 <span data-ttu-id="d0ee1-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0ee1-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0ee1-133">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d0ee1-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d0ee1-134">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0ee1-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0ee1-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0ee1-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ee1-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0ee1-136">See also</span></span>
- [<span data-ttu-id="d0ee1-137">ICorProfilerInfo6, interfejs</span><span class="sxs-lookup"><span data-stu-id="d0ee1-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
