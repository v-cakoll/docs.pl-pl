---
title: <defaultCertificate> Element
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: cce236bf80fa00f01a3b5f4680d975f83fde0c16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400425"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="16924-102">\<defaultCertificate> Element</span><span class="sxs-lookup"><span data-stu-id="16924-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="16924-103">Określa certyfikat X. 509, który ma być używany, gdy usługa lub STS nie zapewnia go za pośrednictwem protokołu negocjacji.</span><span class="sxs-lookup"><span data-stu-id="16924-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="16924-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16924-104">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16924-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="16924-105">Attributes and Elements</span></span>  
 <span data-ttu-id="16924-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="16924-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16924-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="16924-107">Attributes</span></span>  
  
|<span data-ttu-id="16924-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="16924-108">Attribute</span></span>|<span data-ttu-id="16924-109">Opis</span><span class="sxs-lookup"><span data-stu-id="16924-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16924-110">findValue</span><span class="sxs-lookup"><span data-stu-id="16924-110">findValue</span></span>|<span data-ttu-id="16924-111">Ciąg.</span><span class="sxs-lookup"><span data-stu-id="16924-111">String.</span></span> <span data-ttu-id="16924-112">Wartość do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="16924-112">The value to search for.</span></span>|  
|<span data-ttu-id="16924-113">x509FindType</span><span class="sxs-lookup"><span data-stu-id="16924-113">x509FindType</span></span>|<span data-ttu-id="16924-114">Licznik.</span><span class="sxs-lookup"><span data-stu-id="16924-114">Enumeration.</span></span> <span data-ttu-id="16924-115">Jedno z pól certyfikatów do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="16924-115">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="16924-116">storeLocation</span><span class="sxs-lookup"><span data-stu-id="16924-116">storeLocation</span></span>|<span data-ttu-id="16924-117">Licznik.</span><span class="sxs-lookup"><span data-stu-id="16924-117">Enumeration.</span></span> <span data-ttu-id="16924-118">Jedna z dwóch lokalizacji magazynu systemowego do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="16924-118">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="16924-119">storeName</span><span class="sxs-lookup"><span data-stu-id="16924-119">storeName</span></span>|<span data-ttu-id="16924-120">Licznik.</span><span class="sxs-lookup"><span data-stu-id="16924-120">Enumeration.</span></span> <span data-ttu-id="16924-121">Jeden z magazynów systemu do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="16924-121">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="16924-122">findValue — atrybut</span><span class="sxs-lookup"><span data-stu-id="16924-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="16924-123">Wartość</span><span class="sxs-lookup"><span data-stu-id="16924-123">Value</span></span>|<span data-ttu-id="16924-124">Opis</span><span class="sxs-lookup"><span data-stu-id="16924-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="16924-125">String</span><span class="sxs-lookup"><span data-stu-id="16924-125">String</span></span>|<span data-ttu-id="16924-126">Wartość jest zależna od pola (określonego przez atrybut X509FindType), który jest przeszukiwany.</span><span class="sxs-lookup"><span data-stu-id="16924-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="16924-127">Na przykład, jeśli szukasz odcisku palca, wartość musi być ciągiem liczb szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="16924-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="16924-128">x509FindType — atrybut</span><span class="sxs-lookup"><span data-stu-id="16924-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="16924-129">Wartość</span><span class="sxs-lookup"><span data-stu-id="16924-129">Value</span></span>|<span data-ttu-id="16924-130">Opis</span><span class="sxs-lookup"><span data-stu-id="16924-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="16924-131">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="16924-131">Enumeration</span></span>|<span data-ttu-id="16924-132">Dostępne są następujące wartości: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="16924-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="16924-133">storeLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="16924-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="16924-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="16924-134">Value</span></span>|<span data-ttu-id="16924-135">Opis</span><span class="sxs-lookup"><span data-stu-id="16924-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="16924-136">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="16924-136">Enumeration</span></span>|<span data-ttu-id="16924-137">CurrentUser lub LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="16924-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="16924-138">storeName — atrybut</span><span class="sxs-lookup"><span data-stu-id="16924-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="16924-139">Wartość</span><span class="sxs-lookup"><span data-stu-id="16924-139">Value</span></span>|<span data-ttu-id="16924-140">Opis</span><span class="sxs-lookup"><span data-stu-id="16924-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="16924-141">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="16924-141">Enumeration</span></span>|<span data-ttu-id="16924-142">Dostępne są następujące wartości: AddressBook, AuthRoot, urząd certyfikacji, niedozwolone, my, root, TrustedPeople i TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="16924-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16924-143">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="16924-143">Child Elements</span></span>  
 <span data-ttu-id="16924-144">Brak.</span><span class="sxs-lookup"><span data-stu-id="16924-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16924-145">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="16924-145">Parent Elements</span></span>  
  
|<span data-ttu-id="16924-146">Element</span><span class="sxs-lookup"><span data-stu-id="16924-146">Element</span></span>|<span data-ttu-id="16924-147">Opis</span><span class="sxs-lookup"><span data-stu-id="16924-147">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="16924-148">Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="16924-148">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16924-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16924-149">Remarks</span></span>  
 <span data-ttu-id="16924-150">W przypadku powiązań korzystających z zabezpieczeń komunikatów opartych na certyfikatach certyfikat określony przez ten element konfiguracji jest używany do szyfrowania komunikatów do usługi i powinien być używany przez usługę do podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="16924-150">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="16924-151">Przechowuje on pojedynczy certyfikat, który będzie używany w przypadku braku certyfikatu określonego przez usługę.</span><span class="sxs-lookup"><span data-stu-id="16924-151">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16924-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="16924-152">Example</span></span>  
 <span data-ttu-id="16924-153">W poniższym przykładzie określono certyfikat używany dla punktów końcowych, których identyfikator URI zaczyna się od `http://www.contoso.com` i certyfikat używany dla wszystkich innych punktów końcowych, które nie wykonują negocjacji certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="16924-153">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16924-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16924-154">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="16924-155">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="16924-155">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="16924-156">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="16924-156">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="16924-157">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="16924-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
