---
title: '&lt;security&gt; w &lt;wsFederationHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 333379096b7bfe37d043c58763b76b72f2f719d1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="421c2-102">&lt;security&gt; w &lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="421c2-102">&lt;security&gt; of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="421c2-103">Definiuje ustawienia zabezpieczeń [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="421c2-103">Defines the security settings of the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="421c2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="421c2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="421c2-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="421c2-105">\<bindings></span></span>  
<span data-ttu-id="421c2-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="421c2-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="421c2-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="421c2-107">\<binding></span></span>  
<span data-ttu-id="421c2-108">\<security></span><span class="sxs-lookup"><span data-stu-id="421c2-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="421c2-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="421c2-109">Syntax</span></span>  
  
```xml  
<wsFederationBinding>  
    <binding >  
       <security mode="None/Message/TransportWithMessageCredential">  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
            <claimTypeRequirements>  
               <add claimType="URI"  
                    isOptional="Boolean" />  
            </claimTypeRequirements>  
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
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
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
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
               </identity>  
                        </issuerMetadata>  
            <tokenRequestParameters>  
               <xmlElement>  
               </xmlElement>  
            </tokenRequestParameters>  
         </message>  
       </security>  
    </binding>  
</wsFederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="421c2-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="421c2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="421c2-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="421c2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="421c2-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="421c2-112">Attributes</span></span>  
  
|<span data-ttu-id="421c2-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="421c2-113">Attribute</span></span>|<span data-ttu-id="421c2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="421c2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="421c2-115">Tryb</span><span class="sxs-lookup"><span data-stu-id="421c2-115">Mode</span></span>|<span data-ttu-id="421c2-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="421c2-116">Optional.</span></span> <span data-ttu-id="421c2-117">Określa typ zabezpieczeń, która została zastosowana.</span><span class="sxs-lookup"><span data-stu-id="421c2-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="421c2-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="421c2-118">The default value is `Message`.</span></span> <span data-ttu-id="421c2-119">Ten atrybut jest typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="421c2-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="421c2-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="421c2-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="421c2-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="421c2-121">Value</span></span>|<span data-ttu-id="421c2-122">Opis</span><span class="sxs-lookup"><span data-stu-id="421c2-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="421c2-123">Brak</span><span class="sxs-lookup"><span data-stu-id="421c2-123">None</span></span>|<span data-ttu-id="421c2-124">Komunikatu protokołu SOAP nie jest bezpieczne podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="421c2-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="421c2-125">Komunikat</span><span class="sxs-lookup"><span data-stu-id="421c2-125">Message</span></span>|<span data-ttu-id="421c2-126">Korzystanie z zabezpieczeń komunikatów SOAP są udostępniane integralności, poufność, uwierzytelnianie serwera i uwierzytelnianie klienta.</span><span class="sxs-lookup"><span data-stu-id="421c2-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="421c2-127">Domyślnie treści zostaje zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="421c2-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="421c2-128">Usługa musi być skonfigurowana przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="421c2-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="421c2-129">Uwierzytelnianie klienta jest oparta na token wystawiony przez usługę tokenu zabezpieczającego klienta</span><span class="sxs-lookup"><span data-stu-id="421c2-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="421c2-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="421c2-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="421c2-131">Uwierzytelnianie integralności i poufności serwera są udostępniane przez protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="421c2-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="421c2-132">Usługa musi być skonfigurowana przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="421c2-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="421c2-133">Uwierzytelnianie klienta jest dostarczany za pomocą zabezpieczeń wiadomości SOAP i opierają się na token wystawiony do klienta przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="421c2-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="421c2-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="421c2-134">Child Elements</span></span>  
  
|<span data-ttu-id="421c2-135">Element</span><span class="sxs-lookup"><span data-stu-id="421c2-135">Element</span></span>|<span data-ttu-id="421c2-136">Opis</span><span class="sxs-lookup"><span data-stu-id="421c2-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="421c2-137">\<message></span><span class="sxs-lookup"><span data-stu-id="421c2-137">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="421c2-138">Definiuje ustawienia zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="421c2-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="421c2-139">Ten element jest typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="421c2-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="421c2-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="421c2-140">Parent Elements</span></span>  
  
|<span data-ttu-id="421c2-141">Element</span><span class="sxs-lookup"><span data-stu-id="421c2-141">Element</span></span>|<span data-ttu-id="421c2-142">Opis</span><span class="sxs-lookup"><span data-stu-id="421c2-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="421c2-143">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="421c2-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="421c2-144">Definiuje wszystkie możliwości powiązania [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="421c2-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="421c2-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="421c2-145">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="421c2-146">Instrukcje: tworzenie elementu WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="421c2-146">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="421c2-147">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="421c2-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="421c2-148">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="421c2-148">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="421c2-149">Powiązania</span><span class="sxs-lookup"><span data-stu-id="421c2-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="421c2-150">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="421c2-150">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="421c2-151">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="421c2-151">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="421c2-152">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="421c2-152">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
