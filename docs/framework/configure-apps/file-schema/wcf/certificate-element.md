---
title: '&lt;certificate&gt;, element'
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: 02444e66326bec10150ba52541aedd02ec7bb784
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltcertificategt-element"></a><span data-ttu-id="d84ae-102">&lt;certificate&gt;, element</span><span class="sxs-lookup"><span data-stu-id="d84ae-102">&lt;certificate&gt; Element</span></span>
<span data-ttu-id="d84ae-103">Określa certyfikat X.509 do użycia podczas podpisywania i szyfrowania wiadomości dla klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="d84ae-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="d84ae-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d84ae-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d84ae-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="d84ae-105">\<behaviors></span></span>  
<span data-ttu-id="d84ae-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d84ae-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="d84ae-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d84ae-107">\<behavior></span></span>  
<span data-ttu-id="d84ae-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="d84ae-108">\<clientCredentials></span></span>  
<span data-ttu-id="d84ae-109">\<peer ></span><span class="sxs-lookup"><span data-stu-id="d84ae-109">\<peer></span></span>  
<span data-ttu-id="d84ae-110">\<certyfikat ></span><span class="sxs-lookup"><span data-stu-id="d84ae-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d84ae-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="d84ae-111">Syntax</span></span>  
  
```xml  
<certificate findValue="String"   
  
storeLocation="LocalMachine/CurrentUser"  
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d84ae-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d84ae-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d84ae-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d84ae-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d84ae-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d84ae-114">Attributes</span></span>  
  
|<span data-ttu-id="d84ae-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d84ae-115">Attribute</span></span>|<span data-ttu-id="d84ae-116">Opis</span><span class="sxs-lookup"><span data-stu-id="d84ae-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="d84ae-117">Ciąg, który zawiera wartość do wyszukania w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="d84ae-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="d84ae-118">Typ zawartych w atrybucie muszą spełniać wymagania określonego `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="d84ae-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="d84ae-119">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="d84ae-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="d84ae-120">Określa lokalizację magazynu certyfikatu X.509, którego klient używa do walidacji certyfikatu węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="d84ae-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="d84ae-121">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="d84ae-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d84ae-122">-LocalMachine: Magazyn certyfikatów przypisany do komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="d84ae-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="d84ae-123">-CurrentUser: Magazyn certyfikatów przypisany do bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d84ae-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="d84ae-124">Wartość domyślna jest komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="d84ae-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="d84ae-125">Określa nazwę magazynu certyfikatu X.509 do otwarcia.</span><span class="sxs-lookup"><span data-stu-id="d84ae-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="d84ae-126">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="d84ae-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d84ae-127">-Książka adresowa: Magazyn certyfikatów dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="d84ae-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="d84ae-128">-AuthRoot: Certyfikatu sklepu dla firm urzędy certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="d84ae-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="d84ae-129">-Urzędów certyfikacji: Magazyn certyfikatów dla pośrednie urzędy certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="d84ae-129">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="d84ae-130">— Niedozwolone: Magazyn certyfikatów odwołanych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d84ae-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="d84ae-131">-Moje: Magazynu certyfikatów osobistych.</span><span class="sxs-lookup"><span data-stu-id="d84ae-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="d84ae-132">-Katalog główny: Magazyn certyfikatów dla zaufanych głównych urzędów certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="d84ae-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="d84ae-133">-TrustedPeople: Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.</span><span class="sxs-lookup"><span data-stu-id="d84ae-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="d84ae-134">-TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.</span><span class="sxs-lookup"><span data-stu-id="d84ae-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="d84ae-135">Wartość domyślna to Moje.</span><span class="sxs-lookup"><span data-stu-id="d84ae-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="d84ae-136">Określa typ wyszukiwania X.509 w celu wykonania.</span><span class="sxs-lookup"><span data-stu-id="d84ae-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="d84ae-137">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="d84ae-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d84ae-138">-Postać FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="d84ae-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="d84ae-139">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="d84ae-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="d84ae-140">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="d84ae-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="d84ae-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="d84ae-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="d84ae-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="d84ae-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="d84ae-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="d84ae-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="d84ae-144">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="d84ae-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="d84ae-145">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="d84ae-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="d84ae-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="d84ae-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="d84ae-147">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="d84ae-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="d84ae-148">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="d84ae-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="d84ae-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="d84ae-149">-   FindByExtension</span></span><br /><span data-ttu-id="d84ae-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="d84ae-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="d84ae-151">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="d84ae-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="d84ae-152">Typ zawarty w `findValue` atrybutu muszą spełniać wymagania dotyczące określonego `X509FindType`.</span><span class="sxs-lookup"><span data-stu-id="d84ae-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="d84ae-153">Wartość domyślna to FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="d84ae-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d84ae-154">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d84ae-154">Child Elements</span></span>  
 <span data-ttu-id="d84ae-155">Brak.</span><span class="sxs-lookup"><span data-stu-id="d84ae-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d84ae-156">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d84ae-156">Parent Elements</span></span>  
  
|<span data-ttu-id="d84ae-157">Element</span><span class="sxs-lookup"><span data-stu-id="d84ae-157">Element</span></span>|<span data-ttu-id="d84ae-158">Opis</span><span class="sxs-lookup"><span data-stu-id="d84ae-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d84ae-159">\<peer ></span><span class="sxs-lookup"><span data-stu-id="d84ae-159">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="d84ae-160">Określa poświadczenia używane podczas uwierzytelniania klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="d84ae-160">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d84ae-161">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d84ae-161">Remarks</span></span>  
 <span data-ttu-id="d84ae-162">Ten element konfiguracji zawiera wystąpienie X509Certificate2, używany podczas uwierzytelniania sąsiadów w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="d84ae-162">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="d84ae-163">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="d84ae-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d84ae-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="d84ae-164">Example</span></span>  
 <span data-ttu-id="d84ae-165">Poniższy kod określa sposób znaleźć certyfikat używany w scenariuszu peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="d84ae-165">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
```  
  
## <a name="see-also"></a><span data-ttu-id="d84ae-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d84ae-166">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 [<span data-ttu-id="d84ae-167">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="d84ae-167">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="d84ae-168">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="d84ae-168">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="d84ae-169">Uwierzytelnianie wiadomości kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="d84ae-169">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="d84ae-170">Niestandardowe uwierzytelnianie kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="d84ae-170">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="d84ae-171">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="d84ae-171">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
