---
title: <issuedTokenAuthentication> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 6d468a27ee05fb4dd8cf087d10e5d170783d3454
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400358"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="c94df-102">\<issuedTokenAuthentication> dla \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c94df-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="c94df-103">Określa niestandardowy token wystawiony jako poświadczenia usługi.</span><span class="sxs-lookup"><span data-stu-id="c94df-103">Specifies a custom token issued as a service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="c94df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c94df-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c94df-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c94df-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c94df-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c94df-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c94df-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c94df-107">Attributes</span></span>  
  
|<span data-ttu-id="c94df-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c94df-108">Attribute</span></span>|<span data-ttu-id="c94df-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c94df-109">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="c94df-110">Pobiera zestaw docelowych identyfikatorów URI, dla których <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można go było traktować jako ważny przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="c94df-110">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="c94df-111">Aby uzyskać więcej informacji na temat używania tego atrybutu, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A> .</span><span class="sxs-lookup"><span data-stu-id="c94df-111">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="c94df-112">Wartość logiczna określająca, czy są dozwolone niezaufane wystawcy certyfikatu RSA.</span><span class="sxs-lookup"><span data-stu-id="c94df-112">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="c94df-113">Certyfikaty są podpisywane przez urzędy certyfikacji w celu zweryfikowania autentyczności.</span><span class="sxs-lookup"><span data-stu-id="c94df-113">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="c94df-114">Niezaufany wystawca to urząd certyfikacji, który nie został określony jako zaufany do podpisywania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="c94df-114">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="c94df-115">Pobiera wartość określającą, czy <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpieczający <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> ma być zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="c94df-115">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="c94df-116">Ta wartość jest typu <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="c94df-116">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="c94df-117">Aby uzyskać więcej informacji na temat używania tego atrybutu, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A> .</span><span class="sxs-lookup"><span data-stu-id="c94df-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="c94df-118">Ustawia tryb walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="c94df-118">Sets the certificate validation mode.</span></span> <span data-ttu-id="c94df-119">Jedna z prawidłowych wartości <xref:System.ServiceModel.Security.X509CertificateValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="c94df-119">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="c94df-120">Jeśli jest ustawiona na `Custom` , `customCertificateValidator` należy również podać wartość.</span><span class="sxs-lookup"><span data-stu-id="c94df-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="c94df-121">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="c94df-121">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="c94df-122">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="c94df-122">Optional string.</span></span> <span data-ttu-id="c94df-123">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="c94df-123">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="c94df-124">Ten atrybut musi być ustawiony `certificateValidationMode` , gdy jest ustawiony na `Custom` .</span><span class="sxs-lookup"><span data-stu-id="c94df-124">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="c94df-125">Ustawia tryb odwołania, który określa, czy sprawdzanie odwołania odbywa się, a jeśli jest wykonywane w trybie online lub offline.</span><span class="sxs-lookup"><span data-stu-id="c94df-125">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="c94df-126">Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .</span><span class="sxs-lookup"><span data-stu-id="c94df-126">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="c94df-127">Opcjonalny atrybut ciągu, który określa typ elementu element SamlSerializer, który jest używany na potrzeby poświadczenia usługi.</span><span class="sxs-lookup"><span data-stu-id="c94df-127">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="c94df-128">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="c94df-128">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="c94df-129">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="c94df-129">Optional enumeration.</span></span> <span data-ttu-id="c94df-130">Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="c94df-130">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c94df-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c94df-131">Child Elements</span></span>  
  
|<span data-ttu-id="c94df-132">Element</span><span class="sxs-lookup"><span data-stu-id="c94df-132">Element</span></span>|<span data-ttu-id="c94df-133">Opis</span><span class="sxs-lookup"><span data-stu-id="c94df-133">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="c94df-134">Określa kolekcję <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elementów, które określają zaufanych wystawców poświadczeń usługi.</span><span class="sxs-lookup"><span data-stu-id="c94df-134">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c94df-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c94df-135">Parent Elements</span></span>  
  
|<span data-ttu-id="c94df-136">Element</span><span class="sxs-lookup"><span data-stu-id="c94df-136">Element</span></span>|<span data-ttu-id="c94df-137">Opis</span><span class="sxs-lookup"><span data-stu-id="c94df-137">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="c94df-138">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="c94df-138">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c94df-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c94df-139">Remarks</span></span>  
 <span data-ttu-id="c94df-140">Scenariusz wystawionego tokenu ma trzy etapy.</span><span class="sxs-lookup"><span data-stu-id="c94df-140">The issued token scenario has three stages.</span></span> <span data-ttu-id="c94df-141">Na pierwszym etapie klient próbujący uzyskać dostęp do usługi jest nazywany *usługą bezpiecznego tokenu*.</span><span class="sxs-lookup"><span data-stu-id="c94df-141">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="c94df-142">Usługa Secure Tokens następnie uwierzytelnia klienta, a następnie wystawia klientowi token, zwykle tokena "Security Assertions Markup Language" (SAML).</span><span class="sxs-lookup"><span data-stu-id="c94df-142">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="c94df-143">Klient następnie wraca do usługi przy użyciu tokenu.</span><span class="sxs-lookup"><span data-stu-id="c94df-143">The client then returns to the service with the token.</span></span> <span data-ttu-id="c94df-144">Usługa bada token dla danych, które umożliwiają usłudze uwierzytelnianie tokenu i w związku z tym klienta.</span><span class="sxs-lookup"><span data-stu-id="c94df-144">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="c94df-145">Aby uwierzytelnić token, certyfikat, którego używa usługa bezpiecznego tokenu, musi być znany usłudze.</span><span class="sxs-lookup"><span data-stu-id="c94df-145">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="c94df-146">Ten element jest repozytorium dla wszystkich takich certyfikatów usługi Secure Token Service.</span><span class="sxs-lookup"><span data-stu-id="c94df-146">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="c94df-147">Aby dodać certyfikaty, użyj [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="c94df-147">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="c94df-148">Wstaw [\<add>](add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c94df-148">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="c94df-149">Domyślnie certyfikaty muszą być uzyskiwane z usługi bezpiecznego tokenu.</span><span class="sxs-lookup"><span data-stu-id="c94df-149">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="c94df-150">Te "znane" certyfikaty zapewniają dostęp do usługi tylko uprawnionym klientom.</span><span class="sxs-lookup"><span data-stu-id="c94df-150">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="c94df-151">Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji, zobacz [How to: Configure Credentials in a a usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="c94df-151">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c94df-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c94df-152">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="c94df-153">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="c94df-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c94df-154">Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="c94df-154">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
