---
title: <add> dla <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 29b067e6ec20992084f9ab3bab087222bdd56da2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400619"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="38525-102">\<Dodawanie > \<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="38525-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="38525-103">Dodaje certyfikat X. 509 do kolekcji znanych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="38525-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
<span data-ttu-id="38525-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="38525-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="38525-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="38525-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="38525-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="38525-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="38525-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="38525-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="38525-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="38525-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="38525-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ServiceCredentials**](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="38525-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="38525-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenAuthentication >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="38525-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="38525-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<knownCertificates >** ](knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="38525-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)</span></span>\
<span data-ttu-id="38525-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="38525-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38525-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="38525-113">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38525-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="38525-114">Attributes and Elements</span></span>  
 <span data-ttu-id="38525-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="38525-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38525-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="38525-116">Attributes</span></span>  
  
|<span data-ttu-id="38525-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="38525-117">Attribute</span></span>|<span data-ttu-id="38525-118">Opis</span><span class="sxs-lookup"><span data-stu-id="38525-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38525-119">findValue</span><span class="sxs-lookup"><span data-stu-id="38525-119">findValue</span></span>|<span data-ttu-id="38525-120">Parametry.</span><span class="sxs-lookup"><span data-stu-id="38525-120">String.</span></span> <span data-ttu-id="38525-121">Wartość do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="38525-121">The value to search for.</span></span>|  
|<span data-ttu-id="38525-122">storeLocation</span><span class="sxs-lookup"><span data-stu-id="38525-122">storeLocation</span></span>|<span data-ttu-id="38525-123">Licznik.</span><span class="sxs-lookup"><span data-stu-id="38525-123">Enumeration.</span></span> <span data-ttu-id="38525-124">Jedna z dwóch lokalizacji przechowywania do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="38525-124">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="38525-125">storeName</span><span class="sxs-lookup"><span data-stu-id="38525-125">storeName</span></span>|<span data-ttu-id="38525-126">Licznik.</span><span class="sxs-lookup"><span data-stu-id="38525-126">Enumeration.</span></span> <span data-ttu-id="38525-127">Jeden z magazynów systemu do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="38525-127">One of the system stores to search.</span></span>|  
|<span data-ttu-id="38525-128">x509FindType</span><span class="sxs-lookup"><span data-stu-id="38525-128">x509FindType</span></span>|<span data-ttu-id="38525-129">Licznik.</span><span class="sxs-lookup"><span data-stu-id="38525-129">Enumeration.</span></span> <span data-ttu-id="38525-130">Jedno z pól certyfikatów do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="38525-130">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="38525-131">findValue — atrybut</span><span class="sxs-lookup"><span data-stu-id="38525-131">findValue Attribute</span></span>  
  
|<span data-ttu-id="38525-132">Wartość</span><span class="sxs-lookup"><span data-stu-id="38525-132">Value</span></span>|<span data-ttu-id="38525-133">Opis</span><span class="sxs-lookup"><span data-stu-id="38525-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38525-134">String</span><span class="sxs-lookup"><span data-stu-id="38525-134">String</span></span>|<span data-ttu-id="38525-135">Wartość jest zależna od pola (określonego przez atrybut X509FindType), który jest przeszukiwany.</span><span class="sxs-lookup"><span data-stu-id="38525-135">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="38525-136">Na przykład, jeśli szukasz odcisku palca, wartość musi być ciągiem liczb szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="38525-136">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="38525-137">x509FindType — atrybut</span><span class="sxs-lookup"><span data-stu-id="38525-137">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="38525-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="38525-138">Value</span></span>|<span data-ttu-id="38525-139">Opis</span><span class="sxs-lookup"><span data-stu-id="38525-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38525-140">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="38525-140">Enumeration</span></span>|<span data-ttu-id="38525-141">Dostępne są następujące wartości: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="38525-141">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="38525-142">storeLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="38525-142">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="38525-143">Wartość</span><span class="sxs-lookup"><span data-stu-id="38525-143">Value</span></span>|<span data-ttu-id="38525-144">Opis</span><span class="sxs-lookup"><span data-stu-id="38525-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38525-145">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="38525-145">Enumeration</span></span>|<span data-ttu-id="38525-146">CurrentUser lub LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="38525-146">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="38525-147">storeName — atrybut</span><span class="sxs-lookup"><span data-stu-id="38525-147">storeName Attribute</span></span>  
  
|<span data-ttu-id="38525-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="38525-148">Value</span></span>|<span data-ttu-id="38525-149">Opis</span><span class="sxs-lookup"><span data-stu-id="38525-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38525-150">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="38525-150">Enumeration</span></span>|<span data-ttu-id="38525-151">Dostępne są następujące wartości: AddressBook, AuthRoot, urząd certyfikacji, niedozwolone, my, root, TrustedPeople i TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="38525-151">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38525-152">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="38525-152">Child Elements</span></span>  
 <span data-ttu-id="38525-153">Brak.</span><span class="sxs-lookup"><span data-stu-id="38525-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38525-154">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="38525-154">Parent Elements</span></span>  
  
|<span data-ttu-id="38525-155">Element</span><span class="sxs-lookup"><span data-stu-id="38525-155">Element</span></span>|<span data-ttu-id="38525-156">Opis</span><span class="sxs-lookup"><span data-stu-id="38525-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38525-157">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="38525-157">\<knownCertificates></span></span>](knowncertificates.md)|<span data-ttu-id="38525-158">Reprezentuje kolekcję certyfikatów X. 509, które są dostarczane przez usługę tokenu zabezpieczającego (STS) do sprawdzania poprawności tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="38525-158">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38525-159">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38525-159">Remarks</span></span>  
 <span data-ttu-id="38525-160">Scenariusz wystawionego tokenu ma trzy etapy.</span><span class="sxs-lookup"><span data-stu-id="38525-160">The issued token scenario has three stages.</span></span> <span data-ttu-id="38525-161">Na pierwszym etapie klient próbujący uzyskać dostęp do usługi jest nazywany *usługą bezpiecznego tokenu*.</span><span class="sxs-lookup"><span data-stu-id="38525-161">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="38525-162">Usługa Secure Tokens następnie uwierzytelnia klienta, a następnie wystawia klientowi token, zwykle tokena "Security Assertions Markup Language" (SAML).</span><span class="sxs-lookup"><span data-stu-id="38525-162">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="38525-163">Klient następnie wraca do usługi przy użyciu tokenu.</span><span class="sxs-lookup"><span data-stu-id="38525-163">The client then returns to the service with the token.</span></span> <span data-ttu-id="38525-164">Usługa bada token dla danych, które umożliwiają usłudze uwierzytelnianie tokenu i w związku z tym klienta.</span><span class="sxs-lookup"><span data-stu-id="38525-164">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="38525-165">Aby uwierzytelnić token, certyfikat, którego używa usługa bezpiecznego tokenu, musi być znany usłudze.</span><span class="sxs-lookup"><span data-stu-id="38525-165">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="38525-166">Element > IssuedTokenAuthentication jest repozytorium dla wszystkich takich certyfikatów usługi Secure Token Service. [ \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="38525-166">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="38525-167">Aby dodać certyfikaty, użyj [ \<> knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="38525-167">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="38525-168">Wstaw element [> knownCertificates element \<> dla każdego certyfikatu, jak pokazano w poniższym przykładzie. \<](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="38525-168">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="38525-169">Domyślnie certyfikaty muszą być uzyskiwane z usługi bezpiecznego tokenu.</span><span class="sxs-lookup"><span data-stu-id="38525-169">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="38525-170">Te "znane" certyfikaty zapewniają dostęp do usługi tylko uprawnionym klientom.</span><span class="sxs-lookup"><span data-stu-id="38525-170">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="38525-171">Aby sprawdzić warunki wymagane do uwierzytelnienia klienta przez usługę federacyjną, a także więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [How to: Skonfiguruj poświadczenia na usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="38525-171">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="38525-172">Aby uzyskać więcej informacji na temat scenariuszy federacyjnych, zobacz [federacyjnego i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="38525-172">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="38525-173">Przykład</span><span class="sxs-lookup"><span data-stu-id="38525-173">Example</span></span>  
 <span data-ttu-id="38525-174">Poniższy przykład dodaje certyfikat do repozytorium dla wszystkich certyfikatów usługi STS.</span><span class="sxs-lookup"><span data-stu-id="38525-174">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38525-175">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38525-175">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="38525-176">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="38525-176">\<knownCertificates></span></span>](knowncertificates.md)
- [<span data-ttu-id="38525-177">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="38525-177">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="38525-178">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="38525-178">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="38525-179">Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna</span><span class="sxs-lookup"><span data-stu-id="38525-179">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="38525-180">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="38525-180">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
