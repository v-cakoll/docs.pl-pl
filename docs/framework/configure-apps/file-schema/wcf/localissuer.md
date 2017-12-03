---
title: '&lt;localIssuer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8836d9e57dd7c4d9cfdc20c5e4856e384e6d67b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="cda88-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="cda88-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="cda88-103">Określa adres i powiązanie wystawcy lokalnego używanego do uzyskania tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="cda88-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="cda88-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="cda88-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cda88-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="cda88-105">\<behaviors></span></span>  
<span data-ttu-id="cda88-106">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="cda88-106">endpointBehaviors section</span></span>  
<span data-ttu-id="cda88-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="cda88-107">\<behavior></span></span>  
<span data-ttu-id="cda88-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="cda88-108">\<clientCredentials></span></span>  
<span data-ttu-id="cda88-109">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="cda88-109">\<issuedToken></span></span>  
<span data-ttu-id="cda88-110">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="cda88-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cda88-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="cda88-111">Syntax</span></span>  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cda88-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cda88-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cda88-113">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cda88-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cda88-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cda88-114">Attributes</span></span>  
  
|<span data-ttu-id="cda88-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cda88-115">Attribute</span></span>|<span data-ttu-id="cda88-116">Opis</span><span class="sxs-lookup"><span data-stu-id="cda88-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cda88-117">adres</span><span class="sxs-lookup"><span data-stu-id="cda88-117">address</span></span>|<span data-ttu-id="cda88-118">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="cda88-118">Required string.</span></span> <span data-ttu-id="cda88-119">Określa identyfikator URI wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="cda88-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="cda88-120">powiązanie</span><span class="sxs-lookup"><span data-stu-id="cda88-120">binding</span></span>|<span data-ttu-id="cda88-121">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="cda88-121">Optional string.</span></span> <span data-ttu-id="cda88-122">Jedno z powiązań dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="cda88-122">One of the system-provided bindings.</span></span> <span data-ttu-id="cda88-123">Aby uzyskać listę, zobacz [powiązania System-Provided](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="cda88-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="cda88-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="cda88-124">bindingConfiguration</span></span>|<span data-ttu-id="cda88-125">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="cda88-125">Optional string.</span></span> <span data-ttu-id="cda88-126">Określa konfigurację powiązania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cda88-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cda88-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cda88-127">Child Elements</span></span>  
  
|<span data-ttu-id="cda88-128">Element</span><span class="sxs-lookup"><span data-stu-id="cda88-128">Element</span></span>|<span data-ttu-id="cda88-129">Opis</span><span class="sxs-lookup"><span data-stu-id="cda88-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cda88-130">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="cda88-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="cda88-131">Określa informacje o tożsamości wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="cda88-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="cda88-132">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="cda88-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="cda88-133">Kolekcja nagłówków adresowych, które są wymagane do prawidłowego adresowania wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="cda88-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="cda88-134">Można użyć `add` — słowo kluczowe, aby dodać nagłówek do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cda88-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cda88-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cda88-135">Parent Elements</span></span>  
  
|<span data-ttu-id="cda88-136">Element</span><span class="sxs-lookup"><span data-stu-id="cda88-136">Element</span></span>|<span data-ttu-id="cda88-137">Opis</span><span class="sxs-lookup"><span data-stu-id="cda88-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cda88-138">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="cda88-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="cda88-139">Określa niestandardowy token używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="cda88-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cda88-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cda88-140">Remarks</span></span>  
 <span data-ttu-id="cda88-141">Podczas uzyskiwania wystawionego tokenu z zabezpieczeń tokenu usługi (STS), aplikacja klienta musi być skonfigurowana z adres i powiązanie na potrzeby komunikacji z STS.</span><span class="sxs-lookup"><span data-stu-id="cda88-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="cda88-142">Gdy <xref:System.ServiceModel.WSFederationHttpBinding> nie dostarcza adres URL usługi tokenu zabezpieczeń, lub gdy adres wystawcy wiązania federacyjnego jest http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous lub `null`, klienta [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] kanał używane wartości określone przez `address` i `binding` do komunikacji z STS uzyskanie wystawionego tokenu.</span><span class="sxs-lookup"><span data-stu-id="cda88-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous or `null`, the client's [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="cda88-143">Aby uzyskać więcej informacji na temat konfigurowania wystawcy lokalnego, zobacz [porady: Konfigurowanie lokalnego wystawcy](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="cda88-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cda88-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="cda88-144">Example</span></span>  
 <span data-ttu-id="cda88-145">W poniższym przykładzie `address`, `binding`, i `bindingConfiguration` atrybuty `localIssuer` elementu.</span><span class="sxs-lookup"><span data-stu-id="cda88-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cda88-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cda88-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="cda88-147">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="cda88-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="cda88-148">Porady: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="cda88-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="cda88-149">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="cda88-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="cda88-150">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="cda88-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="cda88-151">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="cda88-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="cda88-152">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="cda88-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="cda88-153">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="cda88-153">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="cda88-154">Porady: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="cda88-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="cda88-155">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="cda88-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
