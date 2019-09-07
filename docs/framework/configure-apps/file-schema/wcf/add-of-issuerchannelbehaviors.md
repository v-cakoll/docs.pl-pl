---
title: <add> dla <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398335"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="568fc-102">\<Dodawanie > \<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="568fc-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="568fc-103">Dodaje zachowanie punktu końcowego, które ma być używane podczas komunikacji z usługą STS.</span><span class="sxs-lookup"><span data-stu-id="568fc-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="568fc-104">Jeśli dowolne zachowanie punktu końcowego zawiera [ \<element ClientCredentials >](clientcredentials.md) , zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="568fc-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="568fc-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="568fc-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="568fc-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="568fc-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="568fc-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="568fc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="568fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="568fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="568fc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="568fc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="568fc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Obiekt clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="568fc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="568fc-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="568fc-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="568fc-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuerChannelBehaviors >** ](issuerchannelbehaviors-element.md)</span><span class="sxs-lookup"><span data-stu-id="568fc-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)</span></span>\
<span data-ttu-id="568fc-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="568fc-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="568fc-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="568fc-114">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="568fc-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="568fc-115">Attributes and Elements</span></span>

<span data-ttu-id="568fc-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="568fc-116">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="568fc-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="568fc-117">Attributes</span></span>

|<span data-ttu-id="568fc-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="568fc-118">Attribute</span></span>|<span data-ttu-id="568fc-119">Opis</span><span class="sxs-lookup"><span data-stu-id="568fc-119">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="568fc-120">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="568fc-120">issuerAddress</span></span>|<span data-ttu-id="568fc-121">Identyfikator URI wystawcy tokenu zabezpieczającego do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="568fc-121">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="568fc-122">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="568fc-122">behaviorConfiguration</span></span>|<span data-ttu-id="568fc-123">Nazwa zachowania punktu końcowego zdefiniowana w tym samym pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="568fc-123">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="568fc-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="568fc-124">Child Elements</span></span>

<span data-ttu-id="568fc-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="568fc-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="568fc-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="568fc-126">Parent Elements</span></span>

|<span data-ttu-id="568fc-127">Element</span><span class="sxs-lookup"><span data-stu-id="568fc-127">Element</span></span>|<span data-ttu-id="568fc-128">Opis</span><span class="sxs-lookup"><span data-stu-id="568fc-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="568fc-129">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="568fc-129">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="568fc-130">Zawiera kolekcję zachowań punktu końcowego klienta programu Windows Communication Foundation (WCF), które mają być używane podczas komunikowania się z określonymi usługami tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="568fc-130">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="568fc-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="568fc-131">Remarks</span></span>

<span data-ttu-id="568fc-132">`issuerAddress`zawiera identyfikator URI usługi tokenu zabezpieczającego, z którą klient chce się skomunikować.</span><span class="sxs-lookup"><span data-stu-id="568fc-132">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="568fc-133">`behaviorConfiguration`wskazuje zachowanie punktu końcowego, którego aplikacja używa w kanałach utworzonych przez Windows Communication Foundation (WCF) do pobierania wystawionych tokenów z usług tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="568fc-133">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="568fc-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="568fc-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="568fc-135">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="568fc-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="568fc-136">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="568fc-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="568fc-137">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="568fc-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="568fc-138">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="568fc-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="568fc-139">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="568fc-139">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="568fc-140">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="568fc-140">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="568fc-141">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="568fc-141">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="568fc-142">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="568fc-142">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="568fc-143">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="568fc-143">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)
