---
title: '&lt;add&gt; w &lt;authorizationPolicies&gt;'
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 008f465134860141293776130ebd75cd39120f5e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a><span data-ttu-id="2a047-102">&lt;add&gt; w &lt;authorizationPolicies&gt;</span><span class="sxs-lookup"><span data-stu-id="2a047-102">&lt;add&gt; of &lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="2a047-103">Określa zasady autoryzacji dla transformacji roszczenia.</span><span class="sxs-lookup"><span data-stu-id="2a047-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="2a047-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2a047-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a047-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="2a047-105">\<behaviors></span></span>  
<span data-ttu-id="2a047-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="2a047-106">\<behavior></span></span>  
<span data-ttu-id="2a047-107">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="2a047-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="2a047-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="2a047-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="2a047-109">\<add></span><span class="sxs-lookup"><span data-stu-id="2a047-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a047-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a047-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## <a name="type"></a><span data-ttu-id="2a047-111">Typ</span><span class="sxs-lookup"><span data-stu-id="2a047-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a047-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2a047-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2a047-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2a047-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a047-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2a047-114">Attributes</span></span>  
  
|<span data-ttu-id="2a047-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2a047-115">Attribute</span></span>|<span data-ttu-id="2a047-116">Opis</span><span class="sxs-lookup"><span data-stu-id="2a047-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="2a047-117">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="2a047-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="2a047-118">Model kontroli dostępu Windows Communication Foundation (WCF) obsługuje zapewnienie zestawu zasad autoryzacji jako typów.</span><span class="sxs-lookup"><span data-stu-id="2a047-118">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="2a047-119">Ten atrybut określa zasady autoryzacji, dzięki czemu przekształcania jednego zestawu oświadczeń wejściowych do innego zestawu oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="2a047-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="2a047-120">Udzielono lub odmówiono kontrola dostępu oparta na.</span><span class="sxs-lookup"><span data-stu-id="2a047-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a047-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2a047-121">Child Elements</span></span>  
 <span data-ttu-id="2a047-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="2a047-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a047-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2a047-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2a047-124">Element</span><span class="sxs-lookup"><span data-stu-id="2a047-124">Element</span></span>|<span data-ttu-id="2a047-125">Opis</span><span class="sxs-lookup"><span data-stu-id="2a047-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a047-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="2a047-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="2a047-127">Określa kolekcję typów zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="2a047-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a047-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a047-128">Remarks</span></span>  
 <span data-ttu-id="2a047-129">Każdej zasady autoryzacji zawiera jeden z wymaganych `policyType` atrybut, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="2a047-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="2a047-130">Ten atrybut określa zasady autoryzacji, dzięki czemu przekształcania jednego zestawu oświadczeń wejściowych do innego zestawu oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="2a047-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="2a047-131">Udzielono lub odmówiono kontrola dostępu oparta na.</span><span class="sxs-lookup"><span data-stu-id="2a047-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="2a047-132">Aby uzyskać więcej informacji dotyczących sposobu działania zasad autoryzacji, zobacz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i [zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="2a047-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a047-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a047-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="2a047-134">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="2a047-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="2a047-135">Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi</span><span class="sxs-lookup"><span data-stu-id="2a047-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="2a047-136">\<add></span><span class="sxs-lookup"><span data-stu-id="2a047-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="2a047-137">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="2a047-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
