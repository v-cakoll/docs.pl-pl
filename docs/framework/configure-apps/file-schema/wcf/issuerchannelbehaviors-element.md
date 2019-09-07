---
title: <issuerChannelBehaviors>, element
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 2c0e0d8d041565edd25c4b2c2802bfd2a589b4f7
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397901"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="e51d0-102">\<issuerChannelBehaviors, element ></span><span class="sxs-lookup"><span data-stu-id="e51d0-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="e51d0-103">Zawiera kolekcję zachowań punktu końcowego klienta w programie Windows Communication Foundation (w ramach konfiguracji), które mają być używane podczas komunikowania się z określonymi usługami tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="e51d0-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="e51d0-104">Zdefiniowane zachowania nie mogą zawierać żadnych [ \<elementów ClientCredentials >](clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="e51d0-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

<span data-ttu-id="e51d0-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e51d0-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e51d0-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e51d0-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e51d0-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e51d0-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="e51d0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e51d0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="e51d0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e51d0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="e51d0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Obiekt clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="e51d0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="e51d0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="e51d0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="e51d0-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerChannelBehaviors >**</span><span class="sxs-lookup"><span data-stu-id="e51d0-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerChannelBehaviors>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="e51d0-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="e51d0-113">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e51d0-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e51d0-114">Attributes and Elements</span></span>

<span data-ttu-id="e51d0-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e51d0-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e51d0-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e51d0-116">Attributes</span></span>

<span data-ttu-id="e51d0-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="e51d0-117">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e51d0-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e51d0-118">Child Elements</span></span>

|<span data-ttu-id="e51d0-119">Element</span><span class="sxs-lookup"><span data-stu-id="e51d0-119">Element</span></span>|<span data-ttu-id="e51d0-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e51d0-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e51d0-121">\<add></span><span class="sxs-lookup"><span data-stu-id="e51d0-121">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="e51d0-122">Dodaje zachowanie do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e51d0-122">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e51d0-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e51d0-123">Parent Elements</span></span>

|<span data-ttu-id="e51d0-124">Element</span><span class="sxs-lookup"><span data-stu-id="e51d0-124">Element</span></span>|<span data-ttu-id="e51d0-125">Opis</span><span class="sxs-lookup"><span data-stu-id="e51d0-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e51d0-126">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="e51d0-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="e51d0-127">Określa niestandardowy token używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e51d0-127">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e51d0-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e51d0-128">Remarks</span></span>

<span data-ttu-id="e51d0-129">Użyj tego elementu, gdy do komunikacji z usługą należy używać wszelkich `<clientCredentials>` zachowań (oprócz zachowań zawierających elementy).</span><span class="sxs-lookup"><span data-stu-id="e51d0-129">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="e51d0-130">Na przykład jeśli [ \<element zachowań > DataContractSerializer](datacontractserializer-element.md) musi być uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="e51d0-130">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="e51d0-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e51d0-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="e51d0-132">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="e51d0-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e51d0-133">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e51d0-133">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e51d0-134">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="e51d0-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e51d0-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="e51d0-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e51d0-136">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="e51d0-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="e51d0-137">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="e51d0-137">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="e51d0-138">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="e51d0-138">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="e51d0-139">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="e51d0-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
