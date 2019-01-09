---
title: '&lt;knownCertificates&gt;'
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: ed2bd5ec5b3a2a3e7b929b954df1c00be0849d71
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149762"
---
# <a name="ltknowncertificatesgt"></a><span data-ttu-id="bf8c8-102">&lt;knownCertificates&gt;</span><span class="sxs-lookup"><span data-stu-id="bf8c8-102">&lt;knownCertificates&gt;</span></span>
<span data-ttu-id="bf8c8-103">Reprezentuje kolekcję certyfikatów X.509, które są dostarczane do uwierzytelnienia poświadczeń zabezpieczenia wydawanych z Usługa tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="bf8c8-103">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="bf8c8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bf8c8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bf8c8-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="bf8c8-105">\<behaviors></span></span>  
<span data-ttu-id="bf8c8-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="bf8c8-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="bf8c8-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="bf8c8-107">\<behavior></span></span>  
<span data-ttu-id="bf8c8-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="bf8c8-108">\<serviceCredentials></span></span>  
<span data-ttu-id="bf8c8-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="bf8c8-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="bf8c8-110">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="bf8c8-110">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf8c8-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf8c8-111">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf8c8-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bf8c8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bf8c8-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bf8c8-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf8c8-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bf8c8-114">Attributes</span></span>  
 <span data-ttu-id="bf8c8-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="bf8c8-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf8c8-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bf8c8-116">Child Elements</span></span>  
  
|<span data-ttu-id="bf8c8-117">Element</span><span class="sxs-lookup"><span data-stu-id="bf8c8-117">Element</span></span>|<span data-ttu-id="bf8c8-118">Opis</span><span class="sxs-lookup"><span data-stu-id="bf8c8-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf8c8-119">\<add></span><span class="sxs-lookup"><span data-stu-id="bf8c8-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|<span data-ttu-id="bf8c8-120">Dodaje certyfikat X.509 do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bf8c8-120">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf8c8-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bf8c8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="bf8c8-122">Element</span><span class="sxs-lookup"><span data-stu-id="bf8c8-122">Element</span></span>|<span data-ttu-id="bf8c8-123">Opis</span><span class="sxs-lookup"><span data-stu-id="bf8c8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf8c8-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="bf8c8-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="bf8c8-125">Określa token wydany jako poświadczenie usługi.</span><span class="sxs-lookup"><span data-stu-id="bf8c8-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf8c8-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf8c8-126">Remarks</span></span>  
 <span data-ttu-id="bf8c8-127">Wystawiony token scenariusz ma trzy etapy.</span><span class="sxs-lookup"><span data-stu-id="bf8c8-127">The issued token scenario has three stages.</span></span> <span data-ttu-id="bf8c8-128">W pierwszym etapie klienta próby uzyskania dostępu do usługi jest określane *secure token service*.</span><span class="sxs-lookup"><span data-stu-id="bf8c8-128">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="bf8c8-129">Usługa bezpiecznych tokenów następnie uwierzytelnia klienta, a następnie wystawia token, zazwyczaj token zabezpieczeń potwierdzenia Markup Language (SAML) klienta.</span><span class="sxs-lookup"><span data-stu-id="bf8c8-129">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="bf8c8-130">Klient powraca do usługi przy użyciu tokenu.</span><span class="sxs-lookup"><span data-stu-id="bf8c8-130">The client then returns to the service with the token.</span></span> <span data-ttu-id="bf8c8-131">Usługa sprawdza, czy token dla danych, które umożliwia usłudze uwierzytelniania tokenu, a w związku z tym klientem.</span><span class="sxs-lookup"><span data-stu-id="bf8c8-131">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="bf8c8-132">W celu uwierzytelnienia tokenu certyfikatu używa usługa bezpiecznych tokenów musi być znane, do usługi.</span><span class="sxs-lookup"><span data-stu-id="bf8c8-132">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="bf8c8-133">[ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element jest repozytorium dla wszystkich certyfikatów usługa bezpiecznych tokenów.</span><span class="sxs-lookup"><span data-stu-id="bf8c8-133">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="bf8c8-134">Aby dodać certyfikaty, należy użyć [ \<knownCertificates > element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="bf8c8-134">To add certificates, use the [\<knownCertificates> element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="bf8c8-135">Wstaw [ \<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bf8c8-135">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="bf8c8-136">Domyślnie certyfikaty musi pochodzić od usługa bezpiecznych tokenów.</span><span class="sxs-lookup"><span data-stu-id="bf8c8-136">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="bf8c8-137">Te certyfikaty, upewnij się, że wiarygodnych tylko klienci "znane" Uzyskiwanie dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="bf8c8-137">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="bf8c8-138">Aby przejrzeć warunki wymagane do klienta, może zostać uwierzytelniony przez usługi federacyjnej, jak również więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [jak: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="bf8c8-138">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="bf8c8-139">Aby uzyskać więcej informacji o scenariuszach obejmujących Federację, zobacz [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="bf8c8-139">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="bf8c8-140">Na przykład, który pokazuje, jak wypełnić kolekcji w konfiguracji, zobacz [ \<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="bf8c8-140">For an example that shows how to populate the collection in configuration, see [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf8c8-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf8c8-141">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>  
 [<span data-ttu-id="bf8c8-142">\<add></span><span class="sxs-lookup"><span data-stu-id="bf8c8-142">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [<span data-ttu-id="bf8c8-143">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="bf8c8-143">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="bf8c8-144">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="bf8c8-144">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="bf8c8-145">Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="bf8c8-145">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="bf8c8-146">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="bf8c8-146">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="bf8c8-147">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="bf8c8-147">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="bf8c8-148">\<add></span><span class="sxs-lookup"><span data-stu-id="bf8c8-148">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [<span data-ttu-id="bf8c8-149">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="bf8c8-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
