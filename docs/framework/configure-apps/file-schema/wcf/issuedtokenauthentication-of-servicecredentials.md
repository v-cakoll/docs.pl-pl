---
title: <issuedTokenAuthentication> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 6d468a27ee05fb4dd8cf087d10e5d170783d3454
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400358"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="b7b3d-102">\<IssuedTokenAuthentication > z \<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="b7b3d-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="b7b3d-103">Określa niestandardowy token wystawiony jako poświadczenia usługi.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-103">Specifies a custom token issued as a service credential.</span></span>  
  
<span data-ttu-id="b7b3d-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b7b3d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b7b3d-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b7b3d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b7b3d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b7b3d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="b7b3d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b7b3d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="b7b3d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b7b3d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="b7b3d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ServiceCredentials**](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="b7b3d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="b7b3d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuedTokenAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="b7b3d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7b3d-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7b3d-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7b3d-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b7b3d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b7b3d-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7b3d-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b7b3d-114">Attributes</span></span>  
  
|<span data-ttu-id="b7b3d-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b7b3d-115">Attribute</span></span>|<span data-ttu-id="b7b3d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="b7b3d-116">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="b7b3d-117">Pobiera zestaw docelowych identyfikatorów URI, dla których <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można go było traktować jako ważny <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-117">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="b7b3d-118">Aby uzyskać więcej informacji na temat używania tego atrybutu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-118">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="b7b3d-119">Wartość logiczna określająca, czy są dozwolone niezaufane wystawcy certyfikatu RSA.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-119">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="b7b3d-120">Certyfikaty są podpisywane przez urzędy certyfikacji w celu zweryfikowania autentyczności.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-120">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="b7b3d-121">Niezaufany wystawca to urząd certyfikacji, który nie został określony jako zaufany do podpisywania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-121">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="b7b3d-122">Pobiera wartość określającą, czy <xref:System.IdentityModel.Tokens.SamlSecurityToken> <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> token zabezpieczający ma być zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-122">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="b7b3d-123">Ta wartość jest typu <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-123">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="b7b3d-124">Aby uzyskać więcej informacji na temat używania tego atrybutu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-124">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="b7b3d-125">Ustawia tryb walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-125">Sets the certificate validation mode.</span></span> <span data-ttu-id="b7b3d-126">Jedna z prawidłowych wartości <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-126">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="b7b3d-127">Jeśli jest ustawiona `Custom`na, należy `customCertificateValidator` również podać wartość.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-127">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="b7b3d-128">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-128">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="b7b3d-129">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-129">Optional string.</span></span> <span data-ttu-id="b7b3d-130">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-130">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="b7b3d-131">Ten atrybut musi być ustawiony, `certificateValidationMode` gdy jest ustawiony `Custom`na.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-131">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="b7b3d-132">Ustawia tryb odwołania, który określa, czy sprawdzanie odwołania odbywa się, a jeśli jest wykonywane w trybie online lub offline.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-132">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="b7b3d-133">Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-133">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="b7b3d-134">Opcjonalny atrybut ciągu, który określa typ elementu element SamlSerializer, który jest używany na potrzeby poświadczenia usługi.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-134">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="b7b3d-135">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-135">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="b7b3d-136">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-136">Optional enumeration.</span></span> <span data-ttu-id="b7b3d-137">Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-137">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7b3d-138">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b7b3d-138">Child Elements</span></span>  
  
|<span data-ttu-id="b7b3d-139">Element</span><span class="sxs-lookup"><span data-stu-id="b7b3d-139">Element</span></span>|<span data-ttu-id="b7b3d-140">Opis</span><span class="sxs-lookup"><span data-stu-id="b7b3d-140">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="b7b3d-141">Określa kolekcję <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elementów, które określają zaufanych wystawców poświadczeń usługi.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-141">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7b3d-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b7b3d-142">Parent Elements</span></span>  
  
|<span data-ttu-id="b7b3d-143">Element</span><span class="sxs-lookup"><span data-stu-id="b7b3d-143">Element</span></span>|<span data-ttu-id="b7b3d-144">Opis</span><span class="sxs-lookup"><span data-stu-id="b7b3d-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7b3d-145">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="b7b3d-145">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="b7b3d-146">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-146">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7b3d-147">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7b3d-147">Remarks</span></span>  
 <span data-ttu-id="b7b3d-148">Scenariusz wystawionego tokenu ma trzy etapy.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-148">The issued token scenario has three stages.</span></span> <span data-ttu-id="b7b3d-149">Na pierwszym etapie klient próbujący uzyskać dostęp do usługi jest nazywany *usługą bezpiecznego tokenu*.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-149">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="b7b3d-150">Usługa Secure Tokens następnie uwierzytelnia klienta, a następnie wystawia klientowi token, zwykle tokena "Security Assertions Markup Language" (SAML).</span><span class="sxs-lookup"><span data-stu-id="b7b3d-150">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="b7b3d-151">Klient następnie wraca do usługi przy użyciu tokenu.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-151">The client then returns to the service with the token.</span></span> <span data-ttu-id="b7b3d-152">Usługa bada token dla danych, które umożliwiają usłudze uwierzytelnianie tokenu i w związku z tym klienta.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-152">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="b7b3d-153">Aby uwierzytelnić token, certyfikat, którego używa usługa bezpiecznego tokenu, musi być znany usłudze.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-153">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="b7b3d-154">Ten element jest repozytorium dla wszystkich takich certyfikatów usługi Secure Token Service.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-154">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="b7b3d-155">Aby dodać certyfikaty, użyj [ \<> knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="b7b3d-155">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="b7b3d-156">Wstaw > dodawania dla każdego certyfikatu, jak pokazano w poniższym przykładzie. [ \<](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="b7b3d-156">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="b7b3d-157">Domyślnie certyfikaty muszą być uzyskiwane z usługi bezpiecznego tokenu.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-157">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="b7b3d-158">Te "znane" certyfikaty zapewniają dostęp do usługi tylko uprawnionym klientom.</span><span class="sxs-lookup"><span data-stu-id="b7b3d-158">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="b7b3d-159">Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji [, zobacz How to: Skonfiguruj poświadczenia na usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="b7b3d-159">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b3d-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7b3d-160">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="b7b3d-161">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="b7b3d-161">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b7b3d-162">Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna</span><span class="sxs-lookup"><span data-stu-id="b7b3d-162">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
