---
title: "IAppIdAuthority — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppIdAuthority
api_location: fusion.dll
api_type: COM
f1_keywords: IAppIdAuthority
helpviewer_keywords: IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07bfd26a43d264babc9854b0fd0da909dd329405
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="3f51b-102">IAppIdAuthority — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3f51b-102">IAppIdAuthority Interface</span></span>
<span data-ttu-id="3f51b-103">Udostępnia metody, które Generowanie i klucze dla tożsamości aplikacji i odwołania do porównania.</span><span class="sxs-lookup"><span data-stu-id="3f51b-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f51b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3f51b-104">Methods</span></span>  
  
|<span data-ttu-id="3f51b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3f51b-105">Method</span></span>|<span data-ttu-id="3f51b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3f51b-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="3f51b-107">Pobiera wartość wskazującą, czy dwa określone [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) wystąpienia są takie same.</span><span class="sxs-lookup"><span data-stu-id="3f51b-107">Gets a value that indicates whether the two specified [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="3f51b-108">Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION zignorowanie informacji o ich odpowiedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="3f51b-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="3f51b-109">Pobiera wartość wskazującą, czy dwa określone [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) wystąpienia są takie same.</span><span class="sxs-lookup"><span data-stu-id="3f51b-109">Gets a value that indicates whether the two specified [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="3f51b-110">Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION zignorowanie informacji o ich odpowiedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="3f51b-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="3f51b-111">Pobiera wartość wskazującą, czy dwie definicje określonego ciągu są takie same.</span><span class="sxs-lookup"><span data-stu-id="3f51b-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="3f51b-112">Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION zignorowanie informacji o ich odpowiedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="3f51b-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="3f51b-113">Pobiera wartość wskazującą, czy dwa odwołania określonego ciągu są takie same.</span><span class="sxs-lookup"><span data-stu-id="3f51b-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="3f51b-114">Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION zignorowanie informacji o ich odpowiedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="3f51b-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="3f51b-115">Pobiera wskaźnika interfejsu do nowo utworzonego `IDefinitionAppId` wystąpienia, który reprezentuje zestaw w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="3f51b-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="3f51b-116">Pobiera wskaźnika interfejsu, aby nowo utworzony `IReferenceAppId` reprezentujący zestawu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="3f51b-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="3f51b-117">Pobiera wersję ciągu określonego `IDefinitionAppId`, przy użyciu flagi określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="3f51b-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="3f51b-118">Pobiera wartość wskazującą, czy określony `IDefinitionAppId` i `IReferenceAppId` reprezentują tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f51b-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="3f51b-119">Pobiera wartość wskazującą, czy określona definicja ciągu i ciąg odwołania reprezentują tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f51b-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="3f51b-120">Pobiera klucz ciąg reprezentujący określonego `IDefinitionAppId` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3f51b-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="3f51b-121">Pobiera klucz ciąg reprezentujący określonego `IReferenceAppId` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3f51b-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="3f51b-122">Pobiera klucz wyznaczania wartości skrótu dla określonego `IDefinitionAppId` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3f51b-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="3f51b-123">Pobiera klucz wyznaczania wartości skrótu dla określonego `IReferenceAppId` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3f51b-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="3f51b-124">Pobiera wersję ciągu określonego `IReferenceAppId`, przy użyciu flagi określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="3f51b-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="3f51b-125">Pobiera wskaźnika interfejsu do `IDefinitionAppId` wystąpienia, reprezentujący zestaw odwołuje się określony ciąg klucza.</span><span class="sxs-lookup"><span data-stu-id="3f51b-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="3f51b-126">Pobiera wskaźnika interfejsu do `IReferenceAppId` wystąpienia, reprezentujący zestaw odwołuje się określony ciąg klucza.</span><span class="sxs-lookup"><span data-stu-id="3f51b-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f51b-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f51b-127">Requirements</span></span>  
 <span data-ttu-id="3f51b-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f51b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f51b-129">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="3f51b-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="3f51b-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f51b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f51b-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f51b-131">See Also</span></span>  
 [<span data-ttu-id="3f51b-132">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="3f51b-132">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
