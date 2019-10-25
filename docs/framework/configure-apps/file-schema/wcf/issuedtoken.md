---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 56439748926ada642018f48a5787634a50d0f180
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846856"
---
# <a name="issuedtoken"></a><span data-ttu-id="2fa83-101">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="2fa83-101">\<issuedToken></span></span>
<span data-ttu-id="2fa83-102">Określa niestandardowy token używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="2fa83-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
<span data-ttu-id="2fa83-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2fa83-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2fa83-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="2fa83-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2fa83-105">&nbsp;&nbsp;&nbsp;&nbsp;[**zachowania\<** ](behaviors.md) ></span><span class="sxs-lookup"><span data-stu-id="2fa83-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\</span></span>
<span data-ttu-id="2fa83-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors**](endpointbehaviors.md) ></span><span class="sxs-lookup"><span data-stu-id="2fa83-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="2fa83-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zachowanie**](behavior-of-endpointbehaviors.md) ></span><span class="sxs-lookup"><span data-stu-id="2fa83-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="2fa83-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ClientCredentials**](clientcredentials.md) ></span><span class="sxs-lookup"><span data-stu-id="2fa83-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="2fa83-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuedToken >**</span><span class="sxs-lookup"><span data-stu-id="2fa83-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa83-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="2fa83-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fa83-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2fa83-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2fa83-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2fa83-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fa83-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2fa83-113">Attributes</span></span>  
  
|<span data-ttu-id="2fa83-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2fa83-114">Attribute</span></span>|<span data-ttu-id="2fa83-115">Opis</span><span class="sxs-lookup"><span data-stu-id="2fa83-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="2fa83-116">Opcjonalny atrybut logiczny, który określa, czy tokeny są buforowane.</span><span class="sxs-lookup"><span data-stu-id="2fa83-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="2fa83-117">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="2fa83-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="2fa83-118">Opcjonalny atrybut ciągu, który określa, które losowe wartości (entropie) są używane dla operacji uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="2fa83-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="2fa83-119">Wartości to `ClientEntropy`, `ServerEntropy`i `CombinedEntropy`. wartość domyślna to `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="2fa83-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="2fa83-120">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="2fa83-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="2fa83-121">Opcjonalny atrybut Integer, który określa wartość procentową prawidłowego przedziału czasowego (dostarczonych przez wystawcę tokenu), która może upłynąć przed odnowieniem tokenu.</span><span class="sxs-lookup"><span data-stu-id="2fa83-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="2fa83-122">Wartości to od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="2fa83-122">Values are from 0 to 100.</span></span> <span data-ttu-id="2fa83-123">Wartość domyślna to 60, co oznacza, że 60% czasu kończy się przed próbą odnowienia.</span><span class="sxs-lookup"><span data-stu-id="2fa83-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="2fa83-124">Opcjonalny atrybut, który określa zachowania kanału do użycia podczas komunikacji z wystawcą.</span><span class="sxs-lookup"><span data-stu-id="2fa83-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="2fa83-125">Opcjonalny atrybut, który określa zachowania kanału do użycia podczas komunikowania się z lokalnym wystawcą.</span><span class="sxs-lookup"><span data-stu-id="2fa83-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="2fa83-126">Opcjonalny atrybut TimeSpan, który określa czas, przez jaki wystawione tokeny są buforowane, gdy Wystawca tokenu (STS) nie określa czasu.</span><span class="sxs-lookup"><span data-stu-id="2fa83-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="2fa83-127">Wartość domyślna to "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="2fa83-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fa83-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2fa83-128">Child Elements</span></span>  
  
|<span data-ttu-id="2fa83-129">Element</span><span class="sxs-lookup"><span data-stu-id="2fa83-129">Element</span></span>|<span data-ttu-id="2fa83-130">Opis</span><span class="sxs-lookup"><span data-stu-id="2fa83-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fa83-131">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="2fa83-131">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="2fa83-132">Określa adres lokalnego wystawcy tokenu i powiązania używanego do komunikacji z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="2fa83-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="2fa83-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2fa83-133">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="2fa83-134">Określa zachowania punktu końcowego, który ma być używany podczas kontaktowania się z lokalnym wystawcą.</span><span class="sxs-lookup"><span data-stu-id="2fa83-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2fa83-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2fa83-135">Parent Elements</span></span>  
  
|<span data-ttu-id="2fa83-136">Element</span><span class="sxs-lookup"><span data-stu-id="2fa83-136">Element</span></span>|<span data-ttu-id="2fa83-137">Opis</span><span class="sxs-lookup"><span data-stu-id="2fa83-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fa83-138">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="2fa83-138">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="2fa83-139">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="2fa83-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fa83-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2fa83-140">Remarks</span></span>  
 <span data-ttu-id="2fa83-141">Wystawiony token jest niestandardowym typem poświadczeń używanym na przykład podczas uwierzytelniania przy użyciu usługi bezpiecznego tokenu (STS) w scenariuszu federacyjnym.</span><span class="sxs-lookup"><span data-stu-id="2fa83-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="2fa83-142">Domyślnie token jest tokenem SAML.</span><span class="sxs-lookup"><span data-stu-id="2fa83-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="2fa83-143">Aby uzyskać więcej informacji, zobacz [federacyjne i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)oraz [federacyjnego i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="2fa83-143">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="2fa83-144">Ta sekcja zawiera elementy używane do konfigurowania lokalnego wystawcy tokenów lub zachowań używanych z usługą tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="2fa83-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="2fa83-145">Aby uzyskać instrukcje dotyczące konfigurowania klienta do korzystania z wystawcy lokalnego, zobacz [How to: Configure a Local wystawca](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="2fa83-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa83-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2fa83-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="2fa83-147">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2fa83-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="2fa83-148">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="2fa83-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2fa83-149">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="2fa83-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="2fa83-150">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="2fa83-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="2fa83-151">Instrukcje: tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="2fa83-151">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="2fa83-152">Instrukcje: konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="2fa83-152">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="2fa83-153">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="2fa83-153">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
