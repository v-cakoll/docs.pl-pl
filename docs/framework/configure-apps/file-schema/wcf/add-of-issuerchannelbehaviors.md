---
title: <add> z <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 5c9937cb6302a194228461f3e2e06ecdf4d43269
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377758"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="3501d-102">\<Dodaj > z \<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3501d-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="3501d-103">Dodaje zachowanie punktu końcowego, który będzie używany podczas komunikacji z usługą STS.</span><span class="sxs-lookup"><span data-stu-id="3501d-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="3501d-104">Jeśli jakiekolwiek zachowanie punktu końcowego zawiera [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3501d-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="3501d-105">\<system.ServiceModel>\\</span><span class="sxs-lookup"><span data-stu-id="3501d-105">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="3501d-106">\<zachowania > \\</span><span class="sxs-lookup"><span data-stu-id="3501d-106">\<behaviors>\\</span></span>
<span data-ttu-id="3501d-107">sekcja endpointBehaviors \<zachowanie > \\</span><span class="sxs-lookup"><span data-stu-id="3501d-107">endpointBehaviors section \<behavior>\\</span></span>
<span data-ttu-id="3501d-108">\<clientCredentials>\\</span><span class="sxs-lookup"><span data-stu-id="3501d-108">\<clientCredentials>\\</span></span>
<span data-ttu-id="3501d-109">\<issuedToken > \\</span><span class="sxs-lookup"><span data-stu-id="3501d-109">\<issuedToken>\\</span></span>
<span data-ttu-id="3501d-110">\<issuerChannelBehaviors > Element\\</span><span class="sxs-lookup"><span data-stu-id="3501d-110">\<issuerChannelBehaviors> Element\\</span></span>
<span data-ttu-id="3501d-111">\<add></span><span class="sxs-lookup"><span data-stu-id="3501d-111">\<add></span></span>

## <a name="syntax"></a><span data-ttu-id="3501d-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="3501d-112">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3501d-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3501d-113">Attributes and Elements</span></span>

<span data-ttu-id="3501d-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3501d-114">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="3501d-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3501d-115">Attributes</span></span>

|<span data-ttu-id="3501d-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3501d-116">Attribute</span></span>|<span data-ttu-id="3501d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="3501d-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="3501d-118">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="3501d-118">issuerAddress</span></span>|<span data-ttu-id="3501d-119">Identyfikator URI do komunikacji z wystawcą tokenu zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="3501d-119">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="3501d-120">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="3501d-120">behaviorConfiguration</span></span>|<span data-ttu-id="3501d-121">Nazwa zachowania punktu końcowego zdefiniowana w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="3501d-121">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3501d-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3501d-122">Child Elements</span></span>

<span data-ttu-id="3501d-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="3501d-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3501d-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3501d-124">Parent Elements</span></span>

|<span data-ttu-id="3501d-125">Element</span><span class="sxs-lookup"><span data-stu-id="3501d-125">Element</span></span>|<span data-ttu-id="3501d-126">Opis</span><span class="sxs-lookup"><span data-stu-id="3501d-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3501d-127">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="3501d-127">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="3501d-128">Zawiera kolekcję zachowań punktu końcowego klienta usługi Windows Communication Foundation (WCF) ma być używany podczas komunikacji z określonej usługi tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="3501d-128">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3501d-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3501d-129">Remarks</span></span>

<span data-ttu-id="3501d-130">`issuerAddress` zawiera identyfikator URI usługi tokenu zabezpieczającego, które klient chce się nawiązać połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="3501d-130">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="3501d-131">`behaviorConfiguration` Wskazuje zachowanie punktu końcowego, którego używa aplikacja w kanałach utworzone przez Windows Communication Foundation (WCF) można pobrać wystawionych tokenów z usługi tokenu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="3501d-131">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="3501d-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3501d-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="3501d-133">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="3501d-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3501d-134">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="3501d-134">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3501d-135">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="3501d-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3501d-136">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="3501d-136">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3501d-137">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="3501d-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="3501d-138">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="3501d-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="3501d-139">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="3501d-139">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="3501d-140">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="3501d-140">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3501d-141">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="3501d-141">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
