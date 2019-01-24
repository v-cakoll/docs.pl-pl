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
ms.openlocfilehash: ab8965ca5d6c9c96cea5f5b351547ce2d4dfacc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546283"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="a5683-102">IIdentityAuthority — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a5683-102">IIdentityAuthority Interface</span></span>
<span data-ttu-id="a5683-103">Zarządza kluczy tożsamości dla obiektów kodu.</span><span class="sxs-lookup"><span data-stu-id="a5683-103">Manages identity keys for code objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5683-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a5683-104">Methods</span></span>  
  
|<span data-ttu-id="a5683-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a5683-105">Method</span></span>|<span data-ttu-id="a5683-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a5683-106">Description</span></span>|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="a5683-107">Pobiera wartość wskazującą, czy dwa określone [idefinitionidentity —](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) wystąpień są takie same.</span><span class="sxs-lookup"><span data-stu-id="a5683-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="a5683-108">Pobiera wartość wskazującą, czy dwa określone [ireferenceidentity —](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) wystąpień są takie same.</span><span class="sxs-lookup"><span data-stu-id="a5683-108">Gets a value that indicates whether the two specified [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="a5683-109">Pobiera wartość wskazującą, czy dwa oświadczenia tożsamości definicji określonego ciągu są takie same.</span><span class="sxs-lookup"><span data-stu-id="a5683-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|  
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="a5683-110">Pobiera wartość wskazującą, czy dwa oświadczenia tożsamości odwołanie do określonego ciągu są takie same.</span><span class="sxs-lookup"><span data-stu-id="a5683-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|  
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="a5683-111">Pobiera wskaźnik do nowego `IDefinitionIdentity` wystąpienia, który reprezentuje obiekt kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="a5683-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="a5683-112">Pobiera wskaźnik do nowego `IReferenceIdentity` wystąpienia, który reprezentuje obiekt kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="a5683-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="a5683-113">Pobiera wersję sformatowany ciąg, z określonym `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="a5683-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="a5683-114">Wypełnia buforu określonego znaku dwubajtowego ciągu wersję określonego `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="a5683-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="a5683-115">Pobiera wartość wskazującą, czy określony `IDefinitionIdentity` i `IReferenceIdentity` wystąpień odnoszą się do tego samego obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="a5683-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="a5683-116">Pobiera wartość wskazującą, czy określone ciągi odnoszą się do tego samego obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="a5683-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|  
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="a5683-117">Pobiera wskaźnik do ciągu nowo utworzony klucz dla określonego `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="a5683-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="a5683-118">Pobiera wskaźnik do ciągu nowo utworzony klucz dla określonego `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="a5683-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="a5683-119">Pobiera wartość skrótu dla określonego `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="a5683-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::HashReference`|<span data-ttu-id="a5683-120">Pobiera wartość skrótu dla określonego `IreferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="a5683-120">Gets a hash value for the specified `IreferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="a5683-121">Pobiera wersję sformatowany ciąg, z określonym `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="a5683-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="a5683-122">Wypełnia buforu określonego znaku dwubajtowego ciągu wersję określonego `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="a5683-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="a5683-123">Pobiera wskaźnik interfejsu do `IDefinitionIdentity` ciąg w formacie wygenerowany na podstawie określonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a5683-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|  
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="a5683-124">Pobiera wskaźnik interfejsu do `IReferenceIdentity` ciąg w formacie wygenerowany na podstawie określonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a5683-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5683-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5683-125">Requirements</span></span>  
 <span data-ttu-id="a5683-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5683-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5683-127">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="a5683-127">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="a5683-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5683-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5683-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5683-129">See also</span></span>
- [<span data-ttu-id="a5683-130">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="a5683-130">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
