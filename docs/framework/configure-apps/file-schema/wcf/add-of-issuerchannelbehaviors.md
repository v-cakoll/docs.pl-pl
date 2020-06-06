---
title: <add> dla <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398335"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="29ecd-102">\<add> dla \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="29ecd-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="29ecd-103">Dodaje zachowanie punktu końcowego, które ma być używane podczas komunikacji z usługą STS.</span><span class="sxs-lookup"><span data-stu-id="29ecd-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="29ecd-104">Jeśli dowolne zachowanie punktu końcowego zawiera [\<clientCredentials>](clientcredentials.md) element, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="29ecd-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="29ecd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="29ecd-105">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="29ecd-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="29ecd-106">Attributes and Elements</span></span>

<span data-ttu-id="29ecd-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="29ecd-107">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="29ecd-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="29ecd-108">Attributes</span></span>

|<span data-ttu-id="29ecd-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="29ecd-109">Attribute</span></span>|<span data-ttu-id="29ecd-110">Opis</span><span class="sxs-lookup"><span data-stu-id="29ecd-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="29ecd-111">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="29ecd-111">issuerAddress</span></span>|<span data-ttu-id="29ecd-112">Identyfikator URI wystawcy tokenu zabezpieczającego do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="29ecd-112">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="29ecd-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="29ecd-113">behaviorConfiguration</span></span>|<span data-ttu-id="29ecd-114">Nazwa zachowania punktu końcowego zdefiniowana w tym samym pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="29ecd-114">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="29ecd-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="29ecd-115">Child Elements</span></span>

<span data-ttu-id="29ecd-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="29ecd-116">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="29ecd-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="29ecd-117">Parent Elements</span></span>

|<span data-ttu-id="29ecd-118">Element</span><span class="sxs-lookup"><span data-stu-id="29ecd-118">Element</span></span>|<span data-ttu-id="29ecd-119">Opis</span><span class="sxs-lookup"><span data-stu-id="29ecd-119">Description</span></span>|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="29ecd-120">Zawiera kolekcję zachowań punktu końcowego klienta programu Windows Communication Foundation (WCF), które mają być używane podczas komunikowania się z określonymi usługami tokenu usługi.</span><span class="sxs-lookup"><span data-stu-id="29ecd-120">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="29ecd-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29ecd-121">Remarks</span></span>

<span data-ttu-id="29ecd-122">`issuerAddress`zawiera identyfikator URI usługi tokenu zabezpieczającego, z którą klient chce się skomunikować.</span><span class="sxs-lookup"><span data-stu-id="29ecd-122">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="29ecd-123">`behaviorConfiguration`wskazuje zachowanie punktu końcowego, którego aplikacja używa w kanałach utworzonych przez Windows Communication Foundation (WCF) do pobierania wystawionych tokenów z usług tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="29ecd-123">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="29ecd-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29ecd-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="29ecd-125">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="29ecd-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="29ecd-126">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="29ecd-126">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="29ecd-127">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="29ecd-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="29ecd-128">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="29ecd-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="29ecd-129">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="29ecd-129">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="29ecd-130">Instrukcje: tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="29ecd-130">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="29ecd-131">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="29ecd-131">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="29ecd-132">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="29ecd-132">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
