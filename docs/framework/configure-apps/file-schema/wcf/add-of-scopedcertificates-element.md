---
title: '&lt;add&gt; w &lt;scopedCertificates&gt;, element'
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: a173d3b137833abfe8a69aed55b972c9b6469890
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146098"
---
# <a name="ltaddgt-of-ltscopedcertificatesgt-element"></a><span data-ttu-id="49396-102">&lt;add&gt; w &lt;scopedCertificates&gt;, element</span><span class="sxs-lookup"><span data-stu-id="49396-102">&lt;add&gt; of &lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="49396-103">Dodaje certyfikat X.509 do kolekcji certyfikatów będących w zakresie.</span><span class="sxs-lookup"><span data-stu-id="49396-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="49396-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="49396-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="49396-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="49396-105">\<behaviors></span></span>  
<span data-ttu-id="49396-106">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="49396-106">endpointBehaviors section</span></span>  
<span data-ttu-id="49396-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="49396-107">\<behavior></span></span>  
<span data-ttu-id="49396-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="49396-108">\<clientCredentials></span></span>  
<span data-ttu-id="49396-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="49396-109">\<serviceCertificate></span></span>  
<span data-ttu-id="49396-110">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="49396-110">\<scopedCertificates></span></span>  
<span data-ttu-id="49396-111">\<Dodaj >, element dla \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="49396-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49396-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="49396-112">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49396-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="49396-113">Attributes and Elements</span></span>  
 <span data-ttu-id="49396-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="49396-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49396-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="49396-115">Attributes</span></span>  
  
|<span data-ttu-id="49396-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="49396-116">Attribute</span></span>|<span data-ttu-id="49396-117">Opis</span><span class="sxs-lookup"><span data-stu-id="49396-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49396-118">targetUri</span><span class="sxs-lookup"><span data-stu-id="49396-118">targetUri</span></span>|<span data-ttu-id="49396-119">ciąg.</span><span class="sxs-lookup"><span data-stu-id="49396-119">String.</span></span> <span data-ttu-id="49396-120">Określa identyfikator URI usługi skojarzony z certyfikatem.</span><span class="sxs-lookup"><span data-stu-id="49396-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="49396-121">findValue</span><span class="sxs-lookup"><span data-stu-id="49396-121">findValue</span></span>|<span data-ttu-id="49396-122">ciąg.</span><span class="sxs-lookup"><span data-stu-id="49396-122">String.</span></span> <span data-ttu-id="49396-123">Wartość do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="49396-123">The value to search for.</span></span>|  
|<span data-ttu-id="49396-124">X509FindType</span><span class="sxs-lookup"><span data-stu-id="49396-124">x509FindType</span></span>|<span data-ttu-id="49396-125">Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="49396-125">Enumeration.</span></span> <span data-ttu-id="49396-126">Jedno z pól certyfikatu do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="49396-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="49396-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="49396-127">storeLocation</span></span>|<span data-ttu-id="49396-128">Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="49396-128">Enumeration.</span></span> <span data-ttu-id="49396-129">Jednym z dwóch lokalizacji przechowywania do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="49396-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="49396-130">storeName</span><span class="sxs-lookup"><span data-stu-id="49396-130">storeName</span></span>|<span data-ttu-id="49396-131">Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="49396-131">Enumeration.</span></span> <span data-ttu-id="49396-132">Jednym z systemów magazynowania do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="49396-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="49396-133">findValue atrybutu</span><span class="sxs-lookup"><span data-stu-id="49396-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="49396-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="49396-134">Value</span></span>|<span data-ttu-id="49396-135">Opis</span><span class="sxs-lookup"><span data-stu-id="49396-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="49396-136">String</span><span class="sxs-lookup"><span data-stu-id="49396-136">String</span></span>|<span data-ttu-id="49396-137">Wartość zależy od pola (określony przez atrybut X509FindType) wyszukiwany.</span><span class="sxs-lookup"><span data-stu-id="49396-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="49396-138">Na przykład jeśli wyszukiwanie odcisku palca, wartość musi być ciągiem liczb szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="49396-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="49396-139">Atrybut x509FindType</span><span class="sxs-lookup"><span data-stu-id="49396-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="49396-140">Wartość</span><span class="sxs-lookup"><span data-stu-id="49396-140">Value</span></span>|<span data-ttu-id="49396-141">Opis</span><span class="sxs-lookup"><span data-stu-id="49396-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="49396-142">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="49396-142">Enumeration</span></span>|<span data-ttu-id="49396-143">Wartości: FindByThumbprint FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="49396-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="49396-144">storeLocation atrybutu</span><span class="sxs-lookup"><span data-stu-id="49396-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="49396-145">Wartość</span><span class="sxs-lookup"><span data-stu-id="49396-145">Value</span></span>|<span data-ttu-id="49396-146">Opis</span><span class="sxs-lookup"><span data-stu-id="49396-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="49396-147">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="49396-147">Enumeration</span></span>|<span data-ttu-id="49396-148">CurrentUser lub LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="49396-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="49396-149">storeName atrybutu</span><span class="sxs-lookup"><span data-stu-id="49396-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="49396-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="49396-150">Value</span></span>|<span data-ttu-id="49396-151">Opis</span><span class="sxs-lookup"><span data-stu-id="49396-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="49396-152">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="49396-152">Enumeration</span></span>|<span data-ttu-id="49396-153">Wartości: Książka adresowa, AuthRoot, urząd certyfikacji, niedozwolone mojej, główny, TrustedPeople i TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="49396-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49396-154">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="49396-154">Child Elements</span></span>  
 <span data-ttu-id="49396-155">Brak.</span><span class="sxs-lookup"><span data-stu-id="49396-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="49396-156">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="49396-156">Parent Elements</span></span>  
  
|<span data-ttu-id="49396-157">Element</span><span class="sxs-lookup"><span data-stu-id="49396-157">Element</span></span>|<span data-ttu-id="49396-158">Opis</span><span class="sxs-lookup"><span data-stu-id="49396-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49396-159">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="49396-159">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="49396-160">Reprezentuje kolekcję certyfikatów X.509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49396-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49396-161">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49396-161">Remarks</span></span>  
 <span data-ttu-id="49396-162">Ten element umożliwia klienta skonfigurować certyfikat usługi do użycia na podstawie adresu URL usługi, którym się komunikuje.</span><span class="sxs-lookup"><span data-stu-id="49396-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="49396-163">Jest to szczególnie przydatne w wystawionych tokenów scenariuszach, gdzie klienta może się komunikować z wielu usług (service zakończenia także usługach tokenów zabezpieczeń pośrednie).</span><span class="sxs-lookup"><span data-stu-id="49396-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="49396-164">Dla powiązań, które korzystają z zabezpieczeń komunikatów opartego na certyfikatach ten certyfikat jest używany do szyfrowania komunikatów do usługi, a powinien być używany przez usługę do podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="49396-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="49396-165">Jeśli powiązanie wymaga certyfikatu dla usługi i nie określonego certyfikatu dla usługi, którą można odnaleźć adresu URL w ScopedCertificates, jest używany certyfikat domyślny.</span><span class="sxs-lookup"><span data-stu-id="49396-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="49396-166">Aby uzyskać więcej informacji, zobacz sekcję "O zakresie certyfikatów" [jak: Tworzenie klienta federacyjnego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="49396-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="49396-167">Przykład</span><span class="sxs-lookup"><span data-stu-id="49396-167">Example</span></span>  
 <span data-ttu-id="49396-168">Poniższy przykład dodaje certyfikat X.509 kolekcji.</span><span class="sxs-lookup"><span data-stu-id="49396-168">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="49396-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49396-169">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="49396-170">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="49396-170">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="49396-171">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="49396-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="49396-172">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="49396-172">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="49396-173">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="49396-173">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
