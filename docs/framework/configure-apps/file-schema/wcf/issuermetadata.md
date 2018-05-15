---
title: '&lt;issuerMetadata&gt;'
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 5f6b8d2f861c4d64a3b81407de4ce13b42d9b864
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="00abd-102">&lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="00abd-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="00abd-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="00abd-103">\<system.serviceModel></span></span>  
<span data-ttu-id="00abd-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="00abd-104">\<bindings></span></span>  
<span data-ttu-id="00abd-105">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="00abd-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="00abd-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="00abd-106">\<binding></span></span>  
<span data-ttu-id="00abd-107">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="00abd-107">\<security></span></span>  
<span data-ttu-id="00abd-108">\<message></span><span class="sxs-lookup"><span data-stu-id="00abd-108">\<message></span></span>  
<span data-ttu-id="00abd-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="00abd-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00abd-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="00abd-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00abd-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="00abd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="00abd-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="00abd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00abd-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="00abd-113">Attributes</span></span>  
  
|<span data-ttu-id="00abd-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="00abd-114">Attribute</span></span>|<span data-ttu-id="00abd-115">Opis</span><span class="sxs-lookup"><span data-stu-id="00abd-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00abd-116">adres</span><span class="sxs-lookup"><span data-stu-id="00abd-116">address</span></span>|<span data-ttu-id="00abd-117">Wymagane `string` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="00abd-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="00abd-118">Określa adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="00abd-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="00abd-119">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="00abd-119">The address must be an absolute URI.</span></span> <span data-ttu-id="00abd-120">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="00abd-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00abd-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="00abd-121">Child Elements</span></span>  
  
|<span data-ttu-id="00abd-122">Element</span><span class="sxs-lookup"><span data-stu-id="00abd-122">Element</span></span>|<span data-ttu-id="00abd-123">Opis</span><span class="sxs-lookup"><span data-stu-id="00abd-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00abd-124">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="00abd-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="00abd-125">Kolekcja nagłówków adresu.</span><span class="sxs-lookup"><span data-stu-id="00abd-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="00abd-126">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="00abd-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="00abd-127">Tożsamości, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.</span><span class="sxs-lookup"><span data-stu-id="00abd-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="00abd-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="00abd-128">Parent Elements</span></span>  
  
|<span data-ttu-id="00abd-129">Element</span><span class="sxs-lookup"><span data-stu-id="00abd-129">Element</span></span>|<span data-ttu-id="00abd-130">Opis</span><span class="sxs-lookup"><span data-stu-id="00abd-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00abd-131">\<message></span><span class="sxs-lookup"><span data-stu-id="00abd-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="00abd-132">Określa ustawienia zabezpieczenia na poziomie komunikatu [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="00abd-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00abd-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00abd-133">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>  
 [<span data-ttu-id="00abd-134">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="00abd-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="00abd-135">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="00abd-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="00abd-136">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="00abd-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="00abd-137">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="00abd-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
