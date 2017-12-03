---
title: '&lt;defaultCertificate&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aae72b7ae006a57683ea0e274fbc072c7f69cfb1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltdefaultcertificategt-element"></a><span data-ttu-id="cfca5-102">&lt;defaultCertificate&gt;, element</span><span class="sxs-lookup"><span data-stu-id="cfca5-102">&lt;defaultCertificate&gt; Element</span></span>
<span data-ttu-id="cfca5-103">Określa certyfikat X.509 do użycia podczas usługa lub STS nie zapewnia go poprzez protokół negocjacji.</span><span class="sxs-lookup"><span data-stu-id="cfca5-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="cfca5-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="cfca5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cfca5-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="cfca5-105">\<behaviors></span></span>  
<span data-ttu-id="cfca5-106">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="cfca5-106">endpointBehaviors section</span></span>  
<span data-ttu-id="cfca5-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="cfca5-107">\<behavior></span></span>  
<span data-ttu-id="cfca5-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="cfca5-108">\<clientCredentials></span></span>  
<span data-ttu-id="cfca5-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="cfca5-109">\<serviceCertificate></span></span>  
<span data-ttu-id="cfca5-110">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="cfca5-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfca5-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfca5-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfca5-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cfca5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cfca5-113">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cfca5-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfca5-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cfca5-114">Attributes</span></span>  
  
|<span data-ttu-id="cfca5-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cfca5-115">Attribute</span></span>|<span data-ttu-id="cfca5-116">Opis</span><span class="sxs-lookup"><span data-stu-id="cfca5-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cfca5-117">findValue</span><span class="sxs-lookup"><span data-stu-id="cfca5-117">findValue</span></span>|<span data-ttu-id="cfca5-118">Ciąg.</span><span class="sxs-lookup"><span data-stu-id="cfca5-118">String.</span></span> <span data-ttu-id="cfca5-119">Wartość do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="cfca5-119">The value to search for.</span></span>|  
|<span data-ttu-id="cfca5-120">X509FindType</span><span class="sxs-lookup"><span data-stu-id="cfca5-120">x509FindType</span></span>|<span data-ttu-id="cfca5-121">Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="cfca5-121">Enumeration.</span></span> <span data-ttu-id="cfca5-122">Jedno z pól certyfikatu do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="cfca5-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="cfca5-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="cfca5-123">storeLocation</span></span>|<span data-ttu-id="cfca5-124">Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="cfca5-124">Enumeration.</span></span> <span data-ttu-id="cfca5-125">Jeden z dwóch systemów przechowywania lokalizacji do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="cfca5-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="cfca5-126">storeName</span><span class="sxs-lookup"><span data-stu-id="cfca5-126">storeName</span></span>|<span data-ttu-id="cfca5-127">Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="cfca5-127">Enumeration.</span></span> <span data-ttu-id="cfca5-128">Jednym z systemów magazynowania do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="cfca5-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="cfca5-129">findValue atrybutu</span><span class="sxs-lookup"><span data-stu-id="cfca5-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="cfca5-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="cfca5-130">Value</span></span>|<span data-ttu-id="cfca5-131">Opis</span><span class="sxs-lookup"><span data-stu-id="cfca5-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cfca5-132">String</span><span class="sxs-lookup"><span data-stu-id="cfca5-132">String</span></span>|<span data-ttu-id="cfca5-133">Wartość jest zależna od pola (określony przez atrybut X509FindType) przeszukiwany.</span><span class="sxs-lookup"><span data-stu-id="cfca5-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="cfca5-134">Na przykład wyszukiwania odcisk palca, wartość musi być ciągiem szesnastkowym liczb.</span><span class="sxs-lookup"><span data-stu-id="cfca5-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="cfca5-135">Atrybut x509FindType</span><span class="sxs-lookup"><span data-stu-id="cfca5-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="cfca5-136">Wartość</span><span class="sxs-lookup"><span data-stu-id="cfca5-136">Value</span></span>|<span data-ttu-id="cfca5-137">Opis</span><span class="sxs-lookup"><span data-stu-id="cfca5-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cfca5-138">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="cfca5-138">Enumeration</span></span>|<span data-ttu-id="cfca5-139">Wartości to: postać FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="cfca5-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="cfca5-140">storeLocation atrybutu</span><span class="sxs-lookup"><span data-stu-id="cfca5-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="cfca5-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="cfca5-141">Value</span></span>|<span data-ttu-id="cfca5-142">Opis</span><span class="sxs-lookup"><span data-stu-id="cfca5-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cfca5-143">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="cfca5-143">Enumeration</span></span>|<span data-ttu-id="cfca5-144">Lub LocalMachine CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="cfca5-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="cfca5-145">storeName atrybutu</span><span class="sxs-lookup"><span data-stu-id="cfca5-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="cfca5-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="cfca5-146">Value</span></span>|<span data-ttu-id="cfca5-147">Opis</span><span class="sxs-lookup"><span data-stu-id="cfca5-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cfca5-148">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="cfca5-148">Enumeration</span></span>|<span data-ttu-id="cfca5-149">Wartości to: książka adresowa, AuthRoot, urząd certyfikacji, niedozwolone mojej, głównego, TrustedPeople i TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="cfca5-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cfca5-150">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cfca5-150">Child Elements</span></span>  
 <span data-ttu-id="cfca5-151">Brak.</span><span class="sxs-lookup"><span data-stu-id="cfca5-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cfca5-152">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cfca5-152">Parent Elements</span></span>  
  
|<span data-ttu-id="cfca5-153">Element</span><span class="sxs-lookup"><span data-stu-id="cfca5-153">Element</span></span>|<span data-ttu-id="cfca5-154">Opis</span><span class="sxs-lookup"><span data-stu-id="cfca5-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfca5-155">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="cfca5-155">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="cfca5-156">Określa certyfikat używany podczas uwierzytelniania usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="cfca5-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfca5-157">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfca5-157">Remarks</span></span>  
 <span data-ttu-id="cfca5-158">Dla powiązań, które korzystają z zabezpieczeń wiadomości opartego na certyfikatach certyfikatu określonego przez ten element konfiguracji jest używany do szyfrowania wiadomości do usługi i powinien być używany przez usługę do podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="cfca5-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="cfca5-159">Przechowuje jeden certyfikat do użycia, gdy żaden certyfikat nie jest określona przez usługę.</span><span class="sxs-lookup"><span data-stu-id="cfca5-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfca5-160">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfca5-160">Example</span></span>  
 <span data-ttu-id="cfca5-161">W poniższym przykładzie certyfikat do użycia dla punktów końcowych, którego identyfikator URI, który rozpoczyna się od http://www.contoso.com i certyfikat do użycia dla wszystkich innych punktów końcowych, które nie wykonuj negocjowanie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="cfca5-161">The following example specifies a certificate to use for endpoints whose URI begins with http://www.contoso.com and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cfca5-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfca5-162">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>  
 [<span data-ttu-id="cfca5-163">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="cfca5-163">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="cfca5-164">\<Uwierzytelnianie ></span><span class="sxs-lookup"><span data-stu-id="cfca5-164">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [<span data-ttu-id="cfca5-165">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="cfca5-165">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="cfca5-166">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="cfca5-166">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
