---
title: '&lt;add&gt; w &lt;authorizationPolicies&gt;'
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: c283f99bedc16352ffca4c41c3d4628271200695
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577528"
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a><span data-ttu-id="83d2a-102">&lt;add&gt; w &lt;authorizationPolicies&gt;</span><span class="sxs-lookup"><span data-stu-id="83d2a-102">&lt;add&gt; of &lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="83d2a-103">Określa zasady autoryzacji dla transformacji roszczenia.</span><span class="sxs-lookup"><span data-stu-id="83d2a-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="83d2a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="83d2a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="83d2a-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="83d2a-105">\<behaviors></span></span>  
<span data-ttu-id="83d2a-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="83d2a-106">\<behavior></span></span>  
<span data-ttu-id="83d2a-107">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="83d2a-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="83d2a-108">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="83d2a-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="83d2a-109">\<add></span><span class="sxs-lookup"><span data-stu-id="83d2a-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83d2a-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="83d2a-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="83d2a-111">Typ</span><span class="sxs-lookup"><span data-stu-id="83d2a-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83d2a-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="83d2a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="83d2a-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="83d2a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83d2a-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="83d2a-114">Attributes</span></span>  
  
|<span data-ttu-id="83d2a-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="83d2a-115">Attribute</span></span>|<span data-ttu-id="83d2a-116">Opis</span><span class="sxs-lookup"><span data-stu-id="83d2a-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="83d2a-117">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="83d2a-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="83d2a-118">Model kontroli dostępu Windows Communication Foundation (WCF) obsługuje zapewnienie zestawu zasad autoryzacji jako typów.</span><span class="sxs-lookup"><span data-stu-id="83d2a-118">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="83d2a-119">Ten atrybut określa zasady autoryzacji, która umożliwia przekształcanie jednego zestawu oświadczeń wejściowych na inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="83d2a-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="83d2a-120">Udzielić lub odmówić kontrola dostępu oparta na.</span><span class="sxs-lookup"><span data-stu-id="83d2a-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83d2a-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="83d2a-121">Child Elements</span></span>  
 <span data-ttu-id="83d2a-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="83d2a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83d2a-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="83d2a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="83d2a-124">Element</span><span class="sxs-lookup"><span data-stu-id="83d2a-124">Element</span></span>|<span data-ttu-id="83d2a-125">Opis</span><span class="sxs-lookup"><span data-stu-id="83d2a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83d2a-126">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="83d2a-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="83d2a-127">Określa kolekcję typów zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="83d2a-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83d2a-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83d2a-128">Remarks</span></span>  
 <span data-ttu-id="83d2a-129">Zasady autoryzacji, każdy zawiera jeden wymagane `policyType` atrybut, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="83d2a-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="83d2a-130">Ten atrybut określa zasady autoryzacji, która umożliwia przekształcanie jednego zestawu oświadczeń wejściowych na inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="83d2a-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="83d2a-131">Udzielić lub odmówić kontrola dostępu oparta na.</span><span class="sxs-lookup"><span data-stu-id="83d2a-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="83d2a-132">Aby uzyskać więcej informacji na temat sposobu działania zasad autoryzacji, zobacz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i [zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="83d2a-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d2a-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83d2a-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="83d2a-134">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="83d2a-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="83d2a-135">Instrukcje: Tworzenie Menedżera autoryzacji niestandardowej dla usługi</span><span class="sxs-lookup"><span data-stu-id="83d2a-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="83d2a-136">\<add></span><span class="sxs-lookup"><span data-stu-id="83d2a-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)
- [<span data-ttu-id="83d2a-137">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="83d2a-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
