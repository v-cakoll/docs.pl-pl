---
title: <messageSenderAuthentication>, element
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: bab0e50d7feba3ea55d505be07cfa41427a5cbbc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397786"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="a334a-102">\<messageSenderAuthentication, element ></span><span class="sxs-lookup"><span data-stu-id="a334a-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="a334a-103">Określa opcje uwierzytelniania dla nadawców wiadomości równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="a334a-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="a334a-104">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci peer-to-](../../../wcf/feature-details/peer-to-peer-networking.md)peer.</span><span class="sxs-lookup"><span data-stu-id="a334a-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
<span data-ttu-id="a334a-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a334a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a334a-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a334a-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a334a-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a334a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a334a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a334a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="a334a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a334a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="a334a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Obiekt clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="a334a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="a334a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> elementów równorzędnych**](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="a334a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="a334a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<messageSenderAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="a334a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a334a-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="a334a-113">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a334a-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a334a-114">Attributes and Elements</span></span>  
 <span data-ttu-id="a334a-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a334a-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a334a-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a334a-116">Attributes</span></span>  
  
|<span data-ttu-id="a334a-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a334a-117">Attribute</span></span>|<span data-ttu-id="a334a-118">Opis</span><span class="sxs-lookup"><span data-stu-id="a334a-118">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="a334a-119">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="a334a-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="a334a-120">Ten atrybut musi być ustawiony, `certificateValidationMode` gdy jest ustawiony `Custom`na.</span><span class="sxs-lookup"><span data-stu-id="a334a-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="a334a-121">Określa jeden z trzech trybów używanych do walidacji poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="a334a-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="a334a-122">Jeśli jest ustawiona `Custom`na, należy `customCertificateValidator` również podać wartość.</span><span class="sxs-lookup"><span data-stu-id="a334a-122">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="a334a-123">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="a334a-123">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="a334a-124">Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="a334a-124">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="a334a-125">Ta wartość jest używana podczas negocjowania certyfikatu usługi z klientem.</span><span class="sxs-lookup"><span data-stu-id="a334a-125">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="a334a-126">Sprawdzanie poprawności jest wykonywane względem magazynu **osób zaufanych** w określonej lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="a334a-126">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="a334a-127">customCertificateValidatorType — atrybut</span><span class="sxs-lookup"><span data-stu-id="a334a-127">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="a334a-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="a334a-128">Value</span></span>|<span data-ttu-id="a334a-129">Opis</span><span class="sxs-lookup"><span data-stu-id="a334a-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a334a-130">String</span><span class="sxs-lookup"><span data-stu-id="a334a-130">String</span></span>|<span data-ttu-id="a334a-131">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a334a-131">Optional.</span></span> <span data-ttu-id="a334a-132">Określa nazwę typu i zestaw oraz inne dane używane do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="a334a-132">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="a334a-133">Minimalna nazwa przestrzeni nazw i typ są wymagane.</span><span class="sxs-lookup"><span data-stu-id="a334a-133">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="a334a-134">Informacje opcjonalne obejmują: nazwę zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="a334a-134">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="a334a-135">certificateValidationMode — atrybut</span><span class="sxs-lookup"><span data-stu-id="a334a-135">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="a334a-136">Wartość</span><span class="sxs-lookup"><span data-stu-id="a334a-136">Value</span></span>|<span data-ttu-id="a334a-137">Opis</span><span class="sxs-lookup"><span data-stu-id="a334a-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a334a-138">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a334a-138">Enumeration</span></span>|<span data-ttu-id="a334a-139">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a334a-139">Optional.</span></span> <span data-ttu-id="a334a-140">Jedna z następujących wartości: `None`, `PeerTrust`, `ChainTrust` `PeerOrChainTrust`,, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="a334a-140">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="a334a-141">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="a334a-141">The default is `ChainTrust`.</span></span> <span data-ttu-id="a334a-142">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="a334a-142">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="a334a-143">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a334a-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="a334a-144">Atrybut odwołania</span><span class="sxs-lookup"><span data-stu-id="a334a-144">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="a334a-145">Wartość</span><span class="sxs-lookup"><span data-stu-id="a334a-145">Value</span></span>|<span data-ttu-id="a334a-146">Opis</span><span class="sxs-lookup"><span data-stu-id="a334a-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a334a-147">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a334a-147">Enumeration</span></span>|<span data-ttu-id="a334a-148">Jedna z następujących wartości: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="a334a-148">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="a334a-149">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="a334a-149">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="a334a-150">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a334a-150">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="a334a-151">trustedStoreLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="a334a-151">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="a334a-152">Wartość</span><span class="sxs-lookup"><span data-stu-id="a334a-152">Value</span></span>|<span data-ttu-id="a334a-153">Opis</span><span class="sxs-lookup"><span data-stu-id="a334a-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a334a-154">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a334a-154">Enumeration</span></span>|<span data-ttu-id="a334a-155">Jedna z następujących wartości: `LocalMachine` lub. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="a334a-155">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="a334a-156">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="a334a-156">The default is `CurrentUser`.</span></span> <span data-ttu-id="a334a-157">Jeśli aplikacja kliencka jest uruchomiona na koncie systemowym, zwykle `LocalMachine`jest to certyfikat.</span><span class="sxs-lookup"><span data-stu-id="a334a-157">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="a334a-158">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, certyfikat zazwyczaj znajduje się w `CurrentUser`temacie.</span><span class="sxs-lookup"><span data-stu-id="a334a-158">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="a334a-159">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="a334a-159">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a334a-160">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a334a-160">Child Elements</span></span>  
 <span data-ttu-id="a334a-161">Brak.</span><span class="sxs-lookup"><span data-stu-id="a334a-161">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a334a-162">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a334a-162">Parent Elements</span></span>  
  
|<span data-ttu-id="a334a-163">Element</span><span class="sxs-lookup"><span data-stu-id="a334a-163">Element</span></span>|<span data-ttu-id="a334a-164">Opis</span><span class="sxs-lookup"><span data-stu-id="a334a-164">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a334a-165">\<> elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="a334a-165">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="a334a-166">Określa poświadczenie używane do uwierzytelniania klienta w usłudze równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="a334a-166">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a334a-167">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a334a-167">Remarks</span></span>  
 <span data-ttu-id="a334a-168">Ten element musi być skonfigurowany, jeśli wybrano opcję Uwierzytelnianie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a334a-168">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="a334a-169">W przypadku kanałów wyjściowych każdy komunikat jest podpisywany przy użyciu certyfikatu dostarczonego przez [ \<> certyfikatów](certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="a334a-169">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="a334a-170">Wszystkie komunikaty, przed dostarczeniem do aplikacji, są sprawdzane pod kątem poświadczeń komunikatów przy użyciu modułu walidacji `customCertificateValidatorType` określonego przez atrybut tego elementu.</span><span class="sxs-lookup"><span data-stu-id="a334a-170">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="a334a-171">Moduł sprawdzania poprawności może zaakceptować lub odrzucić poświadczenie.</span><span class="sxs-lookup"><span data-stu-id="a334a-171">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a334a-172">Przykład</span><span class="sxs-lookup"><span data-stu-id="a334a-172">Example</span></span>  
 <span data-ttu-id="a334a-173">Poniższy kod ustawia tryb `PeerOrChainTrust`walidacji nadawcy wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a334a-173">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a334a-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a334a-174">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="a334a-175">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="a334a-175">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a334a-176">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="a334a-176">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="a334a-177">[Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a334a-177">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="a334a-178">[Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a334a-178">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="a334a-179">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="a334a-179">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
