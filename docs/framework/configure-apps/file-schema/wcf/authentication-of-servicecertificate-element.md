---
title: <authentication><serviceCertificate> elementu
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: d770ba1f9a0a18c927b3a4bf6d4141286e3a380c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919982"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="3052c-102">\<> \<uwierzytelniania elementu > serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="3052c-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="3052c-103">Określa ustawienia używane przez serwer proxy klienta do uwierzytelniania certyfikatów usługi, które są uzyskiwane przy użyciu negocjacji SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="3052c-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
 <span data-ttu-id="3052c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3052c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3052c-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="3052c-105">\<behaviors></span></span>  
<span data-ttu-id="3052c-106">Sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="3052c-106">endpointBehaviors section</span></span>  
<span data-ttu-id="3052c-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="3052c-107">\<behavior></span></span>  
<span data-ttu-id="3052c-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="3052c-108">\<clientCredentials></span></span>  
<span data-ttu-id="3052c-109">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="3052c-109">\<serviceCertificate></span></span>  
<span data-ttu-id="3052c-110">\<> uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="3052c-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3052c-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="3052c-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3052c-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3052c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3052c-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3052c-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3052c-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3052c-114">Attributes</span></span>  
  
|<span data-ttu-id="3052c-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3052c-115">Attribute</span></span>|<span data-ttu-id="3052c-116">Opis</span><span class="sxs-lookup"><span data-stu-id="3052c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3052c-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="3052c-117">customCertificateValidatorType</span></span>|<span data-ttu-id="3052c-118">Parametry.</span><span class="sxs-lookup"><span data-stu-id="3052c-118">String.</span></span> <span data-ttu-id="3052c-119">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="3052c-119">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="3052c-120">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="3052c-120">certificateValidationMode</span></span>|<span data-ttu-id="3052c-121">Określa jeden z trzech trybów używanych do walidacji poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="3052c-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="3052c-122">Jeśli jest ustawiona `Custom`na, należy również podać CustomCertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="3052c-122">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="3052c-123">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="3052c-123">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="3052c-124">odwołaniemode</span><span class="sxs-lookup"><span data-stu-id="3052c-124">revocationMode</span></span>|<span data-ttu-id="3052c-125">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="3052c-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="3052c-126">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="3052c-126">The default is `Online`.</span></span>|  
|<span data-ttu-id="3052c-127">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="3052c-127">trustedStoreLocation</span></span>|<span data-ttu-id="3052c-128">Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="3052c-128">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="3052c-129">Ta wartość jest używana podczas negocjowania certyfikatu usługi z klientem.</span><span class="sxs-lookup"><span data-stu-id="3052c-129">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="3052c-130">Sprawdzanie poprawności jest wykonywane względem magazynu **osób zaufanych** w określonej lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="3052c-130">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="3052c-131">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="3052c-131">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="3052c-132">customCertificateValidator — atrybut</span><span class="sxs-lookup"><span data-stu-id="3052c-132">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="3052c-133">Wartość</span><span class="sxs-lookup"><span data-stu-id="3052c-133">Value</span></span>|<span data-ttu-id="3052c-134">Opis</span><span class="sxs-lookup"><span data-stu-id="3052c-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3052c-135">String</span><span class="sxs-lookup"><span data-stu-id="3052c-135">String</span></span>|<span data-ttu-id="3052c-136">Określa nazwę typu i zestaw oraz inne dane używane do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="3052c-136">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="3052c-137">certificateValidationMode — atrybut</span><span class="sxs-lookup"><span data-stu-id="3052c-137">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="3052c-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="3052c-138">Value</span></span>|<span data-ttu-id="3052c-139">Opis</span><span class="sxs-lookup"><span data-stu-id="3052c-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3052c-140">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3052c-140">Enumeration</span></span>|<span data-ttu-id="3052c-141">Jedna z następujących wartości: None, zaufania elementów równorzędnych, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="3052c-141">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="3052c-142">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="3052c-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="3052c-143">Atrybut odwołania</span><span class="sxs-lookup"><span data-stu-id="3052c-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="3052c-144">Wartość</span><span class="sxs-lookup"><span data-stu-id="3052c-144">Value</span></span>|<span data-ttu-id="3052c-145">Opis</span><span class="sxs-lookup"><span data-stu-id="3052c-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3052c-146">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3052c-146">Enumeration</span></span>|<span data-ttu-id="3052c-147">Jedna z następujących wartości: NOCHECK, online, offline.</span><span class="sxs-lookup"><span data-stu-id="3052c-147">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="3052c-148">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="3052c-148">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="3052c-149">trustedStoreLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="3052c-149">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="3052c-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="3052c-150">Value</span></span>|<span data-ttu-id="3052c-151">Opis</span><span class="sxs-lookup"><span data-stu-id="3052c-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3052c-152">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3052c-152">Enumeration</span></span>|<span data-ttu-id="3052c-153">Jedna z następujących wartości: LocalMachine lub CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="3052c-153">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="3052c-154">Wartość domyślna to CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="3052c-154">The default is CurrentUser.</span></span> <span data-ttu-id="3052c-155">Jeśli aplikacja kliencka jest uruchomiona na koncie systemowym, certyfikat jest zwykle w obszarze LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="3052c-155">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="3052c-156">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, certyfikat zazwyczaj znajduje się w CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="3052c-156">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3052c-157">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3052c-157">Child Elements</span></span>  
 <span data-ttu-id="3052c-158">Brak.</span><span class="sxs-lookup"><span data-stu-id="3052c-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3052c-159">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3052c-159">Parent Elements</span></span>  
  
|<span data-ttu-id="3052c-160">Element</span><span class="sxs-lookup"><span data-stu-id="3052c-160">Element</span></span>|<span data-ttu-id="3052c-161">Opis</span><span class="sxs-lookup"><span data-stu-id="3052c-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3052c-162">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="3052c-162">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="3052c-163">Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="3052c-163">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3052c-164">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3052c-164">Remarks</span></span>  
 <span data-ttu-id="3052c-165">`certificateValidationMode` Atrybut tego elementu konfiguracji określa poziom zaufania używany do uwierzytelniania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="3052c-165">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="3052c-166">Domyślnie poziom jest ustawiony na `ChainTrust`, który określa, że każdy certyfikat musi znajdować się w hierarchii certyfikatów kończących się zaufanym urzędem certyfikacji w górnej części łańcucha.</span><span class="sxs-lookup"><span data-stu-id="3052c-166">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="3052c-167">Jest to najbardziej bezpieczny tryb.</span><span class="sxs-lookup"><span data-stu-id="3052c-167">This is the most secure mode.</span></span> <span data-ttu-id="3052c-168">Można również ustawić wartość na `PeerOrChainTrust`, która określa, że certyfikaty samodzielne (relacja równorzędna) są akceptowane, a także certyfikaty, które znajdują się w zaufanym łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="3052c-168">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="3052c-169">Ta wartość jest używana podczas tworzenia i debugowania klientów i usług, ponieważ certyfikaty wystawione przez siebie nie muszą zostać zakupione z zaufanego urzędu.</span><span class="sxs-lookup"><span data-stu-id="3052c-169">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="3052c-170">Podczas wdrażania klienta należy zamiast tego użyć `ChainTrust` wartości.</span><span class="sxs-lookup"><span data-stu-id="3052c-170">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="3052c-171">Możesz również ustawić wartość na `Custom` lub. `None`</span><span class="sxs-lookup"><span data-stu-id="3052c-171">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="3052c-172">Aby użyć `Custom` wartości, należy również `customCertificateValidator` ustawić atrybut na zestaw i typ używany do walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="3052c-172">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="3052c-173">Aby utworzyć własny niestandardowy moduł sprawdzania poprawności, należy dziedziczyć z klasy abstrakcyjnej X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="3052c-173">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="3052c-174">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="3052c-174">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="3052c-175">Ten `revocationMode` atrybut określa, jak certyfikaty są sprawdzane pod kątem odwołania.</span><span class="sxs-lookup"><span data-stu-id="3052c-175">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="3052c-176">Wartość domyślna `online` wskazuje, że certyfikaty będą sprawdzane automatycznie w celu odwołania.</span><span class="sxs-lookup"><span data-stu-id="3052c-176">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="3052c-177">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="3052c-177">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3052c-178">Przykład</span><span class="sxs-lookup"><span data-stu-id="3052c-178">Example</span></span>  
 <span data-ttu-id="3052c-179">Poniższy przykład wykonuje dwa zadania.</span><span class="sxs-lookup"><span data-stu-id="3052c-179">The following example does two tasks.</span></span> <span data-ttu-id="3052c-180">Najpierw określa certyfikat usługi, który ma być używany przez klienta podczas komunikowania się z punktami końcowymi, których nazwa domeny znajduje się `www.contoso.com` za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="3052c-180">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="3052c-181">Po drugie określa tryb odwołania i lokalizację magazynu używane podczas uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3052c-181">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3052c-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3052c-182">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="3052c-183">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="3052c-183">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3052c-184">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="3052c-184">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3052c-185">Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów</span><span class="sxs-lookup"><span data-stu-id="3052c-185">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="3052c-186">\<> uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="3052c-186">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="3052c-187">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="3052c-187">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="3052c-188">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="3052c-188">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
