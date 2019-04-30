---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 83061b283c9430af7bcda9cbc832811fa805ed4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756289"
---
# <a name="issuedtoken"></a><span data-ttu-id="ef774-101">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="ef774-101">\<issuedToken></span></span>
<span data-ttu-id="ef774-102">Określa niestandardowy token używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="ef774-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="ef774-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ef774-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ef774-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="ef774-104">\<behaviors></span></span>  
<span data-ttu-id="ef774-105">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="ef774-105">endpointBehaviors section</span></span>  
<span data-ttu-id="ef774-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ef774-106">\<behavior></span></span>  
<span data-ttu-id="ef774-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="ef774-107">\<clientCredentials></span></span>  
<span data-ttu-id="ef774-108">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="ef774-108">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef774-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef774-109">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef774-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ef774-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ef774-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ef774-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef774-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ef774-112">Attributes</span></span>  
  
|<span data-ttu-id="ef774-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ef774-113">Attribute</span></span>|<span data-ttu-id="ef774-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ef774-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="ef774-115">Opcjonalny logiczny atrybut, który określa, czy tokeny są buforowane.</span><span class="sxs-lookup"><span data-stu-id="ef774-115">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="ef774-116">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="ef774-116">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="ef774-117">Atrybut opcjonalny ciąg, który określa, które losowe wartości (entropie) są używane dla operacji uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="ef774-117">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="ef774-118">Wartości obejmują `ClientEntropy`, `ServerEntropy`, i `CombinedEntropy`, wartość domyślna to `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="ef774-118">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="ef774-119">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="ef774-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="ef774-120">Atrybut opcjonalną liczbą całkowitą, który określa procent prawidłowego przedziału czasowego (dostarczonych przez emitenta tokenu) jaki może upłynąć, zanim token jest odnawiany.</span><span class="sxs-lookup"><span data-stu-id="ef774-120">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="ef774-121">Są wartości z zakresu od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="ef774-121">Values are from 0 to 100.</span></span> <span data-ttu-id="ef774-122">Wartość domyślna to 60%, która określa 60% upływu czasu, przed próbą odnowienia.</span><span class="sxs-lookup"><span data-stu-id="ef774-122">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="ef774-123">Opcjonalny atrybut, który określa zachowania kanału do użycia przy komunikacji z wystawcą.</span><span class="sxs-lookup"><span data-stu-id="ef774-123">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="ef774-124">Opcjonalny atrybut, który określa zachowania kanału do użycia przy komunikacji z lokalnym wystawcą.</span><span class="sxs-lookup"><span data-stu-id="ef774-124">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="ef774-125">Opcjonalny atrybut Timespan określający czas trwania buforowania wystawionych tokenów są buforowane, gdy emitent tokenów (STS) określił czasu.</span><span class="sxs-lookup"><span data-stu-id="ef774-125">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="ef774-126">Wartość domyślna to "10675199.02:48:05.4775807."</span><span class="sxs-lookup"><span data-stu-id="ef774-126">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef774-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ef774-127">Child Elements</span></span>  
  
|<span data-ttu-id="ef774-128">Element</span><span class="sxs-lookup"><span data-stu-id="ef774-128">Element</span></span>|<span data-ttu-id="ef774-129">Opis</span><span class="sxs-lookup"><span data-stu-id="ef774-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef774-130">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="ef774-130">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="ef774-131">Określa adres lokalnego wystawcy token i powiązania, używany do komunikacji z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="ef774-131">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="ef774-132">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="ef774-132">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="ef774-133">Określa zachowania punktu końcowego do użycia podczas nawiązywania kontaktu z wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="ef774-133">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ef774-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ef774-134">Parent Elements</span></span>  
  
|<span data-ttu-id="ef774-135">Element</span><span class="sxs-lookup"><span data-stu-id="ef774-135">Element</span></span>|<span data-ttu-id="ef774-136">Opis</span><span class="sxs-lookup"><span data-stu-id="ef774-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef774-137">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="ef774-137">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="ef774-138">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="ef774-138">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef774-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef774-139">Remarks</span></span>  
 <span data-ttu-id="ef774-140">Wystawiony token jest używany, na przykład podczas uwierzytelniania za pomocą Secure Token Service (STS) w federacyjnym scenariuszu typu niestandardowych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="ef774-140">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="ef774-141">Domyślnie token jest SAML token.</span><span class="sxs-lookup"><span data-stu-id="ef774-141">By default, the token is a SAML token.</span></span> <span data-ttu-id="ef774-142">Aby uzyskać więcej informacji, zobacz [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="ef774-142">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="ef774-143">i [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="ef774-143">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="ef774-144">Ta sekcja zawiera elementy służące do Konfigurowanie lokalnego wystawcy tokenów lub zachowania używane z usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="ef774-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="ef774-145">Aby uzyskać instrukcje na temat konfigurowania klienta Użyj wystawcy lokalnego, zobacz [jak: Konfigurowanie lokalnego wystawcy](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="ef774-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef774-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef774-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="ef774-147">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ef774-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ef774-148">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ef774-148">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ef774-149">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="ef774-149">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ef774-150">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="ef774-150">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="ef774-151">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="ef774-151">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="ef774-152">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="ef774-152">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="ef774-153">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="ef774-153">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
