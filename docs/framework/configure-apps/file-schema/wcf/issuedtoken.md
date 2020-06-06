---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 56439748926ada642018f48a5787634a50d0f180
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "72846856"
---
# \<issuedToken>
<span data-ttu-id="7a58b-101">Określa niestandardowy token używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="7a58b-101">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**  
  
## <a name="syntax"></a><span data-ttu-id="7a58b-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a58b-102">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a58b-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7a58b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7a58b-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7a58b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a58b-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7a58b-105">Attributes</span></span>  
  
|<span data-ttu-id="7a58b-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7a58b-106">Attribute</span></span>|<span data-ttu-id="7a58b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7a58b-107">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="7a58b-108">Opcjonalny atrybut logiczny, który określa, czy tokeny są buforowane.</span><span class="sxs-lookup"><span data-stu-id="7a58b-108">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="7a58b-109">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="7a58b-109">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="7a58b-110">Opcjonalny atrybut ciągu, który określa, które losowe wartości (entropie) są używane dla operacji uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="7a58b-110">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="7a58b-111">Wartości to `ClientEntropy` , `ServerEntropy` i `CombinedEntropy` , wartość domyślna to `CombinedEntropy` .</span><span class="sxs-lookup"><span data-stu-id="7a58b-111">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="7a58b-112">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> .</span><span class="sxs-lookup"><span data-stu-id="7a58b-112">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="7a58b-113">Opcjonalny atrybut Integer, który określa wartość procentową prawidłowego przedziału czasowego (dostarczonych przez wystawcę tokenu), która może upłynąć przed odnowieniem tokenu.</span><span class="sxs-lookup"><span data-stu-id="7a58b-113">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="7a58b-114">Wartości to od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="7a58b-114">Values are from 0 to 100.</span></span> <span data-ttu-id="7a58b-115">Wartość domyślna to 60, co oznacza, że 60% czasu kończy się przed próbą odnowienia.</span><span class="sxs-lookup"><span data-stu-id="7a58b-115">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="7a58b-116">Opcjonalny atrybut, który określa zachowania kanału do użycia podczas komunikacji z wystawcą.</span><span class="sxs-lookup"><span data-stu-id="7a58b-116">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="7a58b-117">Opcjonalny atrybut, który określa zachowania kanału do użycia podczas komunikowania się z lokalnym wystawcą.</span><span class="sxs-lookup"><span data-stu-id="7a58b-117">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="7a58b-118">Opcjonalny atrybut TimeSpan, który określa czas, przez jaki wystawione tokeny są buforowane, gdy Wystawca tokenu (STS) nie określa czasu.</span><span class="sxs-lookup"><span data-stu-id="7a58b-118">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="7a58b-119">Wartość domyślna to "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="7a58b-119">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a58b-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7a58b-120">Child Elements</span></span>  
  
|<span data-ttu-id="7a58b-121">Element</span><span class="sxs-lookup"><span data-stu-id="7a58b-121">Element</span></span>|<span data-ttu-id="7a58b-122">Opis</span><span class="sxs-lookup"><span data-stu-id="7a58b-122">Description</span></span>|  
|-------------|-----------------|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="7a58b-123">Określa adres lokalnego wystawcy tokenu i powiązania używanego do komunikacji z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="7a58b-123">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="7a58b-124">Określa zachowania punktu końcowego, który ma być używany podczas kontaktowania się z lokalnym wystawcą.</span><span class="sxs-lookup"><span data-stu-id="7a58b-124">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7a58b-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7a58b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="7a58b-126">Element</span><span class="sxs-lookup"><span data-stu-id="7a58b-126">Element</span></span>|<span data-ttu-id="7a58b-127">Opis</span><span class="sxs-lookup"><span data-stu-id="7a58b-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="7a58b-128">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="7a58b-128">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a58b-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a58b-129">Remarks</span></span>  
 <span data-ttu-id="7a58b-130">Wystawiony token jest niestandardowym typem poświadczeń używanym na przykład podczas uwierzytelniania przy użyciu usługi bezpiecznego tokenu (STS) w scenariuszu federacyjnym.</span><span class="sxs-lookup"><span data-stu-id="7a58b-130">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="7a58b-131">Domyślnie token jest tokenem SAML.</span><span class="sxs-lookup"><span data-stu-id="7a58b-131">By default, the token is a SAML token.</span></span> <span data-ttu-id="7a58b-132">Aby uzyskać więcej informacji, zobacz [federacyjne i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)oraz [federacyjnego i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="7a58b-132">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="7a58b-133">Ta sekcja zawiera elementy używane do konfigurowania lokalnego wystawcy tokenów lub zachowań używanych z usługą tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="7a58b-133">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="7a58b-134">Aby uzyskać instrukcje dotyczące konfigurowania klienta do korzystania z wystawcy lokalnego, zobacz [How to: Configure a Local wystawca](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="7a58b-134">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a58b-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a58b-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="7a58b-136">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7a58b-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="7a58b-137">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="7a58b-137">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7a58b-138">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="7a58b-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7a58b-139">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="7a58b-139">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="7a58b-140">Instrukcje: tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="7a58b-140">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="7a58b-141">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="7a58b-141">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="7a58b-142">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="7a58b-142">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
