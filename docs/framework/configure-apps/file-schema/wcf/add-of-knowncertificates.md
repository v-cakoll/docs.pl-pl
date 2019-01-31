---
title: <add> z <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 022030489551bfaf48cffd4ba983bbd3c99abc87
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274290"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="d864d-102">\<Dodaj > z \<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="d864d-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="d864d-103">Dodaje certyfikat X.509 do kolekcji znanych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d864d-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
 <span data-ttu-id="d864d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d864d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d864d-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="d864d-105">\<behaviors></span></span>  
<span data-ttu-id="d864d-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d864d-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d864d-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d864d-107">\<behavior></span></span>  
<span data-ttu-id="d864d-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="d864d-108">\<serviceCredentials></span></span>  
<span data-ttu-id="d864d-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="d864d-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="d864d-110">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="d864d-110">\<knownCertificates></span></span>  
<span data-ttu-id="d864d-111">\<add></span><span class="sxs-lookup"><span data-stu-id="d864d-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d864d-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="d864d-112">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d864d-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d864d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d864d-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d864d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d864d-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d864d-115">Attributes</span></span>  
  
|<span data-ttu-id="d864d-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d864d-116">Attribute</span></span>|<span data-ttu-id="d864d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d864d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d864d-118">findValue</span><span class="sxs-lookup"><span data-stu-id="d864d-118">findValue</span></span>|<span data-ttu-id="d864d-119">ciąg.</span><span class="sxs-lookup"><span data-stu-id="d864d-119">String.</span></span> <span data-ttu-id="d864d-120">Wartość do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="d864d-120">The value to search for.</span></span>|  
|<span data-ttu-id="d864d-121">storeLocation</span><span class="sxs-lookup"><span data-stu-id="d864d-121">storeLocation</span></span>|<span data-ttu-id="d864d-122">Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="d864d-122">Enumeration.</span></span> <span data-ttu-id="d864d-123">Jednym z dwóch lokalizacji przechowywania do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="d864d-123">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="d864d-124">storeName</span><span class="sxs-lookup"><span data-stu-id="d864d-124">storeName</span></span>|<span data-ttu-id="d864d-125">Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="d864d-125">Enumeration.</span></span> <span data-ttu-id="d864d-126">Jednym z systemów magazynowania do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="d864d-126">One of the system stores to search.</span></span>|  
|<span data-ttu-id="d864d-127">x509FindType</span><span class="sxs-lookup"><span data-stu-id="d864d-127">x509FindType</span></span>|<span data-ttu-id="d864d-128">Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="d864d-128">Enumeration.</span></span> <span data-ttu-id="d864d-129">Jedno z pól certyfikatu do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="d864d-129">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="d864d-130">findValue atrybutu</span><span class="sxs-lookup"><span data-stu-id="d864d-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="d864d-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="d864d-131">Value</span></span>|<span data-ttu-id="d864d-132">Opis</span><span class="sxs-lookup"><span data-stu-id="d864d-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d864d-133">String</span><span class="sxs-lookup"><span data-stu-id="d864d-133">String</span></span>|<span data-ttu-id="d864d-134">Wartość zależy od pola (określony przez atrybut X509FindType) wyszukiwany.</span><span class="sxs-lookup"><span data-stu-id="d864d-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="d864d-135">Na przykład jeśli wyszukiwanie odcisku palca, wartość musi być ciągiem liczb szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="d864d-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="d864d-136">x509FindType Attribute</span><span class="sxs-lookup"><span data-stu-id="d864d-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="d864d-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="d864d-137">Value</span></span>|<span data-ttu-id="d864d-138">Opis</span><span class="sxs-lookup"><span data-stu-id="d864d-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d864d-139">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d864d-139">Enumeration</span></span>|<span data-ttu-id="d864d-140">Wartości: FindByThumbprint FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="d864d-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="d864d-141">storeLocation atrybutu</span><span class="sxs-lookup"><span data-stu-id="d864d-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="d864d-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="d864d-142">Value</span></span>|<span data-ttu-id="d864d-143">Opis</span><span class="sxs-lookup"><span data-stu-id="d864d-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d864d-144">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d864d-144">Enumeration</span></span>|<span data-ttu-id="d864d-145">CurrentUser lub LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="d864d-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="d864d-146">storeName atrybutu</span><span class="sxs-lookup"><span data-stu-id="d864d-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="d864d-147">Wartość</span><span class="sxs-lookup"><span data-stu-id="d864d-147">Value</span></span>|<span data-ttu-id="d864d-148">Opis</span><span class="sxs-lookup"><span data-stu-id="d864d-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d864d-149">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d864d-149">Enumeration</span></span>|<span data-ttu-id="d864d-150">Wartości: Książka adresowa, AuthRoot, urząd certyfikacji, niedozwolone mojej, główny, TrustedPeople i TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="d864d-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d864d-151">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d864d-151">Child Elements</span></span>  
 <span data-ttu-id="d864d-152">Brak.</span><span class="sxs-lookup"><span data-stu-id="d864d-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d864d-153">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d864d-153">Parent Elements</span></span>  
  
|<span data-ttu-id="d864d-154">Element</span><span class="sxs-lookup"><span data-stu-id="d864d-154">Element</span></span>|<span data-ttu-id="d864d-155">Opis</span><span class="sxs-lookup"><span data-stu-id="d864d-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d864d-156">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="d864d-156">\<knownCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)|<span data-ttu-id="d864d-157">Reprezentuje kolekcję certyfikatów X.509, które są dostarczane przez Usługa tokenu zabezpieczającego (STS) do weryfikacji tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="d864d-157">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d864d-158">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d864d-158">Remarks</span></span>  
 <span data-ttu-id="d864d-159">Wystawiony token scenariusz ma trzy etapy.</span><span class="sxs-lookup"><span data-stu-id="d864d-159">The issued token scenario has three stages.</span></span> <span data-ttu-id="d864d-160">W pierwszym etapie klienta próby uzyskania dostępu do usługi jest określane *secure token service*.</span><span class="sxs-lookup"><span data-stu-id="d864d-160">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="d864d-161">Usługa bezpiecznych tokenów następnie uwierzytelnia klienta, a następnie wystawia token, zazwyczaj token zabezpieczeń potwierdzenia Markup Language (SAML) klienta.</span><span class="sxs-lookup"><span data-stu-id="d864d-161">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="d864d-162">Klient powraca do usługi przy użyciu tokenu.</span><span class="sxs-lookup"><span data-stu-id="d864d-162">The client then returns to the service with the token.</span></span> <span data-ttu-id="d864d-163">Usługa sprawdza, czy token dla danych, które umożliwia usłudze uwierzytelniania tokenu, a w związku z tym klientem.</span><span class="sxs-lookup"><span data-stu-id="d864d-163">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="d864d-164">W celu uwierzytelnienia tokenu certyfikatu używa usługa bezpiecznych tokenów musi być znane, do usługi.</span><span class="sxs-lookup"><span data-stu-id="d864d-164">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="d864d-165">[ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element jest repozytorium dla wszystkich certyfikatów usługa bezpiecznych tokenów.</span><span class="sxs-lookup"><span data-stu-id="d864d-165">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="d864d-166">Aby dodać certyfikaty, należy użyć [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="d864d-166">To add certificates, use the [\<knownCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="d864d-167">Wstaw [ \<Dodaj > element \<knownCertificates > Element](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d864d-167">Insert an [\<add> element \<knownCertificates> Element](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="d864d-168">Domyślnie certyfikaty musi pochodzić od usługa bezpiecznych tokenów.</span><span class="sxs-lookup"><span data-stu-id="d864d-168">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="d864d-169">Te certyfikaty, upewnij się, że wiarygodnych tylko klienci "znane" Uzyskiwanie dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="d864d-169">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="d864d-170">Aby przejrzeć warunki wymagane do klienta, może zostać uwierzytelniony przez usługi federacyjnej, jak również więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [jak: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="d864d-170">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="d864d-171">Aby uzyskać więcej informacji o scenariuszach obejmujących Federację, zobacz [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="d864d-171">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d864d-172">Przykład</span><span class="sxs-lookup"><span data-stu-id="d864d-172">Example</span></span>  
 <span data-ttu-id="d864d-173">Poniższy przykład dodaje certyfikat do repozytorium dla wszystkich certyfikatów usługi STS.</span><span class="sxs-lookup"><span data-stu-id="d864d-173">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <serviceCredentials>
      <issuedTokenAuthentication>
        <knownCertificates>
          <add findValue="www.contoso.com"
               storeLocation="LocalMachine"
               storeName="CertificateAuthority"
               x509FindType="FindByIssuerName" />
        </knownCertificates>
      </issuedTokenAuthentication>
    </serviceCredentials>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="d864d-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d864d-174">See also</span></span>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="d864d-175">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="d864d-175">\<knownCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)
- [<span data-ttu-id="d864d-176">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="d864d-176">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="d864d-177">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="d864d-177">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d864d-178">Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="d864d-178">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="d864d-179">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="d864d-179">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
