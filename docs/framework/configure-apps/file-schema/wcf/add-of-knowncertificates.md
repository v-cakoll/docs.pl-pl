---
title: <add> dla <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 939718e8dacca2698b6f71a3bdc1262a5dc3ee20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926677"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="144b2-102">\<Dodawanie > \<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="144b2-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="144b2-103">Dodaje certyfikat X. 509 do kolekcji znanych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="144b2-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
 <span data-ttu-id="144b2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="144b2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="144b2-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="144b2-105">\<behaviors></span></span>  
<span data-ttu-id="144b2-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="144b2-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="144b2-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="144b2-107">\<behavior></span></span>  
<span data-ttu-id="144b2-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="144b2-108">\<serviceCredentials></span></span>  
<span data-ttu-id="144b2-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="144b2-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="144b2-110">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="144b2-110">\<knownCertificates></span></span>  
<span data-ttu-id="144b2-111">\<add></span><span class="sxs-lookup"><span data-stu-id="144b2-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="144b2-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="144b2-112">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="144b2-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="144b2-113">Attributes and Elements</span></span>  
 <span data-ttu-id="144b2-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="144b2-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="144b2-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="144b2-115">Attributes</span></span>  
  
|<span data-ttu-id="144b2-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="144b2-116">Attribute</span></span>|<span data-ttu-id="144b2-117">Opis</span><span class="sxs-lookup"><span data-stu-id="144b2-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="144b2-118">findValue</span><span class="sxs-lookup"><span data-stu-id="144b2-118">findValue</span></span>|<span data-ttu-id="144b2-119">Parametry.</span><span class="sxs-lookup"><span data-stu-id="144b2-119">String.</span></span> <span data-ttu-id="144b2-120">Wartość do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="144b2-120">The value to search for.</span></span>|  
|<span data-ttu-id="144b2-121">storeLocation</span><span class="sxs-lookup"><span data-stu-id="144b2-121">storeLocation</span></span>|<span data-ttu-id="144b2-122">Licznik.</span><span class="sxs-lookup"><span data-stu-id="144b2-122">Enumeration.</span></span> <span data-ttu-id="144b2-123">Jedna z dwóch lokalizacji przechowywania do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="144b2-123">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="144b2-124">storeName</span><span class="sxs-lookup"><span data-stu-id="144b2-124">storeName</span></span>|<span data-ttu-id="144b2-125">Licznik.</span><span class="sxs-lookup"><span data-stu-id="144b2-125">Enumeration.</span></span> <span data-ttu-id="144b2-126">Jeden z magazynów systemu do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="144b2-126">One of the system stores to search.</span></span>|  
|<span data-ttu-id="144b2-127">x509FindType</span><span class="sxs-lookup"><span data-stu-id="144b2-127">x509FindType</span></span>|<span data-ttu-id="144b2-128">Licznik.</span><span class="sxs-lookup"><span data-stu-id="144b2-128">Enumeration.</span></span> <span data-ttu-id="144b2-129">Jedno z pól certyfikatów do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="144b2-129">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="144b2-130">findValue — atrybut</span><span class="sxs-lookup"><span data-stu-id="144b2-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="144b2-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="144b2-131">Value</span></span>|<span data-ttu-id="144b2-132">Opis</span><span class="sxs-lookup"><span data-stu-id="144b2-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="144b2-133">String</span><span class="sxs-lookup"><span data-stu-id="144b2-133">String</span></span>|<span data-ttu-id="144b2-134">Wartość jest zależna od pola (określonego przez atrybut X509FindType), który jest przeszukiwany.</span><span class="sxs-lookup"><span data-stu-id="144b2-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="144b2-135">Na przykład, jeśli szukasz odcisku palca, wartość musi być ciągiem liczb szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="144b2-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="144b2-136">x509FindType — atrybut</span><span class="sxs-lookup"><span data-stu-id="144b2-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="144b2-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="144b2-137">Value</span></span>|<span data-ttu-id="144b2-138">Opis</span><span class="sxs-lookup"><span data-stu-id="144b2-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="144b2-139">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="144b2-139">Enumeration</span></span>|<span data-ttu-id="144b2-140">Dostępne są następujące wartości: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="144b2-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="144b2-141">storeLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="144b2-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="144b2-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="144b2-142">Value</span></span>|<span data-ttu-id="144b2-143">Opis</span><span class="sxs-lookup"><span data-stu-id="144b2-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="144b2-144">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="144b2-144">Enumeration</span></span>|<span data-ttu-id="144b2-145">CurrentUser lub LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="144b2-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="144b2-146">storeName — atrybut</span><span class="sxs-lookup"><span data-stu-id="144b2-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="144b2-147">Wartość</span><span class="sxs-lookup"><span data-stu-id="144b2-147">Value</span></span>|<span data-ttu-id="144b2-148">Opis</span><span class="sxs-lookup"><span data-stu-id="144b2-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="144b2-149">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="144b2-149">Enumeration</span></span>|<span data-ttu-id="144b2-150">Dostępne są następujące wartości: AddressBook, AuthRoot, urząd certyfikacji, niedozwolone, my, root, TrustedPeople i TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="144b2-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="144b2-151">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="144b2-151">Child Elements</span></span>  
 <span data-ttu-id="144b2-152">Brak.</span><span class="sxs-lookup"><span data-stu-id="144b2-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="144b2-153">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="144b2-153">Parent Elements</span></span>  
  
|<span data-ttu-id="144b2-154">Element</span><span class="sxs-lookup"><span data-stu-id="144b2-154">Element</span></span>|<span data-ttu-id="144b2-155">Opis</span><span class="sxs-lookup"><span data-stu-id="144b2-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="144b2-156">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="144b2-156">\<knownCertificates></span></span>](knowncertificates.md)|<span data-ttu-id="144b2-157">Reprezentuje kolekcję certyfikatów X. 509, które są dostarczane przez usługę tokenu zabezpieczającego (STS) do sprawdzania poprawności tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="144b2-157">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="144b2-158">Uwagi</span><span class="sxs-lookup"><span data-stu-id="144b2-158">Remarks</span></span>  
 <span data-ttu-id="144b2-159">Scenariusz wystawionego tokenu ma trzy etapy.</span><span class="sxs-lookup"><span data-stu-id="144b2-159">The issued token scenario has three stages.</span></span> <span data-ttu-id="144b2-160">Na pierwszym etapie klient próbujący uzyskać dostęp do usługi jest nazywany *usługą bezpiecznego tokenu*.</span><span class="sxs-lookup"><span data-stu-id="144b2-160">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="144b2-161">Usługa Secure Tokens następnie uwierzytelnia klienta, a następnie wystawia klientowi token, zwykle tokena "Security Assertions Markup Language" (SAML).</span><span class="sxs-lookup"><span data-stu-id="144b2-161">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="144b2-162">Klient następnie wraca do usługi przy użyciu tokenu.</span><span class="sxs-lookup"><span data-stu-id="144b2-162">The client then returns to the service with the token.</span></span> <span data-ttu-id="144b2-163">Usługa bada token dla danych, które umożliwiają usłudze uwierzytelnianie tokenu i w związku z tym klienta.</span><span class="sxs-lookup"><span data-stu-id="144b2-163">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="144b2-164">Aby uwierzytelnić token, certyfikat, którego używa usługa bezpiecznego tokenu, musi być znany usłudze.</span><span class="sxs-lookup"><span data-stu-id="144b2-164">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="144b2-165">Element > IssuedTokenAuthentication jest repozytorium dla wszystkich takich certyfikatów usługi Secure Token Service. [ \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="144b2-165">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="144b2-166">Aby dodać certyfikaty, użyj [ \<> knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="144b2-166">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="144b2-167">Wstaw element [> knownCertificates element \<> dla każdego certyfikatu, jak pokazano w poniższym przykładzie. \<](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="144b2-167">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="144b2-168">Domyślnie certyfikaty muszą być uzyskiwane z usługi bezpiecznego tokenu.</span><span class="sxs-lookup"><span data-stu-id="144b2-168">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="144b2-169">Te "znane" certyfikaty zapewniają dostęp do usługi tylko uprawnionym klientom.</span><span class="sxs-lookup"><span data-stu-id="144b2-169">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="144b2-170">Aby sprawdzić warunki wymagane do uwierzytelnienia klienta przez usługę federacyjną, a także więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [How to: Skonfiguruj poświadczenia na usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="144b2-170">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="144b2-171">Aby uzyskać więcej informacji na temat scenariuszy federacyjnych, zobacz [federacyjnego i](../../../wcf/feature-details/federation-and-issued-tokens.md)wystawione tokeny.</span><span class="sxs-lookup"><span data-stu-id="144b2-171">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="144b2-172">Przykład</span><span class="sxs-lookup"><span data-stu-id="144b2-172">Example</span></span>  
 <span data-ttu-id="144b2-173">Poniższy przykład dodaje certyfikat do repozytorium dla wszystkich certyfikatów usługi STS.</span><span class="sxs-lookup"><span data-stu-id="144b2-173">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="144b2-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="144b2-174">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="144b2-175">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="144b2-175">\<knownCertificates></span></span>](knowncertificates.md)
- [<span data-ttu-id="144b2-176">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="144b2-176">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="144b2-177">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="144b2-177">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="144b2-178">Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna</span><span class="sxs-lookup"><span data-stu-id="144b2-178">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="144b2-179">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="144b2-179">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
