---
title: <authentication><clientCertificate>elementu
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 99084f6b7afbdd8586ee706cd6ec44b349d81ff2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398267"
---
# <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="adcfe-102">\<authentication>\<clientCertificate>elementu</span><span class="sxs-lookup"><span data-stu-id="adcfe-102">\<authentication> of \<clientCertificate> Element</span></span>
<span data-ttu-id="adcfe-103">Określa zachowania uwierzytelniania dla certyfikatów klienta używanych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="adcfe-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="adcfe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="adcfe-104">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adcfe-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="adcfe-105">Attributes and Elements</span></span>  
 <span data-ttu-id="adcfe-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="adcfe-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adcfe-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="adcfe-107">Attributes</span></span>  
  
|<span data-ttu-id="adcfe-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="adcfe-108">Attribute</span></span>|<span data-ttu-id="adcfe-109">Opis</span><span class="sxs-lookup"><span data-stu-id="adcfe-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="adcfe-110">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="adcfe-110">customCertificateValidatorType</span></span>|<span data-ttu-id="adcfe-111">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="adcfe-111">Optional string.</span></span> <span data-ttu-id="adcfe-112">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="adcfe-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="adcfe-113">Ten atrybut musi być ustawiony `certificateValidationMode` , gdy jest ustawiony na `Custom` .</span><span class="sxs-lookup"><span data-stu-id="adcfe-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="adcfe-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="adcfe-114">certificateValidationMode</span></span>|<span data-ttu-id="adcfe-115">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="adcfe-115">Optional enumeration.</span></span> <span data-ttu-id="adcfe-116">Określa jeden z trybów używanych do walidacji poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="adcfe-116">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="adcfe-117">Ten atrybut jest <xref:System.ServiceModel.Security.X509CertificateValidationMode> typu.</span><span class="sxs-lookup"><span data-stu-id="adcfe-117">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="adcfe-118">Jeśli jest ustawiona na <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType> , `customCertificateValidator` należy również podać wartość.</span><span class="sxs-lookup"><span data-stu-id="adcfe-118">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="adcfe-119">Wartość domyślna to <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="adcfe-119">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="adcfe-120">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="adcfe-120">includeWindowsGroups</span></span>|<span data-ttu-id="adcfe-121">Opcjonalna wartość logiczna.</span><span class="sxs-lookup"><span data-stu-id="adcfe-121">Optional Boolean.</span></span> <span data-ttu-id="adcfe-122">Określa, czy grupy systemu Windows znajdują się w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="adcfe-122">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="adcfe-123">Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ powoduje pełne rozszerzanie grupy.</span><span class="sxs-lookup"><span data-stu-id="adcfe-123">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="adcfe-124">Ustaw ten atrybut na `false` , jeśli nie ma potrzeby ustanawiania listy grup, do których należy użytkownik.</span><span class="sxs-lookup"><span data-stu-id="adcfe-124">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="adcfe-125">mapClientCertificateToWindowsAccount</span><span class="sxs-lookup"><span data-stu-id="adcfe-125">mapClientCertificateToWindowsAccount</span></span>|<span data-ttu-id="adcfe-126">Typu.</span><span class="sxs-lookup"><span data-stu-id="adcfe-126">Boolean.</span></span> <span data-ttu-id="adcfe-127">Określa, czy klient może być zamapowany na tożsamość systemu Windows przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="adcfe-127">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="adcfe-128">Aby to zrobić, należy włączyć Active Directory.</span><span class="sxs-lookup"><span data-stu-id="adcfe-128">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="adcfe-129">odwołaniemode</span><span class="sxs-lookup"><span data-stu-id="adcfe-129">revocationMode</span></span>|<span data-ttu-id="adcfe-130">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="adcfe-130">Optional enumeration.</span></span> <span data-ttu-id="adcfe-131">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (RCL).</span><span class="sxs-lookup"><span data-stu-id="adcfe-131">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="adcfe-132">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="adcfe-132">The default is `Online`.</span></span> <span data-ttu-id="adcfe-133">Ta wartość jest ignorowana w przypadku korzystania z zabezpieczeń transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="adcfe-133">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="adcfe-134">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="adcfe-134">trustedStoreLocation</span></span>|<span data-ttu-id="adcfe-135">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="adcfe-135">Optional enumeration.</span></span> <span data-ttu-id="adcfe-136">Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="adcfe-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="adcfe-137">Ta wartość jest używana podczas negocjowania certyfikatu usługi z klientem.</span><span class="sxs-lookup"><span data-stu-id="adcfe-137">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="adcfe-138">Sprawdzanie poprawności jest wykonywane względem magazynu **osób zaufanych** w określonej lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="adcfe-138">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="adcfe-139">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="adcfe-139">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="adcfe-140">customCertificateValidatorType — atrybut</span><span class="sxs-lookup"><span data-stu-id="adcfe-140">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="adcfe-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="adcfe-141">Value</span></span>|<span data-ttu-id="adcfe-142">Opis</span><span class="sxs-lookup"><span data-stu-id="adcfe-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="adcfe-143">String</span><span class="sxs-lookup"><span data-stu-id="adcfe-143">String</span></span>|<span data-ttu-id="adcfe-144">Określa nazwę typu i zestaw oraz inne dane używane do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="adcfe-144">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="adcfe-145">certificateValidationMode — atrybut</span><span class="sxs-lookup"><span data-stu-id="adcfe-145">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="adcfe-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="adcfe-146">Value</span></span>|<span data-ttu-id="adcfe-147">Opis</span><span class="sxs-lookup"><span data-stu-id="adcfe-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="adcfe-148">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="adcfe-148">Enumeration</span></span>|<span data-ttu-id="adcfe-149">Jedna z następujących wartości: None, zaufania elementów równorzędnych, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="adcfe-149">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="adcfe-150">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="adcfe-150">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="adcfe-151">Atrybut odwołania</span><span class="sxs-lookup"><span data-stu-id="adcfe-151">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="adcfe-152">Wartość</span><span class="sxs-lookup"><span data-stu-id="adcfe-152">Value</span></span>|<span data-ttu-id="adcfe-153">Opis</span><span class="sxs-lookup"><span data-stu-id="adcfe-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="adcfe-154">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="adcfe-154">Enumeration</span></span>|<span data-ttu-id="adcfe-155">Jedna z następujących wartości: NOCHECK, online i offline.</span><span class="sxs-lookup"><span data-stu-id="adcfe-155">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="adcfe-156">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="adcfe-156">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="adcfe-157">trustedStoreLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="adcfe-157">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="adcfe-158">Wartość</span><span class="sxs-lookup"><span data-stu-id="adcfe-158">Value</span></span>|<span data-ttu-id="adcfe-159">Opis</span><span class="sxs-lookup"><span data-stu-id="adcfe-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="adcfe-160">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="adcfe-160">Enumeration</span></span>|<span data-ttu-id="adcfe-161">Jedna z następujących wartości: `LocalMachine` lub `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="adcfe-161">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="adcfe-162">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="adcfe-162">The default is `CurrentUser`.</span></span> <span data-ttu-id="adcfe-163">Jeśli aplikacja kliencka jest uruchomiona na koncie systemowym, zwykle jest to certyfikat `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="adcfe-163">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="adcfe-164">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, certyfikat zazwyczaj znajduje się w temacie `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="adcfe-164">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adcfe-165">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="adcfe-165">Child Elements</span></span>  
 <span data-ttu-id="adcfe-166">Brak.</span><span class="sxs-lookup"><span data-stu-id="adcfe-166">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="adcfe-167">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="adcfe-167">Parent Elements</span></span>  
  
|<span data-ttu-id="adcfe-168">Element</span><span class="sxs-lookup"><span data-stu-id="adcfe-168">Element</span></span>|<span data-ttu-id="adcfe-169">Opis</span><span class="sxs-lookup"><span data-stu-id="adcfe-169">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="adcfe-170">Definiuje certyfikat X. 509 używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="adcfe-170">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adcfe-171">Uwagi</span><span class="sxs-lookup"><span data-stu-id="adcfe-171">Remarks</span></span>  
 <span data-ttu-id="adcfe-172">`<authentication>`Element odnosi się do <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> klasy.</span><span class="sxs-lookup"><span data-stu-id="adcfe-172">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="adcfe-173">Umożliwia dostosowanie sposobu uwierzytelniania klientów.</span><span class="sxs-lookup"><span data-stu-id="adcfe-173">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="adcfe-174">Można ustawić `certificateValidationMode` atrybut na `None` , `ChainTrust` ,,, `PeerOrChainTrust` `PeerTrust` lub `Custom` .</span><span class="sxs-lookup"><span data-stu-id="adcfe-174">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="adcfe-175">Domyślnie poziom jest ustawiony na `ChainTrust` , który określa, że każdy certyfikat musi znajdować się w hierarchii certyfikatów kończących się w *urzędzie głównym* w górnej części łańcucha.</span><span class="sxs-lookup"><span data-stu-id="adcfe-175">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="adcfe-176">Jest to najbardziej bezpieczny tryb.</span><span class="sxs-lookup"><span data-stu-id="adcfe-176">This is the most secure mode.</span></span> <span data-ttu-id="adcfe-177">Można również ustawić wartość na `PeerOrChainTrust` , która określa, że certyfikaty samodzielne (relacja równorzędna) są akceptowane, a także certyfikaty, które znajdują się w zaufanym łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="adcfe-177">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="adcfe-178">Ta wartość jest używana podczas tworzenia i debugowania klientów i usług, ponieważ certyfikaty wystawione przez siebie nie muszą zostać zakupione z zaufanego urzędu.</span><span class="sxs-lookup"><span data-stu-id="adcfe-178">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="adcfe-179">Podczas wdrażania klienta należy `ChainTrust` zamiast tego użyć wartości.</span><span class="sxs-lookup"><span data-stu-id="adcfe-179">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="adcfe-180">Możesz również ustawić wartość na `Custom` .</span><span class="sxs-lookup"><span data-stu-id="adcfe-180">You can also set the value to `Custom`.</span></span> <span data-ttu-id="adcfe-181">W przypadku ustawienia `Custom` wartości należy również ustawić `customCertificateValidatorType` atrybut na zestaw i typ używany do weryfikacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="adcfe-181">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="adcfe-182">Aby utworzyć własny niestandardowy moduł sprawdzania poprawności, należy dziedziczyć z klasy abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="adcfe-182">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="adcfe-183">Aby uzyskać więcej informacji, zobacz [How to: Create a Service, która korzysta z niestandardowego modułu weryfikacji certyfikatu](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="adcfe-183">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="adcfe-184">Przykład</span><span class="sxs-lookup"><span data-stu-id="adcfe-184">Example</span></span>  
 <span data-ttu-id="adcfe-185">Poniższy kod określa certyfikat X. 509 i niestandardowy typ walidacji w `<authentication>` elemencie.</span><span class="sxs-lookup"><span data-stu-id="adcfe-185">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
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
  
## <a name="see-also"></a><span data-ttu-id="adcfe-186">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="adcfe-186">See also</span></span>

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [<span data-ttu-id="adcfe-187">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="adcfe-187">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="adcfe-188">Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów</span><span class="sxs-lookup"><span data-stu-id="adcfe-188">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="adcfe-189">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="adcfe-189">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
