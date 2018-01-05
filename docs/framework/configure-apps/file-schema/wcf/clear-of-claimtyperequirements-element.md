---
title: '&lt;clear&gt; w &lt;claimTypeRequirements&gt;. element,'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71cc4516362691484408ae2f81dfee462bd560d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="3c0ce-102">&lt;clear&gt; w &lt;claimTypeRequirements&gt;. element,</span><span class="sxs-lookup"><span data-stu-id="3c0ce-102">&lt;clear&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="3c0ce-103">Określa, że wszystkie typy roszczeń do usunięcia w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="3c0ce-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="3c0ce-104">Dzięki temu, że kolekcji zaczyna się pusta.</span><span class="sxs-lookup"><span data-stu-id="3c0ce-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="3c0ce-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3c0ce-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="3c0ce-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="3c0ce-106">\<bindings></span></span>  
<span data-ttu-id="3c0ce-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="3c0ce-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="3c0ce-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="3c0ce-108">\<binding></span></span>  
<span data-ttu-id="3c0ce-109">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="3c0ce-109">\<security></span></span>  
<span data-ttu-id="3c0ce-110">\<komunikat ></span><span class="sxs-lookup"><span data-stu-id="3c0ce-110">\<message></span></span>  
<span data-ttu-id="3c0ce-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="3c0ce-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c0ce-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c0ce-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <clear />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c0ce-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3c0ce-113">Attributes and Elements</span></span>  
 <span data-ttu-id="3c0ce-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3c0ce-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c0ce-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3c0ce-115">Attributes</span></span>  
 <span data-ttu-id="3c0ce-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="3c0ce-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3c0ce-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3c0ce-117">Child Elements</span></span>  
 <span data-ttu-id="3c0ce-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="3c0ce-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c0ce-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3c0ce-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3c0ce-120">Element</span><span class="sxs-lookup"><span data-stu-id="3c0ce-120">Element</span></span>|<span data-ttu-id="3c0ce-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3c0ce-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c0ce-122">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="3c0ce-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="3c0ce-123">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="3c0ce-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="3c0ce-124">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="3c0ce-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="3c0ce-125">W federacyjnym scenariuszu usług stanu wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="3c0ce-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="3c0ce-126">Na przykład poświadczenia przychodzące musi mieć określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="3c0ce-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="3c0ce-127">Każdy element w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, które mogą występować w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="3c0ce-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c0ce-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c0ce-128">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
