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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b73d090aa47e18792d313b3d086e7a667e74bb08
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltissuerchannelbehaviorsgt-element"></a><span data-ttu-id="7d014-102">&lt;issuerChannelBehaviors&gt;, element</span><span class="sxs-lookup"><span data-stu-id="7d014-102">&lt;issuerChannelBehaviors&gt; Element</span></span>
<span data-ttu-id="7d014-103">Zawiera kolekcję [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] zachowania punktu końcowego klienta (zdefiniowane w konfiguracji) ma być używany podczas komunikacji z określonych usług tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="7d014-103">Contains a collection of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="7d014-104">Zdefiniowanych zachowań nie może zawierać żadnego [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="7d014-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>  
  
 <span data-ttu-id="7d014-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7d014-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="7d014-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="7d014-106">\<behaviors></span></span>  
<span data-ttu-id="7d014-107">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="7d014-107">endpointBehaviors section</span></span>  
<span data-ttu-id="7d014-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="7d014-108">\<behavior></span></span>  
<span data-ttu-id="7d014-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="7d014-109">\<clientCredentials></span></span>  
<span data-ttu-id="7d014-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="7d014-110">\<issuedToken></span></span>  
<span data-ttu-id="7d014-111">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7d014-111">\<issuerChannelBehaviors></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d014-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d014-112">Syntax</span></span>  
  
```xml  
<issuerChannelBehaviors>  
      <add behaviorConfiguraton="string"  
                issuerAddress="string" />  
</issuerChannelBehaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d014-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7d014-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7d014-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7d014-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d014-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d014-115">Attributes</span></span>  
 <span data-ttu-id="7d014-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="7d014-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7d014-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d014-117">Child Elements</span></span>  
  
|<span data-ttu-id="7d014-118">Element</span><span class="sxs-lookup"><span data-stu-id="7d014-118">Element</span></span>|<span data-ttu-id="7d014-119">Opis</span><span class="sxs-lookup"><span data-stu-id="7d014-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d014-120">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="7d014-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="7d014-121">Dodaje zachowanie do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7d014-121">Adds a behavior to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d014-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d014-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7d014-123">Element</span><span class="sxs-lookup"><span data-stu-id="7d014-123">Element</span></span>|<span data-ttu-id="7d014-124">Opis</span><span class="sxs-lookup"><span data-stu-id="7d014-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d014-125">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="7d014-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="7d014-126">Określa niestandardowy token używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="7d014-126">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d014-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d014-127">Remarks</span></span>  
 <span data-ttu-id="7d014-128">Użyj tego elementu, gdy dowolne zachowania (innych niż zachowania, które obejmują `<clientCredentials>` elementy) musi być używany do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="7d014-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="7d014-129">Na przykład jeśli [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) zachowanie elementu muszą być włączone.</span><span class="sxs-lookup"><span data-stu-id="7d014-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d014-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d014-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="7d014-131">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="7d014-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="7d014-132">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7d014-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="7d014-133">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="7d014-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="7d014-134">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="7d014-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="7d014-135">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="7d014-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="7d014-136">Porady: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="7d014-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="7d014-137">Porady: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="7d014-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="7d014-138">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="7d014-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
