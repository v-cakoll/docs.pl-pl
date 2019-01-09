---
title: '&lt;peerAuthentication&gt;, element'
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 8937df6a2fcab305a519d566f7d666a3d94b4061
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149719"
---
# <a name="ltpeerauthenticationgt-element"></a><span data-ttu-id="ee9ea-102">&lt;peerAuthentication&gt;, element</span><span class="sxs-lookup"><span data-stu-id="ee9ea-102">&lt;peerAuthentication&gt; Element</span></span>
<span data-ttu-id="ee9ea-103">Określa opcje uwierzytelniania dla klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="ee9ea-104">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="ee9ea-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="ee9ea-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ee9ea-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ee9ea-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="ee9ea-106">\<behaviors></span></span>  
<span data-ttu-id="ee9ea-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="ee9ea-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="ee9ea-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ee9ea-108">\<behavior></span></span>  
<span data-ttu-id="ee9ea-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="ee9ea-109">\<clientCredentials></span></span>  
<span data-ttu-id="ee9ea-110">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="ee9ea-110">\<peer></span></span>  
<span data-ttu-id="ee9ea-111">\<PeerAuthentication></span><span class="sxs-lookup"><span data-stu-id="ee9ea-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee9ea-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee9ea-112">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee9ea-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ee9ea-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ee9ea-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ee9ea-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee9ea-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ee9ea-115">Attributes</span></span>  
  
|<span data-ttu-id="ee9ea-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ee9ea-116">Attribute</span></span>|<span data-ttu-id="ee9ea-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ee9ea-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="ee9ea-118">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-118">Optional string.</span></span> <span data-ttu-id="ee9ea-119">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="ee9ea-120">Ten atrybut musi być ustawiane podczas `certificateValidationMode` ustawiono `Custom`.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certifcateValidationMode`|<span data-ttu-id="ee9ea-121">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-121">Optional enumeration.</span></span> <span data-ttu-id="ee9ea-122">Określa jeden z trzech trybów używanych do walidacji poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="ee9ea-123">Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` musi również zostać dostarczony.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="ee9ea-124">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="ee9ea-125">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-125">Optional enumeration.</span></span> <span data-ttu-id="ee9ea-126">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="ee9ea-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="ee9ea-127">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="ee9ea-128">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-128">Optional enumeration.</span></span> <span data-ttu-id="ee9ea-129">Jedną z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="ee9ea-130">Ta wartość jest używana, gdy certyfikat usługi jest negocjowane do klienta.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="ee9ea-131">Sprawdzanie poprawności jest wykonywane względem **zaufane osoby** są przechowywane w lokalizacji określonego magazynu.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="ee9ea-132">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="ee9ea-133">customCertificateValidatorType atrybutu</span><span class="sxs-lookup"><span data-stu-id="ee9ea-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="ee9ea-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="ee9ea-134">Value</span></span>|<span data-ttu-id="ee9ea-135">Opis</span><span class="sxs-lookup"><span data-stu-id="ee9ea-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ee9ea-136">String</span><span class="sxs-lookup"><span data-stu-id="ee9ea-136">String</span></span>|<span data-ttu-id="ee9ea-137">Określa nazwę typu i zestawu i inne dane, używana do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="ee9ea-138">Co najmniej nazwy przestrzeni nazw i typ są wymagane.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="ee9ea-139">Zawiera informacje opcjonalne: Nazwa zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="ee9ea-140">tryb certificateValidationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="ee9ea-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="ee9ea-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="ee9ea-141">Value</span></span>|<span data-ttu-id="ee9ea-142">Opis</span><span class="sxs-lookup"><span data-stu-id="ee9ea-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ee9ea-143">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ee9ea-143">Enumeration</span></span>|<span data-ttu-id="ee9ea-144">Jedną z następujących wartości: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="ee9ea-145">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="ee9ea-146">Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="ee9ea-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="ee9ea-147">revocationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="ee9ea-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="ee9ea-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="ee9ea-148">Value</span></span>|<span data-ttu-id="ee9ea-149">Opis</span><span class="sxs-lookup"><span data-stu-id="ee9ea-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ee9ea-150">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ee9ea-150">Enumeration</span></span>|<span data-ttu-id="ee9ea-151">Jedną z następujących wartości: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="ee9ea-152">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="ee9ea-153">Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="ee9ea-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="ee9ea-154">trustedStoreLocation atrybutu</span><span class="sxs-lookup"><span data-stu-id="ee9ea-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="ee9ea-155">Wartość</span><span class="sxs-lookup"><span data-stu-id="ee9ea-155">Value</span></span>|<span data-ttu-id="ee9ea-156">Opis</span><span class="sxs-lookup"><span data-stu-id="ee9ea-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ee9ea-157">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ee9ea-157">Enumeration</span></span>|<span data-ttu-id="ee9ea-158">Jedną z następujących wartości: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="ee9ea-159">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="ee9ea-160">Jeśli aplikacja kliencka jest uruchomiona w ramach konta systemowego, a następnie certyfikatu wynosi zazwyczaj `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="ee9ea-161">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, a następnie certyfikat znajduje się zwykle w `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee9ea-162">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ee9ea-162">Child Elements</span></span>  
 <span data-ttu-id="ee9ea-163">Brak.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee9ea-164">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ee9ea-164">Parent Elements</span></span>  
  
|<span data-ttu-id="ee9ea-165">Element</span><span class="sxs-lookup"><span data-stu-id="ee9ea-165">Element</span></span>|<span data-ttu-id="ee9ea-166">Opis</span><span class="sxs-lookup"><span data-stu-id="ee9ea-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee9ea-167">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="ee9ea-167">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="ee9ea-168">Określa poświadczenie używane do uwierzytelniania klienta do usługi elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee9ea-169">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee9ea-169">Remarks</span></span>  
 <span data-ttu-id="ee9ea-170">`<authentication>` Element odpowiada <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> klasy.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="ee9ea-171">Ten element Określa moduł weryfikacji, który jest wywoływany podczas uwierzytelniania sąsiada sąsiada w siatce.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="ee9ea-172">Próba nawiązania połączenia sąsiada przez nowego elementu równorzędnego przekazuje swoje własne poświadczenia dla elementu równorzędnego działa prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="ee9ea-173">Modułu sprawdzania poprawności obiektu odpowiadającego jest wywoływana, aby zweryfikować poświadczenia zdalnego innych firm.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="ee9ea-174">Zawsze, gdy nawiązaniu połączenia równorzędnego w siatce, zarówno komputery są wzajemnie uwierzytelnione, znaczenie modułów sprawdzania poprawności na obu końcach są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee9ea-175">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee9ea-175">Example</span></span>  
 <span data-ttu-id="ee9ea-176">Poniższy kod ustawia tryb walidacji certyfikatu `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="ee9ea-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <peerAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="ee9ea-177">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee9ea-177">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="ee9ea-178">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="ee9ea-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="ee9ea-179">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="ee9ea-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="ee9ea-180">Uwierzytelnianie wiadomości z kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="ee9ea-180">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="ee9ea-181">Kanał elementu równorzędnego uwierzytelniania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="ee9ea-181">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="ee9ea-182">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="ee9ea-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
