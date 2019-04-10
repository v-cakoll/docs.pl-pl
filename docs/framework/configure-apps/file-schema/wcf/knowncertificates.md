---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 5c20baecf3e9fe83385c986e3fb58f0c03eeeb47
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224198"
---
# <a name="knowncertificates"></a><span data-ttu-id="7d152-101">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="7d152-101">\<knownCertificates></span></span>
<span data-ttu-id="7d152-102">Reprezentuje kolekcję certyfikatów X.509, które są dostarczane do uwierzytelnienia poświadczeń zabezpieczenia wydawanych z Usługa tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="7d152-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="7d152-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7d152-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7d152-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="7d152-104">\<behaviors></span></span>  
<span data-ttu-id="7d152-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7d152-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="7d152-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="7d152-106">\<behavior></span></span>  
<span data-ttu-id="7d152-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="7d152-107">\<serviceCredentials></span></span>  
<span data-ttu-id="7d152-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="7d152-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="7d152-109">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="7d152-109">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d152-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d152-110">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d152-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7d152-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7d152-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d152-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d152-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d152-113">Attributes</span></span>  
 <span data-ttu-id="7d152-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="7d152-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7d152-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d152-115">Child Elements</span></span>  
  
|<span data-ttu-id="7d152-116">Element</span><span class="sxs-lookup"><span data-stu-id="7d152-116">Element</span></span>|<span data-ttu-id="7d152-117">Opis</span><span class="sxs-lookup"><span data-stu-id="7d152-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d152-118">\<add></span><span class="sxs-lookup"><span data-stu-id="7d152-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|<span data-ttu-id="7d152-119">Dodaje certyfikat X.509 do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7d152-119">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d152-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d152-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7d152-121">Element</span><span class="sxs-lookup"><span data-stu-id="7d152-121">Element</span></span>|<span data-ttu-id="7d152-122">Opis</span><span class="sxs-lookup"><span data-stu-id="7d152-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d152-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="7d152-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="7d152-124">Określa token wydany jako poświadczenie usługi.</span><span class="sxs-lookup"><span data-stu-id="7d152-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d152-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d152-125">Remarks</span></span>  
 <span data-ttu-id="7d152-126">Wystawiony token scenariusz ma trzy etapy.</span><span class="sxs-lookup"><span data-stu-id="7d152-126">The issued token scenario has three stages.</span></span> <span data-ttu-id="7d152-127">W pierwszym etapie klienta próby uzyskania dostępu do usługi jest określane *secure token service*.</span><span class="sxs-lookup"><span data-stu-id="7d152-127">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="7d152-128">Usługa bezpiecznych tokenów następnie uwierzytelnia klienta, a następnie wystawia token, zazwyczaj token zabezpieczeń potwierdzenia Markup Language (SAML) klienta.</span><span class="sxs-lookup"><span data-stu-id="7d152-128">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="7d152-129">Klient powraca do usługi przy użyciu tokenu.</span><span class="sxs-lookup"><span data-stu-id="7d152-129">The client then returns to the service with the token.</span></span> <span data-ttu-id="7d152-130">Usługa sprawdza, czy token dla danych, które umożliwia usłudze uwierzytelniania tokenu, a w związku z tym klientem.</span><span class="sxs-lookup"><span data-stu-id="7d152-130">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="7d152-131">W celu uwierzytelnienia tokenu certyfikatu używa usługa bezpiecznych tokenów musi być znane, do usługi.</span><span class="sxs-lookup"><span data-stu-id="7d152-131">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="7d152-132">[ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element jest repozytorium dla wszystkich certyfikatów usługa bezpiecznych tokenów.</span><span class="sxs-lookup"><span data-stu-id="7d152-132">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="7d152-133">Aby dodać certyfikaty, należy użyć [ \<knownCertificates > element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="7d152-133">To add certificates, use the [\<knownCertificates> element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="7d152-134">Wstaw [ \<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7d152-134">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="7d152-135">Domyślnie certyfikaty musi pochodzić od usługa bezpiecznych tokenów.</span><span class="sxs-lookup"><span data-stu-id="7d152-135">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="7d152-136">Te certyfikaty, upewnij się, że wiarygodnych tylko klienci "znane" Uzyskiwanie dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="7d152-136">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="7d152-137">Aby przejrzeć warunki wymagane do klienta, może zostać uwierzytelniony przez usługi federacyjnej, jak również więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [jak: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="7d152-137">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="7d152-138">Aby uzyskać więcej informacji o scenariuszach obejmujących Federację, zobacz [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="7d152-138">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="7d152-139">Na przykład, który pokazuje, jak wypełnić kolekcji w konfiguracji, zobacz [ \<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="7d152-139">For an example that shows how to populate the collection in configuration, see [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d152-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d152-140">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="7d152-141">\<add></span><span class="sxs-lookup"><span data-stu-id="7d152-141">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)
- [<span data-ttu-id="7d152-142">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="7d152-142">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="7d152-143">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7d152-143">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="7d152-144">Instrukcje: konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="7d152-144">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="7d152-145">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="7d152-145">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="7d152-146">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="7d152-146">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7d152-147">\<add></span><span class="sxs-lookup"><span data-stu-id="7d152-147">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)
- [<span data-ttu-id="7d152-148">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="7d152-148">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
