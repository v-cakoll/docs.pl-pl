---
title: '&lt;wystawcy&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e034b3ed0813d621ed86c2c3e86bb901ab39e40b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuergt"></a><span data-ttu-id="9a017-102">&lt;wystawcy&gt;</span><span class="sxs-lookup"><span data-stu-id="9a017-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="9a017-103">Określa zabezpieczeń tokenu usługi (STS), która wystawia tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="9a017-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="9a017-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9a017-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9a017-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="9a017-105">\<bindings></span></span>  
<span data-ttu-id="9a017-106">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="9a017-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="9a017-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="9a017-107">\<binding></span></span>  
<span data-ttu-id="9a017-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="9a017-108">\<security></span></span>  
<span data-ttu-id="9a017-109">\<komunikat ></span><span class="sxs-lookup"><span data-stu-id="9a017-109">\<message></span></span>  
<span data-ttu-id="9a017-110">\<Wystawca ></span><span class="sxs-lookup"><span data-stu-id="9a017-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a017-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a017-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" >  
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
</issuer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a017-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9a017-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9a017-113">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9a017-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a017-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9a017-114">Attributes</span></span>  
  
|<span data-ttu-id="9a017-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9a017-115">Attribute</span></span>|<span data-ttu-id="9a017-116">Opis</span><span class="sxs-lookup"><span data-stu-id="9a017-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9a017-117">adres</span><span class="sxs-lookup"><span data-stu-id="9a017-117">address</span></span>|<span data-ttu-id="9a017-118">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="9a017-118">Required string.</span></span> <span data-ttu-id="9a017-119">Adres URL usługi STS.</span><span class="sxs-lookup"><span data-stu-id="9a017-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a017-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9a017-120">Child Elements</span></span>  
  
|<span data-ttu-id="9a017-121">Element</span><span class="sxs-lookup"><span data-stu-id="9a017-121">Element</span></span>|<span data-ttu-id="9a017-122">Opis</span><span class="sxs-lookup"><span data-stu-id="9a017-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a017-123">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="9a017-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="9a017-124">Kolekcja nagłówków adresu dla punktów końcowych, które można utworzyć konstruktora.</span><span class="sxs-lookup"><span data-stu-id="9a017-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="9a017-125">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="9a017-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="9a017-126">Korzystając z wystawionego tokenu, określa ustawienia, które umożliwiają klienta do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="9a017-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9a017-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9a017-127">Parent Elements</span></span>  
  
|<span data-ttu-id="9a017-128">Element</span><span class="sxs-lookup"><span data-stu-id="9a017-128">Element</span></span>|<span data-ttu-id="9a017-129">Opis</span><span class="sxs-lookup"><span data-stu-id="9a017-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a017-130">\<komunikat ></span><span class="sxs-lookup"><span data-stu-id="9a017-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="9a017-131">Określa ustawienia zabezpieczenia na poziomie komunikatu [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="9a017-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a017-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a017-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="9a017-133">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="9a017-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="9a017-134">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="9a017-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="9a017-135">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="9a017-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="9a017-136">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="9a017-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="9a017-137">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="9a017-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="9a017-138">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="9a017-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
