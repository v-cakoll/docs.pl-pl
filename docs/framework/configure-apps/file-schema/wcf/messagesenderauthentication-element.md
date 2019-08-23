---
title: <messageSenderAuthentication>, element
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 1e63b6fa93e1abfa87c83da4b5d46f492c59b9bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931376"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="05b6f-102">\<messageSenderAuthentication, element ></span><span class="sxs-lookup"><span data-stu-id="05b6f-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="05b6f-103">Określa opcje uwierzytelniania dla nadawców wiadomości równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="05b6f-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="05b6f-104">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci peer-to-](../../../wcf/feature-details/peer-to-peer-networking.md)peer.</span><span class="sxs-lookup"><span data-stu-id="05b6f-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="05b6f-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="05b6f-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="05b6f-106">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="05b6f-106">\<behaviors></span></span>  
<span data-ttu-id="05b6f-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="05b6f-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="05b6f-108">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="05b6f-108">\<behavior></span></span>  
<span data-ttu-id="05b6f-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="05b6f-109">\<clientCredentials></span></span>  
<span data-ttu-id="05b6f-110">\<> elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="05b6f-110">\<peer></span></span>  
<span data-ttu-id="05b6f-111">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="05b6f-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05b6f-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="05b6f-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05b6f-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="05b6f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="05b6f-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="05b6f-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05b6f-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="05b6f-115">Attributes</span></span>  
  
|<span data-ttu-id="05b6f-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="05b6f-116">Attribute</span></span>|<span data-ttu-id="05b6f-117">Opis</span><span class="sxs-lookup"><span data-stu-id="05b6f-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="05b6f-118">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="05b6f-118">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="05b6f-119">Ten atrybut musi być ustawiony, `certificateValidationMode` gdy jest ustawiony `Custom`na.</span><span class="sxs-lookup"><span data-stu-id="05b6f-119">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="05b6f-120">Określa jeden z trzech trybów używanych do walidacji poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="05b6f-120">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="05b6f-121">Jeśli jest ustawiona `Custom`na, należy `customCertificateValidator` również podać wartość.</span><span class="sxs-lookup"><span data-stu-id="05b6f-121">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="05b6f-122">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="05b6f-122">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="05b6f-123">Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="05b6f-123">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="05b6f-124">Ta wartość jest używana podczas negocjowania certyfikatu usługi z klientem.</span><span class="sxs-lookup"><span data-stu-id="05b6f-124">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="05b6f-125">Sprawdzanie poprawności jest wykonywane względem magazynu **osób zaufanych** w określonej lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="05b6f-125">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="05b6f-126">customCertificateValidatorType — atrybut</span><span class="sxs-lookup"><span data-stu-id="05b6f-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="05b6f-127">Wartość</span><span class="sxs-lookup"><span data-stu-id="05b6f-127">Value</span></span>|<span data-ttu-id="05b6f-128">Opis</span><span class="sxs-lookup"><span data-stu-id="05b6f-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05b6f-129">String</span><span class="sxs-lookup"><span data-stu-id="05b6f-129">String</span></span>|<span data-ttu-id="05b6f-130">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="05b6f-130">Optional.</span></span> <span data-ttu-id="05b6f-131">Określa nazwę typu i zestaw oraz inne dane używane do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="05b6f-131">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="05b6f-132">Minimalna nazwa przestrzeni nazw i typ są wymagane.</span><span class="sxs-lookup"><span data-stu-id="05b6f-132">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="05b6f-133">Informacje opcjonalne obejmują: nazwę zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="05b6f-133">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="05b6f-134">certificateValidationMode — atrybut</span><span class="sxs-lookup"><span data-stu-id="05b6f-134">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="05b6f-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="05b6f-135">Value</span></span>|<span data-ttu-id="05b6f-136">Opis</span><span class="sxs-lookup"><span data-stu-id="05b6f-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05b6f-137">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="05b6f-137">Enumeration</span></span>|<span data-ttu-id="05b6f-138">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="05b6f-138">Optional.</span></span> <span data-ttu-id="05b6f-139">Jedna z następujących wartości: `None`, `PeerTrust`, `ChainTrust` `PeerOrChainTrust`,, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="05b6f-139">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="05b6f-140">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="05b6f-140">The default is `ChainTrust`.</span></span> <span data-ttu-id="05b6f-141">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="05b6f-141">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="05b6f-142">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="05b6f-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="05b6f-143">Atrybut odwołania</span><span class="sxs-lookup"><span data-stu-id="05b6f-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="05b6f-144">Wartość</span><span class="sxs-lookup"><span data-stu-id="05b6f-144">Value</span></span>|<span data-ttu-id="05b6f-145">Opis</span><span class="sxs-lookup"><span data-stu-id="05b6f-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05b6f-146">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="05b6f-146">Enumeration</span></span>|<span data-ttu-id="05b6f-147">Jedna z następujących wartości: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="05b6f-147">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="05b6f-148">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="05b6f-148">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="05b6f-149">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="05b6f-149">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="05b6f-150">trustedStoreLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="05b6f-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="05b6f-151">Wartość</span><span class="sxs-lookup"><span data-stu-id="05b6f-151">Value</span></span>|<span data-ttu-id="05b6f-152">Opis</span><span class="sxs-lookup"><span data-stu-id="05b6f-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05b6f-153">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="05b6f-153">Enumeration</span></span>|<span data-ttu-id="05b6f-154">Jedna z następujących wartości: `LocalMachine` lub. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="05b6f-154">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="05b6f-155">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="05b6f-155">The default is `CurrentUser`.</span></span> <span data-ttu-id="05b6f-156">Jeśli aplikacja kliencka jest uruchomiona na koncie systemowym, zwykle `LocalMachine`jest to certyfikat.</span><span class="sxs-lookup"><span data-stu-id="05b6f-156">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="05b6f-157">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, certyfikat zazwyczaj znajduje się w `CurrentUser`temacie.</span><span class="sxs-lookup"><span data-stu-id="05b6f-157">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="05b6f-158">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="05b6f-158">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05b6f-159">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="05b6f-159">Child Elements</span></span>  
 <span data-ttu-id="05b6f-160">Brak.</span><span class="sxs-lookup"><span data-stu-id="05b6f-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05b6f-161">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="05b6f-161">Parent Elements</span></span>  
  
|<span data-ttu-id="05b6f-162">Element</span><span class="sxs-lookup"><span data-stu-id="05b6f-162">Element</span></span>|<span data-ttu-id="05b6f-163">Opis</span><span class="sxs-lookup"><span data-stu-id="05b6f-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05b6f-164">\<> elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="05b6f-164">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="05b6f-165">Określa poświadczenie używane do uwierzytelniania klienta w usłudze równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="05b6f-165">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05b6f-166">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05b6f-166">Remarks</span></span>  
 <span data-ttu-id="05b6f-167">Ten element musi być skonfigurowany, jeśli wybrano opcję Uwierzytelnianie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="05b6f-167">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="05b6f-168">W przypadku kanałów wyjściowych każdy komunikat jest podpisywany przy użyciu certyfikatu dostarczonego przez [ \<> certyfikatów](certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="05b6f-168">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="05b6f-169">Wszystkie komunikaty, przed dostarczeniem do aplikacji, są sprawdzane pod kątem poświadczeń komunikatów przy użyciu modułu walidacji `customCertificateValidatorType` określonego przez atrybut tego elementu.</span><span class="sxs-lookup"><span data-stu-id="05b6f-169">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="05b6f-170">Moduł sprawdzania poprawności może zaakceptować lub odrzucić poświadczenie.</span><span class="sxs-lookup"><span data-stu-id="05b6f-170">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05b6f-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="05b6f-171">Example</span></span>  
 <span data-ttu-id="05b6f-172">Poniższy kod ustawia tryb `PeerOrChainTrust`walidacji nadawcy wiadomości.</span><span class="sxs-lookup"><span data-stu-id="05b6f-172">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05b6f-173">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05b6f-173">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="05b6f-174">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="05b6f-174">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="05b6f-175">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="05b6f-175">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="05b6f-176">[Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="05b6f-176">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="05b6f-177">[Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="05b6f-177">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="05b6f-178">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="05b6f-178">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
