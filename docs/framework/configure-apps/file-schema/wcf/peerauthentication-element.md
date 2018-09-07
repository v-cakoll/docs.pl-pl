---
title: '&lt;peerAuthentication&gt;, element'
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4fb8cc4989313afa3ef16c90b54e0feae1ccb71d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44076491"
---
# <a name="ltpeerauthenticationgt-element"></a><span data-ttu-id="23d25-102">&lt;peerAuthentication&gt;, element</span><span class="sxs-lookup"><span data-stu-id="23d25-102">&lt;peerAuthentication&gt; Element</span></span>
<span data-ttu-id="23d25-103">Określa opcje uwierzytelniania dla klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="23d25-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="23d25-104">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="23d25-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="23d25-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="23d25-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="23d25-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="23d25-106">\<behaviors></span></span>  
<span data-ttu-id="23d25-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="23d25-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="23d25-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="23d25-108">\<behavior></span></span>  
<span data-ttu-id="23d25-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="23d25-109">\<clientCredentials></span></span>  
<span data-ttu-id="23d25-110">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="23d25-110">\<peer></span></span>  
<span data-ttu-id="23d25-111">\<PeerAuthentication></span><span class="sxs-lookup"><span data-stu-id="23d25-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23d25-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="23d25-112">Syntax</span></span>  
  
```xml  
<peerAuthentication  
customCertificateValidatorType = "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23d25-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="23d25-113">Attributes and Elements</span></span>  
 <span data-ttu-id="23d25-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="23d25-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23d25-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="23d25-115">Attributes</span></span>  
  
|<span data-ttu-id="23d25-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="23d25-116">Attribute</span></span>|<span data-ttu-id="23d25-117">Opis</span><span class="sxs-lookup"><span data-stu-id="23d25-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="23d25-118">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="23d25-118">Optional string.</span></span> <span data-ttu-id="23d25-119">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="23d25-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="23d25-120">Ten atrybut musi być ustawiane podczas `certificateValidationMode` ustawiono `Custom`.</span><span class="sxs-lookup"><span data-stu-id="23d25-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certifcateValidationMode`|<span data-ttu-id="23d25-121">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="23d25-121">Optional enumeration.</span></span> <span data-ttu-id="23d25-122">Określa jeden z trzech trybów używanych do walidacji poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="23d25-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="23d25-123">Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` musi również zostać dostarczony.</span><span class="sxs-lookup"><span data-stu-id="23d25-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="23d25-124">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="23d25-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="23d25-125">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="23d25-125">Optional enumeration.</span></span> <span data-ttu-id="23d25-126">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="23d25-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="23d25-127">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="23d25-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="23d25-128">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="23d25-128">Optional enumeration.</span></span> <span data-ttu-id="23d25-129">Jedną z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="23d25-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="23d25-130">Ta wartość jest używana, gdy certyfikat usługi jest negocjowane do klienta.</span><span class="sxs-lookup"><span data-stu-id="23d25-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="23d25-131">Sprawdzanie poprawności jest wykonywane względem **zaufane osoby** są przechowywane w lokalizacji określonego magazynu.</span><span class="sxs-lookup"><span data-stu-id="23d25-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="23d25-132">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="23d25-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="23d25-133">customCertificateValidatorType atrybutu</span><span class="sxs-lookup"><span data-stu-id="23d25-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="23d25-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="23d25-134">Value</span></span>|<span data-ttu-id="23d25-135">Opis</span><span class="sxs-lookup"><span data-stu-id="23d25-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23d25-136">String</span><span class="sxs-lookup"><span data-stu-id="23d25-136">String</span></span>|<span data-ttu-id="23d25-137">Określa nazwę typu i zestawu i inne dane, używana do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="23d25-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="23d25-138">Co najmniej nazwy przestrzeni nazw i typ są wymagane.</span><span class="sxs-lookup"><span data-stu-id="23d25-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="23d25-139">Zawiera informacje opcjonalne: Nazwa zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="23d25-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="23d25-140">tryb certificateValidationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="23d25-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="23d25-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="23d25-141">Value</span></span>|<span data-ttu-id="23d25-142">Opis</span><span class="sxs-lookup"><span data-stu-id="23d25-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23d25-143">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="23d25-143">Enumeration</span></span>|<span data-ttu-id="23d25-144">Jedną z następujących wartości: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="23d25-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="23d25-145">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="23d25-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="23d25-146">Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="23d25-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="23d25-147">revocationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="23d25-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="23d25-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="23d25-148">Value</span></span>|<span data-ttu-id="23d25-149">Opis</span><span class="sxs-lookup"><span data-stu-id="23d25-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23d25-150">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="23d25-150">Enumeration</span></span>|<span data-ttu-id="23d25-151">Jedną z następujących wartości: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="23d25-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="23d25-152">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="23d25-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="23d25-153">Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="23d25-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="23d25-154">trustedStoreLocation atrybutu</span><span class="sxs-lookup"><span data-stu-id="23d25-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="23d25-155">Wartość</span><span class="sxs-lookup"><span data-stu-id="23d25-155">Value</span></span>|<span data-ttu-id="23d25-156">Opis</span><span class="sxs-lookup"><span data-stu-id="23d25-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23d25-157">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="23d25-157">Enumeration</span></span>|<span data-ttu-id="23d25-158">Jedną z następujących wartości: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="23d25-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="23d25-159">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="23d25-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="23d25-160">Jeśli aplikacja kliencka jest uruchomiona w ramach konta systemowego, a następnie certyfikatu wynosi zazwyczaj `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="23d25-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="23d25-161">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, a następnie certyfikat znajduje się zwykle w `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="23d25-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23d25-162">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="23d25-162">Child Elements</span></span>  
 <span data-ttu-id="23d25-163">Brak.</span><span class="sxs-lookup"><span data-stu-id="23d25-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23d25-164">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="23d25-164">Parent Elements</span></span>  
  
|<span data-ttu-id="23d25-165">Element</span><span class="sxs-lookup"><span data-stu-id="23d25-165">Element</span></span>|<span data-ttu-id="23d25-166">Opis</span><span class="sxs-lookup"><span data-stu-id="23d25-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23d25-167">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="23d25-167">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="23d25-168">Określa poświadczenie używane do uwierzytelniania klienta do usługi elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="23d25-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23d25-169">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23d25-169">Remarks</span></span>  
 <span data-ttu-id="23d25-170">`<authentication>` Element odpowiada <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> klasy.</span><span class="sxs-lookup"><span data-stu-id="23d25-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="23d25-171">Ten element Określa moduł weryfikacji, który jest wywoływany podczas uwierzytelniania sąsiada sąsiada w siatce.</span><span class="sxs-lookup"><span data-stu-id="23d25-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="23d25-172">Próba nawiązania połączenia sąsiada przez nowego elementu równorzędnego przekazuje swoje własne poświadczenia dla elementu równorzędnego działa prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="23d25-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="23d25-173">Modułu sprawdzania poprawności obiektu odpowiadającego jest wywoływana, aby zweryfikować poświadczenia zdalnego innych firm.</span><span class="sxs-lookup"><span data-stu-id="23d25-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="23d25-174">Zawsze, gdy nawiązaniu połączenia równorzędnego w siatce, zarówno komputery są wzajemnie uwierzytelnione, znaczenie modułów sprawdzania poprawności na obu końcach są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="23d25-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23d25-175">Przykład</span><span class="sxs-lookup"><span data-stu-id="23d25-175">Example</span></span>  
 <span data-ttu-id="23d25-176">Poniższy kod ustawia tryb walidacji certyfikatu `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="23d25-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
     <peerAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
     <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="23d25-177">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23d25-177">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="23d25-178">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="23d25-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="23d25-179">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="23d25-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="23d25-180">Uwierzytelnianie wiadomości z kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="23d25-180">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="23d25-181">Kanał elementu równorzędnego uwierzytelniania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="23d25-181">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="23d25-182">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="23d25-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
