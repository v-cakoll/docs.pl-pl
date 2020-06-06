---
title: <add> dla <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 29b067e6ec20992084f9ab3bab087222bdd56da2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400619"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="0fd6b-102">\<add> dla \<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="0fd6b-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="0fd6b-103">Dodaje certyfikat X. 509 do kolekcji znanych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="0fd6b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fd6b-104">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fd6b-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0fd6b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0fd6b-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fd6b-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0fd6b-107">Attributes</span></span>  
  
|<span data-ttu-id="0fd6b-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0fd6b-108">Attribute</span></span>|<span data-ttu-id="0fd6b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="0fd6b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0fd6b-110">findValue</span><span class="sxs-lookup"><span data-stu-id="0fd6b-110">findValue</span></span>|<span data-ttu-id="0fd6b-111">Ciąg.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-111">String.</span></span> <span data-ttu-id="0fd6b-112">Wartość do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-112">The value to search for.</span></span>|  
|<span data-ttu-id="0fd6b-113">storeLocation</span><span class="sxs-lookup"><span data-stu-id="0fd6b-113">storeLocation</span></span>|<span data-ttu-id="0fd6b-114">Licznik.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-114">Enumeration.</span></span> <span data-ttu-id="0fd6b-115">Jedna z dwóch lokalizacji przechowywania do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-115">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="0fd6b-116">storeName</span><span class="sxs-lookup"><span data-stu-id="0fd6b-116">storeName</span></span>|<span data-ttu-id="0fd6b-117">Licznik.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-117">Enumeration.</span></span> <span data-ttu-id="0fd6b-118">Jeden z magazynów systemu do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-118">One of the system stores to search.</span></span>|  
|<span data-ttu-id="0fd6b-119">x509FindType</span><span class="sxs-lookup"><span data-stu-id="0fd6b-119">x509FindType</span></span>|<span data-ttu-id="0fd6b-120">Licznik.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-120">Enumeration.</span></span> <span data-ttu-id="0fd6b-121">Jedno z pól certyfikatów do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-121">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="0fd6b-122">findValue — atrybut</span><span class="sxs-lookup"><span data-stu-id="0fd6b-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="0fd6b-123">Wartość</span><span class="sxs-lookup"><span data-stu-id="0fd6b-123">Value</span></span>|<span data-ttu-id="0fd6b-124">Opis</span><span class="sxs-lookup"><span data-stu-id="0fd6b-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0fd6b-125">String</span><span class="sxs-lookup"><span data-stu-id="0fd6b-125">String</span></span>|<span data-ttu-id="0fd6b-126">Wartość jest zależna od pola (określonego przez atrybut X509FindType), który jest przeszukiwany.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="0fd6b-127">Na przykład, jeśli szukasz odcisku palca, wartość musi być ciągiem liczb szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="0fd6b-128">x509FindType — atrybut</span><span class="sxs-lookup"><span data-stu-id="0fd6b-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="0fd6b-129">Wartość</span><span class="sxs-lookup"><span data-stu-id="0fd6b-129">Value</span></span>|<span data-ttu-id="0fd6b-130">Opis</span><span class="sxs-lookup"><span data-stu-id="0fd6b-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0fd6b-131">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0fd6b-131">Enumeration</span></span>|<span data-ttu-id="0fd6b-132">Dostępne są następujące wartości: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="0fd6b-133">storeLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="0fd6b-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="0fd6b-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="0fd6b-134">Value</span></span>|<span data-ttu-id="0fd6b-135">Opis</span><span class="sxs-lookup"><span data-stu-id="0fd6b-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0fd6b-136">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0fd6b-136">Enumeration</span></span>|<span data-ttu-id="0fd6b-137">CurrentUser lub LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="0fd6b-138">storeName — atrybut</span><span class="sxs-lookup"><span data-stu-id="0fd6b-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="0fd6b-139">Wartość</span><span class="sxs-lookup"><span data-stu-id="0fd6b-139">Value</span></span>|<span data-ttu-id="0fd6b-140">Opis</span><span class="sxs-lookup"><span data-stu-id="0fd6b-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0fd6b-141">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0fd6b-141">Enumeration</span></span>|<span data-ttu-id="0fd6b-142">Dostępne są następujące wartości: AddressBook, AuthRoot, urząd certyfikacji, niedozwolone, my, root, TrustedPeople i TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fd6b-143">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0fd6b-143">Child Elements</span></span>  
 <span data-ttu-id="0fd6b-144">Brak.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0fd6b-145">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0fd6b-145">Parent Elements</span></span>  
  
|<span data-ttu-id="0fd6b-146">Element</span><span class="sxs-lookup"><span data-stu-id="0fd6b-146">Element</span></span>|<span data-ttu-id="0fd6b-147">Opis</span><span class="sxs-lookup"><span data-stu-id="0fd6b-147">Description</span></span>|  
|-------------|-----------------|  
|[\<knownCertificates>](knowncertificates.md)|<span data-ttu-id="0fd6b-148">Reprezentuje kolekcję certyfikatów X. 509, które są dostarczane przez usługę tokenu zabezpieczającego (STS) do sprawdzania poprawności tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-148">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fd6b-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0fd6b-149">Remarks</span></span>  
 <span data-ttu-id="0fd6b-150">Scenariusz wystawionego tokenu ma trzy etapy.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-150">The issued token scenario has three stages.</span></span> <span data-ttu-id="0fd6b-151">Na pierwszym etapie klient próbujący uzyskać dostęp do usługi jest nazywany *usługą bezpiecznego tokenu*.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-151">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="0fd6b-152">Usługa Secure Tokens następnie uwierzytelnia klienta, a następnie wystawia klientowi token, zwykle tokena "Security Assertions Markup Language" (SAML).</span><span class="sxs-lookup"><span data-stu-id="0fd6b-152">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="0fd6b-153">Klient następnie wraca do usługi przy użyciu tokenu.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-153">The client then returns to the service with the token.</span></span> <span data-ttu-id="0fd6b-154">Usługa bada token dla danych, które umożliwiają usłudze uwierzytelnianie tokenu i w związku z tym klienta.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-154">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="0fd6b-155">Aby uwierzytelnić token, certyfikat, którego używa usługa bezpiecznego tokenu, musi być znany usłudze.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-155">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="0fd6b-156">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)Element jest repozytorium dla wszystkich takich certyfikatów usługi Secure Token Service.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-156">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="0fd6b-157">Aby dodać certyfikaty, użyj [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="0fd6b-157">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="0fd6b-158">Wstaw [ \<add> \<knownCertificates> element](add-of-knowncertificates.md) elementu dla każdego certyfikatu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-158">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="0fd6b-159">Domyślnie certyfikaty muszą być uzyskiwane z usługi bezpiecznego tokenu.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-159">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="0fd6b-160">Te "znane" certyfikaty zapewniają dostęp do usługi tylko uprawnionym klientom.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-160">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="0fd6b-161">Aby sprawdzić warunki wymagane przez klienta do uwierzytelniania za pomocą usługi federacyjnej, a także więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [How to: Configure Credentials in a usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="0fd6b-161">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="0fd6b-162">Aby uzyskać więcej informacji na temat scenariuszy federacyjnych, zobacz [federacyjnego i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="0fd6b-162">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fd6b-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fd6b-163">Example</span></span>  
 <span data-ttu-id="0fd6b-164">Poniższy przykład dodaje certyfikat do repozytorium dla wszystkich certyfikatów usługi STS.</span><span class="sxs-lookup"><span data-stu-id="0fd6b-164">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0fd6b-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fd6b-165">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<knownCertificates>](knowncertificates.md)
- [<span data-ttu-id="0fd6b-166">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="0fd6b-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="0fd6b-167">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="0fd6b-167">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0fd6b-168">Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="0fd6b-168">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="0fd6b-169">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="0fd6b-169">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
