---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397864"
---
# <a name="localissuer"></a><span data-ttu-id="f85f7-101">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="f85f7-101">\<localIssuer></span></span>
<span data-ttu-id="f85f7-102">Określa adres i powiązanie wystawcy lokalnego używanego do uzyskania tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="f85f7-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
<span data-ttu-id="f85f7-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f85f7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f85f7-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f85f7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f85f7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f85f7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="f85f7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f85f7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="f85f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f85f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="f85f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Obiekt clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="f85f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="f85f7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="f85f7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="f85f7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<localIssuer >**</span><span class="sxs-lookup"><span data-stu-id="f85f7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f85f7-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="f85f7-111">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f85f7-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f85f7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f85f7-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f85f7-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f85f7-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f85f7-114">Attributes</span></span>  
  
|<span data-ttu-id="f85f7-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f85f7-115">Attribute</span></span>|<span data-ttu-id="f85f7-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f85f7-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f85f7-117">adres</span><span class="sxs-lookup"><span data-stu-id="f85f7-117">address</span></span>|<span data-ttu-id="f85f7-118">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="f85f7-118">Required string.</span></span> <span data-ttu-id="f85f7-119">Określa identyfikator URI wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="f85f7-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="f85f7-120">powiązanie</span><span class="sxs-lookup"><span data-stu-id="f85f7-120">binding</span></span>|<span data-ttu-id="f85f7-121">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="f85f7-121">Optional string.</span></span> <span data-ttu-id="f85f7-122">Jedno z powiązań dostarczonych przez system.</span><span class="sxs-lookup"><span data-stu-id="f85f7-122">One of the system-provided bindings.</span></span> <span data-ttu-id="f85f7-123">Aby uzyskać listę, zobacz [powiązania dostarczone przez system](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="f85f7-123">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="f85f7-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="f85f7-124">bindingConfiguration</span></span>|<span data-ttu-id="f85f7-125">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="f85f7-125">Optional string.</span></span> <span data-ttu-id="f85f7-126">Określa konfigurację powiązania znalezioną w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f85f7-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f85f7-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f85f7-127">Child Elements</span></span>  
  
|<span data-ttu-id="f85f7-128">Element</span><span class="sxs-lookup"><span data-stu-id="f85f7-128">Element</span></span>|<span data-ttu-id="f85f7-129">Opis</span><span class="sxs-lookup"><span data-stu-id="f85f7-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f85f7-130">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="f85f7-130">\<identity></span></span>](identity.md)|<span data-ttu-id="f85f7-131">Określa informacje o tożsamości dla wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="f85f7-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="f85f7-132">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="f85f7-132">\<headers></span></span>](headers-element.md)|<span data-ttu-id="f85f7-133">Kolekcja nagłówków adresów, które są wymagane w celu prawidłowego adresowania wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="f85f7-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="f85f7-134">Możesz użyć słowa kluczowego, `add` aby dodać nagłówek do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f85f7-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f85f7-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f85f7-135">Parent Elements</span></span>  
  
|<span data-ttu-id="f85f7-136">Element</span><span class="sxs-lookup"><span data-stu-id="f85f7-136">Element</span></span>|<span data-ttu-id="f85f7-137">Opis</span><span class="sxs-lookup"><span data-stu-id="f85f7-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f85f7-138">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="f85f7-138">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="f85f7-139">Określa niestandardowy token używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="f85f7-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f85f7-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f85f7-140">Remarks</span></span>  
 <span data-ttu-id="f85f7-141">W przypadku uzyskiwania wystawionego tokenu z usługi tokenu zabezpieczającego (STS), aplikacja kliencka musi być skonfigurowana przy użyciu adresu i powiązania, które ma być używane do komunikacji z usługą STS.</span><span class="sxs-lookup"><span data-stu-id="f85f7-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="f85f7-142">Gdy program `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null`nie poda adresu URL usługi tokenu zabezpieczającego lub gdy adres wystawcy powiązania federacyjnego to lub, kanał Windows Communication Foundation (WCF) klienta używa wartości określonych przez <xref:System.ServiceModel.WSFederationHttpBinding> `address` i`binding` aby komunikować się z usługą STS w celu uzyskania wystawionego tokenu.</span><span class="sxs-lookup"><span data-stu-id="f85f7-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="f85f7-143">Aby uzyskać więcej informacji na temat konfigurowania wystawcy [lokalnego, zobacz How to: Konfigurowanie lokalnego wystawcy](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="f85f7-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f85f7-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="f85f7-144">Example</span></span>  
 <span data-ttu-id="f85f7-145">W `address`poniższym przykładzie ustawiono atrybuty, `binding` `bindingConfiguration` , i `localIssuer` elementu.</span><span class="sxs-lookup"><span data-stu-id="f85f7-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f85f7-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f85f7-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="f85f7-147">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="f85f7-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="f85f7-148">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="f85f7-148">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="f85f7-149">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="f85f7-149">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="f85f7-150">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="f85f7-150">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="f85f7-151">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="f85f7-151">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="f85f7-152">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="f85f7-152">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f85f7-153">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="f85f7-153">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="f85f7-154">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="f85f7-154">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="f85f7-155">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="f85f7-155">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
