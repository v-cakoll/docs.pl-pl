---
title: <issuedTokenAuthentication> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 280aa49019f68a0906307e24842a585a92c6600a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925370"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="69f36-102">\<IssuedTokenAuthentication > z \<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="69f36-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="69f36-103">Określa niestandardowy token wystawiony jako poświadczenia usługi.</span><span class="sxs-lookup"><span data-stu-id="69f36-103">Specifies a custom token issued as a service credential.</span></span>  
  
 <span data-ttu-id="69f36-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="69f36-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="69f36-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="69f36-105">\<behaviors></span></span>  
<span data-ttu-id="69f36-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="69f36-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="69f36-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="69f36-107">\<behavior></span></span>  
<span data-ttu-id="69f36-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="69f36-108">\<serviceCredentials></span></span>  
<span data-ttu-id="69f36-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="69f36-109">\<issuedTokenAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f36-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="69f36-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69f36-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="69f36-111">Attributes and Elements</span></span>  
 <span data-ttu-id="69f36-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="69f36-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69f36-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="69f36-113">Attributes</span></span>  
  
|<span data-ttu-id="69f36-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="69f36-114">Attribute</span></span>|<span data-ttu-id="69f36-115">Opis</span><span class="sxs-lookup"><span data-stu-id="69f36-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="69f36-116">Pobiera zestaw docelowych identyfikatorów URI, dla których <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można go było traktować jako ważny <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="69f36-116">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="69f36-117">Aby uzyskać więcej informacji na temat używania tego atrybutu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="69f36-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="69f36-118">Wartość logiczna określająca, czy są dozwolone niezaufane wystawcy certyfikatu RSA.</span><span class="sxs-lookup"><span data-stu-id="69f36-118">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="69f36-119">Certyfikaty są podpisywane przez urzędy certyfikacji w celu zweryfikowania autentyczności.</span><span class="sxs-lookup"><span data-stu-id="69f36-119">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="69f36-120">Niezaufany wystawca to urząd certyfikacji, który nie został określony jako zaufany do podpisywania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="69f36-120">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="69f36-121">Pobiera wartość określającą, czy <xref:System.IdentityModel.Tokens.SamlSecurityToken> <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> token zabezpieczający ma być zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="69f36-121">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="69f36-122">Ta wartość jest typu <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="69f36-122">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="69f36-123">Aby uzyskać więcej informacji na temat używania tego atrybutu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="69f36-123">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="69f36-124">Ustawia tryb walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="69f36-124">Sets the certificate validation mode.</span></span> <span data-ttu-id="69f36-125">Jedna z prawidłowych wartości <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="69f36-125">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="69f36-126">Jeśli jest ustawiona `Custom`na, należy `customCertificateValidator` również podać wartość.</span><span class="sxs-lookup"><span data-stu-id="69f36-126">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="69f36-127">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="69f36-127">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="69f36-128">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="69f36-128">Optional string.</span></span> <span data-ttu-id="69f36-129">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="69f36-129">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="69f36-130">Ten atrybut musi być ustawiony, `certificateValidationMode` gdy jest ustawiony `Custom`na.</span><span class="sxs-lookup"><span data-stu-id="69f36-130">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="69f36-131">Ustawia tryb odwołania, który określa, czy sprawdzanie odwołania odbywa się, a jeśli jest wykonywane w trybie online lub offline.</span><span class="sxs-lookup"><span data-stu-id="69f36-131">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="69f36-132">Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="69f36-132">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="69f36-133">Opcjonalny atrybut ciągu, który określa typ elementu element SamlSerializer, który jest używany na potrzeby poświadczenia usługi.</span><span class="sxs-lookup"><span data-stu-id="69f36-133">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="69f36-134">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="69f36-134">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="69f36-135">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="69f36-135">Optional enumeration.</span></span> <span data-ttu-id="69f36-136">Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="69f36-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69f36-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="69f36-137">Child Elements</span></span>  
  
|<span data-ttu-id="69f36-138">Element</span><span class="sxs-lookup"><span data-stu-id="69f36-138">Element</span></span>|<span data-ttu-id="69f36-139">Opis</span><span class="sxs-lookup"><span data-stu-id="69f36-139">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="69f36-140">Określa kolekcję <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elementów, które określają zaufanych wystawców poświadczeń usługi.</span><span class="sxs-lookup"><span data-stu-id="69f36-140">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69f36-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="69f36-141">Parent Elements</span></span>  
  
|<span data-ttu-id="69f36-142">Element</span><span class="sxs-lookup"><span data-stu-id="69f36-142">Element</span></span>|<span data-ttu-id="69f36-143">Opis</span><span class="sxs-lookup"><span data-stu-id="69f36-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69f36-144">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="69f36-144">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="69f36-145">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="69f36-145">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69f36-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69f36-146">Remarks</span></span>  
 <span data-ttu-id="69f36-147">Scenariusz wystawionego tokenu ma trzy etapy.</span><span class="sxs-lookup"><span data-stu-id="69f36-147">The issued token scenario has three stages.</span></span> <span data-ttu-id="69f36-148">Na pierwszym etapie klient próbujący uzyskać dostęp do usługi jest nazywany *usługą bezpiecznego tokenu*.</span><span class="sxs-lookup"><span data-stu-id="69f36-148">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="69f36-149">Usługa Secure Tokens następnie uwierzytelnia klienta, a następnie wystawia klientowi token, zwykle tokena "Security Assertions Markup Language" (SAML).</span><span class="sxs-lookup"><span data-stu-id="69f36-149">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="69f36-150">Klient następnie wraca do usługi przy użyciu tokenu.</span><span class="sxs-lookup"><span data-stu-id="69f36-150">The client then returns to the service with the token.</span></span> <span data-ttu-id="69f36-151">Usługa bada token dla danych, które umożliwiają usłudze uwierzytelnianie tokenu i w związku z tym klienta.</span><span class="sxs-lookup"><span data-stu-id="69f36-151">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="69f36-152">Aby uwierzytelnić token, certyfikat, którego używa usługa bezpiecznego tokenu, musi być znany usłudze.</span><span class="sxs-lookup"><span data-stu-id="69f36-152">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="69f36-153">Ten element jest repozytorium dla wszystkich takich certyfikatów usługi Secure Token Service.</span><span class="sxs-lookup"><span data-stu-id="69f36-153">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="69f36-154">Aby dodać certyfikaty, użyj [ \<> knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="69f36-154">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="69f36-155">Wstaw > dodawania dla każdego certyfikatu, jak pokazano w poniższym przykładzie. [ \<](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="69f36-155">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="69f36-156">Domyślnie certyfikaty muszą być uzyskiwane z usługi bezpiecznego tokenu.</span><span class="sxs-lookup"><span data-stu-id="69f36-156">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="69f36-157">Te "znane" certyfikaty zapewniają dostęp do usługi tylko uprawnionym klientom.</span><span class="sxs-lookup"><span data-stu-id="69f36-157">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="69f36-158">Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji [, zobacz How to: Skonfiguruj poświadczenia na usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="69f36-158">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69f36-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69f36-159">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="69f36-160">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="69f36-160">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="69f36-161">Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna</span><span class="sxs-lookup"><span data-stu-id="69f36-161">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
