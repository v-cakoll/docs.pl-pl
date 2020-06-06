---
title: <certificate> Element
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: e28e7d16073a56f3b6126439644bfff86c9af18b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400554"
---
# <a name="certificate-element"></a><span data-ttu-id="2a6ba-102">\<certificate> Element</span><span class="sxs-lookup"><span data-stu-id="2a6ba-102">\<certificate> Element</span></span>
<span data-ttu-id="2a6ba-103">Określa certyfikat X. 509 używany do podpisywania i szyfrowania komunikatów dla klientów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="2a6ba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a6ba-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a6ba-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2a6ba-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2a6ba-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a6ba-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2a6ba-107">Attributes</span></span>  
  
|<span data-ttu-id="2a6ba-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2a6ba-108">Attribute</span></span>|<span data-ttu-id="2a6ba-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2a6ba-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="2a6ba-110">Ciąg, który zawiera wartość do wyszukania w magazynie certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="2a6ba-111">Typ zawarty w atrybucie musi spełniać wymagania określone `x509FindType` .</span><span class="sxs-lookup"><span data-stu-id="2a6ba-111">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="2a6ba-112">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="2a6ba-113">Określa lokalizację magazynu certyfikatów X. 509, którego klient używa do weryfikacji certyfikatu elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-113">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="2a6ba-114">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="2a6ba-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2a6ba-115">-LocalMachine: Magazyn certyfikatów przypisany do komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="2a6ba-116">-CurrentUser: Magazyn certyfikatów przypisany do bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="2a6ba-117">Wartość domyślna to LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="2a6ba-118">Określa nazwę magazynu certyfikatu X. 509 do otwarcia.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="2a6ba-119">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="2a6ba-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2a6ba-120">-AddressBook: Magazyn certyfikatów dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="2a6ba-121">-AuthRoot: Magazyn certyfikatów dla urzędów certyfikacji innych firm.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="2a6ba-122">-Urząd certyfikacji: Magazyn certyfikatów dla pośrednich urzędów certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="2a6ba-122">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="2a6ba-123">-Niedozwolone: Magazyn certyfikatów dla odwołanych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="2a6ba-124">-My: Magazyn certyfikatów dla certyfikatów osobistych.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="2a6ba-125">-Root: Magazyn certyfikatów dla zaufanych głównych urzędów certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="2a6ba-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="2a6ba-126">-TrustedPeople: Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-126">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="2a6ba-127">-TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-127">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="2a6ba-128">Wartość domyślna to Moje.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="2a6ba-129">Określa typ wyszukiwania X. 509, który ma zostać wykonany.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="2a6ba-130">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="2a6ba-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2a6ba-131">- FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="2a6ba-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="2a6ba-132">- FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="2a6ba-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="2a6ba-133">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="2a6ba-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="2a6ba-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="2a6ba-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="2a6ba-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="2a6ba-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="2a6ba-136">- FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="2a6ba-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="2a6ba-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="2a6ba-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="2a6ba-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="2a6ba-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="2a6ba-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="2a6ba-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="2a6ba-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="2a6ba-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="2a6ba-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="2a6ba-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="2a6ba-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="2a6ba-142">-   FindByExtension</span></span><br /><span data-ttu-id="2a6ba-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="2a6ba-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="2a6ba-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="2a6ba-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="2a6ba-145">Typ zawarty w `findValue` atrybucie musi spełniać wymagania określone `X509FindType` .</span><span class="sxs-lookup"><span data-stu-id="2a6ba-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="2a6ba-146">Wartość domyślna to FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a6ba-147">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2a6ba-147">Child Elements</span></span>  
 <span data-ttu-id="2a6ba-148">Brak.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a6ba-149">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2a6ba-149">Parent Elements</span></span>  
  
|<span data-ttu-id="2a6ba-150">Element</span><span class="sxs-lookup"><span data-stu-id="2a6ba-150">Element</span></span>|<span data-ttu-id="2a6ba-151">Opis</span><span class="sxs-lookup"><span data-stu-id="2a6ba-151">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="2a6ba-152">Określa poświadczenia używane podczas uwierzytelniania klientów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-152">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a6ba-153">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a6ba-153">Remarks</span></span>  
 <span data-ttu-id="2a6ba-154">Ten element konfiguracji zawiera wystąpienie X509Certificate2 używane podczas uwierzytelniania sąsiadów w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-154">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="2a6ba-155">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci peer-to-](../../../wcf/feature-details/peer-to-peer-networking.md)peer.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-155">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a6ba-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a6ba-156">Example</span></span>  
 <span data-ttu-id="2a6ba-157">Poniższy kod określa, jak znaleźć certyfikat używany w scenariuszu równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="2a6ba-157">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2a6ba-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a6ba-158">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="2a6ba-159">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="2a6ba-159">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="2a6ba-160">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="2a6ba-160">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="2a6ba-161">[Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2a6ba-161">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="2a6ba-162">[Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2a6ba-162">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="2a6ba-163">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="2a6ba-163">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
