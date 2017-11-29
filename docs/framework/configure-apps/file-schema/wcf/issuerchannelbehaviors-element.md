---
title: '&lt;issuerChannelBehaviors&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 051525738f0138955358587a8fd25272dfdb9d28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuerchannelbehaviorsgt-element"></a><span data-ttu-id="b03d3-102">&lt;issuerChannelBehaviors&gt;, element</span><span class="sxs-lookup"><span data-stu-id="b03d3-102">&lt;issuerChannelBehaviors&gt; Element</span></span>
<span data-ttu-id="b03d3-103">Zawiera kolekcję [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] zachowania punktu końcowego klienta (zdefiniowane w konfiguracji) ma być używany podczas komunikacji z określonych usług tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="b03d3-103">Contains a collection of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="b03d3-104">Zdefiniowanych zachowań nie może zawierać żadnego [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="b03d3-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>  
  
 <span data-ttu-id="b03d3-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b03d3-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b03d3-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="b03d3-106">\<behaviors></span></span>  
<span data-ttu-id="b03d3-107">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="b03d3-107">endpointBehaviors section</span></span>  
<span data-ttu-id="b03d3-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b03d3-108">\<behavior></span></span>  
<span data-ttu-id="b03d3-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="b03d3-109">\<clientCredentials></span></span>  
<span data-ttu-id="b03d3-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="b03d3-110">\<issuedToken></span></span>  
<span data-ttu-id="b03d3-111">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b03d3-111">\<issuerChannelBehaviors></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b03d3-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="b03d3-112">Syntax</span></span>  
  
```xml  
<issuerChannelBehaviors>  
      <add behaviorConfiguraton="string"  
                issuerAddress="string" />  
</issuerChannelBehaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b03d3-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b03d3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b03d3-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b03d3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b03d3-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b03d3-115">Attributes</span></span>  
 <span data-ttu-id="b03d3-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="b03d3-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b03d3-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b03d3-117">Child Elements</span></span>  
  
|<span data-ttu-id="b03d3-118">Element</span><span class="sxs-lookup"><span data-stu-id="b03d3-118">Element</span></span>|<span data-ttu-id="b03d3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b03d3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b03d3-120">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="b03d3-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="b03d3-121">Dodaje zachowanie do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b03d3-121">Adds a behavior to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b03d3-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b03d3-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b03d3-123">Element</span><span class="sxs-lookup"><span data-stu-id="b03d3-123">Element</span></span>|<span data-ttu-id="b03d3-124">Opis</span><span class="sxs-lookup"><span data-stu-id="b03d3-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b03d3-125">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="b03d3-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="b03d3-126">Określa niestandardowy token używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="b03d3-126">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b03d3-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b03d3-127">Remarks</span></span>  
 <span data-ttu-id="b03d3-128">Użyj tego elementu, gdy dowolne zachowania (innych niż zachowania, które obejmują `<clientCredentials>` elementy) musi być używany do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="b03d3-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="b03d3-129">Na przykład jeśli [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) zachowanie elementu muszą być włączone.</span><span class="sxs-lookup"><span data-stu-id="b03d3-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b03d3-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b03d3-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="b03d3-131">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="b03d3-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="b03d3-132">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="b03d3-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="b03d3-133">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="b03d3-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b03d3-134">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="b03d3-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="b03d3-135">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="b03d3-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="b03d3-136">Porady: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="b03d3-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="b03d3-137">Porady: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="b03d3-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="b03d3-138">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="b03d3-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
