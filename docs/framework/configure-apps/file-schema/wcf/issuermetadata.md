---
title: '&lt;issuerMetadata&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28746481bd24eb0d80304456ea8f34f505a016b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="47165-102">&lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="47165-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="47165-103">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="47165-103">\<system.serviceModel></span></span>  
<span data-ttu-id="47165-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="47165-104">\<bindings></span></span>  
<span data-ttu-id="47165-105">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="47165-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="47165-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="47165-106">\<binding></span></span>  
<span data-ttu-id="47165-107">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="47165-107">\<security></span></span>  
<span data-ttu-id="47165-108">\<komunikat ></span><span class="sxs-lookup"><span data-stu-id="47165-108">\<message></span></span>  
<span data-ttu-id="47165-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="47165-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47165-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="47165-110">Syntax</span></span>  
  
```xml  
<issuerMetadata address=String" >  
   <headers>  
      <add name="String"  
                 namespace="String" />  
   </headers>  
   <identity>  
           <certificate encodedValue="String"/>  
      <certificateReference findValue="String"   
         isChainIncluded="Boolean"  
         storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
         storeLocation="LocalMachine/CurrentUser"  
                  x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
      <dns value="String"/>  
      <rsa value="String"/>  
      <servicePrincipalName value="String"/>  
      <usePrincipalName value="String"/>  
   </identity>  
</issuerMetadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47165-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="47165-111">Attributes and Elements</span></span>  
 <span data-ttu-id="47165-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="47165-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47165-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="47165-113">Attributes</span></span>  
  
|<span data-ttu-id="47165-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="47165-114">Attribute</span></span>|<span data-ttu-id="47165-115">Opis</span><span class="sxs-lookup"><span data-stu-id="47165-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47165-116">adres</span><span class="sxs-lookup"><span data-stu-id="47165-116">address</span></span>|<span data-ttu-id="47165-117">Wymagane `string` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="47165-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="47165-118">Określa adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="47165-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="47165-119">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="47165-119">The address must be an absolute URI.</span></span> <span data-ttu-id="47165-120">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="47165-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47165-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="47165-121">Child Elements</span></span>  
  
|<span data-ttu-id="47165-122">Element</span><span class="sxs-lookup"><span data-stu-id="47165-122">Element</span></span>|<span data-ttu-id="47165-123">Opis</span><span class="sxs-lookup"><span data-stu-id="47165-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47165-124">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="47165-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="47165-125">Kolekcja nagłówków adresu.</span><span class="sxs-lookup"><span data-stu-id="47165-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="47165-126">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="47165-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="47165-127">Tożsamości, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.</span><span class="sxs-lookup"><span data-stu-id="47165-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="47165-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="47165-128">Parent Elements</span></span>  
  
|<span data-ttu-id="47165-129">Element</span><span class="sxs-lookup"><span data-stu-id="47165-129">Element</span></span>|<span data-ttu-id="47165-130">Opis</span><span class="sxs-lookup"><span data-stu-id="47165-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47165-131">\<komunikat ></span><span class="sxs-lookup"><span data-stu-id="47165-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="47165-132">Określa ustawienia zabezpieczenia na poziomie komunikatu [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="47165-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47165-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47165-133">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>  
 [<span data-ttu-id="47165-134">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="47165-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="47165-135">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="47165-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="47165-136">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="47165-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="47165-137">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="47165-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
