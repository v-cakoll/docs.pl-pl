---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: a70c694509cd35e9bff7d56ae278da93b9b2b9ce
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273036"
---
# <a name="issuedtoken"></a><span data-ttu-id="5867c-101">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="5867c-101">\<issuedToken></span></span>
<span data-ttu-id="5867c-102">Określa niestandardowy token używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="5867c-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="5867c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5867c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5867c-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="5867c-104">\<behaviors></span></span>  
<span data-ttu-id="5867c-105">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="5867c-105">endpointBehaviors section</span></span>  
<span data-ttu-id="5867c-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="5867c-106">\<behavior></span></span>  
<span data-ttu-id="5867c-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="5867c-107">\<clientCredentials></span></span>  
<span data-ttu-id="5867c-108">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="5867c-108">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5867c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5867c-109">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5867c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5867c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5867c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5867c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5867c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5867c-112">Attributes</span></span>  
  
|<span data-ttu-id="5867c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5867c-113">Attribute</span></span>|<span data-ttu-id="5867c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5867c-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="5867c-115">Opcjonalny logiczny atrybut, który określa, czy tokeny są buforowane.</span><span class="sxs-lookup"><span data-stu-id="5867c-115">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="5867c-116">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="5867c-116">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="5867c-117">Atrybut opcjonalny ciąg, który określa, które losowe wartości (entropie) są używane dla operacji uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="5867c-117">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="5867c-118">Wartości obejmują `ClientEntropy`, `ServerEntropy`, i `CombinedEntropy`, wartość domyślna to `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="5867c-118">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="5867c-119">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="5867c-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="5867c-120">Atrybut opcjonalną liczbą całkowitą, który określa procent prawidłowego przedziału czasowego (dostarczonych przez emitenta tokenu) jaki może upłynąć, zanim token jest odnawiany.</span><span class="sxs-lookup"><span data-stu-id="5867c-120">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="5867c-121">Są wartości z zakresu od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="5867c-121">Values are from 0 to 100.</span></span> <span data-ttu-id="5867c-122">Wartość domyślna to 60%, która określa 60% upływu czasu, przed próbą odnowienia.</span><span class="sxs-lookup"><span data-stu-id="5867c-122">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="5867c-123">Opcjonalny atrybut, który określa zachowania kanału do użycia przy komunikacji z wystawcą.</span><span class="sxs-lookup"><span data-stu-id="5867c-123">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="5867c-124">Opcjonalny atrybut, który określa zachowania kanału do użycia przy komunikacji z lokalnym wystawcą.</span><span class="sxs-lookup"><span data-stu-id="5867c-124">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="5867c-125">Opcjonalny atrybut Timespan określający czas trwania buforowania wystawionych tokenów są buforowane, gdy emitent tokenów (STS) określił czasu.</span><span class="sxs-lookup"><span data-stu-id="5867c-125">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="5867c-126">Wartość domyślna to "10675199.02:48:05.4775807."</span><span class="sxs-lookup"><span data-stu-id="5867c-126">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5867c-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5867c-127">Child Elements</span></span>  
  
|<span data-ttu-id="5867c-128">Element</span><span class="sxs-lookup"><span data-stu-id="5867c-128">Element</span></span>|<span data-ttu-id="5867c-129">Opis</span><span class="sxs-lookup"><span data-stu-id="5867c-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5867c-130">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="5867c-130">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="5867c-131">Określa adres lokalnego wystawcy token i powiązania, używany do komunikacji z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="5867c-131">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="5867c-132">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="5867c-132">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="5867c-133">Określa zachowania punktu końcowego do użycia podczas nawiązywania kontaktu z wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="5867c-133">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5867c-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5867c-134">Parent Elements</span></span>  
  
|<span data-ttu-id="5867c-135">Element</span><span class="sxs-lookup"><span data-stu-id="5867c-135">Element</span></span>|<span data-ttu-id="5867c-136">Opis</span><span class="sxs-lookup"><span data-stu-id="5867c-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5867c-137">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="5867c-137">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="5867c-138">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="5867c-138">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5867c-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5867c-139">Remarks</span></span>  
 <span data-ttu-id="5867c-140">Wystawiony token jest używany, na przykład podczas uwierzytelniania za pomocą Secure Token Service (STS) w federacyjnym scenariuszu typu niestandardowych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="5867c-140">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="5867c-141">Domyślnie token jest SAML token.</span><span class="sxs-lookup"><span data-stu-id="5867c-141">By default, the token is a SAML token.</span></span> <span data-ttu-id="5867c-142">Aby uzyskać więcej informacji, zobacz [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="5867c-142">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="5867c-143">i [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="5867c-143">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="5867c-144">Ta sekcja zawiera elementy służące do Konfigurowanie lokalnego wystawcy tokenów lub zachowania używane z usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="5867c-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="5867c-145">Aby uzyskać instrukcje na temat konfigurowania klienta Użyj wystawcy lokalnego, zobacz [jak: Konfigurowanie lokalnego wystawcy](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="5867c-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5867c-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5867c-146">See also</span></span>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="5867c-147">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5867c-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="5867c-148">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="5867c-148">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5867c-149">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="5867c-149">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5867c-150">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="5867c-150">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="5867c-151">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="5867c-151">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="5867c-152">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="5867c-152">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="5867c-153">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="5867c-153">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
