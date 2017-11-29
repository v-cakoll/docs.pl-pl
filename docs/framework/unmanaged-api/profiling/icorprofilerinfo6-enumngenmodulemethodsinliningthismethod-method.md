---
title: "ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6cf0bccebbfe5620ef329cc8c6f72582a7afe85a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="62080-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod — metoda</span><span class="sxs-lookup"><span data-stu-id="62080-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>
<span data-ttu-id="62080-103">[Obsługiwane w programie .NET Framework 4.6 i nowszymi wersjami]</span><span class="sxs-lookup"><span data-stu-id="62080-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="62080-104">Zwraca moduł wyliczający wszystkie metody, które są zdefiniowane w podanym module NGen i wbudowanego danej metody.</span><span class="sxs-lookup"><span data-stu-id="62080-104">Returns an enumerator to all the methods that          are defined in  a given NGen module and          inline a given method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62080-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="62080-105">Syntax</span></span>  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62080-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="62080-106">Parameters</span></span>  
 `inlinersModuleId`  
 <span data-ttu-id="62080-107">[in] Identyfikator modułu NGen.</span><span class="sxs-lookup"><span data-stu-id="62080-107">[in] The identifier of an NGen module.</span></span>  
  
 `inlineeModuleId`  
 <span data-ttu-id="62080-108">[in] Identyfikator modułu, który definiuje `inlineeMethodId`.</span><span class="sxs-lookup"><span data-stu-id="62080-108">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="62080-109">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="62080-109">See the Remarks section for more information.</span></span>  
  
 `inlineeMethodId`  
 <span data-ttu-id="62080-110">[in] Identyfikator metody śródwierszowych.</span><span class="sxs-lookup"><span data-stu-id="62080-110">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="62080-111">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="62080-111">See the Remarks section for more information.</span></span>  
  
 `incompleteData`  
 <span data-ttu-id="62080-112">[out] Flaga, która wskazuje, czy `ppEnum` zawiera wszystkie metody ze śródwierszowaniem danej metody.</span><span class="sxs-lookup"><span data-stu-id="62080-112">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="62080-113">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="62080-113">See the Remarks section for more information.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="62080-114">[out] Wskaźnik do adresów modułu wyliczającego</span><span class="sxs-lookup"><span data-stu-id="62080-114">[out] A pointer to the address of an enumerator</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62080-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62080-115">Remarks</span></span>  
 <span data-ttu-id="62080-116">`inlineeModuleId`i `inlineeMethodId` tworzą pełny identyfikator metody, które mogą być wbudowane.</span><span class="sxs-lookup"><span data-stu-id="62080-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="62080-117">Załóżmy na przykład, moduł `A` definiuje metodę `Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="62080-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 <span data-ttu-id="62080-118">Moduł Bdefines i `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="62080-118">and module Bdefines `Fancy.AddTwice`:</span></span>  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 <span data-ttu-id="62080-119">Umożliwia również założyć, że `Fancy.AddTwice` inlines wywołania do `SimpleAdd`.</span><span class="sxs-lookup"><span data-stu-id="62080-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="62080-120">Profiler można użyć tego modułu wyliczającego można znaleźć wszystkie metody zdefiniowanego w module B, który wbudowanego `Simple.Add`, i czy wyliczania wynik `AddTwice`.</span><span class="sxs-lookup"><span data-stu-id="62080-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="62080-121">`inlineeModuleId`jest to identyfikator modułu `A`, i `inlineeeMethodId` jest identyfikatorem `Simple.Add(int a, int b)`.</span><span class="sxs-lookup"><span data-stu-id="62080-121">`inlineeModuleId` is the identifier of module `A`,   and `inlineeeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>  
  
 <span data-ttu-id="62080-122">Jeśli `incompleteData` ma wartość true po funkcja zwraca moduł wyliczający nie zawiera wszystkich metod ze śródwierszowaniem danej metody.</span><span class="sxs-lookup"><span data-stu-id="62080-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="62080-123">Może się to zdarzyć, gdy dla jednego lub więcej bezpośrednie lub pośrednie zależności inliners modułu nie zostały jeszcze załadowane.</span><span class="sxs-lookup"><span data-stu-id="62080-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="62080-124">Jeśli profilera musi dokładnych danych, jej powinna ponownie później ładowane więcej modułów, najlepiej na każdym załadowanie modułu.</span><span class="sxs-lookup"><span data-stu-id="62080-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>  
  
 <span data-ttu-id="62080-125">`EnumNgenModuleMethodsInliningThisMethod` Metody można użyć w celu obejścia ograniczenia na ze śródwierszowaniem dla ReJIT.</span><span class="sxs-lookup"><span data-stu-id="62080-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="62080-126">ReJIT umożliwia profilera, zmień implementację metody, a następnie utwórz nowy kod dla niego na bieżąco.</span><span class="sxs-lookup"><span data-stu-id="62080-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="62080-127">Na przykład można zmienić `Simple.Add` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="62080-127">For example, we could change `Simple.Add` as follows:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 <span data-ttu-id="62080-128">Jednak ponieważ `Fancy.AddTwice` ma już wbudowanego `Simple.Add`, nadal mają takie samo zachowanie jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="62080-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="62080-129">W celu obejścia tego ograniczenia, wywołujący ma wyszukiwania dla wszystkich metod we wszystkich modułach tym miejscu `Simple.Add` i użyj `ICorProfilerInfo5::RequestRejit` na każdym z tych metod.</span><span class="sxs-lookup"><span data-stu-id="62080-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="62080-130">Gdy metody są skompilowane ponownie, mają też nowe zachowanie `Simple.Add` zamiast poprzednie działanie.</span><span class="sxs-lookup"><span data-stu-id="62080-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62080-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62080-131">Requirements</span></span>  
 <span data-ttu-id="62080-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62080-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62080-133">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="62080-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="62080-134">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62080-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62080-135">**Wersje programu .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62080-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62080-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62080-136">See Also</span></span>  
 [<span data-ttu-id="62080-137">Interfejs ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="62080-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
