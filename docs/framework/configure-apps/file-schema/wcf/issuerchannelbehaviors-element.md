---
title: <issuerChannelBehaviors>, element
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
no-loc:
- <system.serviceModel>
- <behaviors>
- <endpointBehaviors>
- <behavior>
- <clientCredentials>
- <issuedToken>
- <issuerChannelBehaviors>
- <dataContractSerializer>
ms.openlocfilehash: cbbfb9d3b5af47a360aa82cf837cd6749f61b641
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893159"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="0d1d7-102">\<issuerChannelBehaviors, element ></span><span class="sxs-lookup"><span data-stu-id="0d1d7-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="0d1d7-103">Zawiera kolekcję zachowań punktu końcowego klienta w programie Windows Communication Foundation (w ramach konfiguracji), które mają być używane podczas komunikowania się z określonymi usługami tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="0d1d7-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="0d1d7-104">Zdefiniowane zachowania nie mogą zawierać żadnych [ \<elementów ClientCredentials >](clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="0d1d7-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

<span data-ttu-id="0d1d7-105">[\<> konfiguracji](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d1d7-105">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="0d1d7-106">&nbsp;&nbsp;[\<> System. serviceModel](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0d1d7-106">&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)</span></span>\
<span data-ttu-id="0d1d7-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<> zachowań](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0d1d7-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)</span></span>\
<span data-ttu-id="0d1d7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors >](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0d1d7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)</span></span>\
<span data-ttu-id="0d1d7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<> zachowania](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0d1d7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="0d1d7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<Obiekt clientCredentials >](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="0d1d7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)</span></span>\
<span data-ttu-id="0d1d7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken >](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="0d1d7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)</span></span>\
<span data-ttu-id="0d1d7-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0d1d7-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors></span></span>

## <a name="syntax"></a><span data-ttu-id="0d1d7-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d1d7-113">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d1d7-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0d1d7-114">Attributes and elements</span></span>

<span data-ttu-id="0d1d7-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0d1d7-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d1d7-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0d1d7-116">Attributes</span></span>

<span data-ttu-id="0d1d7-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="0d1d7-117">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0d1d7-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0d1d7-118">Child elements</span></span>

|<span data-ttu-id="0d1d7-119">Element</span><span class="sxs-lookup"><span data-stu-id="0d1d7-119">Element</span></span>|<span data-ttu-id="0d1d7-120">Opis</span><span class="sxs-lookup"><span data-stu-id="0d1d7-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d1d7-121">\<add></span><span class="sxs-lookup"><span data-stu-id="0d1d7-121">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="0d1d7-122">Dodaje zachowanie do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0d1d7-122">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0d1d7-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0d1d7-123">Parent elements</span></span>

|<span data-ttu-id="0d1d7-124">Element</span><span class="sxs-lookup"><span data-stu-id="0d1d7-124">Element</span></span>|<span data-ttu-id="0d1d7-125">Opis</span><span class="sxs-lookup"><span data-stu-id="0d1d7-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d1d7-126">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="0d1d7-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="0d1d7-127">Określa niestandardowy token używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="0d1d7-127">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0d1d7-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d1d7-128">Remarks</span></span>

<span data-ttu-id="0d1d7-129">Użyj tego elementu, gdy do komunikacji z usługą należy używać wszelkich `<clientCredentials>` zachowań (oprócz zachowań zawierających elementy).</span><span class="sxs-lookup"><span data-stu-id="0d1d7-129">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="0d1d7-130">Na przykład jeśli [ \<element zachowań > DataContractSerializer](datacontractserializer-element.md) musi być uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="0d1d7-130">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d1d7-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d1d7-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="0d1d7-132">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="0d1d7-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0d1d7-133">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="0d1d7-133">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="0d1d7-134">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="0d1d7-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0d1d7-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="0d1d7-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0d1d7-136">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="0d1d7-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="0d1d7-137">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="0d1d7-137">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="0d1d7-138">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="0d1d7-138">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="0d1d7-139">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="0d1d7-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
