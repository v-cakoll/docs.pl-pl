---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397864"
---
# \<localIssuer>
<span data-ttu-id="62671-101">Określa adres i powiązanie wystawcy lokalnego używanego do uzyskania tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="62671-101">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**  
  
## <a name="syntax"></a><span data-ttu-id="62671-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="62671-102">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62671-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="62671-103">Attributes and Elements</span></span>  
 <span data-ttu-id="62671-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="62671-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62671-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="62671-105">Attributes</span></span>  
  
|<span data-ttu-id="62671-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="62671-106">Attribute</span></span>|<span data-ttu-id="62671-107">Opis</span><span class="sxs-lookup"><span data-stu-id="62671-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62671-108">adres</span><span class="sxs-lookup"><span data-stu-id="62671-108">address</span></span>|<span data-ttu-id="62671-109">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="62671-109">Required string.</span></span> <span data-ttu-id="62671-110">Określa identyfikator URI wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="62671-110">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="62671-111">powiązanie</span><span class="sxs-lookup"><span data-stu-id="62671-111">binding</span></span>|<span data-ttu-id="62671-112">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="62671-112">Optional string.</span></span> <span data-ttu-id="62671-113">Jedno z powiązań dostarczonych przez system.</span><span class="sxs-lookup"><span data-stu-id="62671-113">One of the system-provided bindings.</span></span> <span data-ttu-id="62671-114">Aby uzyskać listę, zobacz [powiązania dostarczone przez system](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="62671-114">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="62671-115">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="62671-115">bindingConfiguration</span></span>|<span data-ttu-id="62671-116">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="62671-116">Optional string.</span></span> <span data-ttu-id="62671-117">Określa konfigurację powiązania znalezioną w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="62671-117">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62671-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="62671-118">Child Elements</span></span>  
  
|<span data-ttu-id="62671-119">Element</span><span class="sxs-lookup"><span data-stu-id="62671-119">Element</span></span>|<span data-ttu-id="62671-120">Opis</span><span class="sxs-lookup"><span data-stu-id="62671-120">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="62671-121">Określa informacje o tożsamości dla wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="62671-121">Specifies identity information for the local issuer.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="62671-122">Kolekcja nagłówków adresów, które są wymagane w celu prawidłowego adresowania wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="62671-122">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="62671-123">Możesz użyć `add` słowa kluczowego, aby dodać nagłówek do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="62671-123">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62671-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="62671-124">Parent Elements</span></span>  
  
|<span data-ttu-id="62671-125">Element</span><span class="sxs-lookup"><span data-stu-id="62671-125">Element</span></span>|<span data-ttu-id="62671-126">Opis</span><span class="sxs-lookup"><span data-stu-id="62671-126">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="62671-127">Określa niestandardowy token używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="62671-127">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62671-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62671-128">Remarks</span></span>  
 <span data-ttu-id="62671-129">W przypadku uzyskiwania wystawionego tokenu z usługi tokenu zabezpieczającego (STS), aplikacja kliencka musi być skonfigurowana przy użyciu adresu i powiązania, które ma być używane do komunikacji z usługą STS.</span><span class="sxs-lookup"><span data-stu-id="62671-129">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="62671-130">Jeśli nie <xref:System.ServiceModel.WSFederationHttpBinding> podasz adresu URL usługi tokenu zabezpieczającego lub gdy adres wystawcy powiązania federacyjnego to `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` lub `null` , kanał Windows Communication Foundation (WCF) klienta używa wartości określonych przez `address` i `binding` do komunikacji z usługą STS w celu uzyskania wystawionego tokenu.</span><span class="sxs-lookup"><span data-stu-id="62671-130">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="62671-131">Aby uzyskać więcej informacji na temat konfigurowania wystawcy lokalnego, zobacz [How to: Configure a Local wystawca](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="62671-131">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="62671-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="62671-132">Example</span></span>  
 <span data-ttu-id="62671-133">W poniższym przykładzie ustawiono `address` atrybuty, `binding` , i `bindingConfiguration` `localIssuer` elementu.</span><span class="sxs-lookup"><span data-stu-id="62671-133">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="62671-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62671-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="62671-135">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="62671-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="62671-136">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="62671-136">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="62671-137">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="62671-137">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="62671-138">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="62671-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="62671-139">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="62671-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="62671-140">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="62671-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="62671-141">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="62671-141">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="62671-142">Instrukcje: tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="62671-142">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="62671-143">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="62671-143">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
