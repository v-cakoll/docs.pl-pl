---
title: '&lt;messageSenderAuthentication&gt;. element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5a280f9fe59ca5294276b98ec3632d6bc1a7ecba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltmessagesenderauthenticationgt-element"></a><span data-ttu-id="15bd8-102">&lt;messageSenderAuthentication&gt;. element</span><span class="sxs-lookup"><span data-stu-id="15bd8-102">&lt;messageSenderAuthentication&gt; element</span></span>
<span data-ttu-id="15bd8-103">Określa opcje uwierzytelnienia dla nadawców wiadomości peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="15bd8-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="15bd8-104">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="15bd8-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="15bd8-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="15bd8-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="15bd8-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="15bd8-106">\<behaviors></span></span>  
<span data-ttu-id="15bd8-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="15bd8-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="15bd8-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="15bd8-108">\<behavior></span></span>  
<span data-ttu-id="15bd8-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="15bd8-109">\<clientCredentials></span></span>  
<span data-ttu-id="15bd8-110">\<peer ></span><span class="sxs-lookup"><span data-stu-id="15bd8-110">\<peer></span></span>  
<span data-ttu-id="15bd8-111">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="15bd8-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15bd8-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="15bd8-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15bd8-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="15bd8-113">Attributes and Elements</span></span>  
 <span data-ttu-id="15bd8-114">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="15bd8-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15bd8-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="15bd8-115">Attributes</span></span>  
  
|<span data-ttu-id="15bd8-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="15bd8-116">Attribute</span></span>|<span data-ttu-id="15bd8-117">Opis</span><span class="sxs-lookup"><span data-stu-id="15bd8-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="15bd8-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="15bd8-118">customCertificateValidatorType</span></span>|<span data-ttu-id="15bd8-119">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="15bd8-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="15bd8-120">Ten atrybut musi być ustawiane podczas `certificateValidationMode` ma ustawioną wartość `Custom`.</span><span class="sxs-lookup"><span data-stu-id="15bd8-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="15bd8-121">certifcateValidationMode</span><span class="sxs-lookup"><span data-stu-id="15bd8-121">certifcateValidationMode</span></span>|<span data-ttu-id="15bd8-122">Określa jeden z trzech trybów używanych do walidacji poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="15bd8-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="15bd8-123">Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` należy dostarczyć także.</span><span class="sxs-lookup"><span data-stu-id="15bd8-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|<span data-ttu-id="15bd8-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="15bd8-124">revocationMode</span></span>|<span data-ttu-id="15bd8-125">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="15bd8-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|<span data-ttu-id="15bd8-126">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="15bd8-126">trustedStoreLocation</span></span>|<span data-ttu-id="15bd8-127">Jeden z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="15bd8-127">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="15bd8-128">Ta wartość jest używana, gdy negocjowane jest certyfikat usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="15bd8-128">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="15bd8-129">Sprawdzanie poprawności jest wykonywane przed **zaufane osoby** są przechowywane w lokalizacji określonej magazynu.</span><span class="sxs-lookup"><span data-stu-id="15bd8-129">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="15bd8-130">customCertificateValidatorType atrybutu</span><span class="sxs-lookup"><span data-stu-id="15bd8-130">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="15bd8-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="15bd8-131">Value</span></span>|<span data-ttu-id="15bd8-132">Opis</span><span class="sxs-lookup"><span data-stu-id="15bd8-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15bd8-133">String</span><span class="sxs-lookup"><span data-stu-id="15bd8-133">String</span></span>|<span data-ttu-id="15bd8-134">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="15bd8-134">Optional.</span></span> <span data-ttu-id="15bd8-135">Określa nazwę typu i zestawu i innych danych można znaleźć typu.</span><span class="sxs-lookup"><span data-stu-id="15bd8-135">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="15bd8-136">Co najmniej nazwę przestrzeni nazw i typ są wymagane.</span><span class="sxs-lookup"><span data-stu-id="15bd8-136">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="15bd8-137">Zawiera dodatkowe informacje: Nazwa zestawu, numer wersji, kultury i tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="15bd8-137">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="15bd8-138">tryb certificateValidationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="15bd8-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="15bd8-139">Wartość</span><span class="sxs-lookup"><span data-stu-id="15bd8-139">Value</span></span>|<span data-ttu-id="15bd8-140">Opis</span><span class="sxs-lookup"><span data-stu-id="15bd8-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15bd8-141">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="15bd8-141">Enumeration</span></span>|<span data-ttu-id="15bd8-142">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="15bd8-142">Optional.</span></span> <span data-ttu-id="15bd8-143">Jedną z następujących wartości: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="15bd8-143">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="15bd8-144">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="15bd8-144">The default is `ChainTrust`.</span></span> <span data-ttu-id="15bd8-145">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="15bd8-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="15bd8-146">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="15bd8-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="15bd8-147">revocationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="15bd8-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="15bd8-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="15bd8-148">Value</span></span>|<span data-ttu-id="15bd8-149">Opis</span><span class="sxs-lookup"><span data-stu-id="15bd8-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15bd8-150">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="15bd8-150">Enumeration</span></span>|<span data-ttu-id="15bd8-151">Jedną z następujących wartości: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="15bd8-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="15bd8-152">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="15bd8-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="15bd8-153">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="15bd8-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="15bd8-154">trustedStoreLocation atrybutu</span><span class="sxs-lookup"><span data-stu-id="15bd8-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="15bd8-155">Wartość</span><span class="sxs-lookup"><span data-stu-id="15bd8-155">Value</span></span>|<span data-ttu-id="15bd8-156">Opis</span><span class="sxs-lookup"><span data-stu-id="15bd8-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15bd8-157">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="15bd8-157">Enumeration</span></span>|<span data-ttu-id="15bd8-158">Jedną z następujących wartości: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="15bd8-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="15bd8-159">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="15bd8-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="15bd8-160">Jeśli aplikacja kliencka jest uruchomiona na koncie systemu, a następnie certyfikat jest zwykle w obszarze `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="15bd8-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="15bd8-161">Jeśli aplikacja kliencka jest uruchomiona na koncie użytkownika, a następnie certyfikat jest zwykle w `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="15bd8-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="15bd8-162">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="15bd8-162">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15bd8-163">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="15bd8-163">Child Elements</span></span>  
 <span data-ttu-id="15bd8-164">Brak.</span><span class="sxs-lookup"><span data-stu-id="15bd8-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15bd8-165">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="15bd8-165">Parent Elements</span></span>  
  
|<span data-ttu-id="15bd8-166">Element</span><span class="sxs-lookup"><span data-stu-id="15bd8-166">Element</span></span>|<span data-ttu-id="15bd8-167">Opis</span><span class="sxs-lookup"><span data-stu-id="15bd8-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15bd8-168">\<peer ></span><span class="sxs-lookup"><span data-stu-id="15bd8-168">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="15bd8-169">Określa poświadczenie używane w celu uwierzytelniania klienta usługi elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="15bd8-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15bd8-170">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15bd8-170">Remarks</span></span>  
 <span data-ttu-id="15bd8-171">Ten element musi być skonfigurowany, jeśli wybrano opcję uwierzytelniania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="15bd8-171">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="15bd8-172">Dane wyjściowe kanałów, każdy komunikat jest podpisany za pomocą certyfikatu dostarczonego przez [ \<certyfikatu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="15bd8-172">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="15bd8-173">Wszystkie komunikaty przed dostarczeniem do aplikacji, są porównywane z poświadczeniami komunikatu za pomocą modułu sprawdzania poprawności określonego przez `customCertificateValidatorType` atrybutu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="15bd8-173">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="15bd8-174">Moduł weryfikacji można zaakceptowanie lub odrzucenie poświadczenie.</span><span class="sxs-lookup"><span data-stu-id="15bd8-174">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15bd8-175">Przykład</span><span class="sxs-lookup"><span data-stu-id="15bd8-175">Example</span></span>  
 <span data-ttu-id="15bd8-176">Poniższy kod ustawia tryb walidacji nadawcy wiadomości `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="15bd8-176">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
      <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
        <messageSenderAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
       <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="15bd8-177">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15bd8-177">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="15bd8-178">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="15bd8-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="15bd8-179">Sieci peer-to-Peer</span><span class="sxs-lookup"><span data-stu-id="15bd8-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="15bd8-180">Uwierzytelnianie wiadomości kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="15bd8-180">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="15bd8-181">Niestandardowe uwierzytelnianie kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="15bd8-181">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="15bd8-182">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="15bd8-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
