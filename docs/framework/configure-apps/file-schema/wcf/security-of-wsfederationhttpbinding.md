---
title: '&lt;security&gt; w &lt;wsFederationHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 9473fa062867383f84ba5931c394f1ac665a74fb
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199295"
---
# <a name="ltsecuritygt-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="6efe8-102">&lt;security&gt; w &lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="6efe8-102">&lt;security&gt; of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="6efe8-103">Definiuje ustawienia zabezpieczeń [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6efe8-103">Defines the security settings of the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="6efe8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6efe8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6efe8-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="6efe8-105">\<bindings></span></span>  
<span data-ttu-id="6efe8-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="6efe8-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="6efe8-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="6efe8-107">\<binding></span></span>  
<span data-ttu-id="6efe8-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="6efe8-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6efe8-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="6efe8-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6efe8-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6efe8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6efe8-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6efe8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6efe8-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6efe8-112">Attributes</span></span>  
  
|<span data-ttu-id="6efe8-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6efe8-113">Attribute</span></span>|<span data-ttu-id="6efe8-114">Opis</span><span class="sxs-lookup"><span data-stu-id="6efe8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6efe8-115">Tryb</span><span class="sxs-lookup"><span data-stu-id="6efe8-115">Mode</span></span>|<span data-ttu-id="6efe8-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="6efe8-116">Optional.</span></span> <span data-ttu-id="6efe8-117">Określa typ zabezpieczeń, która jest stosowana.</span><span class="sxs-lookup"><span data-stu-id="6efe8-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="6efe8-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="6efe8-118">The default value is `Message`.</span></span> <span data-ttu-id="6efe8-119">Ten atrybut jest typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="6efe8-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6efe8-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="6efe8-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="6efe8-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="6efe8-121">Value</span></span>|<span data-ttu-id="6efe8-122">Opis</span><span class="sxs-lookup"><span data-stu-id="6efe8-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6efe8-123">Brak</span><span class="sxs-lookup"><span data-stu-id="6efe8-123">None</span></span>|<span data-ttu-id="6efe8-124">Komunikat protokołu SOAP nie jest bezpieczne podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="6efe8-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="6efe8-125">Komunikat</span><span class="sxs-lookup"><span data-stu-id="6efe8-125">Message</span></span>|<span data-ttu-id="6efe8-126">Integralność, poufności, uwierzytelnianie serwera i uwierzytelnianie klienta znajdują się korzystanie z zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="6efe8-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="6efe8-127">Domyślnie treść jest zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="6efe8-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="6efe8-128">Usługa musi zostać skonfigurowane przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="6efe8-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="6efe8-129">Uwierzytelnianie klienta jest oparty na token wystawiony przez usługę tokenu zabezpieczającego klienta</span><span class="sxs-lookup"><span data-stu-id="6efe8-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="6efe8-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="6efe8-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="6efe8-131">Integralność, poufności i serwerem uwierzytelniania są dostarczane przez protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6efe8-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="6efe8-132">Usługa musi zostać skonfigurowane przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="6efe8-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="6efe8-133">Uwierzytelnianie klienta znajduje się za pomocą zabezpieczeń wiadomości protokołu SOAP i opiera się na token wystawiony do klienta przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="6efe8-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6efe8-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6efe8-134">Child Elements</span></span>  
  
|<span data-ttu-id="6efe8-135">Element</span><span class="sxs-lookup"><span data-stu-id="6efe8-135">Element</span></span>|<span data-ttu-id="6efe8-136">Opis</span><span class="sxs-lookup"><span data-stu-id="6efe8-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6efe8-137">\<message></span><span class="sxs-lookup"><span data-stu-id="6efe8-137">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="6efe8-138">Definiuje ustawienia zabezpieczeń na poziomie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="6efe8-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="6efe8-139">Ten element jest typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="6efe8-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6efe8-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6efe8-140">Parent Elements</span></span>  
  
|<span data-ttu-id="6efe8-141">Element</span><span class="sxs-lookup"><span data-stu-id="6efe8-141">Element</span></span>|<span data-ttu-id="6efe8-142">Opis</span><span class="sxs-lookup"><span data-stu-id="6efe8-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6efe8-143">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="6efe8-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="6efe8-144">Definiuje wszystkie możliwości wiązania [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6efe8-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6efe8-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6efe8-145">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="6efe8-146">Instrukcje: tworzenie elementu WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6efe8-146">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="6efe8-147">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="6efe8-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="6efe8-148">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="6efe8-148">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="6efe8-149">Powiązania</span><span class="sxs-lookup"><span data-stu-id="6efe8-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6efe8-150">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="6efe8-150">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="6efe8-151">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="6efe8-151">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="6efe8-152">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="6efe8-152">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
