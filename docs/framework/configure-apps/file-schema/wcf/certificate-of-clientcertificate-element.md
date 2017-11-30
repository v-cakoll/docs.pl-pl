---
title: '&lt;certificate&gt; w &lt;clientCertificate&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bef4067d0fa74aa90841040ca5e6b3ea22f1e499
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltcertificategt-of-ltclientcertificategt-element"></a><span data-ttu-id="1c252-102">&lt;certificate&gt; w &lt;clientCertificate&gt;, element</span><span class="sxs-lookup"><span data-stu-id="1c252-102">&lt;certificate&gt; of &lt;clientCertificate&gt; Element</span></span>
<span data-ttu-id="1c252-103">Określa X.509. certyfikat używany do podpisywania i szyfrowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1c252-103">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
 <span data-ttu-id="1c252-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1c252-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1c252-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="1c252-105">\<behaviors></span></span>  
<span data-ttu-id="1c252-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1c252-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1c252-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="1c252-107">\<behavior></span></span>  
<span data-ttu-id="1c252-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="1c252-108">\<serviceCredentials></span></span>  
<span data-ttu-id="1c252-109">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="1c252-109">\<clientCertificate></span></span>  
<span data-ttu-id="1c252-110">\<certyfikat ></span><span class="sxs-lookup"><span data-stu-id="1c252-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c252-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c252-111">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c252-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1c252-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1c252-113">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1c252-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c252-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1c252-114">Attributes</span></span>  
  
|<span data-ttu-id="1c252-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1c252-115">Attribute</span></span>|<span data-ttu-id="1c252-116">Opis</span><span class="sxs-lookup"><span data-stu-id="1c252-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="1c252-117">Ciąg, który zawiera wartość do wyszukania w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="1c252-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="1c252-118">Typ zawartych w atrybucie muszą spełniać wymagania X509FindType określony.</span><span class="sxs-lookup"><span data-stu-id="1c252-118">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="1c252-119">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="1c252-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="1c252-120">Określa lokalizację magazynu certyfikatu X.509, którego klient używa do walidacji certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="1c252-120">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="1c252-121">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="1c252-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1c252-122">-LocalMachine: Magazyn certyfikatów przypisany do komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="1c252-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="1c252-123">-CurrentUser: Magazyn certyfikatów przypisany do bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1c252-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="1c252-124">Wartość domyślna jest komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="1c252-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="1c252-125">Określa nazwę magazynu certyfikatu X.509 do otwarcia.</span><span class="sxs-lookup"><span data-stu-id="1c252-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="1c252-126">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="1c252-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1c252-127">-Książka adresowa: Magazyn certyfikatów dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="1c252-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="1c252-128">-AuthRoot: Certyfikatu sklepu dla firm urzędy certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="1c252-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="1c252-129">-Urząd certyfikacji: Magazyn certyfikatów dla pośrednie urzędy certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="1c252-129">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="1c252-130">— Niedozwolone: Magazyn certyfikatów odwołanych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="1c252-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="1c252-131">-Moje: Magazynu certyfikatów osobistych.</span><span class="sxs-lookup"><span data-stu-id="1c252-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="1c252-132">-Katalog główny: Magazyn certyfikatów dla zaufanych głównych urzędów certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="1c252-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="1c252-133">-TrustedPeople: Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.</span><span class="sxs-lookup"><span data-stu-id="1c252-133">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="1c252-134">-TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.</span><span class="sxs-lookup"><span data-stu-id="1c252-134">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="1c252-135">Wartość domyślna to Moje.</span><span class="sxs-lookup"><span data-stu-id="1c252-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="1c252-136">Określa typ wyszukiwania X.509 w celu wykonania.</span><span class="sxs-lookup"><span data-stu-id="1c252-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="1c252-137">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="1c252-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1c252-138">-Postać FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="1c252-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="1c252-139">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="1c252-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="1c252-140">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="1c252-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="1c252-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="1c252-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="1c252-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="1c252-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="1c252-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="1c252-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="1c252-144">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="1c252-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="1c252-145">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="1c252-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="1c252-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="1c252-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="1c252-147">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="1c252-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="1c252-148">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="1c252-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="1c252-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="1c252-149">-   FindByExtension</span></span><br /><span data-ttu-id="1c252-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="1c252-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="1c252-151">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="1c252-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="1c252-152">Typ zawarty w `findValue` atrybutu muszą spełniać wymagania X509FindType określony.</span><span class="sxs-lookup"><span data-stu-id="1c252-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="1c252-153">Wartość domyślna to FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="1c252-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c252-154">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1c252-154">Child Elements</span></span>  
 <span data-ttu-id="1c252-155">Brak.</span><span class="sxs-lookup"><span data-stu-id="1c252-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c252-156">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1c252-156">Parent Elements</span></span>  
  
|<span data-ttu-id="1c252-157">Element</span><span class="sxs-lookup"><span data-stu-id="1c252-157">Element</span></span>|<span data-ttu-id="1c252-158">Opis</span><span class="sxs-lookup"><span data-stu-id="1c252-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c252-159">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="1c252-159">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="1c252-160">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c252-160">Remarks</span></span>  
 <span data-ttu-id="1c252-161">`<certificate>` Element jest używany, gdy usługa musi mieć certyfikat klienta z wyprzedzeniem do bezpiecznego komunikowania się z klientem.</span><span class="sxs-lookup"><span data-stu-id="1c252-161">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="1c252-162">Dzieje się tak podczas używania wzorca komunikację dupleksową.</span><span class="sxs-lookup"><span data-stu-id="1c252-162">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="1c252-163">We wzorcu bardziej typowego żądania/odpowiedzi klienta obejmuje jego certyfikat w żądaniu, usługa używa do szyfrowania i podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="1c252-163">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="1c252-164">We wzorcu komunikację dupleksową jednak usługa ma żądania z klienta i dlatego wymaga certyfikatu klienta z wyprzedzeniem, aby zabezpieczyć wiadomość do klienta.</span><span class="sxs-lookup"><span data-stu-id="1c252-164">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="1c252-165">W związku z tym należy uzyskać certyfikat klienta w negocjacji poza pasmem oraz określić certyfikat przy użyciu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="1c252-165">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="1c252-166">Aby uzyskać więcej informacji na temat usługi dwukierunkowe, zobacz [porady: tworzenie kontraktu dwukierunkowego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="1c252-166">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c252-167">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c252-167">Example</span></span>  
 <span data-ttu-id="1c252-168">Poniższy kod określa, jak znaleźć odpowiedniego certyfikatu X.509 i niestandardowego sprawdzania poprawności typu w `<authentication>` elementu.</span><span class="sxs-lookup"><span data-stu-id="1c252-168">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c252-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c252-169">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>  
 [<span data-ttu-id="1c252-170">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="1c252-170">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="1c252-171">Porady: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów</span><span class="sxs-lookup"><span data-stu-id="1c252-171">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="1c252-172">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="1c252-172">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
