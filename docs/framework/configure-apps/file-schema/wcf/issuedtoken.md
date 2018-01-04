---
title: '&lt;issuedToken&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c4090dacdbb55f66bf7c27bdd02adf371049f7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuedtokengt"></a><span data-ttu-id="cfea2-102">&lt;issuedToken&gt;</span><span class="sxs-lookup"><span data-stu-id="cfea2-102">&lt;issuedToken&gt;</span></span>
<span data-ttu-id="cfea2-103">Określa niestandardowy token używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="cfea2-103">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="cfea2-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="cfea2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cfea2-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="cfea2-105">\<behaviors></span></span>  
<span data-ttu-id="cfea2-106">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="cfea2-106">endpointBehaviors section</span></span>  
<span data-ttu-id="cfea2-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="cfea2-107">\<behavior></span></span>  
<span data-ttu-id="cfea2-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="cfea2-108">\<clientCredentials></span></span>  
<span data-ttu-id="cfea2-109">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="cfea2-109">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfea2-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfea2-110">Syntax</span></span>  
  
```xml  
<issuedToken   
   cacheIssuedTokens="Boolean"  
   defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"  
   issuedTokenRenewalThresholdPercentage = "0 to 100"  
   issuerChannelBehaviors="String"  
      localIssuerChannelBehaviors="String"  
   maxIssuedTokenCachingTime="TimeSpan"  
</issuedToken>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfea2-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cfea2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cfea2-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cfea2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfea2-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cfea2-113">Attributes</span></span>  
  
|<span data-ttu-id="cfea2-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cfea2-114">Attribute</span></span>|<span data-ttu-id="cfea2-115">Opis</span><span class="sxs-lookup"><span data-stu-id="cfea2-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="cfea2-116">Opcjonalny logiczny atrybut, który określa, czy tokeny są buforowane.</span><span class="sxs-lookup"><span data-stu-id="cfea2-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="cfea2-117">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="cfea2-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="cfea2-118">Atrybut opcjonalny ciąg, który określa, które losowe wartości (entropie) są używane dla operacji uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="cfea2-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="cfea2-119">Wartości to `ClientEntropy`, `ServerEntropy`, i `CombinedEntropy`, wartość domyślna to `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="cfea2-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="cfea2-120">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="cfea2-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="cfea2-121">Atrybut opcjonalny całkowity, który określa procent prawidłowego przedziału czasowego (dostarczonych przez emitenta tokenu) jaki może upłynąć, zanim token jest odnawiany.</span><span class="sxs-lookup"><span data-stu-id="cfea2-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="cfea2-122">Są wartości z zakresu od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="cfea2-122">Values are from 0 to 100.</span></span> <span data-ttu-id="cfea2-123">Wartość domyślna to 60, który określa 60% upływu czasu, przed podjęciem próby odnowienia.</span><span class="sxs-lookup"><span data-stu-id="cfea2-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="cfea2-124">Opcjonalny atrybut, który określa zachowania kanału do użycia przy komunikacji z wystawcą.</span><span class="sxs-lookup"><span data-stu-id="cfea2-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="cfea2-125">Opcjonalny atrybut, który określa zachowania kanału do użycia przy komunikacji z lokalnym wystawcą.</span><span class="sxs-lookup"><span data-stu-id="cfea2-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="cfea2-126">Opcjonalny atrybut Timespan określający okres czasu, który wystawił tokeny są buforowane, gdy emitent tokenów (STS) określił czasu.</span><span class="sxs-lookup"><span data-stu-id="cfea2-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="cfea2-127">Wartość domyślna to "10675199.02:48:05.4775807."</span><span class="sxs-lookup"><span data-stu-id="cfea2-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cfea2-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cfea2-128">Child Elements</span></span>  
  
|<span data-ttu-id="cfea2-129">Element</span><span class="sxs-lookup"><span data-stu-id="cfea2-129">Element</span></span>|<span data-ttu-id="cfea2-130">Opis</span><span class="sxs-lookup"><span data-stu-id="cfea2-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfea2-131">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="cfea2-131">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="cfea2-132">Określa adres wystawcy lokalnego token i powiązania, używany do komunikacji z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="cfea2-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="cfea2-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cfea2-133">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="cfea2-134">Określa zachowania punktu końcowego do użycia podczas nawiązywania kontaktu wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="cfea2-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cfea2-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cfea2-135">Parent Elements</span></span>  
  
|<span data-ttu-id="cfea2-136">Element</span><span class="sxs-lookup"><span data-stu-id="cfea2-136">Element</span></span>|<span data-ttu-id="cfea2-137">Opis</span><span class="sxs-lookup"><span data-stu-id="cfea2-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfea2-138">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="cfea2-138">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="cfea2-139">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="cfea2-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfea2-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfea2-140">Remarks</span></span>  
 <span data-ttu-id="cfea2-141">Wystawiony token jest typu niestandardowego poświadczenia używane, na przykład podczas uwierzytelniania z Secure Token Service (STS) w federacyjnym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="cfea2-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="cfea2-142">Domyślnie token jest tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="cfea2-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="cfea2-143">Aby uzyskać więcej informacji, zobacz [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="cfea2-143">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="cfea2-144">i [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="cfea2-144">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="cfea2-145">Ta sekcja zawiera elementy umożliwia konfigurowanie lokalnego wystawcy tokenów lub zachowania używane z usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="cfea2-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="cfea2-146">Aby uzyskać instrukcje dotyczące konfigurowania klienta do używania wystawcy lokalnego, zobacz [porady: Konfigurowanie lokalnego wystawcy](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="cfea2-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfea2-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfea2-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="cfea2-148">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="cfea2-148">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="cfea2-149">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="cfea2-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="cfea2-150">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="cfea2-150">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="cfea2-151">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="cfea2-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="cfea2-152">Instrukcje: tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="cfea2-152">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="cfea2-153">Instrukcje: konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="cfea2-153">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="cfea2-154">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="cfea2-154">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
