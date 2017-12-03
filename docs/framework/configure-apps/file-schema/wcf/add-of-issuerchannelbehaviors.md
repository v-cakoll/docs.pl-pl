---
title: '&lt;add&gt; w &lt;issuerChannelBehaviors&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ea76a96597796b10c97ea57ca38c3bda453468c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="e5c45-102">&lt;add&gt; w &lt;issuerChannelBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="e5c45-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="e5c45-103">Dodaje zachowanie punktu końcowego, który będzie używany podczas komunikacji z STS.</span><span class="sxs-lookup"><span data-stu-id="e5c45-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5c45-104">Jeśli jakiekolwiek zachowanie punktu końcowego zawiera [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu, zostanie wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e5c45-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="e5c45-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e5c45-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e5c45-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="e5c45-106">\<behaviors></span></span>  
<span data-ttu-id="e5c45-107">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="e5c45-107">endpointBehaviors section</span></span>  
<span data-ttu-id="e5c45-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="e5c45-108">\<behavior></span></span>  
<span data-ttu-id="e5c45-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="e5c45-109">\<clientCredentials></span></span>  
<span data-ttu-id="e5c45-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="e5c45-110">\<issuedToken></span></span>  
<span data-ttu-id="e5c45-111">\<issuerChannelBehaviors > — Element</span><span class="sxs-lookup"><span data-stu-id="e5c45-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="e5c45-112">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="e5c45-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5c45-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5c45-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5c45-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e5c45-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e5c45-115">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e5c45-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5c45-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e5c45-116">Attributes</span></span>  
  
|<span data-ttu-id="e5c45-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e5c45-117">Attribute</span></span>|<span data-ttu-id="e5c45-118">Opis</span><span class="sxs-lookup"><span data-stu-id="e5c45-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5c45-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="e5c45-119">issuerAddress</span></span>|<span data-ttu-id="e5c45-120">Identyfikator URI do komunikacji z wystawcą tokenu zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="e5c45-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="e5c45-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="e5c45-121">behaviorConfiguration</span></span>|<span data-ttu-id="e5c45-122">Nazwa zachowania punktu końcowego zdefiniowana w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="e5c45-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5c45-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e5c45-123">Child Elements</span></span>  
 <span data-ttu-id="e5c45-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="e5c45-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5c45-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e5c45-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e5c45-126">Element</span><span class="sxs-lookup"><span data-stu-id="e5c45-126">Element</span></span>|<span data-ttu-id="e5c45-127">Opis</span><span class="sxs-lookup"><span data-stu-id="e5c45-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5c45-128">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e5c45-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="e5c45-129">Zawiera kolekcję [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] zachowania punktu końcowego klienta do użycia przy komunikacji z określonych usług tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="e5c45-129">Contains a collection of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5c45-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5c45-130">Remarks</span></span>  
 <span data-ttu-id="e5c45-131">`issuerAddress`zawiera identyfikator URI usługi tokenu zabezpieczającego, który klient do komunikacji z.</span><span class="sxs-lookup"><span data-stu-id="e5c45-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="e5c45-132">`behaviorConfiguration`Wskazuje zachowanie punktu końcowego, w której aplikacja będzie używać w kanałach utworzone przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] można pobrać wystawionych tokenów z usługi tokenu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e5c45-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c45-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5c45-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="e5c45-134">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="e5c45-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="e5c45-135">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e5c45-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="e5c45-136">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="e5c45-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="e5c45-137">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="e5c45-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="e5c45-138">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="e5c45-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="e5c45-139">Porady: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="e5c45-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="e5c45-140">Porady: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="e5c45-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="e5c45-141">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="e5c45-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="e5c45-142">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e5c45-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
