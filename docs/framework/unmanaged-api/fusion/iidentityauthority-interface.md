---
title: IIdentityAuthority — Interfejs
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
ms.openlocfilehash: 3e2d2335e37ced9139ea44092f10b19566894681
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127096"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="ee514-102">IIdentityAuthority — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ee514-102">IIdentityAuthority Interface</span></span>

<span data-ttu-id="ee514-103">Zarządza kluczami tożsamości dla obiektów kodu.</span><span class="sxs-lookup"><span data-stu-id="ee514-103">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="ee514-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ee514-104">Methods</span></span>

|<span data-ttu-id="ee514-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ee514-105">Method</span></span>|<span data-ttu-id="ee514-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ee514-106">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="ee514-107">Pobiera wartość wskazującą, czy dwa określone wystąpienia [IDefinitionIdentity —](idefinitionidentity-interface.md) są równe.</span><span class="sxs-lookup"><span data-stu-id="ee514-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="ee514-108">Pobiera wartość wskazującą, czy dwa określone wystąpienia [IReferenceIdentity —](ireferenceidentity-interface.md) są równe.</span><span class="sxs-lookup"><span data-stu-id="ee514-108">Gets a value that indicates whether the two specified [IReferenceIdentity](ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="ee514-109">Pobiera wartość wskazującą, czy dwie określone reprezentacje tożsamości definicji ciągu są równe.</span><span class="sxs-lookup"><span data-stu-id="ee514-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="ee514-110">Pobiera wartość wskazującą, czy dwie określone reprezentacje tożsamości odwołania do ciągu są równe.</span><span class="sxs-lookup"><span data-stu-id="ee514-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="ee514-111">Pobiera wskaźnik do nowego wystąpienia `IDefinitionIdentity`, które reprezentuje obiekt kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="ee514-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="ee514-112">Pobiera wskaźnik do nowego wystąpienia `IReferenceIdentity`, które reprezentuje obiekt kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="ee514-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="ee514-113">Pobiera sformatowaną wersję ciągu określonego `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="ee514-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="ee514-114">Wypełnia określony bufor szerokich znaków za pomocą wersji ciągu określonego `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="ee514-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="ee514-115">Pobiera wartość wskazującą, czy określone wystąpienia `IDefinitionIdentity` i `IReferenceIdentity` odwołują się do tego samego obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="ee514-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="ee514-116">Pobiera wartość wskazującą, czy określone ciągi odwołują się do tego samego obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="ee514-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="ee514-117">Pobiera wskaźnik do nowo utworzonego klucza ciągu dla określonego `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="ee514-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="ee514-118">Pobiera wskaźnik do nowo utworzonego klucza ciągu dla określonego `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="ee514-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="ee514-119">Pobiera wartość skrótu dla określonego `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="ee514-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="ee514-120">Pobiera wartość skrótu dla określonego `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="ee514-120">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="ee514-121">Pobiera sformatowaną wersję ciągu określonego `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="ee514-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="ee514-122">Wypełnia określony bufor szerokich znaków za pomocą wersji ciągu określonego `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="ee514-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="ee514-123">Pobiera wskaźnik interfejsu do wystąpienia `IDefinitionIdentity` wygenerowanego na podstawie określonego sformatowanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="ee514-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="ee514-124">Pobiera wskaźnik interfejsu do wystąpienia `IReferenceIdentity` wygenerowanego na podstawie określonego sformatowanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="ee514-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="ee514-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee514-125">Requirements</span></span>

<span data-ttu-id="ee514-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee514-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ee514-127">**Nagłówek:** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="ee514-127">**Header:** Isolation.h</span></span>

<span data-ttu-id="ee514-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee514-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ee514-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee514-129">See also</span></span>

- [<span data-ttu-id="ee514-130">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="ee514-130">Fusion Interfaces</span></span>](fusion-interfaces.md)
