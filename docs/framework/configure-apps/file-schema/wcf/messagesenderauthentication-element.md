---
title: <messageSenderAuthentication>, element
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: bab0e50d7feba3ea55d505be07cfa41427a5cbbc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397786"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="3d547-102">\<messageSenderAuthentication>, element</span><span class="sxs-lookup"><span data-stu-id="3d547-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="3d547-103">Określa opcje uwierzytelniania dla nadawców wiadomości równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="3d547-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="3d547-104">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci peer-to-](../../../wcf/feature-details/peer-to-peer-networking.md)peer.</span><span class="sxs-lookup"><span data-stu-id="3d547-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="3d547-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d547-105">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d547-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3d547-106">Attributes and Elements</span></span>  
 <span data-ttu-id="3d547-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3d547-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d547-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3d547-108">Attributes</span></span>  
  
|<span data-ttu-id="3d547-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3d547-109">Attribute</span></span>|<span data-ttu-id="3d547-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3d547-110">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="3d547-111">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="3d547-111">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="3d547-112">Ten atrybut musi być ustawiony `certificateValidationMode` , gdy jest ustawiony na `Custom` .</span><span class="sxs-lookup"><span data-stu-id="3d547-112">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="3d547-113">Określa jeden z trzech trybów używanych do walidacji poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="3d547-113">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="3d547-114">Jeśli jest ustawiona na `Custom` , `customCertificateValidator` należy również podać wartość.</span><span class="sxs-lookup"><span data-stu-id="3d547-114">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="3d547-115">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="3d547-115">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="3d547-116">Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="3d547-116">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="3d547-117">Ta wartość jest używana podczas negocjowania certyfikatu usługi z klientem.</span><span class="sxs-lookup"><span data-stu-id="3d547-117">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="3d547-118">Sprawdzanie poprawności jest wykonywane względem magazynu **osób zaufanych** w określonej lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="3d547-118">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="3d547-119">customCertificateValidatorType — atrybut</span><span class="sxs-lookup"><span data-stu-id="3d547-119">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="3d547-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="3d547-120">Value</span></span>|<span data-ttu-id="3d547-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3d547-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d547-122">String</span><span class="sxs-lookup"><span data-stu-id="3d547-122">String</span></span>|<span data-ttu-id="3d547-123">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3d547-123">Optional.</span></span> <span data-ttu-id="3d547-124">Określa nazwę typu i zestaw oraz inne dane używane do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="3d547-124">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="3d547-125">Minimalna nazwa przestrzeni nazw i typ są wymagane.</span><span class="sxs-lookup"><span data-stu-id="3d547-125">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="3d547-126">Informacje opcjonalne obejmują: nazwę zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="3d547-126">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="3d547-127">certificateValidationMode — atrybut</span><span class="sxs-lookup"><span data-stu-id="3d547-127">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="3d547-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="3d547-128">Value</span></span>|<span data-ttu-id="3d547-129">Opis</span><span class="sxs-lookup"><span data-stu-id="3d547-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d547-130">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3d547-130">Enumeration</span></span>|<span data-ttu-id="3d547-131">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3d547-131">Optional.</span></span> <span data-ttu-id="3d547-132">Jedna z następujących wartości: `None` , `PeerTrust` ,, `ChainTrust` `PeerOrChainTrust` , `Custom` .</span><span class="sxs-lookup"><span data-stu-id="3d547-132">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="3d547-133">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="3d547-133">The default is `ChainTrust`.</span></span> <span data-ttu-id="3d547-134">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="3d547-134">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="3d547-135">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="3d547-135">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="3d547-136">Atrybut odwołania</span><span class="sxs-lookup"><span data-stu-id="3d547-136">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="3d547-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="3d547-137">Value</span></span>|<span data-ttu-id="3d547-138">Opis</span><span class="sxs-lookup"><span data-stu-id="3d547-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d547-139">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3d547-139">Enumeration</span></span>|<span data-ttu-id="3d547-140">Jedna z następujących wartości: `NoCheck` , `Online` , `Offline` .</span><span class="sxs-lookup"><span data-stu-id="3d547-140">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="3d547-141">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="3d547-141">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="3d547-142">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="3d547-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="3d547-143">trustedStoreLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="3d547-143">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="3d547-144">Wartość</span><span class="sxs-lookup"><span data-stu-id="3d547-144">Value</span></span>|<span data-ttu-id="3d547-145">Opis</span><span class="sxs-lookup"><span data-stu-id="3d547-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d547-146">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3d547-146">Enumeration</span></span>|<span data-ttu-id="3d547-147">Jedna z następujących wartości: `LocalMachine` lub `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="3d547-147">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="3d547-148">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="3d547-148">The default is `CurrentUser`.</span></span> <span data-ttu-id="3d547-149">Jeśli aplikacja kliencka jest uruchomiona na koncie systemowym, zwykle jest to certyfikat `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="3d547-149">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="3d547-150">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, certyfikat zazwyczaj znajduje się w temacie `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="3d547-150">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="3d547-151">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="3d547-151">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d547-152">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3d547-152">Child Elements</span></span>  
 <span data-ttu-id="3d547-153">Brak.</span><span class="sxs-lookup"><span data-stu-id="3d547-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d547-154">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3d547-154">Parent Elements</span></span>  
  
|<span data-ttu-id="3d547-155">Element</span><span class="sxs-lookup"><span data-stu-id="3d547-155">Element</span></span>|<span data-ttu-id="3d547-156">Opis</span><span class="sxs-lookup"><span data-stu-id="3d547-156">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="3d547-157">Określa poświadczenie używane do uwierzytelniania klienta w usłudze równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="3d547-157">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d547-158">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d547-158">Remarks</span></span>  
 <span data-ttu-id="3d547-159">Ten element musi być skonfigurowany, jeśli wybrano opcję Uwierzytelnianie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3d547-159">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="3d547-160">W przypadku kanałów wyjściowych każdy komunikat jest podpisywany przy użyciu certyfikatu dostarczonego przez [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="3d547-160">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="3d547-161">Wszystkie komunikaty, przed dostarczeniem do aplikacji, są sprawdzane pod kątem poświadczeń komunikatów przy użyciu modułu walidacji określonego przez `customCertificateValidatorType` atrybut tego elementu.</span><span class="sxs-lookup"><span data-stu-id="3d547-161">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="3d547-162">Moduł sprawdzania poprawności może zaakceptować lub odrzucić poświadczenie.</span><span class="sxs-lookup"><span data-stu-id="3d547-162">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d547-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d547-163">Example</span></span>  
 <span data-ttu-id="3d547-164">Poniższy kod ustawia tryb walidacji nadawcy wiadomości `PeerOrChainTrust` .</span><span class="sxs-lookup"><span data-stu-id="3d547-164">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d547-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d547-165">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="3d547-166">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="3d547-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3d547-167">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="3d547-167">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="3d547-168">[Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3d547-168">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="3d547-169">[Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3d547-169">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="3d547-170">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="3d547-170">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
