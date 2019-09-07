---
title: <add><scopedCertificates> elementu
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: b00a342108beca69a906fbf6212915768e98778f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398349"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="76879-102">\<Dodaj > \<elementu scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="76879-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="76879-103">Dodaje certyfikat X. 509 do kolekcji certyfikatów z zakresem.</span><span class="sxs-lookup"><span data-stu-id="76879-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
<span data-ttu-id="76879-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="76879-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="76879-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="76879-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="76879-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="76879-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="76879-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="76879-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="76879-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="76879-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="76879-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Obiekt clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="76879-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="76879-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceCertificate**](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="76879-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="76879-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<scopedCertificates >** ](scopedcertificates-element.md)</span><span class="sxs-lookup"><span data-stu-id="76879-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopedCertificates>**](scopedcertificates-element.md)</span></span>\
<span data-ttu-id="76879-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="76879-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76879-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="76879-113">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76879-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="76879-114">Attributes and Elements</span></span>  
 <span data-ttu-id="76879-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="76879-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76879-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="76879-116">Attributes</span></span>  
  
|<span data-ttu-id="76879-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="76879-117">Attribute</span></span>|<span data-ttu-id="76879-118">Opis</span><span class="sxs-lookup"><span data-stu-id="76879-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76879-119">targetUri</span><span class="sxs-lookup"><span data-stu-id="76879-119">targetUri</span></span>|<span data-ttu-id="76879-120">Parametry.</span><span class="sxs-lookup"><span data-stu-id="76879-120">String.</span></span> <span data-ttu-id="76879-121">Określa identyfikator URI usługi skojarzonej z certyfikatem.</span><span class="sxs-lookup"><span data-stu-id="76879-121">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="76879-122">findValue</span><span class="sxs-lookup"><span data-stu-id="76879-122">findValue</span></span>|<span data-ttu-id="76879-123">Parametry.</span><span class="sxs-lookup"><span data-stu-id="76879-123">String.</span></span> <span data-ttu-id="76879-124">Wartość do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="76879-124">The value to search for.</span></span>|  
|<span data-ttu-id="76879-125">x509FindType</span><span class="sxs-lookup"><span data-stu-id="76879-125">x509FindType</span></span>|<span data-ttu-id="76879-126">Licznik.</span><span class="sxs-lookup"><span data-stu-id="76879-126">Enumeration.</span></span> <span data-ttu-id="76879-127">Jedno z pól certyfikatów do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="76879-127">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="76879-128">storeLocation</span><span class="sxs-lookup"><span data-stu-id="76879-128">storeLocation</span></span>|<span data-ttu-id="76879-129">Licznik.</span><span class="sxs-lookup"><span data-stu-id="76879-129">Enumeration.</span></span> <span data-ttu-id="76879-130">Jedna z dwóch lokalizacji przechowywania do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="76879-130">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="76879-131">storeName</span><span class="sxs-lookup"><span data-stu-id="76879-131">storeName</span></span>|<span data-ttu-id="76879-132">Licznik.</span><span class="sxs-lookup"><span data-stu-id="76879-132">Enumeration.</span></span> <span data-ttu-id="76879-133">Jeden z magazynów systemu do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="76879-133">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="76879-134">findValue — atrybut</span><span class="sxs-lookup"><span data-stu-id="76879-134">findValue Attribute</span></span>  
  
|<span data-ttu-id="76879-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="76879-135">Value</span></span>|<span data-ttu-id="76879-136">Opis</span><span class="sxs-lookup"><span data-stu-id="76879-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="76879-137">String</span><span class="sxs-lookup"><span data-stu-id="76879-137">String</span></span>|<span data-ttu-id="76879-138">Wartość jest zależna od pola (określonego przez atrybut X509FindType), który jest przeszukiwany.</span><span class="sxs-lookup"><span data-stu-id="76879-138">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="76879-139">Na przykład, jeśli szukasz odcisku palca, wartość musi być ciągiem liczb szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="76879-139">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="76879-140">x509FindType — atrybut</span><span class="sxs-lookup"><span data-stu-id="76879-140">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="76879-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="76879-141">Value</span></span>|<span data-ttu-id="76879-142">Opis</span><span class="sxs-lookup"><span data-stu-id="76879-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="76879-143">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="76879-143">Enumeration</span></span>|<span data-ttu-id="76879-144">Dostępne są następujące wartości: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="76879-144">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="76879-145">storeLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="76879-145">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="76879-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="76879-146">Value</span></span>|<span data-ttu-id="76879-147">Opis</span><span class="sxs-lookup"><span data-stu-id="76879-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="76879-148">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="76879-148">Enumeration</span></span>|<span data-ttu-id="76879-149">CurrentUser lub LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="76879-149">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="76879-150">storeName — atrybut</span><span class="sxs-lookup"><span data-stu-id="76879-150">storeName Attribute</span></span>  
  
|<span data-ttu-id="76879-151">Wartość</span><span class="sxs-lookup"><span data-stu-id="76879-151">Value</span></span>|<span data-ttu-id="76879-152">Opis</span><span class="sxs-lookup"><span data-stu-id="76879-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="76879-153">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="76879-153">Enumeration</span></span>|<span data-ttu-id="76879-154">Dostępne są następujące wartości: AddressBook, AuthRoot, urząd certyfikacji, niedozwolone, my, root, TrustedPeople i TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="76879-154">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76879-155">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="76879-155">Child Elements</span></span>  
 <span data-ttu-id="76879-156">Brak.</span><span class="sxs-lookup"><span data-stu-id="76879-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76879-157">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="76879-157">Parent Elements</span></span>  
  
|<span data-ttu-id="76879-158">Element</span><span class="sxs-lookup"><span data-stu-id="76879-158">Element</span></span>|<span data-ttu-id="76879-159">Opis</span><span class="sxs-lookup"><span data-stu-id="76879-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76879-160">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="76879-160">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="76879-161">Reprezentuje kolekcję certyfikatów X. 509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="76879-161">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76879-162">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76879-162">Remarks</span></span>  
 <span data-ttu-id="76879-163">Ten element umożliwia klientowi skonfigurowanie certyfikatu usługi do użycia na podstawie adresu URL usługi, z którą się komunikuje.</span><span class="sxs-lookup"><span data-stu-id="76879-163">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="76879-164">Jest to szczególnie przydatne w scenariuszach wystawionych tokenów, w których klient może komunikować się z wieloma usługami (usługą końcową oraz usługami tokenów zabezpieczających).</span><span class="sxs-lookup"><span data-stu-id="76879-164">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="76879-165">W przypadku powiązań korzystających z zabezpieczeń komunikatów opartych na certyfikatach ten certyfikat jest używany do szyfrowania komunikatów do usługi i powinien być używany przez usługę do podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="76879-165">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="76879-166">Jeśli powiązanie wymaga certyfikatu dla usługi i nie zostanie znaleziony konkretny certyfikat dla adresu URL usługi w ScopedCertificates, zostanie użyty certyfikat domyślny.</span><span class="sxs-lookup"><span data-stu-id="76879-166">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="76879-167">Aby uzyskać więcej informacji, zobacz sekcję ["certyfikaty w zakresie", w jaki sposób: Utwórz klienta](../../../wcf/feature-details/how-to-create-a-federated-client.md)federacyjnego.</span><span class="sxs-lookup"><span data-stu-id="76879-167">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76879-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="76879-168">Example</span></span>  
 <span data-ttu-id="76879-169">Poniższy przykład dodaje do kolekcji certyfikat X. 509.</span><span class="sxs-lookup"><span data-stu-id="76879-169">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76879-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76879-170">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="76879-171">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="76879-171">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="76879-172">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="76879-172">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="76879-173">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="76879-173">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="76879-174">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="76879-174">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
