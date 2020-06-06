---
title: <add> dla <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: e2597bc51e788c919bfe3ce3422ae2911cc6b33b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400702"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="92f11-102">\<add> dla \<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="92f11-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="92f11-103">Określa zasady autoryzacji dla transformacji odszkodowania.</span><span class="sxs-lookup"><span data-stu-id="92f11-103">Specifies an authorization policy for claim transformation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="92f11-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92f11-104">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="92f11-105">Typ</span><span class="sxs-lookup"><span data-stu-id="92f11-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92f11-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="92f11-106">Attributes and Elements</span></span>  
 <span data-ttu-id="92f11-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="92f11-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92f11-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="92f11-108">Attributes</span></span>  
  
|<span data-ttu-id="92f11-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="92f11-109">Attribute</span></span>|<span data-ttu-id="92f11-110">Opis</span><span class="sxs-lookup"><span data-stu-id="92f11-110">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="92f11-111">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="92f11-111">A required String attribute.</span></span><br /><br /> <span data-ttu-id="92f11-112">Model kontroli dostępu Windows Communication Foundation (WCF) obsługuje Inicjowanie obsługi zestawu zasad autoryzacji jako typów.</span><span class="sxs-lookup"><span data-stu-id="92f11-112">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="92f11-113">Ten atrybut określa zasady autoryzacji, które umożliwiają przekształcanie jednego zestawu oświadczeń wejściowych w inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="92f11-113">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="92f11-114">Na podstawie tego można udzielić lub odmówić kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="92f11-114">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92f11-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="92f11-115">Child Elements</span></span>  
 <span data-ttu-id="92f11-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="92f11-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92f11-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="92f11-117">Parent Elements</span></span>  
  
|<span data-ttu-id="92f11-118">Element</span><span class="sxs-lookup"><span data-stu-id="92f11-118">Element</span></span>|<span data-ttu-id="92f11-119">Opis</span><span class="sxs-lookup"><span data-stu-id="92f11-119">Description</span></span>|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|<span data-ttu-id="92f11-120">Określa kolekcję typów zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="92f11-120">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92f11-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92f11-121">Remarks</span></span>  
 <span data-ttu-id="92f11-122">Każda zasada autoryzacji zawiera jeden wymagany `policyType` atrybut, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="92f11-122">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="92f11-123">Ten atrybut określa zasady autoryzacji, które umożliwiają przekształcanie jednego zestawu oświadczeń wejściowych w inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="92f11-123">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="92f11-124">Na podstawie tego można udzielić lub odmówić kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="92f11-124">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="92f11-125">Aby uzyskać więcej informacji na temat działania zasad autoryzacji, zobacz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i [zasady autoryzacji](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="92f11-125">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f11-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92f11-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="92f11-127">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="92f11-127">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="92f11-128">Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi</span><span class="sxs-lookup"><span data-stu-id="92f11-128">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="92f11-129">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="92f11-129">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
