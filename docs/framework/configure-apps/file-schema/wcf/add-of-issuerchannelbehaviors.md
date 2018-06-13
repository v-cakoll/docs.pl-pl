---
title: '&lt;add&gt; w &lt;issuerChannelBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 75531e8ed50ae89f379db23d228804612f4bfccb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752458"
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="b8fb4-102">&lt;add&gt; w &lt;issuerChannelBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="b8fb4-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="b8fb4-103">Dodaje zachowanie punktu końcowego, który będzie używany podczas komunikacji z STS.</span><span class="sxs-lookup"><span data-stu-id="b8fb4-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8fb4-104">Jeśli jakiekolwiek zachowanie punktu końcowego zawiera [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu, zostanie wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b8fb4-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="b8fb4-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b8fb4-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8fb4-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="b8fb4-106">\<behaviors></span></span>  
<span data-ttu-id="b8fb4-107">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="b8fb4-107">endpointBehaviors section</span></span>  
<span data-ttu-id="b8fb4-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b8fb4-108">\<behavior></span></span>  
<span data-ttu-id="b8fb4-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="b8fb4-109">\<clientCredentials></span></span>  
<span data-ttu-id="b8fb4-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="b8fb4-110">\<issuedToken></span></span>  
<span data-ttu-id="b8fb4-111">\<issuerChannelBehaviors > — Element</span><span class="sxs-lookup"><span data-stu-id="b8fb4-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="b8fb4-112">\<add></span><span class="sxs-lookup"><span data-stu-id="b8fb4-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8fb4-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8fb4-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8fb4-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b8fb4-114">Attributes and Elements</span></span>  
 <span data-ttu-id="b8fb4-115">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b8fb4-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8fb4-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b8fb4-116">Attributes</span></span>  
  
|<span data-ttu-id="b8fb4-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b8fb4-117">Attribute</span></span>|<span data-ttu-id="b8fb4-118">Opis</span><span class="sxs-lookup"><span data-stu-id="b8fb4-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8fb4-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="b8fb4-119">issuerAddress</span></span>|<span data-ttu-id="b8fb4-120">Identyfikator URI do komunikacji z wystawcą tokenu zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="b8fb4-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="b8fb4-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="b8fb4-121">behaviorConfiguration</span></span>|<span data-ttu-id="b8fb4-122">Nazwa zachowania punktu końcowego zdefiniowana w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="b8fb4-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8fb4-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b8fb4-123">Child Elements</span></span>  
 <span data-ttu-id="b8fb4-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="b8fb4-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8fb4-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b8fb4-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b8fb4-126">Element</span><span class="sxs-lookup"><span data-stu-id="b8fb4-126">Element</span></span>|<span data-ttu-id="b8fb4-127">Opis</span><span class="sxs-lookup"><span data-stu-id="b8fb4-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8fb4-128">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b8fb4-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="b8fb4-129">Zawiera kolekcję zachowania punktu końcowego klienta Windows Communication Foundation (WCF) używanego podczas komunikacji z określonych usług tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="b8fb4-129">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8fb4-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8fb4-130">Remarks</span></span>  
 <span data-ttu-id="b8fb4-131">`issuerAddress` zawiera identyfikator URI usługi tokenu zabezpieczającego, który klient do komunikacji z.</span><span class="sxs-lookup"><span data-stu-id="b8fb4-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="b8fb4-132">`behaviorConfiguration` Wskazuje zachowanie punktu końcowego, w której aplikacja będzie używać w kanałach utworzony przez Windows Communication Foundation (WCF) można pobrać wystawionych tokenów z usługi tokenu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="b8fb4-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8fb4-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8fb4-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="b8fb4-134">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="b8fb4-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="b8fb4-135">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="b8fb4-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="b8fb4-136">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="b8fb4-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b8fb4-137">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="b8fb4-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="b8fb4-138">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="b8fb4-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="b8fb4-139">Instrukcje: tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="b8fb4-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="b8fb4-140">Instrukcje: konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="b8fb4-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="b8fb4-141">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="b8fb4-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b8fb4-142">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b8fb4-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
