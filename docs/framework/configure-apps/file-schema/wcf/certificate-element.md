---
title: <certificate> Element
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: eea8130911ca3780a6e4e753c17877e58c50b139
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164271"
---
# <a name="certificate-element"></a><span data-ttu-id="90725-102">\<certyfikat > Element</span><span class="sxs-lookup"><span data-stu-id="90725-102">\<certificate> Element</span></span>
<span data-ttu-id="90725-103">Określa certyfikat X.509 do podpisywania i szyfrowania wiadomości dla klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="90725-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="90725-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="90725-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="90725-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="90725-105">\<behaviors></span></span>  
<span data-ttu-id="90725-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="90725-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="90725-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="90725-107">\<behavior></span></span>  
<span data-ttu-id="90725-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="90725-108">\<clientCredentials></span></span>  
<span data-ttu-id="90725-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="90725-109">\<peer></span></span>  
<span data-ttu-id="90725-110">\<certificate></span><span class="sxs-lookup"><span data-stu-id="90725-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90725-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="90725-111">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90725-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="90725-112">Attributes and Elements</span></span>  
 <span data-ttu-id="90725-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="90725-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90725-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="90725-114">Attributes</span></span>  
  
|<span data-ttu-id="90725-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="90725-115">Attribute</span></span>|<span data-ttu-id="90725-116">Opis</span><span class="sxs-lookup"><span data-stu-id="90725-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="90725-117">Ciąg, który zawiera wartość do wyszukania w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="90725-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="90725-118">Typ zawartych w atrybucie musi spełniać wymagania określonego `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="90725-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="90725-119">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="90725-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="90725-120">Określa lokalizację magazynu certyfikatu X.509, którego klient używa do walidacji certyfikatu węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="90725-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="90725-121">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="90725-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="90725-122">-LocalMachine: Magazyn certyfikatów przypisany do komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="90725-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="90725-123">-CurrentUser: Magazyn certyfikatów przypisany do bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="90725-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="90725-124">Wartość domyślna to LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="90725-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="90725-125">Określa nazwę magazynu certyfikatu X.509 do otwarcia.</span><span class="sxs-lookup"><span data-stu-id="90725-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="90725-126">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="90725-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="90725-127">— Książka adresowa: Magazyn certyfikatów dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="90725-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="90725-128">-AuthRoot: Magazyn certyfikatów dla urzędów certyfikacji innych firm (CAs).</span><span class="sxs-lookup"><span data-stu-id="90725-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="90725-129">-Urząd certyfikacji: Magazyn certyfikatów dla pośrednie urzędy certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="90725-129">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="90725-130">-Niedozwolone: Magazyn certyfikatów dla odwołanych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="90725-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="90725-131">-Mój: Magazyn certyfikatów dla certyfikatów osobistych.</span><span class="sxs-lookup"><span data-stu-id="90725-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="90725-132">-Katalog główny: Magazyn certyfikatów zaufanych głównych urzędów certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="90725-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="90725-133">-TrustedPeople: Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.</span><span class="sxs-lookup"><span data-stu-id="90725-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="90725-134">-TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.</span><span class="sxs-lookup"><span data-stu-id="90725-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="90725-135">Wartość domyślna to Mój.</span><span class="sxs-lookup"><span data-stu-id="90725-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="90725-136">Określa typ wyszukania X.509 w celu wykonania.</span><span class="sxs-lookup"><span data-stu-id="90725-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="90725-137">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="90725-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="90725-138">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="90725-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="90725-139">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="90725-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="90725-140">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="90725-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="90725-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="90725-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="90725-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="90725-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="90725-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="90725-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="90725-144">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="90725-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="90725-145">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="90725-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="90725-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="90725-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="90725-147">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="90725-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="90725-148">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="90725-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="90725-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="90725-149">-   FindByExtension</span></span><br /><span data-ttu-id="90725-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="90725-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="90725-151">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="90725-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="90725-152">Typ zawarty w `findValue` atrybut musi spełniać wymagania określonego `X509FindType`.</span><span class="sxs-lookup"><span data-stu-id="90725-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="90725-153">Wartość domyślna to FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="90725-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90725-154">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="90725-154">Child Elements</span></span>  
 <span data-ttu-id="90725-155">Brak.</span><span class="sxs-lookup"><span data-stu-id="90725-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90725-156">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="90725-156">Parent Elements</span></span>  
  
|<span data-ttu-id="90725-157">Element</span><span class="sxs-lookup"><span data-stu-id="90725-157">Element</span></span>|<span data-ttu-id="90725-158">Opis</span><span class="sxs-lookup"><span data-stu-id="90725-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90725-159">\<peer></span><span class="sxs-lookup"><span data-stu-id="90725-159">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="90725-160">Określa poświadczenia używane podczas uwierzytelniania klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="90725-160">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90725-161">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90725-161">Remarks</span></span>  
 <span data-ttu-id="90725-162">Ten element konfiguracji zawiera wystąpienie X509Certificate2 używany podczas uwierzytelniania sąsiadów w siatki elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="90725-162">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="90725-163">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="90725-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="90725-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="90725-164">Example</span></span>  
 <span data-ttu-id="90725-165">Poniższy kod określa, jak znaleźć certyfikat używany w scenariuszu peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="90725-165">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="90725-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90725-166">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="90725-167">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="90725-167">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="90725-168">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="90725-168">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="90725-169">Uwierzytelnianie wiadomości z kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="90725-169">Peer Channel Message Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [<span data-ttu-id="90725-170">Kanał elementu równorzędnego uwierzytelniania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="90725-170">Peer Channel Custom Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [<span data-ttu-id="90725-171">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="90725-171">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
