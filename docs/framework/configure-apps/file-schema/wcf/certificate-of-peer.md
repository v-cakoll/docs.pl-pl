---
title: '&lt;certificate&gt; w &lt;peer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f46ebab92cbca616b06db5be6dc155a44558aa7e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificategt-of-ltpeergt"></a><span data-ttu-id="8cc5a-102">&lt;certificate&gt; w &lt;peer&gt;</span><span class="sxs-lookup"><span data-stu-id="8cc5a-102">&lt;certificate&gt; of &lt;peer&gt;</span></span>
<span data-ttu-id="8cc5a-103">Określa certyfikat używany przez element równorzędny.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-103">Specifies a certificate used by a peer.</span></span>  
  
 <span data-ttu-id="8cc5a-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8cc5a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8cc5a-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="8cc5a-105">\<behaviors></span></span>  
<span data-ttu-id="8cc5a-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8cc5a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="8cc5a-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="8cc5a-107">\<behavior></span></span>  
<span data-ttu-id="8cc5a-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="8cc5a-108">\<serviceCredentials></span></span>  
<span data-ttu-id="8cc5a-109">\<peer ></span><span class="sxs-lookup"><span data-stu-id="8cc5a-109">\<peer></span></span>  
<span data-ttu-id="8cc5a-110">\<certyfikat ></span><span class="sxs-lookup"><span data-stu-id="8cc5a-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cc5a-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="8cc5a-111">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cc5a-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8cc5a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8cc5a-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cc5a-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8cc5a-114">Attributes</span></span>  
  
|<span data-ttu-id="8cc5a-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8cc5a-115">Attribute</span></span>|<span data-ttu-id="8cc5a-116">Opis</span><span class="sxs-lookup"><span data-stu-id="8cc5a-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="8cc5a-117">Ciąg, który zawiera wartość do wyszukania w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="8cc5a-118">Typ zawartych w atrybucie muszą spełniać wymagania określonego `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="8cc5a-119">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="8cc5a-120">Określa lokalizację magazynu certyfikatu X.509, którego klient używa do walidacji certyfikatu węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="8cc5a-121">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="8cc5a-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8cc5a-122">-LocalMachine: Magazyn certyfikatów przypisany do komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="8cc5a-123">-CurrentUser: Magazyn certyfikatów przypisany do bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="8cc5a-124">Wartość domyślna jest komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="8cc5a-125">Określa nazwę magazynu certyfikatu X.509 do otwarcia.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="8cc5a-126">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="8cc5a-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8cc5a-127">-Książka adresowa: Magazyn certyfikatów dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="8cc5a-128">-AuthRoot: Certyfikatu sklepu dla firm urzędy certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="8cc5a-128">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="8cc5a-129">-Urzędów certyfikacji: Magazyn certyfikatów dla certyfikatu pośrednich urzędów certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-129">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="8cc5a-130">— Niedozwolone: Magazyn certyfikatów odwołanych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="8cc5a-131">-Moje: Magazynu certyfikatów osobistych.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="8cc5a-132">-Katalog główny: Magazyn certyfikatów dla zaufane główne urzędy certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="8cc5a-132">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="8cc5a-133">-TrustedPeople: Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="8cc5a-134">-TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="8cc5a-135">Wartość domyślna to Moje.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="8cc5a-136">Określa typ wyszukiwania X.509 w celu wykonania.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="8cc5a-137">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="8cc5a-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8cc5a-138">-Postać FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="8cc5a-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="8cc5a-139">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="8cc5a-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="8cc5a-140">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="8cc5a-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="8cc5a-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="8cc5a-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="8cc5a-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="8cc5a-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="8cc5a-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="8cc5a-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="8cc5a-144">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="8cc5a-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="8cc5a-145">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="8cc5a-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="8cc5a-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="8cc5a-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="8cc5a-147">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="8cc5a-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="8cc5a-148">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="8cc5a-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="8cc5a-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="8cc5a-149">-   FindByExtension</span></span><br /><span data-ttu-id="8cc5a-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="8cc5a-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="8cc5a-151">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="8cc5a-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="8cc5a-152">Typ zawarty w `findValue` atrybutu muszą spełniać wymagania dotyczące określonego `X509FindType`.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="8cc5a-153">Wartość domyślna to FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8cc5a-154">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8cc5a-154">Child Elements</span></span>  
 <span data-ttu-id="8cc5a-155">Brak.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8cc5a-156">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8cc5a-156">Parent Elements</span></span>  
  
|<span data-ttu-id="8cc5a-157">Element</span><span class="sxs-lookup"><span data-stu-id="8cc5a-157">Element</span></span>|<span data-ttu-id="8cc5a-158">Opis</span><span class="sxs-lookup"><span data-stu-id="8cc5a-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cc5a-159">\<peer ></span><span class="sxs-lookup"><span data-stu-id="8cc5a-159">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="8cc5a-160">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-160">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cc5a-161">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8cc5a-161">Remarks</span></span>  
 <span data-ttu-id="8cc5a-162">Ten element konfiguracji zawiera `X509Certificate2` wystąpienie używane podczas uwierzytelniania sąsiadów w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="8cc5a-162">This configuration element contains an `X509Certificate2` instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="8cc5a-163">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="8cc5a-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc5a-164">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8cc5a-164">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="8cc5a-165">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="8cc5a-165">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="8cc5a-166">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="8cc5a-166">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="8cc5a-167">Uwierzytelnianie wiadomości kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="8cc5a-167">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="8cc5a-168">Niestandardowe uwierzytelnianie kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="8cc5a-168">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="8cc5a-169">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="8cc5a-169">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="8cc5a-170">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="8cc5a-170">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
