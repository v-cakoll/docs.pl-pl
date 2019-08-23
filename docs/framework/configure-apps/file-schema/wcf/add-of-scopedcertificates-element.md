---
title: <add><scopedCertificates> elementu
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 9756d37527fcf888cad930b24677ae8e6a2c8fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920053"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="ee697-102">\<Dodaj > \<elementu scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="ee697-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="ee697-103">Dodaje certyfikat X. 509 do kolekcji certyfikatów z zakresem.</span><span class="sxs-lookup"><span data-stu-id="ee697-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="ee697-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ee697-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ee697-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="ee697-105">\<behaviors></span></span>  
<span data-ttu-id="ee697-106">Sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="ee697-106">endpointBehaviors section</span></span>  
<span data-ttu-id="ee697-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="ee697-107">\<behavior></span></span>  
<span data-ttu-id="ee697-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="ee697-108">\<clientCredentials></span></span>  
<span data-ttu-id="ee697-109">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="ee697-109">\<serviceCertificate></span></span>  
<span data-ttu-id="ee697-110">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="ee697-110">\<scopedCertificates></span></span>  
<span data-ttu-id="ee697-111">\<Dodaj element > dla \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="ee697-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee697-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee697-112">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee697-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ee697-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ee697-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ee697-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee697-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ee697-115">Attributes</span></span>  
  
|<span data-ttu-id="ee697-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ee697-116">Attribute</span></span>|<span data-ttu-id="ee697-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ee697-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee697-118">targetUri</span><span class="sxs-lookup"><span data-stu-id="ee697-118">targetUri</span></span>|<span data-ttu-id="ee697-119">Parametry.</span><span class="sxs-lookup"><span data-stu-id="ee697-119">String.</span></span> <span data-ttu-id="ee697-120">Określa identyfikator URI usługi skojarzonej z certyfikatem.</span><span class="sxs-lookup"><span data-stu-id="ee697-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="ee697-121">findValue</span><span class="sxs-lookup"><span data-stu-id="ee697-121">findValue</span></span>|<span data-ttu-id="ee697-122">Parametry.</span><span class="sxs-lookup"><span data-stu-id="ee697-122">String.</span></span> <span data-ttu-id="ee697-123">Wartość do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="ee697-123">The value to search for.</span></span>|  
|<span data-ttu-id="ee697-124">x509FindType</span><span class="sxs-lookup"><span data-stu-id="ee697-124">x509FindType</span></span>|<span data-ttu-id="ee697-125">Licznik.</span><span class="sxs-lookup"><span data-stu-id="ee697-125">Enumeration.</span></span> <span data-ttu-id="ee697-126">Jedno z pól certyfikatów do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="ee697-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="ee697-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="ee697-127">storeLocation</span></span>|<span data-ttu-id="ee697-128">Licznik.</span><span class="sxs-lookup"><span data-stu-id="ee697-128">Enumeration.</span></span> <span data-ttu-id="ee697-129">Jedna z dwóch lokalizacji przechowywania do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="ee697-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="ee697-130">storeName</span><span class="sxs-lookup"><span data-stu-id="ee697-130">storeName</span></span>|<span data-ttu-id="ee697-131">Licznik.</span><span class="sxs-lookup"><span data-stu-id="ee697-131">Enumeration.</span></span> <span data-ttu-id="ee697-132">Jeden z magazynów systemu do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="ee697-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="ee697-133">findValue — atrybut</span><span class="sxs-lookup"><span data-stu-id="ee697-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="ee697-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="ee697-134">Value</span></span>|<span data-ttu-id="ee697-135">Opis</span><span class="sxs-lookup"><span data-stu-id="ee697-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ee697-136">String</span><span class="sxs-lookup"><span data-stu-id="ee697-136">String</span></span>|<span data-ttu-id="ee697-137">Wartość jest zależna od pola (określonego przez atrybut X509FindType), który jest przeszukiwany.</span><span class="sxs-lookup"><span data-stu-id="ee697-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="ee697-138">Na przykład, jeśli szukasz odcisku palca, wartość musi być ciągiem liczb szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="ee697-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="ee697-139">x509FindType — atrybut</span><span class="sxs-lookup"><span data-stu-id="ee697-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="ee697-140">Wartość</span><span class="sxs-lookup"><span data-stu-id="ee697-140">Value</span></span>|<span data-ttu-id="ee697-141">Opis</span><span class="sxs-lookup"><span data-stu-id="ee697-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ee697-142">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ee697-142">Enumeration</span></span>|<span data-ttu-id="ee697-143">Dostępne są następujące wartości: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="ee697-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="ee697-144">storeLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="ee697-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="ee697-145">Wartość</span><span class="sxs-lookup"><span data-stu-id="ee697-145">Value</span></span>|<span data-ttu-id="ee697-146">Opis</span><span class="sxs-lookup"><span data-stu-id="ee697-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ee697-147">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ee697-147">Enumeration</span></span>|<span data-ttu-id="ee697-148">CurrentUser lub LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="ee697-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="ee697-149">storeName — atrybut</span><span class="sxs-lookup"><span data-stu-id="ee697-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="ee697-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="ee697-150">Value</span></span>|<span data-ttu-id="ee697-151">Opis</span><span class="sxs-lookup"><span data-stu-id="ee697-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ee697-152">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ee697-152">Enumeration</span></span>|<span data-ttu-id="ee697-153">Dostępne są następujące wartości: AddressBook, AuthRoot, urząd certyfikacji, niedozwolone, my, root, TrustedPeople i TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="ee697-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee697-154">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ee697-154">Child Elements</span></span>  
 <span data-ttu-id="ee697-155">Brak.</span><span class="sxs-lookup"><span data-stu-id="ee697-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee697-156">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ee697-156">Parent Elements</span></span>  
  
|<span data-ttu-id="ee697-157">Element</span><span class="sxs-lookup"><span data-stu-id="ee697-157">Element</span></span>|<span data-ttu-id="ee697-158">Opis</span><span class="sxs-lookup"><span data-stu-id="ee697-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee697-159">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="ee697-159">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="ee697-160">Reprezentuje kolekcję certyfikatów X. 509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ee697-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee697-161">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee697-161">Remarks</span></span>  
 <span data-ttu-id="ee697-162">Ten element umożliwia klientowi skonfigurowanie certyfikatu usługi do użycia na podstawie adresu URL usługi, z którą się komunikuje.</span><span class="sxs-lookup"><span data-stu-id="ee697-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="ee697-163">Jest to szczególnie przydatne w scenariuszach wystawionych tokenów, w których klient może komunikować się z wieloma usługami (usługą końcową oraz usługami tokenów zabezpieczających).</span><span class="sxs-lookup"><span data-stu-id="ee697-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="ee697-164">W przypadku powiązań korzystających z zabezpieczeń komunikatów opartych na certyfikatach ten certyfikat jest używany do szyfrowania komunikatów do usługi i powinien być używany przez usługę do podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="ee697-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="ee697-165">Jeśli powiązanie wymaga certyfikatu dla usługi i nie zostanie znaleziony konkretny certyfikat dla adresu URL usługi w ScopedCertificates, zostanie użyty certyfikat domyślny.</span><span class="sxs-lookup"><span data-stu-id="ee697-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="ee697-166">Aby uzyskać więcej informacji, zobacz sekcję ["certyfikaty w zakresie", w jaki sposób: Utwórz klienta](../../../wcf/feature-details/how-to-create-a-federated-client.md)federacyjnego.</span><span class="sxs-lookup"><span data-stu-id="ee697-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee697-167">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee697-167">Example</span></span>  
 <span data-ttu-id="ee697-168">Poniższy przykład dodaje do kolekcji certyfikat X. 509.</span><span class="sxs-lookup"><span data-stu-id="ee697-168">The following example adds an X.509 certificate the collection.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <serviceCertificate>
          <scopedCertificates>
            <add targetUri="http://www.contoso.com"
                 findValue="www.Contoso.com"
                 storeLocation="LocalMachine"
                 storeName="Root"
                 x509FindType="FindByIssuerName" />
          </scopedCertificates>
        </serviceCertificate>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="ee697-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee697-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="ee697-170">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="ee697-170">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="ee697-171">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="ee697-171">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="ee697-172">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="ee697-172">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="ee697-173">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ee697-173">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
