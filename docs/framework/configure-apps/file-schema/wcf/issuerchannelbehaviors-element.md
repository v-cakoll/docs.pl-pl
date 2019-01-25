---
title: '&lt;issuerChannelBehaviors&gt;, element'
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: b77d0ce79557dff4b5a243da4d24703ed45fde07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677111"
---
# <a name="ltissuerchannelbehaviorsgt-element"></a><span data-ttu-id="92469-102">&lt;issuerChannelBehaviors&gt;, element</span><span class="sxs-lookup"><span data-stu-id="92469-102">&lt;issuerChannelBehaviors&gt; Element</span></span>
<span data-ttu-id="92469-103">Zawiera zbiór zachowań punktu końcowego klienta usługi Windows Communication Foundation (WCF) (zdefiniowane w konfiguracji), który będzie używany podczas komunikacji z określonej usługi tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="92469-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="92469-104">Zachowania zdefiniowane nie może zawierać żadnego [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="92469-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>  
  
 <span data-ttu-id="92469-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="92469-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="92469-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="92469-106">\<behaviors></span></span>  
<span data-ttu-id="92469-107">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="92469-107">endpointBehaviors section</span></span>  
<span data-ttu-id="92469-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="92469-108">\<behavior></span></span>  
<span data-ttu-id="92469-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="92469-109">\<clientCredentials></span></span>  
<span data-ttu-id="92469-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="92469-110">\<issuedToken></span></span>  
<span data-ttu-id="92469-111">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="92469-111">\<issuerChannelBehaviors></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92469-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="92469-112">Syntax</span></span>  
  
```xml  
<issuerChannelBehaviors>
  <add behaviorConfiguraton="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92469-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="92469-113">Attributes and Elements</span></span>  
 <span data-ttu-id="92469-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="92469-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92469-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="92469-115">Attributes</span></span>  
 <span data-ttu-id="92469-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="92469-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="92469-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="92469-117">Child Elements</span></span>  
  
|<span data-ttu-id="92469-118">Element</span><span class="sxs-lookup"><span data-stu-id="92469-118">Element</span></span>|<span data-ttu-id="92469-119">Opis</span><span class="sxs-lookup"><span data-stu-id="92469-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92469-120">\<add></span><span class="sxs-lookup"><span data-stu-id="92469-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="92469-121">Dodaje zachowanie do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="92469-121">Adds a behavior to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92469-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="92469-122">Parent Elements</span></span>  
  
|<span data-ttu-id="92469-123">Element</span><span class="sxs-lookup"><span data-stu-id="92469-123">Element</span></span>|<span data-ttu-id="92469-124">Opis</span><span class="sxs-lookup"><span data-stu-id="92469-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92469-125">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="92469-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="92469-126">Określa niestandardowy token używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="92469-126">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92469-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92469-127">Remarks</span></span>  
 <span data-ttu-id="92469-128">Użyj tego elementu, gdy którykolwiek zachowania (innych niż zachowania, które obejmują `<clientCredentials>` elementy) musi być używany do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="92469-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="92469-129">Na przykład jeśli [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) zachowanie elementu muszą być włączone.</span><span class="sxs-lookup"><span data-stu-id="92469-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92469-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92469-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="92469-131">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="92469-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="92469-132">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="92469-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="92469-133">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="92469-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="92469-134">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="92469-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="92469-135">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="92469-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="92469-136">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="92469-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="92469-137">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="92469-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="92469-138">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="92469-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
