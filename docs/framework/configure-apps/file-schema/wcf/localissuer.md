---
title: '&lt;localIssuer&gt;'
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 893ac2cb0e6c54beae68e2607c31564baafd95fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527552"
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="37441-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="37441-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="37441-103">Określa adres i powiązanie wystawcy lokalnego, można użyć do uzyskania tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="37441-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="37441-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="37441-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="37441-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="37441-105">\<behaviors></span></span>  
<span data-ttu-id="37441-106">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="37441-106">endpointBehaviors section</span></span>  
<span data-ttu-id="37441-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="37441-107">\<behavior></span></span>  
<span data-ttu-id="37441-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="37441-108">\<clientCredentials></span></span>  
<span data-ttu-id="37441-109">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="37441-109">\<issuedToken></span></span>  
<span data-ttu-id="37441-110">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="37441-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37441-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="37441-111">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37441-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="37441-112">Attributes and Elements</span></span>  
 <span data-ttu-id="37441-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="37441-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37441-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="37441-114">Attributes</span></span>  
  
|<span data-ttu-id="37441-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="37441-115">Attribute</span></span>|<span data-ttu-id="37441-116">Opis</span><span class="sxs-lookup"><span data-stu-id="37441-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37441-117">adres</span><span class="sxs-lookup"><span data-stu-id="37441-117">address</span></span>|<span data-ttu-id="37441-118">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="37441-118">Required string.</span></span> <span data-ttu-id="37441-119">Określa identyfikator URI wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="37441-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="37441-120">powiązanie</span><span class="sxs-lookup"><span data-stu-id="37441-120">binding</span></span>|<span data-ttu-id="37441-121">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="37441-121">Optional string.</span></span> <span data-ttu-id="37441-122">Jedno z powiązań dostarczanych przez system.</span><span class="sxs-lookup"><span data-stu-id="37441-122">One of the system-provided bindings.</span></span> <span data-ttu-id="37441-123">Aby uzyskać listę, zobacz [powiązania System-Provided](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="37441-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="37441-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="37441-124">bindingConfiguration</span></span>|<span data-ttu-id="37441-125">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="37441-125">Optional string.</span></span> <span data-ttu-id="37441-126">Określa konfigurację powiązania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="37441-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37441-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="37441-127">Child Elements</span></span>  
  
|<span data-ttu-id="37441-128">Element</span><span class="sxs-lookup"><span data-stu-id="37441-128">Element</span></span>|<span data-ttu-id="37441-129">Opis</span><span class="sxs-lookup"><span data-stu-id="37441-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37441-130">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="37441-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="37441-131">Określa informacje o tożsamości dla wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="37441-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="37441-132">\<headers></span><span class="sxs-lookup"><span data-stu-id="37441-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="37441-133">Kolekcja nagłówków adresowych, które są wymagane do prawidłowego adresowania wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="37441-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="37441-134">Możesz użyć `add` — słowo kluczowe, aby dodać nagłówek do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="37441-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37441-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="37441-135">Parent Elements</span></span>  
  
|<span data-ttu-id="37441-136">Element</span><span class="sxs-lookup"><span data-stu-id="37441-136">Element</span></span>|<span data-ttu-id="37441-137">Opis</span><span class="sxs-lookup"><span data-stu-id="37441-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37441-138">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="37441-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="37441-139">Określa niestandardowy token używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="37441-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37441-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37441-140">Remarks</span></span>  
 <span data-ttu-id="37441-141">W przypadku uzyskania wystawiony token z Usługa tokenu zabezpieczającego (STS), należy skonfigurować aplikację klienta przy użyciu adresu i powiązania do użycia do komunikowania się z usługi STS.</span><span class="sxs-lookup"><span data-stu-id="37441-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="37441-142">Gdy <xref:System.ServiceModel.WSFederationHttpBinding> nie dostarcza adres URL dla usługi tokenu zabezpieczającego lub gdy adres wystawcy powiązania federacyjnego `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` lub `null`, klienta programu Windows Communication Foundation (WCF) kanału używa wartości określonych przez `address`i `binding` nawiązać połączenia z usługą STS uzyskać Wystawiony token.</span><span class="sxs-lookup"><span data-stu-id="37441-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="37441-143">Aby uzyskać więcej informacji na temat konfigurowania lokalnego wystawcy, zobacz [jak: Konfigurowanie lokalnego wystawcy](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="37441-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="37441-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="37441-144">Example</span></span>  
 <span data-ttu-id="37441-145">Poniższy przykład ustawia `address`, `binding`, i `bindingConfiguration` atrybuty `localIssuer` elementu.</span><span class="sxs-lookup"><span data-stu-id="37441-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="MyEndpointBehavior">
        <clientCredentials>
          <issuedToken cacheIssuedTokens="false"
                       defaultKeyEntropyMode="ClientEntropy">
            <localIssuer address="net.tcp://cohowinery/tokens"
                         binding="netTcpBinding"
                         bindingConfiguration="myTcpBindingConfig" />
          </issuedToken>
        </clientCredentials>
      </behavior>
    </endpointBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="37441-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37441-146">See also</span></span>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="37441-147">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="37441-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="37441-148">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="37441-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="37441-149">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="37441-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="37441-150">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="37441-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="37441-151">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="37441-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="37441-152">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="37441-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="37441-153">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="37441-153">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="37441-154">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="37441-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="37441-155">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="37441-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
