---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 68e3a0802a10b14148188a81ee24ed901caa147f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925381"
---
# <a name="issuedtoken"></a><span data-ttu-id="7f98e-101">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="7f98e-101">\<issuedToken></span></span>
<span data-ttu-id="7f98e-102">Określa niestandardowy token używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="7f98e-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="7f98e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7f98e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7f98e-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="7f98e-104">\<behaviors></span></span>  
<span data-ttu-id="7f98e-105">Sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="7f98e-105">endpointBehaviors section</span></span>  
<span data-ttu-id="7f98e-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="7f98e-106">\<behavior></span></span>  
<span data-ttu-id="7f98e-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="7f98e-107">\<clientCredentials></span></span>  
<span data-ttu-id="7f98e-108">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="7f98e-108">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f98e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f98e-109">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f98e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7f98e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7f98e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7f98e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f98e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7f98e-112">Attributes</span></span>  
  
|<span data-ttu-id="7f98e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7f98e-113">Attribute</span></span>|<span data-ttu-id="7f98e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7f98e-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="7f98e-115">Opcjonalny atrybut logiczny, który określa, czy tokeny są buforowane.</span><span class="sxs-lookup"><span data-stu-id="7f98e-115">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="7f98e-116">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="7f98e-116">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="7f98e-117">Opcjonalny atrybut ciągu, który określa, które losowe wartości (entropie) są używane dla operacji uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="7f98e-117">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="7f98e-118">Wartości to `ClientEntropy`, `ServerEntropy`i `CombinedEntropy`, wartość domyślna to `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="7f98e-118">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="7f98e-119">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="7f98e-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="7f98e-120">Opcjonalny atrybut Integer, który określa wartość procentową prawidłowego przedziału czasowego (dostarczonych przez wystawcę tokenu), która może upłynąć przed odnowieniem tokenu.</span><span class="sxs-lookup"><span data-stu-id="7f98e-120">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="7f98e-121">Wartości to od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="7f98e-121">Values are from 0 to 100.</span></span> <span data-ttu-id="7f98e-122">Wartość domyślna to 60, co oznacza, że 60% czasu kończy się przed próbą odnowienia.</span><span class="sxs-lookup"><span data-stu-id="7f98e-122">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="7f98e-123">Opcjonalny atrybut, który określa zachowania kanału do użycia podczas komunikacji z wystawcą.</span><span class="sxs-lookup"><span data-stu-id="7f98e-123">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="7f98e-124">Opcjonalny atrybut, który określa zachowania kanału do użycia podczas komunikowania się z lokalnym wystawcą.</span><span class="sxs-lookup"><span data-stu-id="7f98e-124">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="7f98e-125">Opcjonalny atrybut TimeSpan, który określa czas, przez jaki wystawione tokeny są buforowane, gdy Wystawca tokenu (STS) nie określa czasu.</span><span class="sxs-lookup"><span data-stu-id="7f98e-125">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="7f98e-126">Wartość domyślna to "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="7f98e-126">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f98e-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7f98e-127">Child Elements</span></span>  
  
|<span data-ttu-id="7f98e-128">Element</span><span class="sxs-lookup"><span data-stu-id="7f98e-128">Element</span></span>|<span data-ttu-id="7f98e-129">Opis</span><span class="sxs-lookup"><span data-stu-id="7f98e-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f98e-130">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="7f98e-130">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="7f98e-131">Określa adres lokalnego wystawcy tokenu i powiązania używanego do komunikacji z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="7f98e-131">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="7f98e-132">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7f98e-132">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="7f98e-133">Określa zachowania punktu końcowego, który ma być używany podczas kontaktowania się z lokalnym wystawcą.</span><span class="sxs-lookup"><span data-stu-id="7f98e-133">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f98e-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7f98e-134">Parent Elements</span></span>  
  
|<span data-ttu-id="7f98e-135">Element</span><span class="sxs-lookup"><span data-stu-id="7f98e-135">Element</span></span>|<span data-ttu-id="7f98e-136">Opis</span><span class="sxs-lookup"><span data-stu-id="7f98e-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f98e-137">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="7f98e-137">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="7f98e-138">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="7f98e-138">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f98e-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f98e-139">Remarks</span></span>  
 <span data-ttu-id="7f98e-140">Wystawiony token jest niestandardowym typem poświadczeń używanym na przykład podczas uwierzytelniania przy użyciu usługi bezpiecznego tokenu (STS) w scenariuszu federacyjnym.</span><span class="sxs-lookup"><span data-stu-id="7f98e-140">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="7f98e-141">Domyślnie token jest tokenem SAML.</span><span class="sxs-lookup"><span data-stu-id="7f98e-141">By default, the token is a SAML token.</span></span> <span data-ttu-id="7f98e-142">Aby uzyskać więcej informacji, zobacz [federacyjne i](../../../wcf/feature-details/federation-and-issued-tokens.md)wystawione tokeny.</span><span class="sxs-lookup"><span data-stu-id="7f98e-142">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="7f98e-143">oraz [tokeny federacyjne i](../../../wcf/feature-details/federation-and-issued-tokens.md)wystawione.</span><span class="sxs-lookup"><span data-stu-id="7f98e-143">and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="7f98e-144">Ta sekcja zawiera elementy używane do konfigurowania lokalnego wystawcy tokenów lub zachowań używanych z usługą tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="7f98e-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="7f98e-145">Aby uzyskać instrukcje dotyczące konfigurowania klienta do korzystania z wystawcy lokalnego [, zobacz How to: Konfigurowanie lokalnego wystawcy](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="7f98e-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f98e-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f98e-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="7f98e-147">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7f98e-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="7f98e-148">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="7f98e-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7f98e-149">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="7f98e-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7f98e-150">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="7f98e-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="7f98e-151">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="7f98e-151">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="7f98e-152">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="7f98e-152">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="7f98e-153">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="7f98e-153">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
