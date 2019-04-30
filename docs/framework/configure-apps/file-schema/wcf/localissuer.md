---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 9a51387cd75d57a6828ecde1dcd788b056f7e27a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766405"
---
# <a name="localissuer"></a><span data-ttu-id="e2927-101">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="e2927-101">\<localIssuer></span></span>
<span data-ttu-id="e2927-102">Określa adres i powiązanie wystawcy lokalnego, można użyć do uzyskania tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="e2927-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="e2927-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e2927-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e2927-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="e2927-104">\<behaviors></span></span>  
<span data-ttu-id="e2927-105">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="e2927-105">endpointBehaviors section</span></span>  
<span data-ttu-id="e2927-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="e2927-106">\<behavior></span></span>  
<span data-ttu-id="e2927-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e2927-107">\<clientCredentials></span></span>  
<span data-ttu-id="e2927-108">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="e2927-108">\<issuedToken></span></span>  
<span data-ttu-id="e2927-109">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="e2927-109">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2927-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2927-110">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2927-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e2927-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e2927-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e2927-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2927-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e2927-113">Attributes</span></span>  
  
|<span data-ttu-id="e2927-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e2927-114">Attribute</span></span>|<span data-ttu-id="e2927-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e2927-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2927-116">adres</span><span class="sxs-lookup"><span data-stu-id="e2927-116">address</span></span>|<span data-ttu-id="e2927-117">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="e2927-117">Required string.</span></span> <span data-ttu-id="e2927-118">Określa identyfikator URI wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="e2927-118">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="e2927-119">powiązanie</span><span class="sxs-lookup"><span data-stu-id="e2927-119">binding</span></span>|<span data-ttu-id="e2927-120">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="e2927-120">Optional string.</span></span> <span data-ttu-id="e2927-121">Jedno z powiązań dostarczanych przez system.</span><span class="sxs-lookup"><span data-stu-id="e2927-121">One of the system-provided bindings.</span></span> <span data-ttu-id="e2927-122">Aby uzyskać listę, zobacz [powiązania System-Provided](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="e2927-122">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="e2927-123">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="e2927-123">bindingConfiguration</span></span>|<span data-ttu-id="e2927-124">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="e2927-124">Optional string.</span></span> <span data-ttu-id="e2927-125">Określa konfigurację powiązania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e2927-125">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2927-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e2927-126">Child Elements</span></span>  
  
|<span data-ttu-id="e2927-127">Element</span><span class="sxs-lookup"><span data-stu-id="e2927-127">Element</span></span>|<span data-ttu-id="e2927-128">Opis</span><span class="sxs-lookup"><span data-stu-id="e2927-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2927-129">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="e2927-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="e2927-130">Określa informacje o tożsamości dla wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="e2927-130">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="e2927-131">\<headers></span><span class="sxs-lookup"><span data-stu-id="e2927-131">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="e2927-132">Kolekcja nagłówków adresowych, które są wymagane do prawidłowego adresowania wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="e2927-132">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="e2927-133">Możesz użyć `add` — słowo kluczowe, aby dodać nagłówek do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e2927-133">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2927-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e2927-134">Parent Elements</span></span>  
  
|<span data-ttu-id="e2927-135">Element</span><span class="sxs-lookup"><span data-stu-id="e2927-135">Element</span></span>|<span data-ttu-id="e2927-136">Opis</span><span class="sxs-lookup"><span data-stu-id="e2927-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2927-137">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="e2927-137">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="e2927-138">Określa niestandardowy token używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="e2927-138">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2927-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2927-139">Remarks</span></span>  
 <span data-ttu-id="e2927-140">W przypadku uzyskania wystawiony token z Usługa tokenu zabezpieczającego (STS), należy skonfigurować aplikację klienta przy użyciu adresu i powiązania do użycia do komunikowania się z usługi STS.</span><span class="sxs-lookup"><span data-stu-id="e2927-140">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="e2927-141">Gdy <xref:System.ServiceModel.WSFederationHttpBinding> nie dostarcza adres URL dla usługi tokenu zabezpieczającego lub gdy adres wystawcy powiązania federacyjnego `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` lub `null`, klienta programu Windows Communication Foundation (WCF) kanału używa wartości określonych przez `address`i `binding` nawiązać połączenia z usługą STS uzyskać Wystawiony token.</span><span class="sxs-lookup"><span data-stu-id="e2927-141">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="e2927-142">Aby uzyskać więcej informacji na temat konfigurowania lokalnego wystawcy, zobacz [jak: Konfigurowanie lokalnego wystawcy](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="e2927-142">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2927-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2927-143">Example</span></span>  
 <span data-ttu-id="e2927-144">Poniższy przykład ustawia `address`, `binding`, i `bindingConfiguration` atrybuty `localIssuer` elementu.</span><span class="sxs-lookup"><span data-stu-id="e2927-144">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e2927-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2927-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="e2927-146">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e2927-146">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e2927-147">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="e2927-147">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="e2927-148">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="e2927-148">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e2927-149">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e2927-149">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e2927-150">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="e2927-150">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e2927-151">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="e2927-151">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e2927-152">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="e2927-152">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="e2927-153">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="e2927-153">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="e2927-154">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="e2927-154">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
