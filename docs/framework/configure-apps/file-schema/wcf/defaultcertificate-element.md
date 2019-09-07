---
title: <defaultCertificate>, element
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: cce236bf80fa00f01a3b5f4680d975f83fde0c16
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400425"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="6448b-102">\<defaultCertificate, element ></span><span class="sxs-lookup"><span data-stu-id="6448b-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="6448b-103">Określa certyfikat X. 509, który ma być używany, gdy usługa lub STS nie zapewnia go za pośrednictwem protokołu negocjacji.</span><span class="sxs-lookup"><span data-stu-id="6448b-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
<span data-ttu-id="6448b-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6448b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6448b-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6448b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6448b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6448b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="6448b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6448b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="6448b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6448b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="6448b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Obiekt clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="6448b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="6448b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceCertificate**](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="6448b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="6448b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultCertificate >**</span><span class="sxs-lookup"><span data-stu-id="6448b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6448b-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="6448b-112">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6448b-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6448b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6448b-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6448b-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6448b-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6448b-115">Attributes</span></span>  
  
|<span data-ttu-id="6448b-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6448b-116">Attribute</span></span>|<span data-ttu-id="6448b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="6448b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6448b-118">findValue</span><span class="sxs-lookup"><span data-stu-id="6448b-118">findValue</span></span>|<span data-ttu-id="6448b-119">Parametry.</span><span class="sxs-lookup"><span data-stu-id="6448b-119">String.</span></span> <span data-ttu-id="6448b-120">Wartość do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="6448b-120">The value to search for.</span></span>|  
|<span data-ttu-id="6448b-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="6448b-121">x509FindType</span></span>|<span data-ttu-id="6448b-122">Licznik.</span><span class="sxs-lookup"><span data-stu-id="6448b-122">Enumeration.</span></span> <span data-ttu-id="6448b-123">Jedno z pól certyfikatów do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="6448b-123">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="6448b-124">storeLocation</span><span class="sxs-lookup"><span data-stu-id="6448b-124">storeLocation</span></span>|<span data-ttu-id="6448b-125">Licznik.</span><span class="sxs-lookup"><span data-stu-id="6448b-125">Enumeration.</span></span> <span data-ttu-id="6448b-126">Jedna z dwóch lokalizacji magazynu systemowego do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="6448b-126">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="6448b-127">storeName</span><span class="sxs-lookup"><span data-stu-id="6448b-127">storeName</span></span>|<span data-ttu-id="6448b-128">Licznik.</span><span class="sxs-lookup"><span data-stu-id="6448b-128">Enumeration.</span></span> <span data-ttu-id="6448b-129">Jeden z magazynów systemu do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="6448b-129">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="6448b-130">findValue — atrybut</span><span class="sxs-lookup"><span data-stu-id="6448b-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="6448b-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="6448b-131">Value</span></span>|<span data-ttu-id="6448b-132">Opis</span><span class="sxs-lookup"><span data-stu-id="6448b-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6448b-133">String</span><span class="sxs-lookup"><span data-stu-id="6448b-133">String</span></span>|<span data-ttu-id="6448b-134">Wartość jest zależna od pola (określonego przez atrybut X509FindType), który jest przeszukiwany.</span><span class="sxs-lookup"><span data-stu-id="6448b-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="6448b-135">Na przykład, jeśli szukasz odcisku palca, wartość musi być ciągiem liczb szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="6448b-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="6448b-136">x509FindType — atrybut</span><span class="sxs-lookup"><span data-stu-id="6448b-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="6448b-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="6448b-137">Value</span></span>|<span data-ttu-id="6448b-138">Opis</span><span class="sxs-lookup"><span data-stu-id="6448b-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6448b-139">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6448b-139">Enumeration</span></span>|<span data-ttu-id="6448b-140">Dostępne są następujące wartości: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="6448b-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="6448b-141">storeLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="6448b-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="6448b-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="6448b-142">Value</span></span>|<span data-ttu-id="6448b-143">Opis</span><span class="sxs-lookup"><span data-stu-id="6448b-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6448b-144">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6448b-144">Enumeration</span></span>|<span data-ttu-id="6448b-145">CurrentUser lub LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="6448b-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="6448b-146">storeName — atrybut</span><span class="sxs-lookup"><span data-stu-id="6448b-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="6448b-147">Wartość</span><span class="sxs-lookup"><span data-stu-id="6448b-147">Value</span></span>|<span data-ttu-id="6448b-148">Opis</span><span class="sxs-lookup"><span data-stu-id="6448b-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6448b-149">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6448b-149">Enumeration</span></span>|<span data-ttu-id="6448b-150">Dostępne są następujące wartości: AddressBook, AuthRoot, urząd certyfikacji, niedozwolone, my, root, TrustedPeople i TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="6448b-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6448b-151">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6448b-151">Child Elements</span></span>  
 <span data-ttu-id="6448b-152">Brak.</span><span class="sxs-lookup"><span data-stu-id="6448b-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6448b-153">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6448b-153">Parent Elements</span></span>  
  
|<span data-ttu-id="6448b-154">Element</span><span class="sxs-lookup"><span data-stu-id="6448b-154">Element</span></span>|<span data-ttu-id="6448b-155">Opis</span><span class="sxs-lookup"><span data-stu-id="6448b-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6448b-156">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="6448b-156">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="6448b-157">Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="6448b-157">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6448b-158">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6448b-158">Remarks</span></span>  
 <span data-ttu-id="6448b-159">W przypadku powiązań korzystających z zabezpieczeń komunikatów opartych na certyfikatach certyfikat określony przez ten element konfiguracji jest używany do szyfrowania komunikatów do usługi i powinien być używany przez usługę do podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="6448b-159">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="6448b-160">Przechowuje on pojedynczy certyfikat, który będzie używany w przypadku braku certyfikatu określonego przez usługę.</span><span class="sxs-lookup"><span data-stu-id="6448b-160">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6448b-161">Przykład</span><span class="sxs-lookup"><span data-stu-id="6448b-161">Example</span></span>  
 <span data-ttu-id="6448b-162">W poniższym przykładzie określono certyfikat używany dla punktów końcowych, których identyfikator URI `http://www.contoso.com` zaczyna się od i certyfikat używany dla wszystkich innych punktów końcowych, które nie wykonują negocjacji certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="6448b-162">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="6448b-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6448b-163">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="6448b-164">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="6448b-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="6448b-165">\<> uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="6448b-165">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="6448b-166">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="6448b-166">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="6448b-167">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="6448b-167">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
