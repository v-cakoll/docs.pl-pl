---
title: <remove> z <claimTypeRequirements> — element
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 9ab1162ff5d86b8a9d43dae79ebf9c9321119206
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783100"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="8625d-102">\<Usuń > z \<claimTypeRequirements > element</span><span class="sxs-lookup"><span data-stu-id="8625d-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="8625d-103">Określa typy roszczeń do usunięcia w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="8625d-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="8625d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8625d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8625d-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="8625d-105">\<bindings></span></span>  
<span data-ttu-id="8625d-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="8625d-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="8625d-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="8625d-107">\<binding></span></span>  
<span data-ttu-id="8625d-108">\<security></span><span class="sxs-lookup"><span data-stu-id="8625d-108">\<security></span></span>  
<span data-ttu-id="8625d-109">\<message></span><span class="sxs-lookup"><span data-stu-id="8625d-109">\<message></span></span>  
<span data-ttu-id="8625d-110">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="8625d-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8625d-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="8625d-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8625d-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8625d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8625d-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8625d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8625d-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8625d-114">Attributes</span></span>  
  
|<span data-ttu-id="8625d-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8625d-115">Attribute</span></span>|<span data-ttu-id="8625d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="8625d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8625d-117">Typ oświadczenia</span><span class="sxs-lookup"><span data-stu-id="8625d-117">claimType</span></span>|<span data-ttu-id="8625d-118">Identyfikator URI definiujący typ oświadczenia do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="8625d-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8625d-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8625d-119">Child Elements</span></span>  
 <span data-ttu-id="8625d-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="8625d-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8625d-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8625d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8625d-122">Element</span><span class="sxs-lookup"><span data-stu-id="8625d-122">Element</span></span>|<span data-ttu-id="8625d-123">Opis</span><span class="sxs-lookup"><span data-stu-id="8625d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8625d-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="8625d-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="8625d-125">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="8625d-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="8625d-126">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="8625d-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="8625d-127">W federacyjnym scenariuszu usługi stanu wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="8625d-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="8625d-128">Na przykład poświadczenia przychodzących musi mieć określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="8625d-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="8625d-129">Każdy element w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, oczekiwano w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="8625d-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8625d-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8625d-130">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
