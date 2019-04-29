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
ms.openlocfilehash: 263dc0f9d686440aaa23e359c26db1b4d3d09b1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609103"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="171a4-102">IIdentityAuthority — Interfejs</span><span class="sxs-lookup"><span data-stu-id="171a4-102">IIdentityAuthority Interface</span></span>

<span data-ttu-id="171a4-103">Zarządza kluczy tożsamości dla obiektów kodu.</span><span class="sxs-lookup"><span data-stu-id="171a4-103">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="171a4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="171a4-104">Methods</span></span>

|<span data-ttu-id="171a4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="171a4-105">Method</span></span>|<span data-ttu-id="171a4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="171a4-106">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="171a4-107">Pobiera wartość wskazującą, czy dwa określone [idefinitionidentity —](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) wystąpień są takie same.</span><span class="sxs-lookup"><span data-stu-id="171a4-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="171a4-108">Pobiera wartość wskazującą, czy dwa określone [ireferenceidentity —](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) wystąpień są takie same.</span><span class="sxs-lookup"><span data-stu-id="171a4-108">Gets a value that indicates whether the two specified [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="171a4-109">Pobiera wartość wskazującą, czy dwa oświadczenia tożsamości definicji określonego ciągu są takie same.</span><span class="sxs-lookup"><span data-stu-id="171a4-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="171a4-110">Pobiera wartość wskazującą, czy dwa oświadczenia tożsamości odwołanie do określonego ciągu są takie same.</span><span class="sxs-lookup"><span data-stu-id="171a4-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="171a4-111">Pobiera wskaźnik do nowego `IDefinitionIdentity` wystąpienia, który reprezentuje obiekt kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="171a4-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="171a4-112">Pobiera wskaźnik do nowego `IReferenceIdentity` wystąpienia, który reprezentuje obiekt kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="171a4-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="171a4-113">Pobiera wersję sformatowany ciąg, z określonym `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="171a4-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="171a4-114">Wypełnia buforu określonego znaku dwubajtowego ciągu wersję określonego `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="171a4-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="171a4-115">Pobiera wartość wskazującą, czy określony `IDefinitionIdentity` i `IReferenceIdentity` wystąpień odnoszą się do tego samego obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="171a4-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="171a4-116">Pobiera wartość wskazującą, czy określone ciągi odnoszą się do tego samego obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="171a4-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="171a4-117">Pobiera wskaźnik do ciągu nowo utworzony klucz dla określonego `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="171a4-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="171a4-118">Pobiera wskaźnik do ciągu nowo utworzony klucz dla określonego `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="171a4-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="171a4-119">Pobiera wartość skrótu dla określonego `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="171a4-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="171a4-120">Pobiera wartość skrótu dla określonego `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="171a4-120">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="171a4-121">Pobiera wersję sformatowany ciąg, z określonym `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="171a4-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="171a4-122">Wypełnia buforu określonego znaku dwubajtowego ciągu wersję określonego `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="171a4-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="171a4-123">Pobiera wskaźnik interfejsu do `IDefinitionIdentity` ciąg w formacie wygenerowany na podstawie określonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="171a4-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="171a4-124">Pobiera wskaźnik interfejsu do `IReferenceIdentity` ciąg w formacie wygenerowany na podstawie określonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="171a4-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="171a4-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="171a4-125">Requirements</span></span>

<span data-ttu-id="171a4-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="171a4-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="171a4-127">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="171a4-127">**Header:** Isolation.h</span></span>

<span data-ttu-id="171a4-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="171a4-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="171a4-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="171a4-129">See also</span></span>

- [<span data-ttu-id="171a4-130">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="171a4-130">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
