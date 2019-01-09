---
title: '&lt;add&gt; w &lt;issuerChannelBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 072e3f4e961f6bf45e7c8b48c64cda36d385cf2b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149543"
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="faed5-102">&lt;add&gt; w &lt;issuerChannelBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="faed5-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="faed5-103">Dodaje zachowanie punktu końcowego, który będzie używany podczas komunikacji z usługą STS.</span><span class="sxs-lookup"><span data-stu-id="faed5-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="faed5-104">Jeśli jakiekolwiek zachowanie punktu końcowego zawiera [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="faed5-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="faed5-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="faed5-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="faed5-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="faed5-106">\<behaviors></span></span>  
<span data-ttu-id="faed5-107">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="faed5-107">endpointBehaviors section</span></span>  
<span data-ttu-id="faed5-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="faed5-108">\<behavior></span></span>  
<span data-ttu-id="faed5-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="faed5-109">\<clientCredentials></span></span>  
<span data-ttu-id="faed5-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="faed5-110">\<issuedToken></span></span>  
<span data-ttu-id="faed5-111">\<issuerChannelBehaviors > Element</span><span class="sxs-lookup"><span data-stu-id="faed5-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="faed5-112">\<add></span><span class="sxs-lookup"><span data-stu-id="faed5-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faed5-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="faed5-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"
     behaviorConfiguraton="string" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="faed5-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="faed5-114">Attributes and Elements</span></span>  
 <span data-ttu-id="faed5-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="faed5-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="faed5-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="faed5-116">Attributes</span></span>  
  
|<span data-ttu-id="faed5-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="faed5-117">Attribute</span></span>|<span data-ttu-id="faed5-118">Opis</span><span class="sxs-lookup"><span data-stu-id="faed5-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="faed5-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="faed5-119">issuerAddress</span></span>|<span data-ttu-id="faed5-120">Identyfikator URI do komunikacji z wystawcą tokenu zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="faed5-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="faed5-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="faed5-121">behaviorConfiguration</span></span>|<span data-ttu-id="faed5-122">Nazwa zachowania punktu końcowego zdefiniowana w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="faed5-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="faed5-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="faed5-123">Child Elements</span></span>  
 <span data-ttu-id="faed5-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="faed5-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="faed5-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="faed5-125">Parent Elements</span></span>  
  
|<span data-ttu-id="faed5-126">Element</span><span class="sxs-lookup"><span data-stu-id="faed5-126">Element</span></span>|<span data-ttu-id="faed5-127">Opis</span><span class="sxs-lookup"><span data-stu-id="faed5-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="faed5-128">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="faed5-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="faed5-129">Zawiera kolekcję zachowań punktu końcowego klienta usługi Windows Communication Foundation (WCF) ma być używany podczas komunikacji z określonej usługi tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="faed5-129">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faed5-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="faed5-130">Remarks</span></span>  
 <span data-ttu-id="faed5-131">`issuerAddress` zawiera identyfikator URI usługi tokenu zabezpieczającego, które klient chce się nawiązać połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="faed5-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="faed5-132">`behaviorConfiguration` Wskazuje zachowanie punktu końcowego, którego używa aplikacja w kanałach utworzone przez Windows Communication Foundation (WCF) można pobrać wystawionych tokenów z usługi tokenu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="faed5-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faed5-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="faed5-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="faed5-134">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="faed5-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="faed5-135">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="faed5-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="faed5-136">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="faed5-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="faed5-137">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="faed5-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="faed5-138">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="faed5-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="faed5-139">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="faed5-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="faed5-140">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="faed5-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="faed5-141">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="faed5-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="faed5-142">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="faed5-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
