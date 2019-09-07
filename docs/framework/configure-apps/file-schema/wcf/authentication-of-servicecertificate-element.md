---
title: <authentication><serviceCertificate> elementu
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 29170f032469b4d55b50f57ca06ce403a5aeaf2c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398228"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="ea2a0-102">\<> \<uwierzytelniania elementu > serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="ea2a0-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="ea2a0-103">Określa ustawienia używane przez serwer proxy klienta do uwierzytelniania certyfikatów usługi, które są uzyskiwane przy użyciu negocjacji SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
<span data-ttu-id="ea2a0-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ea2a0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ea2a0-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ea2a0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ea2a0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ea2a0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ea2a0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ea2a0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="ea2a0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ea2a0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="ea2a0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Obiekt clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="ea2a0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="ea2a0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceCertificate**](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="ea2a0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="ea2a0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> uwierzytelniania**</span><span class="sxs-lookup"><span data-stu-id="ea2a0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea2a0-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea2a0-112">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea2a0-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ea2a0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ea2a0-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea2a0-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ea2a0-115">Attributes</span></span>  
  
|<span data-ttu-id="ea2a0-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ea2a0-116">Attribute</span></span>|<span data-ttu-id="ea2a0-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ea2a0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea2a0-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="ea2a0-118">customCertificateValidatorType</span></span>|<span data-ttu-id="ea2a0-119">Parametry.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-119">String.</span></span> <span data-ttu-id="ea2a0-120">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-120">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="ea2a0-121">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="ea2a0-121">certificateValidationMode</span></span>|<span data-ttu-id="ea2a0-122">Określa jeden z trzech trybów używanych do walidacji poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="ea2a0-123">Jeśli jest ustawiona `Custom`na, należy również podać CustomCertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-123">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="ea2a0-124">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-124">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="ea2a0-125">odwołaniemode</span><span class="sxs-lookup"><span data-stu-id="ea2a0-125">revocationMode</span></span>|<span data-ttu-id="ea2a0-126">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="ea2a0-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="ea2a0-127">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-127">The default is `Online`.</span></span>|  
|<span data-ttu-id="ea2a0-128">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="ea2a0-128">trustedStoreLocation</span></span>|<span data-ttu-id="ea2a0-129">Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="ea2a0-130">Ta wartość jest używana podczas negocjowania certyfikatu usługi z klientem.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="ea2a0-131">Sprawdzanie poprawności jest wykonywane względem magazynu **osób zaufanych** w określonej lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="ea2a0-132">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="ea2a0-133">customCertificateValidator — atrybut</span><span class="sxs-lookup"><span data-stu-id="ea2a0-133">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="ea2a0-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="ea2a0-134">Value</span></span>|<span data-ttu-id="ea2a0-135">Opis</span><span class="sxs-lookup"><span data-stu-id="ea2a0-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ea2a0-136">String</span><span class="sxs-lookup"><span data-stu-id="ea2a0-136">String</span></span>|<span data-ttu-id="ea2a0-137">Określa nazwę typu i zestaw oraz inne dane używane do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-137">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="ea2a0-138">certificateValidationMode — atrybut</span><span class="sxs-lookup"><span data-stu-id="ea2a0-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="ea2a0-139">Wartość</span><span class="sxs-lookup"><span data-stu-id="ea2a0-139">Value</span></span>|<span data-ttu-id="ea2a0-140">Opis</span><span class="sxs-lookup"><span data-stu-id="ea2a0-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ea2a0-141">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ea2a0-141">Enumeration</span></span>|<span data-ttu-id="ea2a0-142">Jedna z następujących wartości: None, zaufania elementów równorzędnych, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-142">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="ea2a0-143">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="ea2a0-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="ea2a0-144">Atrybut odwołania</span><span class="sxs-lookup"><span data-stu-id="ea2a0-144">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="ea2a0-145">Wartość</span><span class="sxs-lookup"><span data-stu-id="ea2a0-145">Value</span></span>|<span data-ttu-id="ea2a0-146">Opis</span><span class="sxs-lookup"><span data-stu-id="ea2a0-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ea2a0-147">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ea2a0-147">Enumeration</span></span>|<span data-ttu-id="ea2a0-148">Jedna z następujących wartości: NOCHECK, online, offline.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-148">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="ea2a0-149">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="ea2a0-149">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="ea2a0-150">trustedStoreLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="ea2a0-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="ea2a0-151">Wartość</span><span class="sxs-lookup"><span data-stu-id="ea2a0-151">Value</span></span>|<span data-ttu-id="ea2a0-152">Opis</span><span class="sxs-lookup"><span data-stu-id="ea2a0-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ea2a0-153">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ea2a0-153">Enumeration</span></span>|<span data-ttu-id="ea2a0-154">Jedna z następujących wartości: LocalMachine lub CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-154">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="ea2a0-155">Wartość domyślna to CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-155">The default is CurrentUser.</span></span> <span data-ttu-id="ea2a0-156">Jeśli aplikacja kliencka jest uruchomiona na koncie systemowym, certyfikat jest zwykle w obszarze LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-156">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="ea2a0-157">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, certyfikat zazwyczaj znajduje się w CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-157">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea2a0-158">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ea2a0-158">Child Elements</span></span>  
 <span data-ttu-id="ea2a0-159">Brak.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea2a0-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ea2a0-160">Parent Elements</span></span>  
  
|<span data-ttu-id="ea2a0-161">Element</span><span class="sxs-lookup"><span data-stu-id="ea2a0-161">Element</span></span>|<span data-ttu-id="ea2a0-162">Opis</span><span class="sxs-lookup"><span data-stu-id="ea2a0-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea2a0-163">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="ea2a0-163">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="ea2a0-164">Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-164">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea2a0-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea2a0-165">Remarks</span></span>  
 <span data-ttu-id="ea2a0-166">`certificateValidationMode` Atrybut tego elementu konfiguracji określa poziom zaufania używany do uwierzytelniania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-166">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="ea2a0-167">Domyślnie poziom jest ustawiony na `ChainTrust`, który określa, że każdy certyfikat musi znajdować się w hierarchii certyfikatów kończących się zaufanym urzędem certyfikacji w górnej części łańcucha.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-167">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="ea2a0-168">Jest to najbardziej bezpieczny tryb.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-168">This is the most secure mode.</span></span> <span data-ttu-id="ea2a0-169">Można również ustawić wartość na `PeerOrChainTrust`, która określa, że certyfikaty samodzielne (relacja równorzędna) są akceptowane, a także certyfikaty, które znajdują się w zaufanym łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-169">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="ea2a0-170">Ta wartość jest używana podczas tworzenia i debugowania klientów i usług, ponieważ certyfikaty wystawione przez siebie nie muszą zostać zakupione z zaufanego urzędu.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-170">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="ea2a0-171">Podczas wdrażania klienta należy zamiast tego użyć `ChainTrust` wartości.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-171">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="ea2a0-172">Możesz również ustawić wartość na `Custom` lub. `None`</span><span class="sxs-lookup"><span data-stu-id="ea2a0-172">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="ea2a0-173">Aby użyć `Custom` wartości, należy również `customCertificateValidator` ustawić atrybut na zestaw i typ używany do walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-173">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="ea2a0-174">Aby utworzyć własny niestandardowy moduł sprawdzania poprawności, należy dziedziczyć z klasy abstrakcyjnej X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-174">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="ea2a0-175">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-175">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="ea2a0-176">Ten `revocationMode` atrybut określa, jak certyfikaty są sprawdzane pod kątem odwołania.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-176">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="ea2a0-177">Wartość domyślna `online` wskazuje, że certyfikaty będą sprawdzane automatycznie w celu odwołania.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-177">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="ea2a0-178">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="ea2a0-178">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea2a0-179">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea2a0-179">Example</span></span>  
 <span data-ttu-id="ea2a0-180">Poniższy przykład wykonuje dwa zadania.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-180">The following example does two tasks.</span></span> <span data-ttu-id="ea2a0-181">Najpierw określa certyfikat usługi, który ma być używany przez klienta podczas komunikowania się z punktami końcowymi, których nazwa domeny znajduje się `www.contoso.com` za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-181">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="ea2a0-182">Po drugie określa tryb odwołania i lokalizację magazynu używane podczas uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-182">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea2a0-183">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea2a0-183">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="ea2a0-184">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ea2a0-184">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ea2a0-185">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="ea2a0-185">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="ea2a0-186">Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów</span><span class="sxs-lookup"><span data-stu-id="ea2a0-186">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="ea2a0-187">\<> uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="ea2a0-187">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="ea2a0-188">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="ea2a0-188">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="ea2a0-189">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ea2a0-189">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
