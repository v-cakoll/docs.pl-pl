---
title: <peerAuthentication>, element
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 1e99f6d117604f9ba2672972a4b09e7fe9f96792
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783386"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="293e2-102">\<peerAuthentication> Element</span><span class="sxs-lookup"><span data-stu-id="293e2-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="293e2-103">Określa opcje uwierzytelniania dla klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="293e2-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="293e2-104">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="293e2-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="293e2-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="293e2-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="293e2-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="293e2-106">\<behaviors></span></span>  
<span data-ttu-id="293e2-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="293e2-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="293e2-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="293e2-108">\<behavior></span></span>  
<span data-ttu-id="293e2-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="293e2-109">\<clientCredentials></span></span>  
<span data-ttu-id="293e2-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="293e2-110">\<peer></span></span>  
<span data-ttu-id="293e2-111">\<PeerAuthentication></span><span class="sxs-lookup"><span data-stu-id="293e2-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="293e2-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="293e2-112">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="293e2-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="293e2-113">Attributes and Elements</span></span>  
 <span data-ttu-id="293e2-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="293e2-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="293e2-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="293e2-115">Attributes</span></span>  
  
|<span data-ttu-id="293e2-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="293e2-116">Attribute</span></span>|<span data-ttu-id="293e2-117">Opis</span><span class="sxs-lookup"><span data-stu-id="293e2-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="293e2-118">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="293e2-118">Optional string.</span></span> <span data-ttu-id="293e2-119">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="293e2-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="293e2-120">Ten atrybut musi być ustawiane podczas `certificateValidationMode` ustawiono `Custom`.</span><span class="sxs-lookup"><span data-stu-id="293e2-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certifcateValidationMode`|<span data-ttu-id="293e2-121">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="293e2-121">Optional enumeration.</span></span> <span data-ttu-id="293e2-122">Określa jeden z trzech trybów używanych do walidacji poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="293e2-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="293e2-123">Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` musi również zostać dostarczony.</span><span class="sxs-lookup"><span data-stu-id="293e2-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="293e2-124">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="293e2-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="293e2-125">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="293e2-125">Optional enumeration.</span></span> <span data-ttu-id="293e2-126">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="293e2-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="293e2-127">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="293e2-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="293e2-128">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="293e2-128">Optional enumeration.</span></span> <span data-ttu-id="293e2-129">Jedną z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="293e2-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="293e2-130">Ta wartość jest używana, gdy certyfikat usługi jest negocjowane do klienta.</span><span class="sxs-lookup"><span data-stu-id="293e2-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="293e2-131">Sprawdzanie poprawności jest wykonywane względem **zaufane osoby** są przechowywane w lokalizacji określonego magazynu.</span><span class="sxs-lookup"><span data-stu-id="293e2-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="293e2-132">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="293e2-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="293e2-133">customCertificateValidatorType Attribute</span><span class="sxs-lookup"><span data-stu-id="293e2-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="293e2-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="293e2-134">Value</span></span>|<span data-ttu-id="293e2-135">Opis</span><span class="sxs-lookup"><span data-stu-id="293e2-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="293e2-136">String</span><span class="sxs-lookup"><span data-stu-id="293e2-136">String</span></span>|<span data-ttu-id="293e2-137">Określa nazwę typu i zestawu i inne dane, używana do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="293e2-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="293e2-138">Co najmniej nazwy przestrzeni nazw i typ są wymagane.</span><span class="sxs-lookup"><span data-stu-id="293e2-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="293e2-139">Zawiera informacje opcjonalne: Nazwa zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="293e2-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="293e2-140">tryb certificateValidationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="293e2-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="293e2-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="293e2-141">Value</span></span>|<span data-ttu-id="293e2-142">Opis</span><span class="sxs-lookup"><span data-stu-id="293e2-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="293e2-143">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="293e2-143">Enumeration</span></span>|<span data-ttu-id="293e2-144">Jedną z następujących wartości: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="293e2-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="293e2-145">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="293e2-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="293e2-146">Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="293e2-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="293e2-147">revocationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="293e2-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="293e2-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="293e2-148">Value</span></span>|<span data-ttu-id="293e2-149">Opis</span><span class="sxs-lookup"><span data-stu-id="293e2-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="293e2-150">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="293e2-150">Enumeration</span></span>|<span data-ttu-id="293e2-151">Jedną z następujących wartości: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="293e2-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="293e2-152">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="293e2-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="293e2-153">Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="293e2-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="293e2-154">trustedStoreLocation atrybutu</span><span class="sxs-lookup"><span data-stu-id="293e2-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="293e2-155">Wartość</span><span class="sxs-lookup"><span data-stu-id="293e2-155">Value</span></span>|<span data-ttu-id="293e2-156">Opis</span><span class="sxs-lookup"><span data-stu-id="293e2-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="293e2-157">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="293e2-157">Enumeration</span></span>|<span data-ttu-id="293e2-158">Jedną z następujących wartości: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="293e2-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="293e2-159">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="293e2-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="293e2-160">Jeśli aplikacja kliencka jest uruchomiona w ramach konta systemowego, a następnie certyfikatu wynosi zazwyczaj `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="293e2-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="293e2-161">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, a następnie certyfikat znajduje się zwykle w `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="293e2-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="293e2-162">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="293e2-162">Child Elements</span></span>  
 <span data-ttu-id="293e2-163">Brak.</span><span class="sxs-lookup"><span data-stu-id="293e2-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="293e2-164">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="293e2-164">Parent Elements</span></span>  
  
|<span data-ttu-id="293e2-165">Element</span><span class="sxs-lookup"><span data-stu-id="293e2-165">Element</span></span>|<span data-ttu-id="293e2-166">Opis</span><span class="sxs-lookup"><span data-stu-id="293e2-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="293e2-167">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="293e2-167">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="293e2-168">Określa poświadczenie używane do uwierzytelniania klienta do usługi elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="293e2-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="293e2-169">Uwagi</span><span class="sxs-lookup"><span data-stu-id="293e2-169">Remarks</span></span>  
 <span data-ttu-id="293e2-170">`<authentication>` Element odpowiada <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> klasy.</span><span class="sxs-lookup"><span data-stu-id="293e2-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="293e2-171">Ten element Określa moduł weryfikacji, który jest wywoływany podczas uwierzytelniania sąsiada sąsiada w siatce.</span><span class="sxs-lookup"><span data-stu-id="293e2-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="293e2-172">Próba nawiązania połączenia sąsiada przez nowego elementu równorzędnego przekazuje swoje własne poświadczenia dla elementu równorzędnego działa prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="293e2-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="293e2-173">Modułu sprawdzania poprawności obiektu odpowiadającego jest wywoływana, aby zweryfikować poświadczenia zdalnego innych firm.</span><span class="sxs-lookup"><span data-stu-id="293e2-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="293e2-174">Zawsze, gdy nawiązaniu połączenia równorzędnego w siatce, zarówno komputery są wzajemnie uwierzytelnione, znaczenie modułów sprawdzania poprawności na obu końcach są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="293e2-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="293e2-175">Przykład</span><span class="sxs-lookup"><span data-stu-id="293e2-175">Example</span></span>  
 <span data-ttu-id="293e2-176">Poniższy kod ustawia tryb walidacji certyfikatu `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="293e2-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="293e2-177">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="293e2-177">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="293e2-178">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="293e2-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="293e2-179">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="293e2-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="293e2-180">[Uwierzytelnianie wiadomości z kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="293e2-180">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="293e2-181">[Kanał elementu równorzędnego uwierzytelniania niestandardowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="293e2-181">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="293e2-182">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="293e2-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
