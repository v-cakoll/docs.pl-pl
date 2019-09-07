---
title: <peerAuthentication>, element
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4c29c84a2cc56a890c8273e410ba31b5f3900732
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400085"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="37a0a-102">\<peerAuthentication, element ></span><span class="sxs-lookup"><span data-stu-id="37a0a-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="37a0a-103">Określa opcje uwierzytelniania dla klientów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="37a0a-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="37a0a-104">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci peer-to-](../../../wcf/feature-details/peer-to-peer-networking.md)peer.</span><span class="sxs-lookup"><span data-stu-id="37a0a-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
<span data-ttu-id="37a0a-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="37a0a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="37a0a-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="37a0a-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="37a0a-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="37a0a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="37a0a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="37a0a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="37a0a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="37a0a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="37a0a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Obiekt clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="37a0a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="37a0a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> elementów równorzędnych**](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="37a0a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="37a0a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<peerAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="37a0a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37a0a-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="37a0a-113">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37a0a-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="37a0a-114">Attributes and Elements</span></span>  
 <span data-ttu-id="37a0a-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="37a0a-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37a0a-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="37a0a-116">Attributes</span></span>  
  
|<span data-ttu-id="37a0a-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="37a0a-117">Attribute</span></span>|<span data-ttu-id="37a0a-118">Opis</span><span class="sxs-lookup"><span data-stu-id="37a0a-118">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="37a0a-119">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="37a0a-119">Optional string.</span></span> <span data-ttu-id="37a0a-120">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="37a0a-120">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="37a0a-121">Ten atrybut musi być ustawiony, `certificateValidationMode` gdy jest ustawiony `Custom`na.</span><span class="sxs-lookup"><span data-stu-id="37a0a-121">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="37a0a-122">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="37a0a-122">Optional enumeration.</span></span> <span data-ttu-id="37a0a-123">Określa jeden z trzech trybów używanych do walidacji poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="37a0a-123">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="37a0a-124">Jeśli jest ustawiona `Custom`na, należy `customCertificateValidator` również podać wartość.</span><span class="sxs-lookup"><span data-stu-id="37a0a-124">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="37a0a-125">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="37a0a-125">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="37a0a-126">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="37a0a-126">Optional enumeration.</span></span> <span data-ttu-id="37a0a-127">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="37a0a-127">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="37a0a-128">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="37a0a-128">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="37a0a-129">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="37a0a-129">Optional enumeration.</span></span> <span data-ttu-id="37a0a-130">Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="37a0a-130">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="37a0a-131">Ta wartość jest używana podczas negocjowania certyfikatu usługi z klientem.</span><span class="sxs-lookup"><span data-stu-id="37a0a-131">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="37a0a-132">Sprawdzanie poprawności jest wykonywane względem magazynu **osób zaufanych** w określonej lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="37a0a-132">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="37a0a-133">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="37a0a-133">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="37a0a-134">customCertificateValidatorType — atrybut</span><span class="sxs-lookup"><span data-stu-id="37a0a-134">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="37a0a-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="37a0a-135">Value</span></span>|<span data-ttu-id="37a0a-136">Opis</span><span class="sxs-lookup"><span data-stu-id="37a0a-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="37a0a-137">String</span><span class="sxs-lookup"><span data-stu-id="37a0a-137">String</span></span>|<span data-ttu-id="37a0a-138">Określa nazwę typu i zestaw oraz inne dane używane do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="37a0a-138">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="37a0a-139">Minimalna nazwa przestrzeni nazw i typ są wymagane.</span><span class="sxs-lookup"><span data-stu-id="37a0a-139">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="37a0a-140">Informacje opcjonalne obejmują: nazwę zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="37a0a-140">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="37a0a-141">certificateValidationMode — atrybut</span><span class="sxs-lookup"><span data-stu-id="37a0a-141">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="37a0a-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="37a0a-142">Value</span></span>|<span data-ttu-id="37a0a-143">Opis</span><span class="sxs-lookup"><span data-stu-id="37a0a-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="37a0a-144">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="37a0a-144">Enumeration</span></span>|<span data-ttu-id="37a0a-145">Jedna z następujących wartości: `None`, `PeerTrust`, `ChainTrust` `PeerOrChainTrust`,, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="37a0a-145">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="37a0a-146">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="37a0a-146">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="37a0a-147">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="37a0a-147">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="37a0a-148">Atrybut odwołania</span><span class="sxs-lookup"><span data-stu-id="37a0a-148">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="37a0a-149">Wartość</span><span class="sxs-lookup"><span data-stu-id="37a0a-149">Value</span></span>|<span data-ttu-id="37a0a-150">Opis</span><span class="sxs-lookup"><span data-stu-id="37a0a-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="37a0a-151">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="37a0a-151">Enumeration</span></span>|<span data-ttu-id="37a0a-152">Jedna z następujących wartości: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="37a0a-152">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="37a0a-153">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="37a0a-153">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="37a0a-154">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="37a0a-154">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="37a0a-155">trustedStoreLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="37a0a-155">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="37a0a-156">Wartość</span><span class="sxs-lookup"><span data-stu-id="37a0a-156">Value</span></span>|<span data-ttu-id="37a0a-157">Opis</span><span class="sxs-lookup"><span data-stu-id="37a0a-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="37a0a-158">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="37a0a-158">Enumeration</span></span>|<span data-ttu-id="37a0a-159">Jedna z następujących wartości: `LocalMachine` lub. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="37a0a-159">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="37a0a-160">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="37a0a-160">The default is `CurrentUser`.</span></span> <span data-ttu-id="37a0a-161">Jeśli aplikacja kliencka jest uruchomiona na koncie systemowym, zwykle `LocalMachine`jest to certyfikat.</span><span class="sxs-lookup"><span data-stu-id="37a0a-161">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="37a0a-162">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, certyfikat zazwyczaj znajduje się w `CurrentUser`temacie.</span><span class="sxs-lookup"><span data-stu-id="37a0a-162">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37a0a-163">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="37a0a-163">Child Elements</span></span>  
 <span data-ttu-id="37a0a-164">Brak.</span><span class="sxs-lookup"><span data-stu-id="37a0a-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37a0a-165">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="37a0a-165">Parent Elements</span></span>  
  
|<span data-ttu-id="37a0a-166">Element</span><span class="sxs-lookup"><span data-stu-id="37a0a-166">Element</span></span>|<span data-ttu-id="37a0a-167">Opis</span><span class="sxs-lookup"><span data-stu-id="37a0a-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37a0a-168">\<> elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="37a0a-168">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="37a0a-169">Określa poświadczenie używane do uwierzytelniania klienta w usłudze równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="37a0a-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37a0a-170">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37a0a-170">Remarks</span></span>  
 <span data-ttu-id="37a0a-171">Element odnosi się do <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> klasy. `<authentication>`</span><span class="sxs-lookup"><span data-stu-id="37a0a-171">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="37a0a-172">Ten element określa moduł sprawdzania poprawności, który jest wywoływany podczas uwierzytelniania sąsiada-sąsiada w sieci.</span><span class="sxs-lookup"><span data-stu-id="37a0a-172">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="37a0a-173">Gdy nowy element równorzędny podejmie próbę nawiązania połączenia sąsiada, przekazuje własne poświadczenie do elementu równorzędnego odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="37a0a-173">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="37a0a-174">Moduł sprawdzania poprawności jest wywoływany w celu zweryfikowania poświadczeń strony zdalnej.</span><span class="sxs-lookup"><span data-stu-id="37a0a-174">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="37a0a-175">Za każdym razem, gdy połączenie równorzędne jest nawiązane w sieci, oba elementy równorzędne są uwierzytelniane wzajemnie, co oznacza, że są wywoływane walidacje na obu końcach.</span><span class="sxs-lookup"><span data-stu-id="37a0a-175">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37a0a-176">Przykład</span><span class="sxs-lookup"><span data-stu-id="37a0a-176">Example</span></span>  
 <span data-ttu-id="37a0a-177">Poniższy kod ustawia tryb `PeerOrChainTrust`walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="37a0a-177">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="37a0a-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37a0a-178">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="37a0a-179">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="37a0a-179">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="37a0a-180">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="37a0a-180">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="37a0a-181">[Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="37a0a-181">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="37a0a-182">[Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="37a0a-182">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="37a0a-183">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="37a0a-183">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
