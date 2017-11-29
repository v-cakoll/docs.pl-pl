---
title: '&lt;add&gt; w &lt;scopedCertificates&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e720e69b9c7ee6e6777a69403ff6cee43e532cd1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltscopedcertificatesgt-element"></a><span data-ttu-id="ab6d6-102">&lt;add&gt; w &lt;scopedCertificates&gt;, element</span><span class="sxs-lookup"><span data-stu-id="ab6d6-102">&lt;add&gt; of &lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="ab6d6-103">Dodaje certyfikat X.509 do kolekcji certyfikatów będących w zakresie.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="ab6d6-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ab6d6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ab6d6-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="ab6d6-105">\<behaviors></span></span>  
<span data-ttu-id="ab6d6-106">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="ab6d6-106">endpointBehaviors section</span></span>  
<span data-ttu-id="ab6d6-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ab6d6-107">\<behavior></span></span>  
<span data-ttu-id="ab6d6-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="ab6d6-108">\<clientCredentials></span></span>  
<span data-ttu-id="ab6d6-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="ab6d6-109">\<serviceCertificate></span></span>  
<span data-ttu-id="ab6d6-110">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="ab6d6-110">\<scopedCertificates></span></span>  
<span data-ttu-id="ab6d6-111">\<Dodaj > elementu \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="ab6d6-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab6d6-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab6d6-112">Syntax</span></span>  
  
```xml  
<add findValue="String"  
          storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
          targetUri="string"  
         x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"   
/>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab6d6-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ab6d6-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ab6d6-114">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ab6d6-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab6d6-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ab6d6-115">Attributes</span></span>  
  
|<span data-ttu-id="ab6d6-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ab6d6-116">Attribute</span></span>|<span data-ttu-id="ab6d6-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ab6d6-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab6d6-118">targetUri</span><span class="sxs-lookup"><span data-stu-id="ab6d6-118">targetUri</span></span>|<span data-ttu-id="ab6d6-119">Ciąg.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-119">String.</span></span> <span data-ttu-id="ab6d6-120">Określa identyfikator URI usługi skojarzony z certyfikatem.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="ab6d6-121">findValue</span><span class="sxs-lookup"><span data-stu-id="ab6d6-121">findValue</span></span>|<span data-ttu-id="ab6d6-122">Ciąg.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-122">String.</span></span> <span data-ttu-id="ab6d6-123">Wartość do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-123">The value to search for.</span></span>|  
|<span data-ttu-id="ab6d6-124">X509FindType</span><span class="sxs-lookup"><span data-stu-id="ab6d6-124">x509FindType</span></span>|<span data-ttu-id="ab6d6-125">Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-125">Enumeration.</span></span> <span data-ttu-id="ab6d6-126">Jedno z pól certyfikatu do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="ab6d6-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="ab6d6-127">storeLocation</span></span>|<span data-ttu-id="ab6d6-128">Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-128">Enumeration.</span></span> <span data-ttu-id="ab6d6-129">Jedna z dwóch lokalizacji przechowywania do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="ab6d6-130">storeName</span><span class="sxs-lookup"><span data-stu-id="ab6d6-130">storeName</span></span>|<span data-ttu-id="ab6d6-131">Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-131">Enumeration.</span></span> <span data-ttu-id="ab6d6-132">Jednym z systemów magazynowania do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="ab6d6-133">findValue atrybutu</span><span class="sxs-lookup"><span data-stu-id="ab6d6-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="ab6d6-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="ab6d6-134">Value</span></span>|<span data-ttu-id="ab6d6-135">Opis</span><span class="sxs-lookup"><span data-stu-id="ab6d6-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab6d6-136">String</span><span class="sxs-lookup"><span data-stu-id="ab6d6-136">String</span></span>|<span data-ttu-id="ab6d6-137">Wartość jest zależna od pola (określony przez atrybut X509FindType) przeszukiwany.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="ab6d6-138">Na przykład wyszukiwania odcisk palca, wartość musi być ciągiem szesnastkowym liczb.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="ab6d6-139">Atrybut x509FindType</span><span class="sxs-lookup"><span data-stu-id="ab6d6-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="ab6d6-140">Wartość</span><span class="sxs-lookup"><span data-stu-id="ab6d6-140">Value</span></span>|<span data-ttu-id="ab6d6-141">Opis</span><span class="sxs-lookup"><span data-stu-id="ab6d6-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab6d6-142">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ab6d6-142">Enumeration</span></span>|<span data-ttu-id="ab6d6-143">Wartości to: postać FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="ab6d6-144">storeLocation atrybutu</span><span class="sxs-lookup"><span data-stu-id="ab6d6-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="ab6d6-145">Wartość</span><span class="sxs-lookup"><span data-stu-id="ab6d6-145">Value</span></span>|<span data-ttu-id="ab6d6-146">Opis</span><span class="sxs-lookup"><span data-stu-id="ab6d6-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab6d6-147">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ab6d6-147">Enumeration</span></span>|<span data-ttu-id="ab6d6-148">Lub LocalMachine CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="ab6d6-149">storeName atrybutu</span><span class="sxs-lookup"><span data-stu-id="ab6d6-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="ab6d6-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="ab6d6-150">Value</span></span>|<span data-ttu-id="ab6d6-151">Opis</span><span class="sxs-lookup"><span data-stu-id="ab6d6-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab6d6-152">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ab6d6-152">Enumeration</span></span>|<span data-ttu-id="ab6d6-153">Wartości to: książka adresowa, AuthRoot, urząd certyfikacji, niedozwolone mojej, głównego, TrustedPeople i TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab6d6-154">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ab6d6-154">Child Elements</span></span>  
 <span data-ttu-id="ab6d6-155">Brak.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab6d6-156">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ab6d6-156">Parent Elements</span></span>  
  
|<span data-ttu-id="ab6d6-157">Element</span><span class="sxs-lookup"><span data-stu-id="ab6d6-157">Element</span></span>|<span data-ttu-id="ab6d6-158">Opis</span><span class="sxs-lookup"><span data-stu-id="ab6d6-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab6d6-159">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="ab6d6-159">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="ab6d6-160">Reprezentuje kolekcję certyfikatów X.509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab6d6-161">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab6d6-161">Remarks</span></span>  
 <span data-ttu-id="ab6d6-162">Ten element umożliwia klientowi skonfigurować certyfikat usługi do użycia na podstawie adresu URL usługi, z którym się komunikuje.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="ab6d6-163">Jest to szczególnie przydatne w wystawionego tokenu scenariuszach, gdzie klient może komunikować się wiele usług (usług a także usługi tokenu zabezpieczeń pośredniczące).</span><span class="sxs-lookup"><span data-stu-id="ab6d6-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="ab6d6-164">Dla powiązań, które korzystają z zabezpieczeń wiadomości opartego na certyfikatach ten certyfikat jest używany do szyfrowania wiadomości do usługi, a powinien być używany przez usługę do podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="ab6d6-165">Jeśli powiązanie wymaga certyfikatu dla usługi i nie określonego certyfikatu dla usługi, którą można odnaleźć adresu URL w ScopedCertificates, jest używany certyfikat domyślny.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="ab6d6-166">Aby uzyskać więcej informacji, zobacz sekcję "O zakresie certyfikatów" [porady: Tworzenie klienta federacyjnego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="ab6d6-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab6d6-167">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab6d6-167">Example</span></span>  
 <span data-ttu-id="ab6d6-168">Poniższy przykład dodaje certyfikat X.509 kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ab6d6-168">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ab6d6-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab6d6-169">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="ab6d6-170">Porady: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="ab6d6-170">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="ab6d6-171">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="ab6d6-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="ab6d6-172">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="ab6d6-172">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="ab6d6-173">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ab6d6-173">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
