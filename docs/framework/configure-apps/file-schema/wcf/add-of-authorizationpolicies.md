---
title: <add> dla <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 65398c5afa9750f215c95899bb6004cae671123a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920272"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="35ee2-102">\<Dodawanie > \<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="35ee2-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="35ee2-103">Określa zasady autoryzacji dla transformacji odszkodowania.</span><span class="sxs-lookup"><span data-stu-id="35ee2-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="35ee2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="35ee2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="35ee2-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="35ee2-105">\<behaviors></span></span>  
<span data-ttu-id="35ee2-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="35ee2-106">\<behavior></span></span>  
<span data-ttu-id="35ee2-107">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="35ee2-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="35ee2-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="35ee2-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="35ee2-109">\<add></span><span class="sxs-lookup"><span data-stu-id="35ee2-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35ee2-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="35ee2-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="35ee2-111">Typ</span><span class="sxs-lookup"><span data-stu-id="35ee2-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35ee2-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="35ee2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="35ee2-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="35ee2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35ee2-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="35ee2-114">Attributes</span></span>  
  
|<span data-ttu-id="35ee2-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="35ee2-115">Attribute</span></span>|<span data-ttu-id="35ee2-116">Opis</span><span class="sxs-lookup"><span data-stu-id="35ee2-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="35ee2-117">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="35ee2-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="35ee2-118">Model kontroli dostępu Windows Communication Foundation (WCF) obsługuje Inicjowanie obsługi zestawu zasad autoryzacji jako typów.</span><span class="sxs-lookup"><span data-stu-id="35ee2-118">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="35ee2-119">Ten atrybut określa zasady autoryzacji, które umożliwiają przekształcanie jednego zestawu oświadczeń wejściowych w inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="35ee2-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="35ee2-120">Na podstawie tego można udzielić lub odmówić kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="35ee2-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35ee2-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="35ee2-121">Child Elements</span></span>  
 <span data-ttu-id="35ee2-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="35ee2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35ee2-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="35ee2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="35ee2-124">Element</span><span class="sxs-lookup"><span data-stu-id="35ee2-124">Element</span></span>|<span data-ttu-id="35ee2-125">Opis</span><span class="sxs-lookup"><span data-stu-id="35ee2-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35ee2-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="35ee2-126">\<authorizationPolicies></span></span>](authorizationpolicies.md)|<span data-ttu-id="35ee2-127">Określa kolekcję typów zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="35ee2-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35ee2-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35ee2-128">Remarks</span></span>  
 <span data-ttu-id="35ee2-129">Każda zasada autoryzacji zawiera jeden wymagany `policyType` atrybut, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="35ee2-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="35ee2-130">Ten atrybut określa zasady autoryzacji, które umożliwiają przekształcanie jednego zestawu oświadczeń wejściowych w inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="35ee2-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="35ee2-131">Na podstawie tego można udzielić lub odmówić kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="35ee2-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="35ee2-132">Aby uzyskać więcej informacji na temat działania zasad autoryzacji, zobacz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i [zasady autoryzacji](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="35ee2-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35ee2-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35ee2-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="35ee2-134">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="35ee2-134">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="35ee2-135">Instrukcje: Tworzenie niestandardowego Menedżera autoryzacji dla usługi</span><span class="sxs-lookup"><span data-stu-id="35ee2-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="35ee2-136">\<add></span><span class="sxs-lookup"><span data-stu-id="35ee2-136">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="35ee2-137">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="35ee2-137">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
