---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: b5ab3c3ad070499d686ea74b9fd459e89f380cfa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397960"
---
# <a name="issuedtoken"></a><span data-ttu-id="84729-101">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="84729-101">\<issuedToken></span></span>
<span data-ttu-id="84729-102">Określa niestandardowy token używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="84729-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
<span data-ttu-id="84729-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="84729-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="84729-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="84729-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="84729-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="84729-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="84729-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="84729-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="84729-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="84729-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="84729-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Obiekt clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="84729-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="84729-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuedToken >**</span><span class="sxs-lookup"><span data-stu-id="84729-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84729-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="84729-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84729-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="84729-111">Attributes and Elements</span></span>  
 <span data-ttu-id="84729-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="84729-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84729-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="84729-113">Attributes</span></span>  
  
|<span data-ttu-id="84729-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="84729-114">Attribute</span></span>|<span data-ttu-id="84729-115">Opis</span><span class="sxs-lookup"><span data-stu-id="84729-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="84729-116">Opcjonalny atrybut logiczny, który określa, czy tokeny są buforowane.</span><span class="sxs-lookup"><span data-stu-id="84729-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="84729-117">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="84729-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="84729-118">Opcjonalny atrybut ciągu, który określa, które losowe wartości (entropie) są używane dla operacji uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="84729-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="84729-119">Wartości to `ClientEntropy`, `ServerEntropy`i `CombinedEntropy`, wartość domyślna to `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="84729-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="84729-120">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="84729-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="84729-121">Opcjonalny atrybut Integer, który określa wartość procentową prawidłowego przedziału czasowego (dostarczonych przez wystawcę tokenu), która może upłynąć przed odnowieniem tokenu.</span><span class="sxs-lookup"><span data-stu-id="84729-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="84729-122">Wartości to od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="84729-122">Values are from 0 to 100.</span></span> <span data-ttu-id="84729-123">Wartość domyślna to 60, co oznacza, że 60% czasu kończy się przed próbą odnowienia.</span><span class="sxs-lookup"><span data-stu-id="84729-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="84729-124">Opcjonalny atrybut, który określa zachowania kanału do użycia podczas komunikacji z wystawcą.</span><span class="sxs-lookup"><span data-stu-id="84729-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="84729-125">Opcjonalny atrybut, który określa zachowania kanału do użycia podczas komunikowania się z lokalnym wystawcą.</span><span class="sxs-lookup"><span data-stu-id="84729-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="84729-126">Opcjonalny atrybut TimeSpan, który określa czas, przez jaki wystawione tokeny są buforowane, gdy Wystawca tokenu (STS) nie określa czasu.</span><span class="sxs-lookup"><span data-stu-id="84729-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="84729-127">Wartość domyślna to "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="84729-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84729-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="84729-128">Child Elements</span></span>  
  
|<span data-ttu-id="84729-129">Element</span><span class="sxs-lookup"><span data-stu-id="84729-129">Element</span></span>|<span data-ttu-id="84729-130">Opis</span><span class="sxs-lookup"><span data-stu-id="84729-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84729-131">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="84729-131">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="84729-132">Określa adres lokalnego wystawcy tokenu i powiązania używanego do komunikacji z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="84729-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="84729-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="84729-133">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="84729-134">Określa zachowania punktu końcowego, który ma być używany podczas kontaktowania się z lokalnym wystawcą.</span><span class="sxs-lookup"><span data-stu-id="84729-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84729-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="84729-135">Parent Elements</span></span>  
  
|<span data-ttu-id="84729-136">Element</span><span class="sxs-lookup"><span data-stu-id="84729-136">Element</span></span>|<span data-ttu-id="84729-137">Opis</span><span class="sxs-lookup"><span data-stu-id="84729-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84729-138">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="84729-138">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="84729-139">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="84729-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84729-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84729-140">Remarks</span></span>  
 <span data-ttu-id="84729-141">Wystawiony token jest niestandardowym typem poświadczeń używanym na przykład podczas uwierzytelniania przy użyciu usługi bezpiecznego tokenu (STS) w scenariuszu federacyjnym.</span><span class="sxs-lookup"><span data-stu-id="84729-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="84729-142">Domyślnie token jest tokenem SAML.</span><span class="sxs-lookup"><span data-stu-id="84729-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="84729-143">Aby uzyskać więcej informacji, zobacz [federacyjne i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="84729-143">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="84729-144">oraz [tokeny federacyjne i wystawione](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="84729-144">and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="84729-145">Ta sekcja zawiera elementy używane do konfigurowania lokalnego wystawcy tokenów lub zachowań używanych z usługą tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="84729-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="84729-146">Aby uzyskać instrukcje dotyczące konfigurowania klienta do korzystania z wystawcy lokalnego [, zobacz How to: Konfigurowanie lokalnego wystawcy](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="84729-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84729-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84729-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="84729-148">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="84729-148">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="84729-149">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="84729-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="84729-150">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="84729-150">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="84729-151">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="84729-151">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="84729-152">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="84729-152">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="84729-153">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="84729-153">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="84729-154">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="84729-154">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
