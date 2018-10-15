---
title: '&lt;authentication&gt; w &lt;serviceCertificate&gt;, element'
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 811d54b49d8cd4fddbf196dbb524c5d303805c4f
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316457"
---
# <a name="ltauthenticationgt-of-ltservicecertificategt-element"></a><span data-ttu-id="1b9c9-102">&lt;authentication&gt; w &lt;serviceCertificate&gt;, element</span><span class="sxs-lookup"><span data-stu-id="1b9c9-102">&lt;authentication&gt; of &lt;serviceCertificate&gt; Element</span></span>
<span data-ttu-id="1b9c9-103">Określa ustawienia używane przez serwer proxy klienta do uwierzytelniania certyfikatów usługi, które są uzyskiwane przy użyciu negocjacji SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
 <span data-ttu-id="1b9c9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1b9c9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1b9c9-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="1b9c9-105">\<behaviors></span></span>  
<span data-ttu-id="1b9c9-106">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="1b9c9-106">endpointBehaviors section</span></span>  
<span data-ttu-id="1b9c9-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="1b9c9-107">\<behavior></span></span>  
<span data-ttu-id="1b9c9-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="1b9c9-108">\<clientCredentials></span></span>  
<span data-ttu-id="1b9c9-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="1b9c9-109">\<serviceCertificate></span></span>  
<span data-ttu-id="1b9c9-110">\<Uwierzytelnianie ></span><span class="sxs-lookup"><span data-stu-id="1b9c9-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b9c9-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b9c9-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String" certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"   
trustedStoreLocation="LocalMachine/CurrentUser" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b9c9-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1b9c9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1b9c9-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1b9c9-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b9c9-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1b9c9-114">Attributes</span></span>  
  
|<span data-ttu-id="1b9c9-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1b9c9-115">Attribute</span></span>|<span data-ttu-id="1b9c9-116">Opis</span><span class="sxs-lookup"><span data-stu-id="1b9c9-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b9c9-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="1b9c9-117">customCertificateValidatorType</span></span>|<span data-ttu-id="1b9c9-118">ciąg.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-118">String.</span></span> <span data-ttu-id="1b9c9-119">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-119">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="1b9c9-120">tryb certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="1b9c9-120">certificateValidationMode</span></span>|<span data-ttu-id="1b9c9-121">Określa jeden z trzech trybów używanych do walidacji poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="1b9c9-122">Jeśli ustawiono `Custom`, a następnie customCertificateValidator musi również zostać dostarczony.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-122">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="1b9c9-123">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-123">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="1b9c9-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="1b9c9-124">revocationMode</span></span>|<span data-ttu-id="1b9c9-125">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="1b9c9-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="1b9c9-126">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-126">The default is `Online`.</span></span>|  
|<span data-ttu-id="1b9c9-127">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="1b9c9-127">trustedStoreLocation</span></span>|<span data-ttu-id="1b9c9-128">Jedną z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-128">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="1b9c9-129">Ta wartość jest używana, gdy certyfikat usługi jest negocjowane do klienta.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-129">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="1b9c9-130">Sprawdzanie poprawności jest wykonywane względem **zaufane osoby** są przechowywane w lokalizacji określonego magazynu.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-130">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="1b9c9-131">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-131">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="1b9c9-132">customCertificateValidator atrybutu</span><span class="sxs-lookup"><span data-stu-id="1b9c9-132">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="1b9c9-133">Wartość</span><span class="sxs-lookup"><span data-stu-id="1b9c9-133">Value</span></span>|<span data-ttu-id="1b9c9-134">Opis</span><span class="sxs-lookup"><span data-stu-id="1b9c9-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1b9c9-135">String</span><span class="sxs-lookup"><span data-stu-id="1b9c9-135">String</span></span>|<span data-ttu-id="1b9c9-136">Określa nazwę typu i zestawu i inne dane, używana do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-136">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="1b9c9-137">tryb certificateValidationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="1b9c9-137">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="1b9c9-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="1b9c9-138">Value</span></span>|<span data-ttu-id="1b9c9-139">Opis</span><span class="sxs-lookup"><span data-stu-id="1b9c9-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1b9c9-140">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1b9c9-140">Enumeration</span></span>|<span data-ttu-id="1b9c9-141">Jedną z następujących wartości: Brak zaufania elementów równorzędnych, ChainTrust, PeerOrChainTrust, niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-141">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="1b9c9-142">Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="1b9c9-142">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="1b9c9-143">revocationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="1b9c9-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="1b9c9-144">Wartość</span><span class="sxs-lookup"><span data-stu-id="1b9c9-144">Value</span></span>|<span data-ttu-id="1b9c9-145">Opis</span><span class="sxs-lookup"><span data-stu-id="1b9c9-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1b9c9-146">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1b9c9-146">Enumeration</span></span>|<span data-ttu-id="1b9c9-147">Jedną z następujących wartości: NoCheck, Online, w trybie Offline.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-147">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="1b9c9-148">Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="1b9c9-148">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="1b9c9-149">trustedStoreLocation atrybutu</span><span class="sxs-lookup"><span data-stu-id="1b9c9-149">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="1b9c9-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="1b9c9-150">Value</span></span>|<span data-ttu-id="1b9c9-151">Opis</span><span class="sxs-lookup"><span data-stu-id="1b9c9-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1b9c9-152">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1b9c9-152">Enumeration</span></span>|<span data-ttu-id="1b9c9-153">Jedną z następujących wartości: LocalMachine lub CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-153">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="1b9c9-154">Wartość domyślna to CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-154">The default is CurrentUser.</span></span> <span data-ttu-id="1b9c9-155">Jeśli aplikacja kliencka jest uruchomiona w ramach konta systemowego, następnie certyfikat jest zazwyczaj w obszarze LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-155">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="1b9c9-156">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, następnie certyfikat znajduje się zwykle w CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-156">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b9c9-157">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1b9c9-157">Child Elements</span></span>  
 <span data-ttu-id="1b9c9-158">Brak.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1b9c9-159">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1b9c9-159">Parent Elements</span></span>  
  
|<span data-ttu-id="1b9c9-160">Element</span><span class="sxs-lookup"><span data-stu-id="1b9c9-160">Element</span></span>|<span data-ttu-id="1b9c9-161">Opis</span><span class="sxs-lookup"><span data-stu-id="1b9c9-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b9c9-162">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="1b9c9-162">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="1b9c9-163">Określa certyfikat używany podczas uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-163">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b9c9-164">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b9c9-164">Remarks</span></span>  
 <span data-ttu-id="1b9c9-165">`certificateValidationMode` Atrybut ten element konfiguracji określa poziom zaufania, używany do uwierzytelniania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-165">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="1b9c9-166">Domyślnie ustawiono poziom `ChainTrust`, która określa, że każdy certyfikat musi zostać znaleziony w hierarchii końcówce zaufanego urzędu certyfikacji w górnej części łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-166">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="1b9c9-167">Jest to najbezpieczniejsza opcja Tryb.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-167">This is the most secure mode.</span></span> <span data-ttu-id="1b9c9-168">Można również ustawić wartość, `PeerOrChainTrust`, która określa, że własnym wystawionych certyfikatów (relacja zaufania elementów równorzędnych) są akceptowane oraz certyfikaty, które znajdują się w zaufanym łańcuchem.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-168">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="1b9c9-169">Ta wartość jest używana podczas opracowywania i debugowania klientów i usług, ponieważ własnym wystawionych certyfikatów nie należy zakupić od zaufanego urzędu.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-169">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="1b9c9-170">Podczas wdrażania klienta, użyj `ChainTrust` jest wartość.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-170">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="1b9c9-171">Można również ustawić wartość, `Custom` lub `None`.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-171">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="1b9c9-172">Aby użyć `Custom` wartości, należy także ustawić `customCertificateValidator` atrybutu do zestawu i typ używany do weryfikacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-172">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="1b9c9-173">Aby utworzyć własny niestandardowy moduł sprawdzania poprawności, musi dziedziczyć z klasy abstrakcyjnej X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-173">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="1b9c9-174">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi korzystającej z modułu weryfikacji certyfikatów niestandardowe](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="1b9c9-174">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="1b9c9-175">`revocationMode` Atrybut określa, jak certyfikaty są sprawdzane pod kątem odwołań.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-175">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="1b9c9-176">Wartość domyślna to `online` co oznacza, że certyfikaty będą automatycznie sprawdzane dla odwołania.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-176">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="1b9c9-177">Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="1b9c9-177">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b9c9-178">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b9c9-178">Example</span></span>  
 <span data-ttu-id="1b9c9-179">Poniższy przykład wykonuje dwa zadania.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-179">The following example does two tasks.</span></span> <span data-ttu-id="1b9c9-180">Najpierw Określa certyfikat usługi dla klienta do użycia podczas komunikowania się z punktami końcowymi, których nazwa domeny jest `www.contoso.com` za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-180">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="1b9c9-181">Po drugie określa wartości odwołania tryb i magazynem lokalizację używane podczas uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="1b9c9-181">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1b9c9-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b9c9-182">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>  
 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>  
 [<span data-ttu-id="1b9c9-183">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="1b9c9-183">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="1b9c9-184">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="1b9c9-184">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="1b9c9-185">Instrukcje: tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów</span><span class="sxs-lookup"><span data-stu-id="1b9c9-185">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="1b9c9-186">\<Uwierzytelnianie ></span><span class="sxs-lookup"><span data-stu-id="1b9c9-186">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [<span data-ttu-id="1b9c9-187">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="1b9c9-187">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="1b9c9-188">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="1b9c9-188">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
