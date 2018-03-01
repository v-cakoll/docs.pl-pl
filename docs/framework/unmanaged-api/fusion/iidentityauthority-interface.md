---
title: "IIdentityAuthority — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 322b15252271472b5bee1dfc6a843079cebbe0b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="6622b-102">IIdentityAuthority — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6622b-102">IIdentityAuthority Interface</span></span>
<span data-ttu-id="6622b-103">Zarządza tożsamości klucze obiekty kod.</span><span class="sxs-lookup"><span data-stu-id="6622b-103">Manages identity keys for code objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6622b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6622b-104">Methods</span></span>  
  
|<span data-ttu-id="6622b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6622b-105">Method</span></span>|<span data-ttu-id="6622b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6622b-106">Description</span></span>|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="6622b-107">Pobiera wartość wskazującą, czy dwa określone [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) wystąpienia są takie same.</span><span class="sxs-lookup"><span data-stu-id="6622b-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="6622b-108">Pobiera wartość wskazującą, czy dwa określone [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) wystąpienia są takie same.</span><span class="sxs-lookup"><span data-stu-id="6622b-108">Gets a value that indicates whether the two specified [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="6622b-109">Pobiera wartość wskazującą, czy dwa oświadczenia tożsamości definicji określonego ciągu są takie same.</span><span class="sxs-lookup"><span data-stu-id="6622b-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|  
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="6622b-110">Pobiera wartość wskazującą, czy dwa oświadczenia tożsamości odwołania określonego ciągu są takie same.</span><span class="sxs-lookup"><span data-stu-id="6622b-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|  
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="6622b-111">Pobiera wskaźnik do nowego `IDefinitionIdentity` wystąpienia, który reprezentuje obiekt kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="6622b-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="6622b-112">Pobiera wskaźnik do nowego `IReferenceIdentity` wystąpienia, który reprezentuje obiekt kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="6622b-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="6622b-113">Pobiera wersję sformatowanego ciągu określonego `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="6622b-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="6622b-114">Wypełnia bufor określony znaków dwubajtowych w ciągu wersji z określonym `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="6622b-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="6622b-115">Pobiera wartość wskazującą, czy określony `IDefinitionIdentity` i `IReferenceIdentity` wystąpień odwoływać się do tego samego obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="6622b-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="6622b-116">Pobiera wartość wskazującą, czy określone ciągi odwoływać się do tego samego obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="6622b-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|  
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="6622b-117">Pobiera wskaźnik do nowo utworzony ciąg klucza dla określonego `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="6622b-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="6622b-118">Pobiera wskaźnik do nowo utworzony ciąg klucza dla określonego `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="6622b-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="6622b-119">Pobiera wartość skrótu dla określonego `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="6622b-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::HashReference`|<span data-ttu-id="6622b-120">Pobiera wartość skrótu dla określonego `IreferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="6622b-120">Gets a hash value for the specified `IreferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="6622b-121">Pobiera wersję sformatowanego ciągu określonego `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="6622b-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="6622b-122">Wypełnia bufor określony znaków dwubajtowych w ciągu wersji z określonym `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="6622b-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="6622b-123">Pobiera wskaźnika interfejsu do `IDefinitionIdentity` ciąg w formacie wygenerowane z określonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6622b-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|  
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="6622b-124">Pobiera wskaźnika interfejsu do `IReferenceIdentity` ciąg w formacie wygenerowane z określonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6622b-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6622b-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6622b-125">Requirements</span></span>  
 <span data-ttu-id="6622b-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6622b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6622b-127">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="6622b-127">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="6622b-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6622b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6622b-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6622b-129">See Also</span></span>  
 [<span data-ttu-id="6622b-130">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="6622b-130">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
