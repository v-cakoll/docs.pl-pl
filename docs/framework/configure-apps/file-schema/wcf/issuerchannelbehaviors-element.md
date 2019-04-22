---
title: <issuerChannelBehaviors>, element
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 7cbd50daa82b0ca937a1bba93786545898b03c8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58890478"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="29efe-102">\<issuerChannelBehaviors> Element</span><span class="sxs-lookup"><span data-stu-id="29efe-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="29efe-103">Zawiera zbiór zachowań punktu końcowego klienta usługi Windows Communication Foundation (WCF) (zdefiniowane w konfiguracji), który będzie używany podczas komunikacji z określonej usługi tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="29efe-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="29efe-104">Zachowania zdefiniowane nie może zawierać żadnego [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="29efe-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>

```xml
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior>
        <clientCredentials>
          <issuedToken>
            <issuerChannelBehaviors>
```

## <a name="syntax"></a><span data-ttu-id="29efe-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="29efe-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="29efe-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="29efe-106">Attributes and Elements</span></span>

<span data-ttu-id="29efe-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="29efe-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="29efe-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="29efe-108">Attributes</span></span>

<span data-ttu-id="29efe-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="29efe-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="29efe-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="29efe-110">Child Elements</span></span>

|<span data-ttu-id="29efe-111">Element</span><span class="sxs-lookup"><span data-stu-id="29efe-111">Element</span></span>|<span data-ttu-id="29efe-112">Opis</span><span class="sxs-lookup"><span data-stu-id="29efe-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29efe-113">\<add></span><span class="sxs-lookup"><span data-stu-id="29efe-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="29efe-114">Dodaje zachowanie do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="29efe-114">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="29efe-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="29efe-115">Parent Elements</span></span>

|<span data-ttu-id="29efe-116">Element</span><span class="sxs-lookup"><span data-stu-id="29efe-116">Element</span></span>|<span data-ttu-id="29efe-117">Opis</span><span class="sxs-lookup"><span data-stu-id="29efe-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29efe-118">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="29efe-118">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="29efe-119">Określa niestandardowy token używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="29efe-119">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="29efe-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29efe-120">Remarks</span></span>

<span data-ttu-id="29efe-121">Użyj tego elementu, gdy którykolwiek zachowania (innych niż zachowania, które obejmują `<clientCredentials>` elementy) musi być używany do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="29efe-121">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="29efe-122">Na przykład jeśli [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) zachowanie elementu muszą być włączone.</span><span class="sxs-lookup"><span data-stu-id="29efe-122">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="29efe-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29efe-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="29efe-124">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="29efe-124">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="29efe-125">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="29efe-125">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="29efe-126">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="29efe-126">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="29efe-127">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="29efe-127">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="29efe-128">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="29efe-128">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="29efe-129">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="29efe-129">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="29efe-130">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="29efe-130">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="29efe-131">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="29efe-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
