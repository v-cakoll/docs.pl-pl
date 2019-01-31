---
title: <add> z <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 6a1a7d6b1ef9732e015536d8a78c058fe348113f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255500"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="64ade-102">\<Dodaj > z \<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="64ade-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="64ade-103">Określa zasady autoryzacji dla transformacji roszczenia.</span><span class="sxs-lookup"><span data-stu-id="64ade-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="64ade-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="64ade-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="64ade-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="64ade-105">\<behaviors></span></span>  
<span data-ttu-id="64ade-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="64ade-106">\<behavior></span></span>  
<span data-ttu-id="64ade-107">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="64ade-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="64ade-108">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="64ade-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="64ade-109">\<add></span><span class="sxs-lookup"><span data-stu-id="64ade-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64ade-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="64ade-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="64ade-111">Typ</span><span class="sxs-lookup"><span data-stu-id="64ade-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64ade-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="64ade-112">Attributes and Elements</span></span>  
 <span data-ttu-id="64ade-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="64ade-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64ade-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="64ade-114">Attributes</span></span>  
  
|<span data-ttu-id="64ade-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="64ade-115">Attribute</span></span>|<span data-ttu-id="64ade-116">Opis</span><span class="sxs-lookup"><span data-stu-id="64ade-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="64ade-117">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="64ade-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="64ade-118">Model kontroli dostępu Windows Communication Foundation (WCF) obsługuje zapewnienie zestawu zasad autoryzacji jako typów.</span><span class="sxs-lookup"><span data-stu-id="64ade-118">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="64ade-119">Ten atrybut określa zasady autoryzacji, która umożliwia przekształcanie jednego zestawu oświadczeń wejściowych na inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="64ade-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="64ade-120">Udzielić lub odmówić kontrola dostępu oparta na.</span><span class="sxs-lookup"><span data-stu-id="64ade-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64ade-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="64ade-121">Child Elements</span></span>  
 <span data-ttu-id="64ade-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="64ade-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="64ade-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="64ade-123">Parent Elements</span></span>  
  
|<span data-ttu-id="64ade-124">Element</span><span class="sxs-lookup"><span data-stu-id="64ade-124">Element</span></span>|<span data-ttu-id="64ade-125">Opis</span><span class="sxs-lookup"><span data-stu-id="64ade-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64ade-126">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="64ade-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="64ade-127">Określa kolekcję typów zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="64ade-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64ade-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="64ade-128">Remarks</span></span>  
 <span data-ttu-id="64ade-129">Zasady autoryzacji, każdy zawiera jeden wymagane `policyType` atrybut, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="64ade-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="64ade-130">Ten atrybut określa zasady autoryzacji, która umożliwia przekształcanie jednego zestawu oświadczeń wejściowych na inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="64ade-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="64ade-131">Udzielić lub odmówić kontrola dostępu oparta na.</span><span class="sxs-lookup"><span data-stu-id="64ade-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="64ade-132">Aby uzyskać więcej informacji na temat sposobu działania zasad autoryzacji, zobacz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i [zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="64ade-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64ade-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64ade-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="64ade-134">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="64ade-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="64ade-135">Instrukcje: Tworzenie Menedżera autoryzacji niestandardowej dla usługi</span><span class="sxs-lookup"><span data-stu-id="64ade-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="64ade-136">\<add></span><span class="sxs-lookup"><span data-stu-id="64ade-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)
- [<span data-ttu-id="64ade-137">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="64ade-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
