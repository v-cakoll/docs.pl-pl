---
title: <peerAuthentication>, element
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 09094c00b8faa28c37e202112251fee7cb4580be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934017"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="0244b-102">\<peerAuthentication, element ></span><span class="sxs-lookup"><span data-stu-id="0244b-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="0244b-103">Określa opcje uwierzytelniania dla klientów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="0244b-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="0244b-104">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci peer-to-](../../../wcf/feature-details/peer-to-peer-networking.md)peer.</span><span class="sxs-lookup"><span data-stu-id="0244b-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="0244b-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0244b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="0244b-106">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="0244b-106">\<behaviors></span></span>  
<span data-ttu-id="0244b-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="0244b-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="0244b-108">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="0244b-108">\<behavior></span></span>  
<span data-ttu-id="0244b-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="0244b-109">\<clientCredentials></span></span>  
<span data-ttu-id="0244b-110">\<> elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="0244b-110">\<peer></span></span>  
<span data-ttu-id="0244b-111">\<PeerAuthentication></span><span class="sxs-lookup"><span data-stu-id="0244b-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0244b-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="0244b-112">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0244b-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0244b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0244b-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0244b-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0244b-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0244b-115">Attributes</span></span>  
  
|<span data-ttu-id="0244b-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0244b-116">Attribute</span></span>|<span data-ttu-id="0244b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="0244b-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="0244b-118">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="0244b-118">Optional string.</span></span> <span data-ttu-id="0244b-119">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="0244b-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="0244b-120">Ten atrybut musi być ustawiony, `certificateValidationMode` gdy jest ustawiony `Custom`na.</span><span class="sxs-lookup"><span data-stu-id="0244b-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="0244b-121">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="0244b-121">Optional enumeration.</span></span> <span data-ttu-id="0244b-122">Określa jeden z trzech trybów używanych do walidacji poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="0244b-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="0244b-123">Jeśli jest ustawiona `Custom`na, należy `customCertificateValidator` również podać wartość.</span><span class="sxs-lookup"><span data-stu-id="0244b-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="0244b-124">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="0244b-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="0244b-125">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="0244b-125">Optional enumeration.</span></span> <span data-ttu-id="0244b-126">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="0244b-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="0244b-127">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="0244b-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="0244b-128">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="0244b-128">Optional enumeration.</span></span> <span data-ttu-id="0244b-129">Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="0244b-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="0244b-130">Ta wartość jest używana podczas negocjowania certyfikatu usługi z klientem.</span><span class="sxs-lookup"><span data-stu-id="0244b-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="0244b-131">Sprawdzanie poprawności jest wykonywane względem magazynu **osób zaufanych** w określonej lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="0244b-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="0244b-132">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="0244b-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="0244b-133">customCertificateValidatorType — atrybut</span><span class="sxs-lookup"><span data-stu-id="0244b-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="0244b-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="0244b-134">Value</span></span>|<span data-ttu-id="0244b-135">Opis</span><span class="sxs-lookup"><span data-stu-id="0244b-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0244b-136">String</span><span class="sxs-lookup"><span data-stu-id="0244b-136">String</span></span>|<span data-ttu-id="0244b-137">Określa nazwę typu i zestaw oraz inne dane używane do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="0244b-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="0244b-138">Minimalna nazwa przestrzeni nazw i typ są wymagane.</span><span class="sxs-lookup"><span data-stu-id="0244b-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="0244b-139">Informacje opcjonalne obejmują: nazwę zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="0244b-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="0244b-140">certificateValidationMode — atrybut</span><span class="sxs-lookup"><span data-stu-id="0244b-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="0244b-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="0244b-141">Value</span></span>|<span data-ttu-id="0244b-142">Opis</span><span class="sxs-lookup"><span data-stu-id="0244b-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0244b-143">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0244b-143">Enumeration</span></span>|<span data-ttu-id="0244b-144">Jedna z następujących wartości: `None`, `PeerTrust`, `ChainTrust` `PeerOrChainTrust`,, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="0244b-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="0244b-145">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="0244b-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="0244b-146">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="0244b-146">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="0244b-147">Atrybut odwołania</span><span class="sxs-lookup"><span data-stu-id="0244b-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="0244b-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="0244b-148">Value</span></span>|<span data-ttu-id="0244b-149">Opis</span><span class="sxs-lookup"><span data-stu-id="0244b-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0244b-150">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0244b-150">Enumeration</span></span>|<span data-ttu-id="0244b-151">Jedna z następujących wartości: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="0244b-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="0244b-152">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="0244b-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="0244b-153">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="0244b-153">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="0244b-154">trustedStoreLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="0244b-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="0244b-155">Wartość</span><span class="sxs-lookup"><span data-stu-id="0244b-155">Value</span></span>|<span data-ttu-id="0244b-156">Opis</span><span class="sxs-lookup"><span data-stu-id="0244b-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0244b-157">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0244b-157">Enumeration</span></span>|<span data-ttu-id="0244b-158">Jedna z następujących wartości: `LocalMachine` lub. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="0244b-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="0244b-159">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="0244b-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="0244b-160">Jeśli aplikacja kliencka jest uruchomiona na koncie systemowym, zwykle `LocalMachine`jest to certyfikat.</span><span class="sxs-lookup"><span data-stu-id="0244b-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="0244b-161">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, certyfikat zazwyczaj znajduje się w `CurrentUser`temacie.</span><span class="sxs-lookup"><span data-stu-id="0244b-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0244b-162">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0244b-162">Child Elements</span></span>  
 <span data-ttu-id="0244b-163">Brak.</span><span class="sxs-lookup"><span data-stu-id="0244b-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0244b-164">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0244b-164">Parent Elements</span></span>  
  
|<span data-ttu-id="0244b-165">Element</span><span class="sxs-lookup"><span data-stu-id="0244b-165">Element</span></span>|<span data-ttu-id="0244b-166">Opis</span><span class="sxs-lookup"><span data-stu-id="0244b-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0244b-167">\<> elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="0244b-167">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="0244b-168">Określa poświadczenie używane do uwierzytelniania klienta w usłudze równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="0244b-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0244b-169">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0244b-169">Remarks</span></span>  
 <span data-ttu-id="0244b-170">Element odnosi się do <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> klasy. `<authentication>`</span><span class="sxs-lookup"><span data-stu-id="0244b-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="0244b-171">Ten element określa moduł sprawdzania poprawności, który jest wywoływany podczas uwierzytelniania sąsiada-sąsiada w sieci.</span><span class="sxs-lookup"><span data-stu-id="0244b-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="0244b-172">Gdy nowy element równorzędny podejmie próbę nawiązania połączenia sąsiada, przekazuje własne poświadczenie do elementu równorzędnego odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="0244b-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="0244b-173">Moduł sprawdzania poprawności jest wywoływany w celu zweryfikowania poświadczeń strony zdalnej.</span><span class="sxs-lookup"><span data-stu-id="0244b-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="0244b-174">Za każdym razem, gdy połączenie równorzędne jest nawiązane w sieci, oba elementy równorzędne są uwierzytelniane wzajemnie, co oznacza, że są wywoływane walidacje na obu końcach.</span><span class="sxs-lookup"><span data-stu-id="0244b-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0244b-175">Przykład</span><span class="sxs-lookup"><span data-stu-id="0244b-175">Example</span></span>  
 <span data-ttu-id="0244b-176">Poniższy kod ustawia tryb `PeerOrChainTrust`walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="0244b-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0244b-177">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0244b-177">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="0244b-178">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="0244b-178">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="0244b-179">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="0244b-179">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="0244b-180">[Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0244b-180">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="0244b-181">[Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0244b-181">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="0244b-182">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="0244b-182">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
