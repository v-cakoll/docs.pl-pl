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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7421e0d0e1a1f0e1a5fbe0d0eb7d5a0ab2a48b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796423"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="e8e8c-102">IIdentityAuthority — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e8e8c-102">IIdentityAuthority Interface</span></span>

<span data-ttu-id="e8e8c-103">Zarządza kluczami tożsamości dla obiektów kodu.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-103">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="e8e8c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e8e8c-104">Methods</span></span>

|<span data-ttu-id="e8e8c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e8e8c-105">Method</span></span>|<span data-ttu-id="e8e8c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e8e8c-106">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="e8e8c-107">Pobiera wartość wskazującą, czy dwa określone wystąpienia [IDefinitionIdentity —](idefinitionidentity-interface.md) są równe.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="e8e8c-108">Pobiera wartość wskazującą, czy dwa określone wystąpienia [IReferenceIdentity —](ireferenceidentity-interface.md) są równe.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-108">Gets a value that indicates whether the two specified [IReferenceIdentity](ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="e8e8c-109">Pobiera wartość wskazującą, czy dwie określone reprezentacje tożsamości definicji ciągu są równe.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="e8e8c-110">Pobiera wartość wskazującą, czy dwie określone reprezentacje tożsamości odwołania do ciągu są równe.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="e8e8c-111">Pobiera wskaźnik do nowego `IDefinitionIdentity` wystąpienia, które reprezentuje obiekt kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="e8e8c-112">Pobiera wskaźnik do nowego `IReferenceIdentity` wystąpienia, które reprezentuje obiekt kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="e8e8c-113">Pobiera sformatowaną wersję ciągu określonego `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="e8e8c-114">Wypełnia określony bufor znaków wide z określoną `IDefinitionIdentity`wersją ciągu.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="e8e8c-115">Pobiera wartość wskazującą, czy określone `IDefinitionIdentity` i `IReferenceIdentity` wystąpienia odwołują się do tego samego obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="e8e8c-116">Pobiera wartość wskazującą, czy określone ciągi odwołują się do tego samego obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="e8e8c-117">Pobiera wskaźnik do nowo utworzonego klucza ciągu dla określonego `IDefinitionIdentity`elementu.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="e8e8c-118">Pobiera wskaźnik do nowo utworzonego klucza ciągu dla określonego `IReferenceIdentity`elementu.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="e8e8c-119">Pobiera wartość skrótu dla określonego `IDefinitionIdentity`elementu.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="e8e8c-120">Pobiera wartość skrótu dla określonego `IReferenceIdentity`elementu.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-120">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="e8e8c-121">Pobiera sformatowaną wersję ciągu określonego `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="e8e8c-122">Wypełnia określony bufor znaków wide z określoną `IReferenceIdentity`wersją ciągu.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="e8e8c-123">Pobiera wskaźnik interfejsu do `IDefinitionIdentity` wystąpienia wygenerowanego na podstawie określonego sformatowanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="e8e8c-124">Pobiera wskaźnik interfejsu do `IReferenceIdentity` wystąpienia wygenerowanego na podstawie określonego sformatowanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="e8e8c-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="e8e8c-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8e8c-125">Requirements</span></span>

<span data-ttu-id="e8e8c-126">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8e8c-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="e8e8c-127">**Nagłówki** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="e8e8c-127">**Header:** Isolation.h</span></span>

<span data-ttu-id="e8e8c-128">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8e8c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e8e8c-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8e8c-129">See also</span></span>

- [<span data-ttu-id="e8e8c-130">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="e8e8c-130">Fusion Interfaces</span></span>](fusion-interfaces.md)
