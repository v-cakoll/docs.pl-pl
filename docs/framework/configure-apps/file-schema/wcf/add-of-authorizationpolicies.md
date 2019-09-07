---
title: <add> dla <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: e2597bc51e788c919bfe3ce3422ae2911cc6b33b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400702"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="8c039-102">\<Dodawanie > \<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="8c039-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="8c039-103">Określa zasady autoryzacji dla transformacji odszkodowania.</span><span class="sxs-lookup"><span data-stu-id="8c039-103">Specifies an authorization policy for claim transformation.</span></span>  
  
<span data-ttu-id="8c039-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8c039-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8c039-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8c039-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8c039-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8c039-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="8c039-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8c039-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="8c039-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8c039-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="8c039-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ServiceAuthorization**](serviceauthorization-element.md)</span><span class="sxs-lookup"><span data-stu-id="8c039-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)</span></span>\
<span data-ttu-id="8c039-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authorizationPolicies >** ](authorizationpolicies.md)</span><span class="sxs-lookup"><span data-stu-id="8c039-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)</span></span>\
<span data-ttu-id="8c039-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="8c039-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c039-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c039-112">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="8c039-113">Typ</span><span class="sxs-lookup"><span data-stu-id="8c039-113">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c039-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8c039-114">Attributes and Elements</span></span>  
 <span data-ttu-id="8c039-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8c039-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c039-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8c039-116">Attributes</span></span>  
  
|<span data-ttu-id="8c039-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8c039-117">Attribute</span></span>|<span data-ttu-id="8c039-118">Opis</span><span class="sxs-lookup"><span data-stu-id="8c039-118">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="8c039-119">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="8c039-119">A required String attribute.</span></span><br /><br /> <span data-ttu-id="8c039-120">Model kontroli dostępu Windows Communication Foundation (WCF) obsługuje Inicjowanie obsługi zestawu zasad autoryzacji jako typów.</span><span class="sxs-lookup"><span data-stu-id="8c039-120">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="8c039-121">Ten atrybut określa zasady autoryzacji, które umożliwiają przekształcanie jednego zestawu oświadczeń wejściowych w inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="8c039-121">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="8c039-122">Na podstawie tego można udzielić lub odmówić kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="8c039-122">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c039-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8c039-123">Child Elements</span></span>  
 <span data-ttu-id="8c039-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="8c039-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c039-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8c039-125">Parent Elements</span></span>  
  
|<span data-ttu-id="8c039-126">Element</span><span class="sxs-lookup"><span data-stu-id="8c039-126">Element</span></span>|<span data-ttu-id="8c039-127">Opis</span><span class="sxs-lookup"><span data-stu-id="8c039-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c039-128">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="8c039-128">\<authorizationPolicies></span></span>](authorizationpolicies.md)|<span data-ttu-id="8c039-129">Określa kolekcję typów zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="8c039-129">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c039-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c039-130">Remarks</span></span>  
 <span data-ttu-id="8c039-131">Każda zasada autoryzacji zawiera jeden wymagany `policyType` atrybut, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="8c039-131">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="8c039-132">Ten atrybut określa zasady autoryzacji, które umożliwiają przekształcanie jednego zestawu oświadczeń wejściowych w inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="8c039-132">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="8c039-133">Na podstawie tego można udzielić lub odmówić kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="8c039-133">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="8c039-134">Aby uzyskać więcej informacji na temat działania zasad autoryzacji, zobacz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i [zasady autoryzacji](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="8c039-134">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c039-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c039-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="8c039-136">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="8c039-136">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="8c039-137">Instrukcje: Tworzenie niestandardowego Menedżera autoryzacji dla usługi</span><span class="sxs-lookup"><span data-stu-id="8c039-137">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="8c039-138">\<add></span><span class="sxs-lookup"><span data-stu-id="8c039-138">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="8c039-139">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="8c039-139">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
