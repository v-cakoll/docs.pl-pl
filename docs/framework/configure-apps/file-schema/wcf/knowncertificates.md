---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 1210e6282a7dd6c40198693d4948a89efe841d59
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913525"
---
# <a name="knowncertificates"></a><span data-ttu-id="41721-101">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="41721-101">\<knownCertificates></span></span>
<span data-ttu-id="41721-102">Reprezentuje kolekcję certyfikatów X. 509, które są dostarczane w celu uwierzytelnienia poświadczeń zabezpieczeń wydanych z usługi tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="41721-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="41721-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="41721-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="41721-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="41721-104">\<behaviors></span></span>  
<span data-ttu-id="41721-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="41721-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="41721-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="41721-106">\<behavior></span></span>  
<span data-ttu-id="41721-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="41721-107">\<serviceCredentials></span></span>  
<span data-ttu-id="41721-108">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="41721-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="41721-109">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="41721-109">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41721-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="41721-110">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41721-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="41721-111">Attributes and Elements</span></span>  
 <span data-ttu-id="41721-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="41721-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41721-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="41721-113">Attributes</span></span>  
 <span data-ttu-id="41721-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="41721-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="41721-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="41721-115">Child Elements</span></span>  
  
|<span data-ttu-id="41721-116">Element</span><span class="sxs-lookup"><span data-stu-id="41721-116">Element</span></span>|<span data-ttu-id="41721-117">Opis</span><span class="sxs-lookup"><span data-stu-id="41721-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41721-118">\<add></span><span class="sxs-lookup"><span data-stu-id="41721-118">\<add></span></span>](add-of-knowncertificates.md)|<span data-ttu-id="41721-119">Dodaje certyfikat X. 509 do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="41721-119">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41721-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="41721-120">Parent Elements</span></span>  
  
|<span data-ttu-id="41721-121">Element</span><span class="sxs-lookup"><span data-stu-id="41721-121">Element</span></span>|<span data-ttu-id="41721-122">Opis</span><span class="sxs-lookup"><span data-stu-id="41721-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41721-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="41721-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="41721-124">Określa token wystawiony jako poświadczenie usługi.</span><span class="sxs-lookup"><span data-stu-id="41721-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41721-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41721-125">Remarks</span></span>  
 <span data-ttu-id="41721-126">Scenariusz wystawionego tokenu ma trzy etapy.</span><span class="sxs-lookup"><span data-stu-id="41721-126">The issued token scenario has three stages.</span></span> <span data-ttu-id="41721-127">Na pierwszym etapie klient próbujący uzyskać dostęp do usługi jest nazywany *usługą bezpiecznego tokenu*.</span><span class="sxs-lookup"><span data-stu-id="41721-127">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="41721-128">Usługa Secure Tokens następnie uwierzytelnia klienta, a następnie wystawia klientowi token, zwykle tokena "Security Assertions Markup Language" (SAML).</span><span class="sxs-lookup"><span data-stu-id="41721-128">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="41721-129">Klient następnie wraca do usługi przy użyciu tokenu.</span><span class="sxs-lookup"><span data-stu-id="41721-129">The client then returns to the service with the token.</span></span> <span data-ttu-id="41721-130">Usługa bada token dla danych, które umożliwiają usłudze uwierzytelnianie tokenu i w związku z tym klienta.</span><span class="sxs-lookup"><span data-stu-id="41721-130">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="41721-131">Aby uwierzytelnić token, certyfikat, którego używa usługa bezpiecznego tokenu, musi być znany usłudze.</span><span class="sxs-lookup"><span data-stu-id="41721-131">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="41721-132">Element > IssuedTokenAuthentication jest repozytorium dla wszystkich takich certyfikatów usługi Secure Token Service. [ \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="41721-132">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="41721-133">Aby dodać certyfikaty, użyj [ \<elementu knownCertificates >](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="41721-133">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="41721-134">Wstaw > dodawania dla każdego certyfikatu, jak pokazano w poniższym przykładzie. [ \<](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="41721-134">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="41721-135">Domyślnie certyfikaty muszą być uzyskiwane z usługi bezpiecznego tokenu.</span><span class="sxs-lookup"><span data-stu-id="41721-135">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="41721-136">Te "znane" certyfikaty zapewniają dostęp do usługi tylko uprawnionym klientom.</span><span class="sxs-lookup"><span data-stu-id="41721-136">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="41721-137">Aby sprawdzić warunki wymagane do uwierzytelnienia klienta przez usługę federacyjną, a także więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [How to: Skonfiguruj poświadczenia na usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="41721-137">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="41721-138">Aby uzyskać więcej informacji na temat scenariuszy federacyjnych, zobacz [federacyjnego i](../../../wcf/feature-details/federation-and-issued-tokens.md)wystawione tokeny.</span><span class="sxs-lookup"><span data-stu-id="41721-138">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="41721-139">Aby zapoznać się z przykładem, który pokazuje, jak wypełnić kolekcję w konfiguracji, zobacz [ \<Dodawanie >](add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="41721-139">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41721-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41721-140">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="41721-141">\<add></span><span class="sxs-lookup"><span data-stu-id="41721-141">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="41721-142">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="41721-142">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="41721-143">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="41721-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="41721-144">Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna</span><span class="sxs-lookup"><span data-stu-id="41721-144">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="41721-145">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="41721-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="41721-146">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="41721-146">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="41721-147">\<add></span><span class="sxs-lookup"><span data-stu-id="41721-147">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="41721-148">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="41721-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
