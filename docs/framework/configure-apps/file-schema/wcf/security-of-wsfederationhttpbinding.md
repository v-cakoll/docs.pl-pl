---
title: '&lt;security&gt; w &lt;wsFederationHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2f2a25f06aa90dc1cbb63f4f91d6032ef017dab2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749806"
---
# <a name="ltsecuritygt-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="fbc78-102">&lt;security&gt; w &lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="fbc78-102">&lt;security&gt; of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="fbc78-103">Definiuje ustawienia zabezpieczeń [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="fbc78-103">Defines the security settings of the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="fbc78-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fbc78-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fbc78-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="fbc78-105">\<bindings></span></span>  
<span data-ttu-id="fbc78-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="fbc78-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="fbc78-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="fbc78-107">\<binding></span></span>  
<span data-ttu-id="fbc78-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="fbc78-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbc78-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbc78-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbc78-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fbc78-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fbc78-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fbc78-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbc78-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fbc78-112">Attributes</span></span>  
  
|<span data-ttu-id="fbc78-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fbc78-113">Attribute</span></span>|<span data-ttu-id="fbc78-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fbc78-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fbc78-115">Tryb</span><span class="sxs-lookup"><span data-stu-id="fbc78-115">Mode</span></span>|<span data-ttu-id="fbc78-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="fbc78-116">Optional.</span></span> <span data-ttu-id="fbc78-117">Określa typ zabezpieczeń, która została zastosowana.</span><span class="sxs-lookup"><span data-stu-id="fbc78-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="fbc78-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="fbc78-118">The default value is `Message`.</span></span> <span data-ttu-id="fbc78-119">Ten atrybut jest typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="fbc78-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="fbc78-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="fbc78-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="fbc78-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="fbc78-121">Value</span></span>|<span data-ttu-id="fbc78-122">Opis</span><span class="sxs-lookup"><span data-stu-id="fbc78-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fbc78-123">Brak</span><span class="sxs-lookup"><span data-stu-id="fbc78-123">None</span></span>|<span data-ttu-id="fbc78-124">Komunikatu protokołu SOAP nie jest bezpieczne podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="fbc78-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="fbc78-125">Komunikat</span><span class="sxs-lookup"><span data-stu-id="fbc78-125">Message</span></span>|<span data-ttu-id="fbc78-126">Korzystanie z zabezpieczeń komunikatów SOAP są udostępniane integralności, poufność, uwierzytelnianie serwera i uwierzytelnianie klienta.</span><span class="sxs-lookup"><span data-stu-id="fbc78-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="fbc78-127">Domyślnie treści zostaje zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="fbc78-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="fbc78-128">Usługa musi być skonfigurowana przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="fbc78-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="fbc78-129">Uwierzytelnianie klienta jest oparta na token wystawiony przez usługę tokenu zabezpieczającego klienta</span><span class="sxs-lookup"><span data-stu-id="fbc78-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="fbc78-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="fbc78-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="fbc78-131">Uwierzytelnianie integralności i poufności serwera są udostępniane przez protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="fbc78-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="fbc78-132">Usługa musi być skonfigurowana przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="fbc78-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="fbc78-133">Uwierzytelnianie klienta jest dostarczany za pomocą zabezpieczeń wiadomości SOAP i opierają się na token wystawiony do klienta przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="fbc78-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fbc78-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fbc78-134">Child Elements</span></span>  
  
|<span data-ttu-id="fbc78-135">Element</span><span class="sxs-lookup"><span data-stu-id="fbc78-135">Element</span></span>|<span data-ttu-id="fbc78-136">Opis</span><span class="sxs-lookup"><span data-stu-id="fbc78-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbc78-137">\<message></span><span class="sxs-lookup"><span data-stu-id="fbc78-137">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="fbc78-138">Definiuje ustawienia zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fbc78-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="fbc78-139">Ten element jest typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="fbc78-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fbc78-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fbc78-140">Parent Elements</span></span>  
  
|<span data-ttu-id="fbc78-141">Element</span><span class="sxs-lookup"><span data-stu-id="fbc78-141">Element</span></span>|<span data-ttu-id="fbc78-142">Opis</span><span class="sxs-lookup"><span data-stu-id="fbc78-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbc78-143">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="fbc78-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="fbc78-144">Definiuje wszystkie możliwości powiązania [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="fbc78-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbc78-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbc78-145">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="fbc78-146">Instrukcje: tworzenie elementu WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="fbc78-146">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="fbc78-147">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="fbc78-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="fbc78-148">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="fbc78-148">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="fbc78-149">Powiązania</span><span class="sxs-lookup"><span data-stu-id="fbc78-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fbc78-150">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="fbc78-150">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="fbc78-151">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="fbc78-151">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="fbc78-152">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="fbc78-152">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
