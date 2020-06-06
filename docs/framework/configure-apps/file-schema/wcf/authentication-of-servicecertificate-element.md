---
title: <authentication><serviceCertificate>elementu
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 29170f032469b4d55b50f57ca06ce403a5aeaf2c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398228"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="115a8-102">\<authentication>\<serviceCertificate>elementu</span><span class="sxs-lookup"><span data-stu-id="115a8-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="115a8-103">Określa ustawienia używane przez serwer proxy klienta do uwierzytelniania certyfikatów usługi, które są uzyskiwane przy użyciu negocjacji SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="115a8-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="115a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="115a8-104">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="115a8-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="115a8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="115a8-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="115a8-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="115a8-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="115a8-107">Attributes</span></span>  
  
|<span data-ttu-id="115a8-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="115a8-108">Attribute</span></span>|<span data-ttu-id="115a8-109">Opis</span><span class="sxs-lookup"><span data-stu-id="115a8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="115a8-110">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="115a8-110">customCertificateValidatorType</span></span>|<span data-ttu-id="115a8-111">Ciąg.</span><span class="sxs-lookup"><span data-stu-id="115a8-111">String.</span></span> <span data-ttu-id="115a8-112">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="115a8-112">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="115a8-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="115a8-113">certificateValidationMode</span></span>|<span data-ttu-id="115a8-114">Określa jeden z trzech trybów używanych do walidacji poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="115a8-114">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="115a8-115">Jeśli jest ustawiona na `Custom` , należy również podać CustomCertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="115a8-115">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="115a8-116">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="115a8-116">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="115a8-117">odwołaniemode</span><span class="sxs-lookup"><span data-stu-id="115a8-117">revocationMode</span></span>|<span data-ttu-id="115a8-118">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="115a8-118">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="115a8-119">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="115a8-119">The default is `Online`.</span></span>|  
|<span data-ttu-id="115a8-120">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="115a8-120">trustedStoreLocation</span></span>|<span data-ttu-id="115a8-121">Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="115a8-121">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="115a8-122">Ta wartość jest używana podczas negocjowania certyfikatu usługi z klientem.</span><span class="sxs-lookup"><span data-stu-id="115a8-122">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="115a8-123">Sprawdzanie poprawności jest wykonywane względem magazynu **osób zaufanych** w określonej lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="115a8-123">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="115a8-124">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="115a8-124">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="115a8-125">customCertificateValidator — atrybut</span><span class="sxs-lookup"><span data-stu-id="115a8-125">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="115a8-126">Wartość</span><span class="sxs-lookup"><span data-stu-id="115a8-126">Value</span></span>|<span data-ttu-id="115a8-127">Opis</span><span class="sxs-lookup"><span data-stu-id="115a8-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="115a8-128">String</span><span class="sxs-lookup"><span data-stu-id="115a8-128">String</span></span>|<span data-ttu-id="115a8-129">Określa nazwę typu i zestaw oraz inne dane używane do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="115a8-129">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="115a8-130">certificateValidationMode — atrybut</span><span class="sxs-lookup"><span data-stu-id="115a8-130">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="115a8-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="115a8-131">Value</span></span>|<span data-ttu-id="115a8-132">Opis</span><span class="sxs-lookup"><span data-stu-id="115a8-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="115a8-133">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="115a8-133">Enumeration</span></span>|<span data-ttu-id="115a8-134">Jedna z następujących wartości: None, zaufania elementów równorzędnych, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="115a8-134">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="115a8-135">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="115a8-135">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="115a8-136">Atrybut odwołania</span><span class="sxs-lookup"><span data-stu-id="115a8-136">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="115a8-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="115a8-137">Value</span></span>|<span data-ttu-id="115a8-138">Opis</span><span class="sxs-lookup"><span data-stu-id="115a8-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="115a8-139">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="115a8-139">Enumeration</span></span>|<span data-ttu-id="115a8-140">Jedna z następujących wartości: NOCHECK, online i offline.</span><span class="sxs-lookup"><span data-stu-id="115a8-140">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="115a8-141">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="115a8-141">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="115a8-142">trustedStoreLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="115a8-142">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="115a8-143">Wartość</span><span class="sxs-lookup"><span data-stu-id="115a8-143">Value</span></span>|<span data-ttu-id="115a8-144">Opis</span><span class="sxs-lookup"><span data-stu-id="115a8-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="115a8-145">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="115a8-145">Enumeration</span></span>|<span data-ttu-id="115a8-146">Jedna z następujących wartości: LocalMachine lub CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="115a8-146">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="115a8-147">Wartość domyślna to CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="115a8-147">The default is CurrentUser.</span></span> <span data-ttu-id="115a8-148">Jeśli aplikacja kliencka jest uruchomiona na koncie systemowym, certyfikat jest zwykle w obszarze LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="115a8-148">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="115a8-149">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, certyfikat zazwyczaj znajduje się w CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="115a8-149">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="115a8-150">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="115a8-150">Child Elements</span></span>  
 <span data-ttu-id="115a8-151">Brak.</span><span class="sxs-lookup"><span data-stu-id="115a8-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="115a8-152">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="115a8-152">Parent Elements</span></span>  
  
|<span data-ttu-id="115a8-153">Element</span><span class="sxs-lookup"><span data-stu-id="115a8-153">Element</span></span>|<span data-ttu-id="115a8-154">Opis</span><span class="sxs-lookup"><span data-stu-id="115a8-154">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="115a8-155">Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="115a8-155">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="115a8-156">Uwagi</span><span class="sxs-lookup"><span data-stu-id="115a8-156">Remarks</span></span>  
 <span data-ttu-id="115a8-157">`certificateValidationMode`Atrybut tego elementu konfiguracji określa poziom zaufania używany do uwierzytelniania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="115a8-157">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="115a8-158">Domyślnie poziom jest ustawiony na `ChainTrust` , który określa, że każdy certyfikat musi znajdować się w hierarchii certyfikatów kończących się zaufanym urzędem certyfikacji w górnej części łańcucha.</span><span class="sxs-lookup"><span data-stu-id="115a8-158">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="115a8-159">Jest to najbardziej bezpieczny tryb.</span><span class="sxs-lookup"><span data-stu-id="115a8-159">This is the most secure mode.</span></span> <span data-ttu-id="115a8-160">Można również ustawić wartość na `PeerOrChainTrust` , która określa, że certyfikaty samodzielne (relacja równorzędna) są akceptowane, a także certyfikaty, które znajdują się w zaufanym łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="115a8-160">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="115a8-161">Ta wartość jest używana podczas tworzenia i debugowania klientów i usług, ponieważ certyfikaty wystawione przez siebie nie muszą zostać zakupione z zaufanego urzędu.</span><span class="sxs-lookup"><span data-stu-id="115a8-161">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="115a8-162">Podczas wdrażania klienta należy `ChainTrust` zamiast tego użyć wartości.</span><span class="sxs-lookup"><span data-stu-id="115a8-162">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="115a8-163">Możesz również ustawić wartość na `Custom` lub `None` .</span><span class="sxs-lookup"><span data-stu-id="115a8-163">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="115a8-164">Aby użyć `Custom` wartości, należy również ustawić `customCertificateValidator` atrybut na zestaw i typ używany do walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="115a8-164">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="115a8-165">Aby utworzyć własny niestandardowy moduł sprawdzania poprawności, należy dziedziczyć z klasy abstrakcyjnej X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="115a8-165">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="115a8-166">Aby uzyskać więcej informacji, zobacz [How to: Create a Service, która korzysta z niestandardowego modułu weryfikacji certyfikatu](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="115a8-166">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="115a8-167">Ten `revocationMode` atrybut określa, jak certyfikaty są sprawdzane pod kątem odwołania.</span><span class="sxs-lookup"><span data-stu-id="115a8-167">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="115a8-168">Wartość domyślna `online` wskazuje, że certyfikaty będą sprawdzane automatycznie w celu odwołania.</span><span class="sxs-lookup"><span data-stu-id="115a8-168">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="115a8-169">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="115a8-169">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="115a8-170">Przykład</span><span class="sxs-lookup"><span data-stu-id="115a8-170">Example</span></span>  
 <span data-ttu-id="115a8-171">Poniższy przykład wykonuje dwa zadania.</span><span class="sxs-lookup"><span data-stu-id="115a8-171">The following example does two tasks.</span></span> <span data-ttu-id="115a8-172">Najpierw określa certyfikat usługi, który ma być używany przez klienta podczas komunikowania się z punktami końcowymi, których nazwa domeny znajduje się `www.contoso.com` za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="115a8-172">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="115a8-173">Po drugie określa tryb odwołania i lokalizację magazynu używane podczas uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="115a8-173">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="115a8-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="115a8-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="115a8-175">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="115a8-175">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="115a8-176">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="115a8-176">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="115a8-177">Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów</span><span class="sxs-lookup"><span data-stu-id="115a8-177">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="115a8-178">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="115a8-178">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="115a8-179">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="115a8-179">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
