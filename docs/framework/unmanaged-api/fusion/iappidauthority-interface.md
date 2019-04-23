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
ms.openlocfilehash: 724ee01e91f1e9f4e34d2262610152a977ed4f53
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206658"
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="8cda7-102">IAppIdAuthority — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8cda7-102">IAppIdAuthority Interface</span></span>
<span data-ttu-id="8cda7-103">Udostępnia metody, generujących i klucze dla tożsamości aplikacji i odwołania do porównania.</span><span class="sxs-lookup"><span data-stu-id="8cda7-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8cda7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8cda7-104">Methods</span></span>  
  
|<span data-ttu-id="8cda7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8cda7-105">Method</span></span>|<span data-ttu-id="8cda7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8cda7-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="8cda7-107">Pobiera wartość wskazującą, czy dwa określone [idefinitionappid —](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) wystąpień są takie same.</span><span class="sxs-lookup"><span data-stu-id="8cda7-107">Gets a value that indicates whether the two specified [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="8cda7-108">Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION ignorowanie informacjami o odpowiedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="8cda7-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="8cda7-109">Pobiera wartość wskazującą, czy dwa określone [ireferenceappid —](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) wystąpień są takie same.</span><span class="sxs-lookup"><span data-stu-id="8cda7-109">Gets a value that indicates whether the two specified [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="8cda7-110">Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION ignorowanie informacjami o odpowiedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="8cda7-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="8cda7-111">Pobiera wartość wskazującą, czy dwie definicje określonego ciągu są takie same.</span><span class="sxs-lookup"><span data-stu-id="8cda7-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="8cda7-112">Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION ignorowanie informacjami o odpowiedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="8cda7-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="8cda7-113">Pobiera wartość wskazującą, czy dwa odwołania określonego ciągu są takie same.</span><span class="sxs-lookup"><span data-stu-id="8cda7-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="8cda7-114">Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION ignorowanie informacjami o odpowiedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="8cda7-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="8cda7-115">Pobiera wskaźnik interfejsu do nowo wygenerowane `IDefinitionAppId` wystąpienia, która reprezentuje zestaw w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="8cda7-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="8cda7-116">Pobiera wskaźnik interfejsu do nowo utworzonego `IReferenceAppId` reprezentujący zestaw w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="8cda7-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="8cda7-117">Pobiera wersję ciągu określonego `IDefinitionAppId`, przy użyciu flagi określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="8cda7-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="8cda7-118">Pobiera wartość wskazującą, czy określony `IDefinitionAppId` i `IReferenceAppId` reprezentują tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8cda7-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="8cda7-119">Pobiera wartość wskazującą, czy podana definicja ciągu i ciąg odwołania reprezentują tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8cda7-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="8cda7-120">Pobiera klucz ciąg, który reprezentuje określony `IDefinitionAppId` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8cda7-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="8cda7-121">Pobiera klucz ciąg, który reprezentuje określony `IReferenceAppId` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8cda7-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="8cda7-122">Pobiera klucz wyznaczania wartości skrótu dla określonego `IDefinitionAppId` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8cda7-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="8cda7-123">Pobiera klucz wyznaczania wartości skrótu dla określonego `IReferenceAppId` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8cda7-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="8cda7-124">Pobiera wersję ciągu określonego `IReferenceAppId`, przy użyciu flagi określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="8cda7-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="8cda7-125">Pobiera wskaźnik interfejsu do `IDefinitionAppId` wystąpienia, która reprezentuje zestaw odwołania za pomocą klucza określonego ciągu.</span><span class="sxs-lookup"><span data-stu-id="8cda7-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="8cda7-126">Pobiera wskaźnik interfejsu do `IReferenceAppId` wystąpienia, która reprezentuje zestaw odwołania za pomocą klucza określonego ciągu.</span><span class="sxs-lookup"><span data-stu-id="8cda7-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8cda7-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8cda7-127">Requirements</span></span>  
 <span data-ttu-id="8cda7-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cda7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cda7-129">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="8cda7-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="8cda7-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cda7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cda7-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cda7-131">See also</span></span>

- [<span data-ttu-id="8cda7-132">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="8cda7-132">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
