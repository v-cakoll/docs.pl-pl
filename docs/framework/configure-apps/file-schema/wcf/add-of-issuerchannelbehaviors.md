---
title: '&lt;add&gt; w &lt;issuerChannelBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: e0f49f71a3f9649492b3ad7ccf263114957ee4e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729934"
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="028a8-102">&lt;add&gt; w &lt;issuerChannelBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="028a8-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="028a8-103">Dodaje zachowanie punktu końcowego, który będzie używany podczas komunikacji z usługą STS.</span><span class="sxs-lookup"><span data-stu-id="028a8-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="028a8-104">Jeśli jakiekolwiek zachowanie punktu końcowego zawiera [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="028a8-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="028a8-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="028a8-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="028a8-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="028a8-106">\<behaviors></span></span>  
<span data-ttu-id="028a8-107">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="028a8-107">endpointBehaviors section</span></span>  
<span data-ttu-id="028a8-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="028a8-108">\<behavior></span></span>  
<span data-ttu-id="028a8-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="028a8-109">\<clientCredentials></span></span>  
<span data-ttu-id="028a8-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="028a8-110">\<issuedToken></span></span>  
<span data-ttu-id="028a8-111">\<issuerChannelBehaviors> Element</span><span class="sxs-lookup"><span data-stu-id="028a8-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="028a8-112">\<add></span><span class="sxs-lookup"><span data-stu-id="028a8-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="028a8-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="028a8-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"
     behaviorConfiguraton="string" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="028a8-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="028a8-114">Attributes and Elements</span></span>  
 <span data-ttu-id="028a8-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="028a8-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="028a8-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="028a8-116">Attributes</span></span>  
  
|<span data-ttu-id="028a8-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="028a8-117">Attribute</span></span>|<span data-ttu-id="028a8-118">Opis</span><span class="sxs-lookup"><span data-stu-id="028a8-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="028a8-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="028a8-119">issuerAddress</span></span>|<span data-ttu-id="028a8-120">Identyfikator URI do komunikacji z wystawcą tokenu zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="028a8-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="028a8-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="028a8-121">behaviorConfiguration</span></span>|<span data-ttu-id="028a8-122">Nazwa zachowania punktu końcowego zdefiniowana w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="028a8-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="028a8-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="028a8-123">Child Elements</span></span>  
 <span data-ttu-id="028a8-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="028a8-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="028a8-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="028a8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="028a8-126">Element</span><span class="sxs-lookup"><span data-stu-id="028a8-126">Element</span></span>|<span data-ttu-id="028a8-127">Opis</span><span class="sxs-lookup"><span data-stu-id="028a8-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="028a8-128">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="028a8-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="028a8-129">Zawiera kolekcję zachowań punktu końcowego klienta usługi Windows Communication Foundation (WCF) ma być używany podczas komunikacji z określonej usługi tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="028a8-129">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="028a8-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="028a8-130">Remarks</span></span>  
 <span data-ttu-id="028a8-131">`issuerAddress` zawiera identyfikator URI usługi tokenu zabezpieczającego, które klient chce się nawiązać połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="028a8-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="028a8-132">`behaviorConfiguration` Wskazuje zachowanie punktu końcowego, którego używa aplikacja w kanałach utworzone przez Windows Communication Foundation (WCF) można pobrać wystawionych tokenów z usługi tokenu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="028a8-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="028a8-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="028a8-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="028a8-134">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="028a8-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="028a8-135">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="028a8-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="028a8-136">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="028a8-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="028a8-137">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="028a8-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="028a8-138">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="028a8-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="028a8-139">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="028a8-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="028a8-140">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="028a8-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="028a8-141">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="028a8-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="028a8-142">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="028a8-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
