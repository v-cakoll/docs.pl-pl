---
title: <clear> z <claimTypeRequirements> — element
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: b20d5c1808bf41d1ecd6b3e3a61606ae45b0fbdd
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270345"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="4748e-102">\<Wyczyść > z \<claimTypeRequirements > element</span><span class="sxs-lookup"><span data-stu-id="4748e-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="4748e-103">Określa, że wszystkie typy roszczeń do usunięcia w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="4748e-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="4748e-104">Daje to gwarancję, że uruchomieniu pusty kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4748e-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="4748e-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4748e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="4748e-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="4748e-106">\<bindings></span></span>  
<span data-ttu-id="4748e-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="4748e-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="4748e-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4748e-108">\<binding></span></span>  
<span data-ttu-id="4748e-109">\<security></span><span class="sxs-lookup"><span data-stu-id="4748e-109">\<security></span></span>  
<span data-ttu-id="4748e-110">\<message></span><span class="sxs-lookup"><span data-stu-id="4748e-110">\<message></span></span>  
<span data-ttu-id="4748e-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="4748e-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4748e-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="4748e-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4748e-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4748e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4748e-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4748e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4748e-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4748e-115">Attributes</span></span>  
 <span data-ttu-id="4748e-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="4748e-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4748e-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4748e-117">Child Elements</span></span>  
 <span data-ttu-id="4748e-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="4748e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4748e-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4748e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4748e-120">Element</span><span class="sxs-lookup"><span data-stu-id="4748e-120">Element</span></span>|<span data-ttu-id="4748e-121">Opis</span><span class="sxs-lookup"><span data-stu-id="4748e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4748e-122">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="4748e-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="4748e-123">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="4748e-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="4748e-124">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="4748e-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="4748e-125">W federacyjnym scenariuszu usługi stanu wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="4748e-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="4748e-126">Na przykład poświadczenia przychodzących musi mieć określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="4748e-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="4748e-127">Każdy element w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, oczekiwano w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="4748e-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4748e-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4748e-128">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
