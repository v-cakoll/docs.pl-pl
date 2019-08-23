---
title: <issuerChannelBehaviors>, element
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: e0e41b4f6d66cd4455c43dda7c77798553f2b58f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929928"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="6d037-102">\<issuerChannelBehaviors, element ></span><span class="sxs-lookup"><span data-stu-id="6d037-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="6d037-103">Zawiera kolekcję zachowań punktu końcowego klienta w programie Windows Communication Foundation (w ramach konfiguracji), które mają być używane podczas komunikowania się z określonymi usługami tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="6d037-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="6d037-104">Zdefiniowane zachowania nie mogą zawierać żadnych [ \<elementów ClientCredentials >](clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="6d037-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

```xml
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior>
        <clientCredentials>
          <issuedToken>
            <issuerChannelBehaviors>
```

## <a name="syntax"></a><span data-ttu-id="6d037-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d037-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6d037-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6d037-106">Attributes and Elements</span></span>

<span data-ttu-id="6d037-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6d037-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6d037-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6d037-108">Attributes</span></span>

<span data-ttu-id="6d037-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="6d037-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6d037-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6d037-110">Child Elements</span></span>

|<span data-ttu-id="6d037-111">Element</span><span class="sxs-lookup"><span data-stu-id="6d037-111">Element</span></span>|<span data-ttu-id="6d037-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6d037-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d037-113">\<add></span><span class="sxs-lookup"><span data-stu-id="6d037-113">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="6d037-114">Dodaje zachowanie do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6d037-114">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6d037-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6d037-115">Parent Elements</span></span>

|<span data-ttu-id="6d037-116">Element</span><span class="sxs-lookup"><span data-stu-id="6d037-116">Element</span></span>|<span data-ttu-id="6d037-117">Opis</span><span class="sxs-lookup"><span data-stu-id="6d037-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d037-118">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="6d037-118">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="6d037-119">Określa niestandardowy token używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="6d037-119">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6d037-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d037-120">Remarks</span></span>

<span data-ttu-id="6d037-121">Użyj tego elementu, gdy do komunikacji z usługą należy używać wszelkich `<clientCredentials>` zachowań (oprócz zachowań zawierających elementy).</span><span class="sxs-lookup"><span data-stu-id="6d037-121">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="6d037-122">Na przykład jeśli [ \<element zachowań > DataContractSerializer](datacontractserializer-element.md) musi być uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="6d037-122">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d037-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d037-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="6d037-124">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="6d037-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="6d037-125">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="6d037-125">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6d037-126">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="6d037-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="6d037-127">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="6d037-127">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6d037-128">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="6d037-128">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="6d037-129">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="6d037-129">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="6d037-130">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="6d037-130">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="6d037-131">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="6d037-131">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
