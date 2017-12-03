---
title: '&lt;peerAuthentication&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ddcb8b5199fc46cf3e5058650168131bb457545d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltpeerauthenticationgt-element"></a><span data-ttu-id="38e4d-102">&lt;peerAuthentication&gt;, element</span><span class="sxs-lookup"><span data-stu-id="38e4d-102">&lt;peerAuthentication&gt; Element</span></span>
<span data-ttu-id="38e4d-103">Określa opcje uwierzytelniania dla klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="38e4d-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="38e4d-104">Zobacz programowania, peer-to-peer [sieci Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="38e4d-104"> peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="38e4d-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="38e4d-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="38e4d-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="38e4d-106">\<behaviors></span></span>  
<span data-ttu-id="38e4d-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="38e4d-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="38e4d-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="38e4d-108">\<behavior></span></span>  
<span data-ttu-id="38e4d-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="38e4d-109">\<clientCredentials></span></span>  
<span data-ttu-id="38e4d-110">\<peer ></span><span class="sxs-lookup"><span data-stu-id="38e4d-110">\<peer></span></span>  
<span data-ttu-id="38e4d-111">\<PeerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="38e4d-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38e4d-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="38e4d-112">Syntax</span></span>  
  
```xml  
<peerAuthentication  
customCertificateValidatorType = "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38e4d-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="38e4d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="38e4d-114">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="38e4d-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38e4d-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="38e4d-115">Attributes</span></span>  
  
|<span data-ttu-id="38e4d-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="38e4d-116">Attribute</span></span>|<span data-ttu-id="38e4d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="38e4d-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="38e4d-118">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="38e4d-118">Optional string.</span></span> <span data-ttu-id="38e4d-119">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="38e4d-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="38e4d-120">Ten atrybut musi być ustawiane podczas `certificateValidationMode` ma ustawioną wartość `Custom`.</span><span class="sxs-lookup"><span data-stu-id="38e4d-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certifcateValidationMode`|<span data-ttu-id="38e4d-121">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="38e4d-121">Optional enumeration.</span></span> <span data-ttu-id="38e4d-122">Określa jeden z trzech trybów używanych do walidacji poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="38e4d-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="38e4d-123">Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` należy dostarczyć także.</span><span class="sxs-lookup"><span data-stu-id="38e4d-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="38e4d-124">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="38e4d-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="38e4d-125">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="38e4d-125">Optional enumeration.</span></span> <span data-ttu-id="38e4d-126">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="38e4d-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="38e4d-127">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="38e4d-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="38e4d-128">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="38e4d-128">Optional enumeration.</span></span> <span data-ttu-id="38e4d-129">Jeden z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="38e4d-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="38e4d-130">Ta wartość jest używana, gdy negocjowane jest certyfikat usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="38e4d-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="38e4d-131">Sprawdzanie poprawności jest wykonywane przed **zaufane osoby** są przechowywane w lokalizacji określonej magazynu.</span><span class="sxs-lookup"><span data-stu-id="38e4d-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="38e4d-132">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="38e4d-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="38e4d-133">customCertificateValidatorType atrybutu</span><span class="sxs-lookup"><span data-stu-id="38e4d-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="38e4d-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="38e4d-134">Value</span></span>|<span data-ttu-id="38e4d-135">Opis</span><span class="sxs-lookup"><span data-stu-id="38e4d-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38e4d-136">String</span><span class="sxs-lookup"><span data-stu-id="38e4d-136">String</span></span>|<span data-ttu-id="38e4d-137">Określa nazwę typu i zestawu i innych danych można znaleźć typu.</span><span class="sxs-lookup"><span data-stu-id="38e4d-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="38e4d-138">Co najmniej nazwę przestrzeni nazw i typ są wymagane.</span><span class="sxs-lookup"><span data-stu-id="38e4d-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="38e4d-139">Zawiera dodatkowe informacje: Nazwa zestawu, numer wersji, kultury i tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="38e4d-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="38e4d-140">tryb certificateValidationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="38e4d-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="38e4d-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="38e4d-141">Value</span></span>|<span data-ttu-id="38e4d-142">Opis</span><span class="sxs-lookup"><span data-stu-id="38e4d-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38e4d-143">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="38e4d-143">Enumeration</span></span>|<span data-ttu-id="38e4d-144">Jedną z następujących wartości: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="38e4d-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="38e4d-145">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="38e4d-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="38e4d-146">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="38e4d-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="38e4d-147">revocationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="38e4d-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="38e4d-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="38e4d-148">Value</span></span>|<span data-ttu-id="38e4d-149">Opis</span><span class="sxs-lookup"><span data-stu-id="38e4d-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38e4d-150">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="38e4d-150">Enumeration</span></span>|<span data-ttu-id="38e4d-151">Jedną z następujących wartości: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="38e4d-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="38e4d-152">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="38e4d-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="38e4d-153">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="38e4d-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="38e4d-154">trustedStoreLocation atrybutu</span><span class="sxs-lookup"><span data-stu-id="38e4d-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="38e4d-155">Wartość</span><span class="sxs-lookup"><span data-stu-id="38e4d-155">Value</span></span>|<span data-ttu-id="38e4d-156">Opis</span><span class="sxs-lookup"><span data-stu-id="38e4d-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38e4d-157">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="38e4d-157">Enumeration</span></span>|<span data-ttu-id="38e4d-158">Jedną z następujących wartości: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="38e4d-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="38e4d-159">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="38e4d-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="38e4d-160">Jeśli aplikacja kliencka jest uruchomiona na koncie systemu, a następnie certyfikat jest zwykle w obszarze `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="38e4d-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="38e4d-161">Jeśli aplikacja kliencka jest uruchomiona na koncie użytkownika, a następnie certyfikat jest zwykle w `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="38e4d-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38e4d-162">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="38e4d-162">Child Elements</span></span>  
 <span data-ttu-id="38e4d-163">Brak.</span><span class="sxs-lookup"><span data-stu-id="38e4d-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38e4d-164">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="38e4d-164">Parent Elements</span></span>  
  
|<span data-ttu-id="38e4d-165">Element</span><span class="sxs-lookup"><span data-stu-id="38e4d-165">Element</span></span>|<span data-ttu-id="38e4d-166">Opis</span><span class="sxs-lookup"><span data-stu-id="38e4d-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38e4d-167">\<peer ></span><span class="sxs-lookup"><span data-stu-id="38e4d-167">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="38e4d-168">Określa poświadczenie używane w celu uwierzytelniania klienta usługi elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="38e4d-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38e4d-169">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38e4d-169">Remarks</span></span>  
 <span data-ttu-id="38e4d-170">`<authentication>` Element odpowiada <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> klasy.</span><span class="sxs-lookup"><span data-stu-id="38e4d-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="38e4d-171">Ten element Określa moduł weryfikacji, który jest wywoływany podczas uwierzytelniania sąsiada sąsiada w siatce.</span><span class="sxs-lookup"><span data-stu-id="38e4d-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="38e4d-172">Próba nawiązania połączenia z elementem sąsiednim przez nowego elementu równorzędnego przekazaniem własną poświadczeń do nieodpowiadający węzłem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="38e4d-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="38e4d-173">Moduł sprawdzania poprawności obiektu odpowiadającego jest wywoływane w celu Sprawdź poświadczenia strona zdalna.</span><span class="sxs-lookup"><span data-stu-id="38e4d-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="38e4d-174">Zawsze, gdy jest nawiązywane połączenie elementu równorzędnego w sieci, zarówno komputery są wzajemnie uwierzytelnione, znaczenie modułów sprawdzania poprawności po obu stronach są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="38e4d-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38e4d-175">Przykład</span><span class="sxs-lookup"><span data-stu-id="38e4d-175">Example</span></span>  
 <span data-ttu-id="38e4d-176">Poniższy kod ustawia tryb walidacji certyfikatu `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="38e4d-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38e4d-177">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38e4d-177">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="38e4d-178">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="38e4d-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="38e4d-179">Sieci peer-to-Peer</span><span class="sxs-lookup"><span data-stu-id="38e4d-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="38e4d-180">Uwierzytelnianie wiadomości kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="38e4d-180">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="38e4d-181">Niestandardowe uwierzytelnianie kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="38e4d-181">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="38e4d-182">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="38e4d-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
