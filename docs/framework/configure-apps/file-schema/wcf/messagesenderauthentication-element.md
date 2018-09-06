---
title: '&lt;messageSenderAuthentication&gt;. element'
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: cb727df7b8d7605cbe984a8f6737c89bf1bfb2be
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788967"
---
# <a name="ltmessagesenderauthenticationgt-element"></a><span data-ttu-id="57eab-102">&lt;messageSenderAuthentication&gt;. element</span><span class="sxs-lookup"><span data-stu-id="57eab-102">&lt;messageSenderAuthentication&gt; element</span></span>
<span data-ttu-id="57eab-103">Określa opcje uwierzytelnienia dla nadawców wiadomości peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="57eab-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="57eab-104">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="57eab-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="57eab-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="57eab-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="57eab-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="57eab-106">\<behaviors></span></span>  
<span data-ttu-id="57eab-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="57eab-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="57eab-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="57eab-108">\<behavior></span></span>  
<span data-ttu-id="57eab-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="57eab-109">\<clientCredentials></span></span>  
<span data-ttu-id="57eab-110">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="57eab-110">\<peer></span></span>  
<span data-ttu-id="57eab-111">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="57eab-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57eab-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="57eab-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57eab-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="57eab-113">Attributes and Elements</span></span>  
 <span data-ttu-id="57eab-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="57eab-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57eab-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="57eab-115">Attributes</span></span>  
  
|<span data-ttu-id="57eab-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="57eab-116">Attribute</span></span>|<span data-ttu-id="57eab-117">Opis</span><span class="sxs-lookup"><span data-stu-id="57eab-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57eab-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="57eab-118">customCertificateValidatorType</span></span>|<span data-ttu-id="57eab-119">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="57eab-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="57eab-120">Ten atrybut musi być ustawiane podczas `certificateValidationMode` ustawiono `Custom`.</span><span class="sxs-lookup"><span data-stu-id="57eab-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="57eab-121">certifcateValidationMode</span><span class="sxs-lookup"><span data-stu-id="57eab-121">certifcateValidationMode</span></span>|<span data-ttu-id="57eab-122">Określa jeden z trzech trybów używanych do walidacji poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="57eab-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="57eab-123">Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` musi również zostać dostarczony.</span><span class="sxs-lookup"><span data-stu-id="57eab-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|<span data-ttu-id="57eab-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="57eab-124">revocationMode</span></span>|<span data-ttu-id="57eab-125">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="57eab-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|<span data-ttu-id="57eab-126">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="57eab-126">trustedStoreLocation</span></span>|<span data-ttu-id="57eab-127">Jedną z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="57eab-127">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="57eab-128">Ta wartość jest używana, gdy certyfikat usługi jest negocjowane do klienta.</span><span class="sxs-lookup"><span data-stu-id="57eab-128">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="57eab-129">Sprawdzanie poprawności jest wykonywane względem **zaufane osoby** są przechowywane w lokalizacji określonego magazynu.</span><span class="sxs-lookup"><span data-stu-id="57eab-129">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="57eab-130">customCertificateValidatorType atrybutu</span><span class="sxs-lookup"><span data-stu-id="57eab-130">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="57eab-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="57eab-131">Value</span></span>|<span data-ttu-id="57eab-132">Opis</span><span class="sxs-lookup"><span data-stu-id="57eab-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="57eab-133">String</span><span class="sxs-lookup"><span data-stu-id="57eab-133">String</span></span>|<span data-ttu-id="57eab-134">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="57eab-134">Optional.</span></span> <span data-ttu-id="57eab-135">Określa nazwę typu i zestawu i inne dane, używana do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="57eab-135">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="57eab-136">Co najmniej nazwy przestrzeni nazw i typ są wymagane.</span><span class="sxs-lookup"><span data-stu-id="57eab-136">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="57eab-137">Zawiera informacje opcjonalne: Nazwa zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="57eab-137">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="57eab-138">tryb certificateValidationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="57eab-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="57eab-139">Wartość</span><span class="sxs-lookup"><span data-stu-id="57eab-139">Value</span></span>|<span data-ttu-id="57eab-140">Opis</span><span class="sxs-lookup"><span data-stu-id="57eab-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="57eab-141">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="57eab-141">Enumeration</span></span>|<span data-ttu-id="57eab-142">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="57eab-142">Optional.</span></span> <span data-ttu-id="57eab-143">Jedną z następujących wartości: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="57eab-143">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="57eab-144">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="57eab-144">The default is `ChainTrust`.</span></span> <span data-ttu-id="57eab-145">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="57eab-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="57eab-146">Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="57eab-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="57eab-147">revocationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="57eab-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="57eab-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="57eab-148">Value</span></span>|<span data-ttu-id="57eab-149">Opis</span><span class="sxs-lookup"><span data-stu-id="57eab-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="57eab-150">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="57eab-150">Enumeration</span></span>|<span data-ttu-id="57eab-151">Jedną z następujących wartości: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="57eab-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="57eab-152">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="57eab-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="57eab-153">Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="57eab-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="57eab-154">trustedStoreLocation atrybutu</span><span class="sxs-lookup"><span data-stu-id="57eab-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="57eab-155">Wartość</span><span class="sxs-lookup"><span data-stu-id="57eab-155">Value</span></span>|<span data-ttu-id="57eab-156">Opis</span><span class="sxs-lookup"><span data-stu-id="57eab-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="57eab-157">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="57eab-157">Enumeration</span></span>|<span data-ttu-id="57eab-158">Jedną z następujących wartości: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="57eab-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="57eab-159">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="57eab-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="57eab-160">Jeśli aplikacja kliencka jest uruchomiona w ramach konta systemowego, a następnie certyfikatu wynosi zazwyczaj `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="57eab-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="57eab-161">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, a następnie certyfikat znajduje się zwykle w `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="57eab-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="57eab-162">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="57eab-162">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57eab-163">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="57eab-163">Child Elements</span></span>  
 <span data-ttu-id="57eab-164">Brak.</span><span class="sxs-lookup"><span data-stu-id="57eab-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57eab-165">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="57eab-165">Parent Elements</span></span>  
  
|<span data-ttu-id="57eab-166">Element</span><span class="sxs-lookup"><span data-stu-id="57eab-166">Element</span></span>|<span data-ttu-id="57eab-167">Opis</span><span class="sxs-lookup"><span data-stu-id="57eab-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57eab-168">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="57eab-168">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="57eab-169">Określa poświadczenie używane do uwierzytelniania klienta do usługi elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="57eab-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57eab-170">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57eab-170">Remarks</span></span>  
 <span data-ttu-id="57eab-171">Ten element musi być skonfigurowany, jeśli wybrano opcję uwierzytelniania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="57eab-171">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="57eab-172">Dla kanałów danych wyjściowych, każdy komunikat jest podpisany przy użyciu certyfikatu dostarczonego przez [ \<certyfikatu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="57eab-172">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="57eab-173">Wszystkie komunikaty zanim dostarczane do aplikacji, są porównywane z poświadczeniami komunikatu przy użyciu modułu sprawdzania poprawności określonego przez `customCertificateValidatorType` atrybutu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="57eab-173">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="57eab-174">Moduł weryfikacji można zaakceptować lub odrzucić poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="57eab-174">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57eab-175">Przykład</span><span class="sxs-lookup"><span data-stu-id="57eab-175">Example</span></span>  
 <span data-ttu-id="57eab-176">Poniższy kod ustawia tryb walidacji nadawcy wiadomości `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="57eab-176">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="57eab-177">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57eab-177">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="57eab-178">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="57eab-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="57eab-179">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="57eab-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="57eab-180">Uwierzytelnianie wiadomości z kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="57eab-180">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="57eab-181">Kanał elementu równorzędnego uwierzytelniania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="57eab-181">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="57eab-182">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="57eab-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
