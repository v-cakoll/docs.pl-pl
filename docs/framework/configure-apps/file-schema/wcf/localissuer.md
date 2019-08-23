---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 4ec5a99139112ae600c1c2bc44feb6d3f62da1e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931738"
---
# <a name="localissuer"></a><span data-ttu-id="0986e-101">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="0986e-101">\<localIssuer></span></span>
<span data-ttu-id="0986e-102">Określa adres i powiązanie wystawcy lokalnego używanego do uzyskania tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="0986e-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="0986e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0986e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0986e-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="0986e-104">\<behaviors></span></span>  
<span data-ttu-id="0986e-105">Sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="0986e-105">endpointBehaviors section</span></span>  
<span data-ttu-id="0986e-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="0986e-106">\<behavior></span></span>  
<span data-ttu-id="0986e-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="0986e-107">\<clientCredentials></span></span>  
<span data-ttu-id="0986e-108">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="0986e-108">\<issuedToken></span></span>  
<span data-ttu-id="0986e-109">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="0986e-109">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0986e-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="0986e-110">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0986e-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0986e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0986e-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0986e-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0986e-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0986e-113">Attributes</span></span>  
  
|<span data-ttu-id="0986e-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0986e-114">Attribute</span></span>|<span data-ttu-id="0986e-115">Opis</span><span class="sxs-lookup"><span data-stu-id="0986e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0986e-116">adres</span><span class="sxs-lookup"><span data-stu-id="0986e-116">address</span></span>|<span data-ttu-id="0986e-117">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="0986e-117">Required string.</span></span> <span data-ttu-id="0986e-118">Określa identyfikator URI wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="0986e-118">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="0986e-119">powiązanie</span><span class="sxs-lookup"><span data-stu-id="0986e-119">binding</span></span>|<span data-ttu-id="0986e-120">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="0986e-120">Optional string.</span></span> <span data-ttu-id="0986e-121">Jedno z powiązań dostarczonych przez system.</span><span class="sxs-lookup"><span data-stu-id="0986e-121">One of the system-provided bindings.</span></span> <span data-ttu-id="0986e-122">Aby uzyskać listę, zobacz [powiązania dostarczone przez system](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="0986e-122">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="0986e-123">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="0986e-123">bindingConfiguration</span></span>|<span data-ttu-id="0986e-124">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="0986e-124">Optional string.</span></span> <span data-ttu-id="0986e-125">Określa konfigurację powiązania znalezioną w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0986e-125">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0986e-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0986e-126">Child Elements</span></span>  
  
|<span data-ttu-id="0986e-127">Element</span><span class="sxs-lookup"><span data-stu-id="0986e-127">Element</span></span>|<span data-ttu-id="0986e-128">Opis</span><span class="sxs-lookup"><span data-stu-id="0986e-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0986e-129">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="0986e-129">\<identity></span></span>](identity.md)|<span data-ttu-id="0986e-130">Określa informacje o tożsamości dla wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="0986e-130">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="0986e-131">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="0986e-131">\<headers></span></span>](headers-element.md)|<span data-ttu-id="0986e-132">Kolekcja nagłówków adresów, które są wymagane w celu prawidłowego adresowania wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="0986e-132">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="0986e-133">Możesz użyć słowa kluczowego, `add` aby dodać nagłówek do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0986e-133">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0986e-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0986e-134">Parent Elements</span></span>  
  
|<span data-ttu-id="0986e-135">Element</span><span class="sxs-lookup"><span data-stu-id="0986e-135">Element</span></span>|<span data-ttu-id="0986e-136">Opis</span><span class="sxs-lookup"><span data-stu-id="0986e-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0986e-137">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="0986e-137">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="0986e-138">Określa niestandardowy token używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="0986e-138">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0986e-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0986e-139">Remarks</span></span>  
 <span data-ttu-id="0986e-140">W przypadku uzyskiwania wystawionego tokenu z usługi tokenu zabezpieczającego (STS), aplikacja kliencka musi być skonfigurowana przy użyciu adresu i powiązania, które ma być używane do komunikacji z usługą STS.</span><span class="sxs-lookup"><span data-stu-id="0986e-140">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="0986e-141">Gdy program `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null`nie poda adresu URL usługi tokenu zabezpieczającego lub gdy adres wystawcy powiązania federacyjnego to lub, kanał Windows Communication Foundation (WCF) klienta używa wartości określonych przez <xref:System.ServiceModel.WSFederationHttpBinding> `address` i`binding` aby komunikować się z usługą STS w celu uzyskania wystawionego tokenu.</span><span class="sxs-lookup"><span data-stu-id="0986e-141">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="0986e-142">Aby uzyskać więcej informacji na temat konfigurowania wystawcy [lokalnego, zobacz How to: Konfigurowanie lokalnego wystawcy](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="0986e-142">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0986e-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="0986e-143">Example</span></span>  
 <span data-ttu-id="0986e-144">W `address`poniższym przykładzie ustawiono atrybuty, `binding` `bindingConfiguration` , i `localIssuer` elementu.</span><span class="sxs-lookup"><span data-stu-id="0986e-144">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0986e-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0986e-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="0986e-146">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="0986e-146">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="0986e-147">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="0986e-147">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="0986e-148">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="0986e-148">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0986e-149">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="0986e-149">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="0986e-150">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="0986e-150">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0986e-151">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="0986e-151">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0986e-152">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="0986e-152">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="0986e-153">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="0986e-153">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="0986e-154">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="0986e-154">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
