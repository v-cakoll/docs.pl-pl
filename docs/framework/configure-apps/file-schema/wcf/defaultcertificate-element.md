---
title: <defaultCertificate>, element
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 93410e815a156f91db1962f05fb1aa6baca7f955
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919264"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="898a7-102">\<defaultCertificate, element ></span><span class="sxs-lookup"><span data-stu-id="898a7-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="898a7-103">Określa certyfikat X. 509, który ma być używany, gdy usługa lub STS nie zapewnia go za pośrednictwem protokołu negocjacji.</span><span class="sxs-lookup"><span data-stu-id="898a7-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="898a7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="898a7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="898a7-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="898a7-105">\<behaviors></span></span>  
<span data-ttu-id="898a7-106">Sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="898a7-106">endpointBehaviors section</span></span>  
<span data-ttu-id="898a7-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="898a7-107">\<behavior></span></span>  
<span data-ttu-id="898a7-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="898a7-108">\<clientCredentials></span></span>  
<span data-ttu-id="898a7-109">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="898a7-109">\<serviceCertificate></span></span>  
<span data-ttu-id="898a7-110">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="898a7-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="898a7-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="898a7-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="898a7-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="898a7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="898a7-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="898a7-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="898a7-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="898a7-114">Attributes</span></span>  
  
|<span data-ttu-id="898a7-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="898a7-115">Attribute</span></span>|<span data-ttu-id="898a7-116">Opis</span><span class="sxs-lookup"><span data-stu-id="898a7-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="898a7-117">findValue</span><span class="sxs-lookup"><span data-stu-id="898a7-117">findValue</span></span>|<span data-ttu-id="898a7-118">Parametry.</span><span class="sxs-lookup"><span data-stu-id="898a7-118">String.</span></span> <span data-ttu-id="898a7-119">Wartość do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="898a7-119">The value to search for.</span></span>|  
|<span data-ttu-id="898a7-120">x509FindType</span><span class="sxs-lookup"><span data-stu-id="898a7-120">x509FindType</span></span>|<span data-ttu-id="898a7-121">Licznik.</span><span class="sxs-lookup"><span data-stu-id="898a7-121">Enumeration.</span></span> <span data-ttu-id="898a7-122">Jedno z pól certyfikatów do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="898a7-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="898a7-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="898a7-123">storeLocation</span></span>|<span data-ttu-id="898a7-124">Licznik.</span><span class="sxs-lookup"><span data-stu-id="898a7-124">Enumeration.</span></span> <span data-ttu-id="898a7-125">Jedna z dwóch lokalizacji magazynu systemowego do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="898a7-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="898a7-126">storeName</span><span class="sxs-lookup"><span data-stu-id="898a7-126">storeName</span></span>|<span data-ttu-id="898a7-127">Licznik.</span><span class="sxs-lookup"><span data-stu-id="898a7-127">Enumeration.</span></span> <span data-ttu-id="898a7-128">Jeden z magazynów systemu do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="898a7-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="898a7-129">findValue — atrybut</span><span class="sxs-lookup"><span data-stu-id="898a7-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="898a7-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="898a7-130">Value</span></span>|<span data-ttu-id="898a7-131">Opis</span><span class="sxs-lookup"><span data-stu-id="898a7-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="898a7-132">String</span><span class="sxs-lookup"><span data-stu-id="898a7-132">String</span></span>|<span data-ttu-id="898a7-133">Wartość jest zależna od pola (określonego przez atrybut X509FindType), który jest przeszukiwany.</span><span class="sxs-lookup"><span data-stu-id="898a7-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="898a7-134">Na przykład, jeśli szukasz odcisku palca, wartość musi być ciągiem liczb szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="898a7-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="898a7-135">x509FindType — atrybut</span><span class="sxs-lookup"><span data-stu-id="898a7-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="898a7-136">Wartość</span><span class="sxs-lookup"><span data-stu-id="898a7-136">Value</span></span>|<span data-ttu-id="898a7-137">Opis</span><span class="sxs-lookup"><span data-stu-id="898a7-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="898a7-138">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="898a7-138">Enumeration</span></span>|<span data-ttu-id="898a7-139">Dostępne są następujące wartości: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="898a7-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="898a7-140">storeLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="898a7-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="898a7-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="898a7-141">Value</span></span>|<span data-ttu-id="898a7-142">Opis</span><span class="sxs-lookup"><span data-stu-id="898a7-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="898a7-143">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="898a7-143">Enumeration</span></span>|<span data-ttu-id="898a7-144">CurrentUser lub LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="898a7-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="898a7-145">storeName — atrybut</span><span class="sxs-lookup"><span data-stu-id="898a7-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="898a7-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="898a7-146">Value</span></span>|<span data-ttu-id="898a7-147">Opis</span><span class="sxs-lookup"><span data-stu-id="898a7-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="898a7-148">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="898a7-148">Enumeration</span></span>|<span data-ttu-id="898a7-149">Dostępne są następujące wartości: AddressBook, AuthRoot, urząd certyfikacji, niedozwolone, my, root, TrustedPeople i TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="898a7-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="898a7-150">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="898a7-150">Child Elements</span></span>  
 <span data-ttu-id="898a7-151">Brak.</span><span class="sxs-lookup"><span data-stu-id="898a7-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="898a7-152">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="898a7-152">Parent Elements</span></span>  
  
|<span data-ttu-id="898a7-153">Element</span><span class="sxs-lookup"><span data-stu-id="898a7-153">Element</span></span>|<span data-ttu-id="898a7-154">Opis</span><span class="sxs-lookup"><span data-stu-id="898a7-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="898a7-155">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="898a7-155">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="898a7-156">Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="898a7-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="898a7-157">Uwagi</span><span class="sxs-lookup"><span data-stu-id="898a7-157">Remarks</span></span>  
 <span data-ttu-id="898a7-158">W przypadku powiązań korzystających z zabezpieczeń komunikatów opartych na certyfikatach certyfikat określony przez ten element konfiguracji jest używany do szyfrowania komunikatów do usługi i powinien być używany przez usługę do podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="898a7-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="898a7-159">Przechowuje on pojedynczy certyfikat, który będzie używany w przypadku braku certyfikatu określonego przez usługę.</span><span class="sxs-lookup"><span data-stu-id="898a7-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="898a7-160">Przykład</span><span class="sxs-lookup"><span data-stu-id="898a7-160">Example</span></span>  
 <span data-ttu-id="898a7-161">W poniższym przykładzie określono certyfikat używany dla punktów końcowych, których identyfikator URI `http://www.contoso.com` zaczyna się od i certyfikat używany dla wszystkich innych punktów końcowych, które nie wykonują negocjacji certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="898a7-161">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="898a7-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="898a7-162">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="898a7-163">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="898a7-163">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="898a7-164">\<> uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="898a7-164">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="898a7-165">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="898a7-165">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="898a7-166">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="898a7-166">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
