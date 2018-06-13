---
title: '&lt;issuerChannelBehaviors&gt;, element'
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 7e5b8ace06a224db3abcc6b9d0ec87ccbc1a6a77
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747060"
---
# <a name="ltissuerchannelbehaviorsgt-element"></a><span data-ttu-id="2ac41-102">&lt;issuerChannelBehaviors&gt;, element</span><span class="sxs-lookup"><span data-stu-id="2ac41-102">&lt;issuerChannelBehaviors&gt; Element</span></span>
<span data-ttu-id="2ac41-103">Zawiera kolekcję zachowania punktu końcowego klienta usługi Windows Communication Foundation (WCF) (zdefiniowany w konfiguracji) ma być używany podczas komunikacji z określonych usług tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="2ac41-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="2ac41-104">Zdefiniowanych zachowań nie może zawierać żadnego [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="2ac41-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>  
  
 <span data-ttu-id="2ac41-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2ac41-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="2ac41-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="2ac41-106">\<behaviors></span></span>  
<span data-ttu-id="2ac41-107">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="2ac41-107">endpointBehaviors section</span></span>  
<span data-ttu-id="2ac41-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="2ac41-108">\<behavior></span></span>  
<span data-ttu-id="2ac41-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="2ac41-109">\<clientCredentials></span></span>  
<span data-ttu-id="2ac41-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="2ac41-110">\<issuedToken></span></span>  
<span data-ttu-id="2ac41-111">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2ac41-111">\<issuerChannelBehaviors></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ac41-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ac41-112">Syntax</span></span>  
  
```xml  
<issuerChannelBehaviors>  
      <add behaviorConfiguraton="string"  
                issuerAddress="string" />  
</issuerChannelBehaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ac41-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2ac41-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2ac41-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2ac41-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ac41-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2ac41-115">Attributes</span></span>  
 <span data-ttu-id="2ac41-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="2ac41-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2ac41-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2ac41-117">Child Elements</span></span>  
  
|<span data-ttu-id="2ac41-118">Element</span><span class="sxs-lookup"><span data-stu-id="2ac41-118">Element</span></span>|<span data-ttu-id="2ac41-119">Opis</span><span class="sxs-lookup"><span data-stu-id="2ac41-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ac41-120">\<add></span><span class="sxs-lookup"><span data-stu-id="2ac41-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="2ac41-121">Dodaje zachowanie do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2ac41-121">Adds a behavior to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2ac41-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2ac41-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2ac41-123">Element</span><span class="sxs-lookup"><span data-stu-id="2ac41-123">Element</span></span>|<span data-ttu-id="2ac41-124">Opis</span><span class="sxs-lookup"><span data-stu-id="2ac41-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ac41-125">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="2ac41-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="2ac41-126">Określa niestandardowy token używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="2ac41-126">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ac41-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ac41-127">Remarks</span></span>  
 <span data-ttu-id="2ac41-128">Użyj tego elementu, gdy dowolne zachowania (innych niż zachowania, które obejmują `<clientCredentials>` elementy) musi być używany do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="2ac41-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="2ac41-129">Na przykład jeśli [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) zachowanie elementu muszą być włączone.</span><span class="sxs-lookup"><span data-stu-id="2ac41-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac41-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ac41-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="2ac41-131">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="2ac41-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="2ac41-132">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2ac41-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="2ac41-133">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="2ac41-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="2ac41-134">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="2ac41-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="2ac41-135">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="2ac41-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="2ac41-136">Instrukcje: tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="2ac41-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="2ac41-137">Instrukcje: konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="2ac41-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="2ac41-138">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="2ac41-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
