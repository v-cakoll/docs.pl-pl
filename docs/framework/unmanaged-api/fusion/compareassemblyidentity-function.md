---
title: CompareAssemblyIdentity — Funkcja
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 652000367c19572f73296c704047830ce1c74574
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231048"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="442c4-102">CompareAssemblyIdentity — Funkcja</span><span class="sxs-lookup"><span data-stu-id="442c4-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="442c4-103">Porównuje dwa tożsamości zestawu do ustalenia, czy są równoważne.</span><span class="sxs-lookup"><span data-stu-id="442c4-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="442c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="442c4-104">Syntax</span></span>  
  
```  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="442c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="442c4-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="442c4-106">[in] Tożsamość tekstową pierwszego zestawu do porównania.</span><span class="sxs-lookup"><span data-stu-id="442c4-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="442c4-107">[in] Flagę logiczną, wskazującą, określonych przez użytkownika ujednolicenie dla `pwzAssemblyIdentity1`.</span><span class="sxs-lookup"><span data-stu-id="442c4-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="442c4-108">[in] Tożsamość tekstową drugiego zestawu do porównania.</span><span class="sxs-lookup"><span data-stu-id="442c4-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="442c4-109">[in] Flagę logiczną, wskazującą, określonych przez użytkownika ujednolicenie dla `pwzAssemblyIdentity2`.</span><span class="sxs-lookup"><span data-stu-id="442c4-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="442c4-110">[out] Flaga wartości logicznej, która wskazuje, czy dwa zestawy są równoważne.</span><span class="sxs-lookup"><span data-stu-id="442c4-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="442c4-111">[out] [Assemblycomparisonresult —](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) wyliczenie, które zawiera szczegółowe informacje na temat porównania.</span><span class="sxs-lookup"><span data-stu-id="442c4-111">[out] An [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="442c4-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="442c4-112">Return Value</span></span>  
 <span data-ttu-id="442c4-113">`pfEquivalent` Zwraca wartość logiczną wskazującą, czy dwa zestawy są równoważne.</span><span class="sxs-lookup"><span data-stu-id="442c4-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="442c4-114">`pResult` Zwraca jedną z `AssemblyComparisonResult` wartości, aby zapewnić bardziej szczegółowe Przyczyna wartość `pfEquivalent`.</span><span class="sxs-lookup"><span data-stu-id="442c4-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="442c4-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="442c4-115">Remarks</span></span>  
 <span data-ttu-id="442c4-116">`CompareAssemblyIdentity` sprawdza, czy `pwzAssemblyIdentity1` i `pwzAssemblyIdentity2` są równoważne.</span><span class="sxs-lookup"><span data-stu-id="442c4-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="442c4-117">`pfEquivalent` ustawiono `true` w jednej lub więcej z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="442c4-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
-   <span data-ttu-id="442c4-118">Tożsamości dwóch zestawów są równoważne.</span><span class="sxs-lookup"><span data-stu-id="442c4-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="442c4-119">Dla zestawów o silnej nazwie równoważności wymaga nazwy zestawu, wersji, token klucza publicznego i kultury być identyczne.</span><span class="sxs-lookup"><span data-stu-id="442c4-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="442c4-120">Po prostu nazwane zestawy równoważności wymaga dopasowania nazwy zestawu i kultury.</span><span class="sxs-lookup"><span data-stu-id="442c4-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
-   <span data-ttu-id="442c4-121">Zarówno tożsamości zestawu odnoszą się do zestawów, korzystających z programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="442c4-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="442c4-122">Zwraca ten warunek `true` nawet wtedy, gdy numery wersji zestawu nie są zgodne.</span><span class="sxs-lookup"><span data-stu-id="442c4-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
-   <span data-ttu-id="442c4-123">Dwa zestawy nie są zarządzane zestawy, ale `fUnified1` lub `fUnified2` została ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="442c4-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="442c4-124">`fUnified` Flaga wskazuje, że wszystkie numery wersji do numeru wersji zestawu o silnej nazwie są uważane za równoważne do zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="442c4-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="442c4-125">Na przykład jeśli wartość `pwzAssemblyIndentity1` jest "MyAssembly, wersji = 3.0.0.0, culture = neutral, publicKeyToken =..." i wartość `fUnified1` jest `true`, oznacza to, że wszystkie wersje MyAssembly z wersji 0.0.0.0 do 3.0.0.0 powinny być traktowane jako równoważne.</span><span class="sxs-lookup"><span data-stu-id="442c4-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="442c4-126">W takim przypadku jeśli `pwzAssemblyIndentity2` odwołuje się do tego samego zestawu co `pwzAssemblyIndentity1`, z tą różnicą, że ma niższy numer wersji `pfEquivalent` jest równa `true`.</span><span class="sxs-lookup"><span data-stu-id="442c4-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="442c4-127">Jeśli `pwzAssemblyIdentity2` odwołuje się do wyższy numer wersji `pfEquivalent` ustawiono `true` tylko wtedy, gdy wartość `fUnified2` jest `true`.</span><span class="sxs-lookup"><span data-stu-id="442c4-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="442c4-128">`pResult` Parametr zawiera szczegółowe informacje na temat przyczyny dwa zestawy są uważane za równoważne lub nie jest równorzędny.</span><span class="sxs-lookup"><span data-stu-id="442c4-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="442c4-129">Aby uzyskać więcej informacji, zobacz [assemblycomparisonresult — wyliczenie](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="442c4-129">For more information, see [AssemblyComparisonResult Enumeration](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="442c4-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="442c4-130">Requirements</span></span>  
 <span data-ttu-id="442c4-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="442c4-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="442c4-132">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="442c4-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="442c4-133">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="442c4-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="442c4-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="442c4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="442c4-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="442c4-135">See also</span></span>

- [<span data-ttu-id="442c4-136">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="442c4-136">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="442c4-137">AssemblyComparisonResult, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="442c4-137">AssemblyComparisonResult Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
