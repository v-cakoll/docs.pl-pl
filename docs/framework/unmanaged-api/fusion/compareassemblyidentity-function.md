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
ms.openlocfilehash: b52d3af38bd09ce5864c25d27e148dbd7f4639b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795449"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="f86cf-102">CompareAssemblyIdentity — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f86cf-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="f86cf-103">Porównuje dwie tożsamości zestawów, aby określić, czy są one równoważne.</span><span class="sxs-lookup"><span data-stu-id="f86cf-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f86cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f86cf-104">Syntax</span></span>  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f86cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f86cf-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="f86cf-106">podczas Tożsamość tekstowa pierwszego zestawu w porównaniu.</span><span class="sxs-lookup"><span data-stu-id="f86cf-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="f86cf-107">podczas Flaga logiczna wskazująca, że nie jest to określone przez `pwzAssemblyIdentity1`użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f86cf-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="f86cf-108">podczas Tożsamość tekstowa drugiego zestawu w porównaniu.</span><span class="sxs-lookup"><span data-stu-id="f86cf-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="f86cf-109">podczas Flaga logiczna wskazująca, że nie jest to określone przez `pwzAssemblyIdentity2`użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f86cf-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="f86cf-110">określoną Flaga logiczna wskazująca, czy dwa zestawy są równoważne.</span><span class="sxs-lookup"><span data-stu-id="f86cf-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="f86cf-111">określoną Wyliczenie [AssemblyComparisonResult —](assemblycomparisonresult-enumeration.md) , które zawiera szczegółowe informacje na temat porównania.</span><span class="sxs-lookup"><span data-stu-id="f86cf-111">[out] An [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f86cf-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f86cf-112">Return Value</span></span>  
 <span data-ttu-id="f86cf-113">`pfEquivalent`Zwraca wartość logiczną wskazującą, czy dwa zestawy są równoważne.</span><span class="sxs-lookup"><span data-stu-id="f86cf-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="f86cf-114">`pResult`zwraca jedną z `AssemblyComparisonResult` wartości, aby bardziej szczegółowo przyczynić się do `pfEquivalent`wartości.</span><span class="sxs-lookup"><span data-stu-id="f86cf-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f86cf-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f86cf-115">Remarks</span></span>  
 <span data-ttu-id="f86cf-116">`CompareAssemblyIdentity`sprawdza, `pwzAssemblyIdentity1` czy `pwzAssemblyIdentity2` i są równoważne.</span><span class="sxs-lookup"><span data-stu-id="f86cf-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="f86cf-117">`pfEquivalent`jest ustawiony na `true` co najmniej jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="f86cf-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
- <span data-ttu-id="f86cf-118">Dwie tożsamości zestawów są równoważne.</span><span class="sxs-lookup"><span data-stu-id="f86cf-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="f86cf-119">W przypadku zestawów o silnych nazwach wartość równoważności wymaga, aby nazwa zestawu, wersja, token klucza publicznego i kultura była taka sama.</span><span class="sxs-lookup"><span data-stu-id="f86cf-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="f86cf-120">W przypadku po prostu nazwane zestawy równoważności wymagają dopasowania w nazwie zestawu i kulturze.</span><span class="sxs-lookup"><span data-stu-id="f86cf-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
- <span data-ttu-id="f86cf-121">Obie tożsamości zestawów odnoszą się do zestawów, które są uruchamiane na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f86cf-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="f86cf-122">Ten warunek zwraca `true` , nawet jeśli numery wersji zestawu nie są zgodne.</span><span class="sxs-lookup"><span data-stu-id="f86cf-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
- <span data-ttu-id="f86cf-123">Dwa zestawy nie są zestawami zarządzanymi, `fUnified1` ale `fUnified2` lub zostały ustawione `true`na.</span><span class="sxs-lookup"><span data-stu-id="f86cf-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="f86cf-124">`fUnified` Flaga wskazuje, że wszystkie numery wersji do numeru wersji silnie nazwanego zestawu są uważane za równoważne zestawowi o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f86cf-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="f86cf-125">Na przykład, jeśli wartość `pwzAssemblyIndentity1` jest równa "". Assembly, Version = 3.0.0.0, Culture = neutral, PublicKeyToken =... "i `fUnified1` wartość is `true`, oznacza to, że wszystkie wersje zestawu elementów z wersji 0.0.0.0 do 3.0.0.0 powinny być traktowane jako równoważne.</span><span class="sxs-lookup"><span data-stu-id="f86cf-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="f86cf-126">W takim `pwzAssemblyIndentity2` przypadku, jeśli odwołuje się do tego samego `pwzAssemblyIndentity1`zestawu, z tą różnicą, że ma niższy numer `pfEquivalent` wersji, jest `true`ustawiony na.</span><span class="sxs-lookup"><span data-stu-id="f86cf-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="f86cf-127">Jeśli `pwzAssemblyIdentity2` odwołuje się do wyższego numeru `pfEquivalent` wersji, jest `true` ustawiana tylko wtedy, `fUnified2` gdy `true`wartość jest.</span><span class="sxs-lookup"><span data-stu-id="f86cf-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="f86cf-128">`pResult` Parametr zawiera szczegółowe informacje o tym, dlaczego te dwa zestawy są uważane za równoważne lub nierównoważne.</span><span class="sxs-lookup"><span data-stu-id="f86cf-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="f86cf-129">Aby uzyskać więcej informacji, zobacz [AssemblyComparisonResult — Enumeration](assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f86cf-129">For more information, see [AssemblyComparisonResult Enumeration](assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f86cf-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f86cf-130">Requirements</span></span>  
 <span data-ttu-id="f86cf-131">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f86cf-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f86cf-132">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f86cf-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f86cf-133">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f86cf-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f86cf-134">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f86cf-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f86cf-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f86cf-135">See also</span></span>

- [<span data-ttu-id="f86cf-136">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="f86cf-136">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="f86cf-137">AssemblyComparisonResult, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f86cf-137">AssemblyComparisonResult Enumeration</span></span>](assemblycomparisonresult-enumeration.md)
