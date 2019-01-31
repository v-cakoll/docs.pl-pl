---
title: <issuedTokenAuthentication> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: c195791250831897b8bc9d09782d17609272e146
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260293"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="92dd3-102">\<issuedTokenAuthentication > z \<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="92dd3-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="92dd3-103">Określa niestandardowy token wydany jako poświadczenie usługi.</span><span class="sxs-lookup"><span data-stu-id="92dd3-103">Specifies a custom token issued as a service credential.</span></span>  
  
 <span data-ttu-id="92dd3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="92dd3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="92dd3-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="92dd3-105">\<behaviors></span></span>  
<span data-ttu-id="92dd3-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="92dd3-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="92dd3-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="92dd3-107">\<behavior></span></span>  
<span data-ttu-id="92dd3-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="92dd3-108">\<serviceCredentials></span></span>  
<span data-ttu-id="92dd3-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="92dd3-109">\<issuedTokenAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92dd3-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="92dd3-110">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92dd3-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="92dd3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="92dd3-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="92dd3-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92dd3-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="92dd3-113">Attributes</span></span>  
  
|<span data-ttu-id="92dd3-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="92dd3-114">Attribute</span></span>|<span data-ttu-id="92dd3-115">Opis</span><span class="sxs-lookup"><span data-stu-id="92dd3-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="92dd3-116">Pobiera zestaw docelowych URI dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczeń może być kierowany aby były uważane za prawidłowe przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="92dd3-116">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="92dd3-117">Aby uzyskać więcej informacji na temat korzystania z tego atrybutu, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span><span class="sxs-lookup"><span data-stu-id="92dd3-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="92dd3-118">Wartość logiczna określająca, jeśli są dozwolone niezaufani wystawcy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="92dd3-118">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="92dd3-119">Certyfikaty są podpisane przez urzędy certyfikacji (CA) w celu sprawdzenia autentyczności.</span><span class="sxs-lookup"><span data-stu-id="92dd3-119">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="92dd3-120">Niezaufane wystawca jest urząd certyfikacji, który nie jest określony jako zaufane do podpisywania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="92dd3-120">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="92dd3-121">Pobiera wartość określającą, czy <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpieczający <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> powinny być weryfikowane.</span><span class="sxs-lookup"><span data-stu-id="92dd3-121">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="92dd3-122">Ta wartość jest typu <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="92dd3-122">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="92dd3-123">Aby uzyskać więcej informacji na temat korzystania z tego atrybutu, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="92dd3-123">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="92dd3-124">Ustawia tryb walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="92dd3-124">Sets the certificate validation mode.</span></span> <span data-ttu-id="92dd3-125">Jedną z prawidłowych wartości z <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="92dd3-125">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="92dd3-126">Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` musi również zostać dostarczony.</span><span class="sxs-lookup"><span data-stu-id="92dd3-126">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="92dd3-127">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="92dd3-127">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="92dd3-128">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="92dd3-128">Optional string.</span></span> <span data-ttu-id="92dd3-129">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="92dd3-129">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="92dd3-130">Ten atrybut musi być ustawiane podczas `certificateValidationMode` ustawiono `Custom`.</span><span class="sxs-lookup"><span data-stu-id="92dd3-130">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="92dd3-131">Ustawia tryb odwołania, który określa, czy sprawdzanie odwołań występuje i czy jest wykonywane w trybie online lub offline.</span><span class="sxs-lookup"><span data-stu-id="92dd3-131">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="92dd3-132">Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="92dd3-132">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="92dd3-133">Atrybut opcjonalny ciąg, który określa typ element SamlSerializer używanego dla poświadczenia usługi.</span><span class="sxs-lookup"><span data-stu-id="92dd3-133">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="92dd3-134">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="92dd3-134">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="92dd3-135">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="92dd3-135">Optional enumeration.</span></span> <span data-ttu-id="92dd3-136">Jedną z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="92dd3-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92dd3-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="92dd3-137">Child Elements</span></span>  
  
|<span data-ttu-id="92dd3-138">Element</span><span class="sxs-lookup"><span data-stu-id="92dd3-138">Element</span></span>|<span data-ttu-id="92dd3-139">Opis</span><span class="sxs-lookup"><span data-stu-id="92dd3-139">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="92dd3-140">Określa kolekcję elementów <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elementy, które określa zaufanymi wystawcami na potrzeby poświadczeń usługi.</span><span class="sxs-lookup"><span data-stu-id="92dd3-140">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92dd3-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="92dd3-141">Parent Elements</span></span>  
  
|<span data-ttu-id="92dd3-142">Element</span><span class="sxs-lookup"><span data-stu-id="92dd3-142">Element</span></span>|<span data-ttu-id="92dd3-143">Opis</span><span class="sxs-lookup"><span data-stu-id="92dd3-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92dd3-144">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="92dd3-144">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="92dd3-145">Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="92dd3-145">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92dd3-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92dd3-146">Remarks</span></span>  
 <span data-ttu-id="92dd3-147">Wystawiony token scenariusz ma trzy etapy.</span><span class="sxs-lookup"><span data-stu-id="92dd3-147">The issued token scenario has three stages.</span></span> <span data-ttu-id="92dd3-148">W pierwszym etapie klienta próby uzyskania dostępu do usługi jest określane *secure token service*.</span><span class="sxs-lookup"><span data-stu-id="92dd3-148">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="92dd3-149">Usługa bezpiecznych tokenów następnie uwierzytelnia klienta, a następnie wystawia token, zazwyczaj token zabezpieczeń potwierdzenia Markup Language (SAML) klienta.</span><span class="sxs-lookup"><span data-stu-id="92dd3-149">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="92dd3-150">Klient powraca do usługi przy użyciu tokenu.</span><span class="sxs-lookup"><span data-stu-id="92dd3-150">The client then returns to the service with the token.</span></span> <span data-ttu-id="92dd3-151">Usługa sprawdza, czy token dla danych, które umożliwia usłudze uwierzytelniania tokenu, a w związku z tym klientem.</span><span class="sxs-lookup"><span data-stu-id="92dd3-151">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="92dd3-152">W celu uwierzytelnienia tokenu certyfikatu używa usługa bezpiecznych tokenów musi być znane, do usługi.</span><span class="sxs-lookup"><span data-stu-id="92dd3-152">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="92dd3-153">Ten element jest repozytorium dla wszystkich certyfikatów usługa bezpiecznych tokenów.</span><span class="sxs-lookup"><span data-stu-id="92dd3-153">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="92dd3-154">Aby dodać certyfikaty, należy użyć [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="92dd3-154">To add certificates, use the [\<knownCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="92dd3-155">Wstaw [ \<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="92dd3-155">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="92dd3-156">Domyślnie certyfikaty musi pochodzić od usługa bezpiecznych tokenów.</span><span class="sxs-lookup"><span data-stu-id="92dd3-156">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="92dd3-157">Te certyfikaty, upewnij się, że wiarygodnych tylko klienci "znane" Uzyskiwanie dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="92dd3-157">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="92dd3-158">Aby uzyskać więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [jak: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="92dd3-158">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92dd3-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92dd3-159">See also</span></span>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="92dd3-160">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="92dd3-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="92dd3-161">Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="92dd3-161">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
