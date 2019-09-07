---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 23fe19258e09e9e8a5e05a94ccef0e40ee1cb5fd
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400338"
---
# <a name="knowncertificates"></a><span data-ttu-id="9cfad-101">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="9cfad-101">\<knownCertificates></span></span>
<span data-ttu-id="9cfad-102">Reprezentuje kolekcję certyfikatów X. 509, które są dostarczane w celu uwierzytelnienia poświadczeń zabezpieczeń wydanych z usługi tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="9cfad-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
<span data-ttu-id="9cfad-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9cfad-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9cfad-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9cfad-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9cfad-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9cfad-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="9cfad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9cfad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="9cfad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9cfad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="9cfad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ServiceCredentials**](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="9cfad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="9cfad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenAuthentication >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="9cfad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="9cfad-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<knownCertificates >**</span><span class="sxs-lookup"><span data-stu-id="9cfad-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cfad-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="9cfad-111">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9cfad-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9cfad-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9cfad-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9cfad-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9cfad-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9cfad-114">Attributes</span></span>  
 <span data-ttu-id="9cfad-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="9cfad-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9cfad-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9cfad-116">Child Elements</span></span>  
  
|<span data-ttu-id="9cfad-117">Element</span><span class="sxs-lookup"><span data-stu-id="9cfad-117">Element</span></span>|<span data-ttu-id="9cfad-118">Opis</span><span class="sxs-lookup"><span data-stu-id="9cfad-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9cfad-119">\<add></span><span class="sxs-lookup"><span data-stu-id="9cfad-119">\<add></span></span>](add-of-knowncertificates.md)|<span data-ttu-id="9cfad-120">Dodaje certyfikat X. 509 do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9cfad-120">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9cfad-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9cfad-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9cfad-122">Element</span><span class="sxs-lookup"><span data-stu-id="9cfad-122">Element</span></span>|<span data-ttu-id="9cfad-123">Opis</span><span class="sxs-lookup"><span data-stu-id="9cfad-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9cfad-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="9cfad-124">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="9cfad-125">Określa token wystawiony jako poświadczenie usługi.</span><span class="sxs-lookup"><span data-stu-id="9cfad-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cfad-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9cfad-126">Remarks</span></span>  
 <span data-ttu-id="9cfad-127">Scenariusz wystawionego tokenu ma trzy etapy.</span><span class="sxs-lookup"><span data-stu-id="9cfad-127">The issued token scenario has three stages.</span></span> <span data-ttu-id="9cfad-128">Na pierwszym etapie klient próbujący uzyskać dostęp do usługi jest nazywany *usługą bezpiecznego tokenu*.</span><span class="sxs-lookup"><span data-stu-id="9cfad-128">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="9cfad-129">Usługa Secure Tokens następnie uwierzytelnia klienta, a następnie wystawia klientowi token, zwykle tokena "Security Assertions Markup Language" (SAML).</span><span class="sxs-lookup"><span data-stu-id="9cfad-129">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="9cfad-130">Klient następnie wraca do usługi przy użyciu tokenu.</span><span class="sxs-lookup"><span data-stu-id="9cfad-130">The client then returns to the service with the token.</span></span> <span data-ttu-id="9cfad-131">Usługa bada token dla danych, które umożliwiają usłudze uwierzytelnianie tokenu i w związku z tym klienta.</span><span class="sxs-lookup"><span data-stu-id="9cfad-131">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="9cfad-132">Aby uwierzytelnić token, certyfikat, którego używa usługa bezpiecznego tokenu, musi być znany usłudze.</span><span class="sxs-lookup"><span data-stu-id="9cfad-132">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="9cfad-133">Element > IssuedTokenAuthentication jest repozytorium dla wszystkich takich certyfikatów usługi Secure Token Service. [ \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="9cfad-133">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="9cfad-134">Aby dodać certyfikaty, użyj [ \<elementu knownCertificates >](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="9cfad-134">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="9cfad-135">Wstaw > dodawania dla każdego certyfikatu, jak pokazano w poniższym przykładzie. [ \<](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="9cfad-135">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 <span data-ttu-id="9cfad-136">Domyślnie certyfikaty muszą być uzyskiwane z usługi bezpiecznego tokenu.</span><span class="sxs-lookup"><span data-stu-id="9cfad-136">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="9cfad-137">Te "znane" certyfikaty zapewniają dostęp do usługi tylko uprawnionym klientom.</span><span class="sxs-lookup"><span data-stu-id="9cfad-137">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="9cfad-138">Aby sprawdzić warunki wymagane do uwierzytelnienia klienta przez usługę federacyjną, a także więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [How to: Skonfiguruj poświadczenia na usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="9cfad-138">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="9cfad-139">Aby uzyskać więcej informacji na temat scenariuszy federacyjnych, zobacz [federacyjnego i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="9cfad-139">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="9cfad-140">Aby zapoznać się z przykładem, który pokazuje, jak wypełnić kolekcję w konfiguracji, zobacz [ \<Dodawanie >](add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="9cfad-140">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cfad-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cfad-141">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="9cfad-142">\<add></span><span class="sxs-lookup"><span data-stu-id="9cfad-142">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="9cfad-143">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="9cfad-143">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="9cfad-144">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="9cfad-144">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="9cfad-145">Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna</span><span class="sxs-lookup"><span data-stu-id="9cfad-145">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="9cfad-146">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="9cfad-146">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="9cfad-147">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="9cfad-147">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9cfad-148">\<add></span><span class="sxs-lookup"><span data-stu-id="9cfad-148">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="9cfad-149">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="9cfad-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
