---
title: <add> dla <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 325d6b8111115384b18547bd11ccec8a4a8af711
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920114"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="34cc4-102">\<Dodawanie > \<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="34cc4-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="34cc4-103">Dodaje zachowanie punktu końcowego, które ma być używane podczas komunikacji z usługą STS.</span><span class="sxs-lookup"><span data-stu-id="34cc4-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="34cc4-104">Jeśli dowolne zachowanie punktu końcowego zawiera [ \<element ClientCredentials >](clientcredentials.md) , zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="34cc4-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="34cc4-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="34cc4-105">\<system.ServiceModel></span></span>\
<span data-ttu-id="34cc4-106">\<zachowania > </span><span class="sxs-lookup"><span data-stu-id="34cc4-106">\<behaviors></span></span>\
<span data-ttu-id="34cc4-107">> zachowanie \<sekcji endpointBehaviors </span><span class="sxs-lookup"><span data-stu-id="34cc4-107">endpointBehaviors section \<behavior></span></span>\
<span data-ttu-id="34cc4-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="34cc4-108">\<clientCredentials></span></span>\
<span data-ttu-id="34cc4-109">\<issuedToken > </span><span class="sxs-lookup"><span data-stu-id="34cc4-109">\<issuedToken></span></span>\
<span data-ttu-id="34cc4-110">\<issuerChannelBehaviors > element </span><span class="sxs-lookup"><span data-stu-id="34cc4-110">\<issuerChannelBehaviors> Element</span></span>\
<span data-ttu-id="34cc4-111">\<add></span><span class="sxs-lookup"><span data-stu-id="34cc4-111">\<add></span></span>

## <a name="syntax"></a><span data-ttu-id="34cc4-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="34cc4-112">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34cc4-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34cc4-113">Attributes and Elements</span></span>

<span data-ttu-id="34cc4-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="34cc4-114">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="34cc4-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34cc4-115">Attributes</span></span>

|<span data-ttu-id="34cc4-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="34cc4-116">Attribute</span></span>|<span data-ttu-id="34cc4-117">Opis</span><span class="sxs-lookup"><span data-stu-id="34cc4-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="34cc4-118">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="34cc4-118">issuerAddress</span></span>|<span data-ttu-id="34cc4-119">Identyfikator URI wystawcy tokenu zabezpieczającego do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="34cc4-119">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="34cc4-120">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="34cc4-120">behaviorConfiguration</span></span>|<span data-ttu-id="34cc4-121">Nazwa zachowania punktu końcowego zdefiniowana w tym samym pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="34cc4-121">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="34cc4-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34cc4-122">Child Elements</span></span>

<span data-ttu-id="34cc4-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="34cc4-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34cc4-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34cc4-124">Parent Elements</span></span>

|<span data-ttu-id="34cc4-125">Element</span><span class="sxs-lookup"><span data-stu-id="34cc4-125">Element</span></span>|<span data-ttu-id="34cc4-126">Opis</span><span class="sxs-lookup"><span data-stu-id="34cc4-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34cc4-127">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="34cc4-127">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="34cc4-128">Zawiera kolekcję zachowań punktu końcowego klienta programu Windows Communication Foundation (WCF), które mają być używane podczas komunikowania się z określonymi usługami tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="34cc4-128">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="34cc4-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34cc4-129">Remarks</span></span>

<span data-ttu-id="34cc4-130">`issuerAddress`zawiera identyfikator URI usługi tokenu zabezpieczającego, z którą klient chce się skomunikować.</span><span class="sxs-lookup"><span data-stu-id="34cc4-130">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="34cc4-131">`behaviorConfiguration`wskazuje zachowanie punktu końcowego, którego aplikacja używa w kanałach utworzonych przez Windows Communication Foundation (WCF) do pobierania wystawionych tokenów z usług tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="34cc4-131">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="34cc4-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34cc4-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="34cc4-133">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="34cc4-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="34cc4-134">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="34cc4-134">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="34cc4-135">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="34cc4-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="34cc4-136">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="34cc4-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="34cc4-137">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="34cc4-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="34cc4-138">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="34cc4-138">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="34cc4-139">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="34cc4-139">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="34cc4-140">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="34cc4-140">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="34cc4-141">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="34cc4-141">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)
