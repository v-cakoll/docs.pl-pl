---
title: <messageSenderAuthentication>, element
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 804c280bcdb0fecc87f71121b7d95b5fd0268de9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423125"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="35ddb-102">\<messageSenderAuthentication > element</span><span class="sxs-lookup"><span data-stu-id="35ddb-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="35ddb-103">Określa opcje uwierzytelnienia dla nadawców wiadomości peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="35ddb-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="35ddb-104">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="35ddb-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="35ddb-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="35ddb-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="35ddb-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="35ddb-106">\<behaviors></span></span>  
<span data-ttu-id="35ddb-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="35ddb-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="35ddb-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="35ddb-108">\<behavior></span></span>  
<span data-ttu-id="35ddb-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="35ddb-109">\<clientCredentials></span></span>  
<span data-ttu-id="35ddb-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="35ddb-110">\<peer></span></span>  
<span data-ttu-id="35ddb-111">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="35ddb-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35ddb-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="35ddb-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35ddb-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="35ddb-113">Attributes and Elements</span></span>  
 <span data-ttu-id="35ddb-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="35ddb-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35ddb-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="35ddb-115">Attributes</span></span>  
  
|<span data-ttu-id="35ddb-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="35ddb-116">Attribute</span></span>|<span data-ttu-id="35ddb-117">Opis</span><span class="sxs-lookup"><span data-stu-id="35ddb-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="35ddb-118">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="35ddb-118">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="35ddb-119">Ten atrybut musi być ustawiane podczas `certificateValidationMode` ustawiono `Custom`.</span><span class="sxs-lookup"><span data-stu-id="35ddb-119">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="35ddb-120">Określa jeden z trzech trybów używanych do walidacji poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="35ddb-120">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="35ddb-121">Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` musi również zostać dostarczony.</span><span class="sxs-lookup"><span data-stu-id="35ddb-121">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="35ddb-122">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="35ddb-122">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="35ddb-123">Jedną z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="35ddb-123">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="35ddb-124">Ta wartość jest używana, gdy certyfikat usługi jest negocjowane do klienta.</span><span class="sxs-lookup"><span data-stu-id="35ddb-124">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="35ddb-125">Sprawdzanie poprawności jest wykonywane względem **zaufane osoby** są przechowywane w lokalizacji określonego magazynu.</span><span class="sxs-lookup"><span data-stu-id="35ddb-125">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="35ddb-126">customCertificateValidatorType Attribute</span><span class="sxs-lookup"><span data-stu-id="35ddb-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="35ddb-127">Wartość</span><span class="sxs-lookup"><span data-stu-id="35ddb-127">Value</span></span>|<span data-ttu-id="35ddb-128">Opis</span><span class="sxs-lookup"><span data-stu-id="35ddb-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="35ddb-129">String</span><span class="sxs-lookup"><span data-stu-id="35ddb-129">String</span></span>|<span data-ttu-id="35ddb-130">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="35ddb-130">Optional.</span></span> <span data-ttu-id="35ddb-131">Określa nazwę typu i zestawu i inne dane, używana do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="35ddb-131">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="35ddb-132">Co najmniej nazwy przestrzeni nazw i typ są wymagane.</span><span class="sxs-lookup"><span data-stu-id="35ddb-132">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="35ddb-133">Zawiera informacje opcjonalne: Nazwa zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="35ddb-133">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="35ddb-134">tryb certificateValidationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="35ddb-134">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="35ddb-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="35ddb-135">Value</span></span>|<span data-ttu-id="35ddb-136">Opis</span><span class="sxs-lookup"><span data-stu-id="35ddb-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="35ddb-137">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="35ddb-137">Enumeration</span></span>|<span data-ttu-id="35ddb-138">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="35ddb-138">Optional.</span></span> <span data-ttu-id="35ddb-139">Jedną z następujących wartości: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="35ddb-139">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="35ddb-140">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="35ddb-140">The default is `ChainTrust`.</span></span> <span data-ttu-id="35ddb-141">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="35ddb-141">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="35ddb-142">Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="35ddb-142">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="35ddb-143">revocationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="35ddb-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="35ddb-144">Wartość</span><span class="sxs-lookup"><span data-stu-id="35ddb-144">Value</span></span>|<span data-ttu-id="35ddb-145">Opis</span><span class="sxs-lookup"><span data-stu-id="35ddb-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="35ddb-146">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="35ddb-146">Enumeration</span></span>|<span data-ttu-id="35ddb-147">Jedną z następujących wartości: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="35ddb-147">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="35ddb-148">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="35ddb-148">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="35ddb-149">Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="35ddb-149">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="35ddb-150">trustedStoreLocation atrybutu</span><span class="sxs-lookup"><span data-stu-id="35ddb-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="35ddb-151">Wartość</span><span class="sxs-lookup"><span data-stu-id="35ddb-151">Value</span></span>|<span data-ttu-id="35ddb-152">Opis</span><span class="sxs-lookup"><span data-stu-id="35ddb-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="35ddb-153">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="35ddb-153">Enumeration</span></span>|<span data-ttu-id="35ddb-154">Jedną z następujących wartości: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="35ddb-154">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="35ddb-155">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="35ddb-155">The default is `CurrentUser`.</span></span> <span data-ttu-id="35ddb-156">Jeśli aplikacja kliencka jest uruchomiona w ramach konta systemowego, a następnie certyfikatu wynosi zazwyczaj `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="35ddb-156">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="35ddb-157">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, a następnie certyfikat znajduje się zwykle w `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="35ddb-157">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="35ddb-158">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="35ddb-158">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35ddb-159">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="35ddb-159">Child Elements</span></span>  
 <span data-ttu-id="35ddb-160">Brak.</span><span class="sxs-lookup"><span data-stu-id="35ddb-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35ddb-161">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="35ddb-161">Parent Elements</span></span>  
  
|<span data-ttu-id="35ddb-162">Element</span><span class="sxs-lookup"><span data-stu-id="35ddb-162">Element</span></span>|<span data-ttu-id="35ddb-163">Opis</span><span class="sxs-lookup"><span data-stu-id="35ddb-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35ddb-164">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="35ddb-164">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="35ddb-165">Określa poświadczenie używane do uwierzytelniania klienta do usługi elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="35ddb-165">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35ddb-166">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35ddb-166">Remarks</span></span>  
 <span data-ttu-id="35ddb-167">Ten element musi być skonfigurowany, jeśli wybrano opcję uwierzytelniania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="35ddb-167">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="35ddb-168">Dla kanałów danych wyjściowych, każdy komunikat jest podpisany przy użyciu certyfikatu dostarczonego przez [ \<certyfikatu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="35ddb-168">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="35ddb-169">Wszystkie komunikaty zanim dostarczane do aplikacji, są porównywane z poświadczeniami komunikatu przy użyciu modułu sprawdzania poprawności określonego przez `customCertificateValidatorType` atrybutu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="35ddb-169">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="35ddb-170">Moduł weryfikacji można zaakceptować lub odrzucić poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="35ddb-170">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35ddb-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="35ddb-171">Example</span></span>  
 <span data-ttu-id="35ddb-172">Poniższy kod ustawia tryb walidacji nadawcy wiadomości `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="35ddb-172">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="35ddb-173">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35ddb-173">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="35ddb-174">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="35ddb-174">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="35ddb-175">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="35ddb-175">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="35ddb-176">[Uwierzytelnianie wiadomości z kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="35ddb-176">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="35ddb-177">[Kanał elementu równorzędnego uwierzytelniania niestandardowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="35ddb-177">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="35ddb-178">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="35ddb-178">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
