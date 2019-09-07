---
title: <certificate>, element
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: e28e7d16073a56f3b6126439644bfff86c9af18b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400554"
---
# <a name="certificate-element"></a><span data-ttu-id="9398a-102">\<certyfikat > element</span><span class="sxs-lookup"><span data-stu-id="9398a-102">\<certificate> Element</span></span>
<span data-ttu-id="9398a-103">Określa certyfikat X. 509 używany do podpisywania i szyfrowania komunikatów dla klientów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="9398a-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
<span data-ttu-id="9398a-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9398a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9398a-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9398a-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9398a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9398a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="9398a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9398a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="9398a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9398a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="9398a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Obiekt clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="9398a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="9398a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> elementów równorzędnych**](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="9398a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="9398a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> certyfikatów**</span><span class="sxs-lookup"><span data-stu-id="9398a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9398a-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="9398a-112">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9398a-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9398a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9398a-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9398a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9398a-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9398a-115">Attributes</span></span>  
  
|<span data-ttu-id="9398a-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9398a-116">Attribute</span></span>|<span data-ttu-id="9398a-117">Opis</span><span class="sxs-lookup"><span data-stu-id="9398a-117">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="9398a-118">Ciąg, który zawiera wartość do wyszukania w magazynie certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="9398a-118">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="9398a-119">Typ zawarty w atrybucie musi spełniać wymagania określone `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="9398a-119">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="9398a-120">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="9398a-120">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="9398a-121">Określa lokalizację magazynu certyfikatów X. 509, którego klient używa do weryfikacji certyfikatu elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="9398a-121">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="9398a-122">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="9398a-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9398a-123">-LocalMachine: Magazyn certyfikatów przypisany do komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="9398a-123">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="9398a-124">-CurrentUser: Magazyn certyfikatów przypisany do bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9398a-124">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="9398a-125">Wartość domyślna to LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="9398a-125">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="9398a-126">Określa nazwę magazynu certyfikatu X. 509 do otwarcia.</span><span class="sxs-lookup"><span data-stu-id="9398a-126">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="9398a-127">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="9398a-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9398a-128">- AddressBook: Magazyn certyfikatów dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="9398a-128">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="9398a-129">AuthRoot Magazyn certyfikatów dla urzędów certyfikacji innych firm (CAs).</span><span class="sxs-lookup"><span data-stu-id="9398a-129">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="9398a-130">Urząd certyfikacji Magazyn certyfikatów dla pośrednich urzędów certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="9398a-130">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="9398a-131">Niedozwolone Magazyn certyfikatów dla odwołanych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="9398a-131">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="9398a-132">Komputer Magazyn certyfikatów dla certyfikatów osobistych.</span><span class="sxs-lookup"><span data-stu-id="9398a-132">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="9398a-133">Pierwiastek Magazyn certyfikatów dla zaufanych głównych urzędów certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="9398a-133">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="9398a-134">TrustedPeople Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.</span><span class="sxs-lookup"><span data-stu-id="9398a-134">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="9398a-135">- TrustedPublisher: Magazyn certyfikatów dla wydawców bezpośrednio zaufanych.</span><span class="sxs-lookup"><span data-stu-id="9398a-135">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="9398a-136">Wartość domyślna to my.</span><span class="sxs-lookup"><span data-stu-id="9398a-136">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="9398a-137">Określa typ wyszukiwania X. 509, który ma zostać wykonany.</span><span class="sxs-lookup"><span data-stu-id="9398a-137">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="9398a-138">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="9398a-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9398a-139">- FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="9398a-139">-   FindByThumbPrint</span></span><br /><span data-ttu-id="9398a-140">- FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="9398a-140">-   FindBySubjectName</span></span><br /><span data-ttu-id="9398a-141">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="9398a-141">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="9398a-142">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="9398a-142">-   FindByIssuerName</span></span><br /><span data-ttu-id="9398a-143">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="9398a-143">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="9398a-144">- FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="9398a-144">-   FindBySerialNumber</span></span><br /><span data-ttu-id="9398a-145">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="9398a-145">-   FindByTimeValid</span></span><br /><span data-ttu-id="9398a-146">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="9398a-146">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="9398a-147">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="9398a-147">-   FindByTemplateName</span></span><br /><span data-ttu-id="9398a-148">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="9398a-148">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="9398a-149">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="9398a-149">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="9398a-150">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="9398a-150">-   FindByExtension</span></span><br /><span data-ttu-id="9398a-151">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="9398a-151">-   FindByKeyUsage</span></span><br /><span data-ttu-id="9398a-152">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="9398a-152">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="9398a-153">Typ zawarty w `findValue` atrybucie musi spełniać wymagania określone `X509FindType`.</span><span class="sxs-lookup"><span data-stu-id="9398a-153">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="9398a-154">Wartość domyślna to FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="9398a-154">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9398a-155">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9398a-155">Child Elements</span></span>  
 <span data-ttu-id="9398a-156">Brak.</span><span class="sxs-lookup"><span data-stu-id="9398a-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9398a-157">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9398a-157">Parent Elements</span></span>  
  
|<span data-ttu-id="9398a-158">Element</span><span class="sxs-lookup"><span data-stu-id="9398a-158">Element</span></span>|<span data-ttu-id="9398a-159">Opis</span><span class="sxs-lookup"><span data-stu-id="9398a-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9398a-160">\<> elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="9398a-160">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="9398a-161">Określa poświadczenia używane podczas uwierzytelniania klientów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="9398a-161">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9398a-162">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9398a-162">Remarks</span></span>  
 <span data-ttu-id="9398a-163">Ten element konfiguracji zawiera wystąpienie X509Certificate2 używane podczas uwierzytelniania sąsiadów w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="9398a-163">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="9398a-164">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci peer-to-](../../../wcf/feature-details/peer-to-peer-networking.md)peer.</span><span class="sxs-lookup"><span data-stu-id="9398a-164">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9398a-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="9398a-165">Example</span></span>  
 <span data-ttu-id="9398a-166">Poniższy kod określa, jak znaleźć certyfikat używany w scenariuszu równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="9398a-166">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="9398a-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9398a-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="9398a-168">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="9398a-168">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="9398a-169">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="9398a-169">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="9398a-170">[Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9398a-170">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="9398a-171">[Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9398a-171">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="9398a-172">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="9398a-172">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
