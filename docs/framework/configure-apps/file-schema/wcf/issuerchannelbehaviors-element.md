---
title: <issuerChannelBehaviors> Element
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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70893159"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="8270a-102">\<issuerChannelBehaviors> Element</span><span class="sxs-lookup"><span data-stu-id="8270a-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="8270a-103">Zawiera kolekcję zachowań punktu końcowego klienta w programie Windows Communication Foundation (w ramach konfiguracji), które mają być używane podczas komunikowania się z określonymi usługami tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="8270a-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="8270a-104">Zdefiniowane zachowania nie mogą zawierać żadnych [\<clientCredentials>](clientcredentials.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="8270a-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors>

## <a name="syntax"></a><span data-ttu-id="8270a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8270a-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8270a-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8270a-106">Attributes and elements</span></span>

<span data-ttu-id="8270a-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8270a-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8270a-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8270a-108">Attributes</span></span>

<span data-ttu-id="8270a-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="8270a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8270a-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8270a-110">Child elements</span></span>

|<span data-ttu-id="8270a-111">Element</span><span class="sxs-lookup"><span data-stu-id="8270a-111">Element</span></span>|<span data-ttu-id="8270a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8270a-112">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="8270a-113">Dodaje zachowanie do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8270a-113">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8270a-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8270a-114">Parent elements</span></span>

|<span data-ttu-id="8270a-115">Element</span><span class="sxs-lookup"><span data-stu-id="8270a-115">Element</span></span>|<span data-ttu-id="8270a-116">Opis</span><span class="sxs-lookup"><span data-stu-id="8270a-116">Description</span></span>|
|-------------|-----------------|
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="8270a-117">Określa niestandardowy token używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="8270a-117">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8270a-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8270a-118">Remarks</span></span>

<span data-ttu-id="8270a-119">Użyj tego elementu `<clientCredentials>` , gdy do komunikacji z usługą należy używać wszelkich zachowań (oprócz zachowań zawierających elementy).</span><span class="sxs-lookup"><span data-stu-id="8270a-119">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="8270a-120">Na przykład jeśli [\<dataContractSerializer>](datacontractserializer-element.md) element Behavior musi być uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="8270a-120">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="8270a-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8270a-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="8270a-122">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="8270a-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="8270a-123">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="8270a-123">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="8270a-124">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="8270a-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="8270a-125">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="8270a-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8270a-126">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="8270a-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="8270a-127">Instrukcje: tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="8270a-127">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="8270a-128">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="8270a-128">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="8270a-129">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="8270a-129">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
