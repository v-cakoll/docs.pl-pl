---
title: IAppIdAuthority — Interfejs
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91ab2f71e7fb74f8e0e517b566d46d61c316ebe2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796836"
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="b0df4-102">IAppIdAuthority — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b0df4-102">IAppIdAuthority Interface</span></span>
<span data-ttu-id="b0df4-103">Dostarcza metody, które generują i porównują klucze dla tożsamości i odwołań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b0df4-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0df4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b0df4-104">Methods</span></span>  
  
|<span data-ttu-id="b0df4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b0df4-105">Method</span></span>|<span data-ttu-id="b0df4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b0df4-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="b0df4-107">Pobiera wartość wskazującą, czy dwa określone wystąpienia [IDefinitionAppId —](idefinitionappid-interface.md) są równe.</span><span class="sxs-lookup"><span data-stu-id="b0df4-107">Gets a value that indicates whether the two specified [IDefinitionAppId](idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="b0df4-108">Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION, aby zignorować odpowiednie informacje o wersji.</span><span class="sxs-lookup"><span data-stu-id="b0df4-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="b0df4-109">Pobiera wartość wskazującą, czy dwa określone wystąpienia [IReferenceAppId —](ireferenceappid-interface.md) są równe.</span><span class="sxs-lookup"><span data-stu-id="b0df4-109">Gets a value that indicates whether the two specified [IReferenceAppId](ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="b0df4-110">Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION, aby zignorować odpowiednie informacje o wersji.</span><span class="sxs-lookup"><span data-stu-id="b0df4-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="b0df4-111">Pobiera wartość wskazującą, czy dwa określone definicje ciągów są równe.</span><span class="sxs-lookup"><span data-stu-id="b0df4-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="b0df4-112">Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION, aby zignorować odpowiednie informacje o wersji.</span><span class="sxs-lookup"><span data-stu-id="b0df4-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="b0df4-113">Pobiera wartość wskazującą, czy dwa określone odwołania do ciągu są równe.</span><span class="sxs-lookup"><span data-stu-id="b0df4-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="b0df4-114">Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION, aby zignorować odpowiednie informacje o wersji.</span><span class="sxs-lookup"><span data-stu-id="b0df4-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="b0df4-115">Pobiera wskaźnik interfejsu do nowo wygenerowanego `IDefinitionAppId` wystąpienia, które reprezentuje zestaw w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="b0df4-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="b0df4-116">Pobiera wskaźnik interfejsu do nowo utworzonego `IReferenceAppId` , który reprezentuje zestaw w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="b0df4-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="b0df4-117">Pobiera wersję ciągu określonego `IDefinitionAppId`przy użyciu określonych wartości flagi.</span><span class="sxs-lookup"><span data-stu-id="b0df4-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="b0df4-118">Pobiera wartość wskazującą, czy określony `IDefinitionAppId` i `IReferenceAppId` reprezentuje ten sam zestaw.</span><span class="sxs-lookup"><span data-stu-id="b0df4-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="b0df4-119">Pobiera wartość wskazującą, czy określony ciąg definicji i ciąg odwołania reprezentują ten sam zestaw.</span><span class="sxs-lookup"><span data-stu-id="b0df4-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="b0df4-120">Pobiera klucz ciągu, który reprezentuje określone `IDefinitionAppId` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="b0df4-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="b0df4-121">Pobiera klucz ciągu, który reprezentuje określone `IReferenceAppId` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="b0df4-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="b0df4-122">Pobiera klucz skrótu dla określonego `IDefinitionAppId` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b0df4-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="b0df4-123">Pobiera klucz skrótu dla określonego `IReferenceAppId` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b0df4-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="b0df4-124">Pobiera wersję ciągu określonego `IReferenceAppId`przy użyciu określonych wartości flagi.</span><span class="sxs-lookup"><span data-stu-id="b0df4-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="b0df4-125">Pobiera wskaźnik interfejsu do `IDefinitionAppId` wystąpienia, które reprezentuje zestaw, do którego odwołuje się określony klucz ciągu.</span><span class="sxs-lookup"><span data-stu-id="b0df4-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="b0df4-126">Pobiera wskaźnik interfejsu do `IReferenceAppId` wystąpienia, które reprezentuje zestaw, do którego odwołuje się określony klucz ciągu.</span><span class="sxs-lookup"><span data-stu-id="b0df4-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0df4-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0df4-127">Requirements</span></span>  
 <span data-ttu-id="b0df4-128">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0df4-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0df4-129">**Nagłówki** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="b0df4-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b0df4-130">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0df4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0df4-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0df4-131">See also</span></span>

- [<span data-ttu-id="b0df4-132">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="b0df4-132">Fusion Interfaces</span></span>](fusion-interfaces.md)
