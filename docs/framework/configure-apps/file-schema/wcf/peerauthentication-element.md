---
title: <peerAuthentication> Element
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4c29c84a2cc56a890c8273e410ba31b5f3900732
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400085"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="8f8a4-102">\<peerAuthentication> Element</span><span class="sxs-lookup"><span data-stu-id="8f8a4-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="8f8a4-103">Określa opcje uwierzytelniania dla klientów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="8f8a4-104">Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci peer-to-](../../../wcf/feature-details/peer-to-peer-networking.md)peer.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="8f8a4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f8a4-105">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f8a4-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8f8a4-106">Attributes and Elements</span></span>  
 <span data-ttu-id="8f8a4-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f8a4-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8f8a4-108">Attributes</span></span>  
  
|<span data-ttu-id="8f8a4-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8f8a4-109">Attribute</span></span>|<span data-ttu-id="8f8a4-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8f8a4-110">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="8f8a4-111">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-111">Optional string.</span></span> <span data-ttu-id="8f8a4-112">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="8f8a4-113">Ten atrybut musi być ustawiony `certificateValidationMode` , gdy jest ustawiony na `Custom` .</span><span class="sxs-lookup"><span data-stu-id="8f8a4-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="8f8a4-114">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-114">Optional enumeration.</span></span> <span data-ttu-id="8f8a4-115">Określa jeden z trzech trybów używanych do walidacji poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-115">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="8f8a4-116">Jeśli jest ustawiona na `Custom` , `customCertificateValidator` należy również podać wartość.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-116">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="8f8a4-117">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-117">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="8f8a4-118">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-118">Optional enumeration.</span></span> <span data-ttu-id="8f8a4-119">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="8f8a4-119">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="8f8a4-120">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-120">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="8f8a4-121">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-121">Optional enumeration.</span></span> <span data-ttu-id="8f8a4-122">Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="8f8a4-122">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="8f8a4-123">Ta wartość jest używana podczas negocjowania certyfikatu usługi z klientem.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-123">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="8f8a4-124">Sprawdzanie poprawności jest wykonywane względem magazynu **osób zaufanych** w określonej lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-124">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="8f8a4-125">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-125">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="8f8a4-126">customCertificateValidatorType — atrybut</span><span class="sxs-lookup"><span data-stu-id="8f8a4-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="8f8a4-127">Wartość</span><span class="sxs-lookup"><span data-stu-id="8f8a4-127">Value</span></span>|<span data-ttu-id="8f8a4-128">Opis</span><span class="sxs-lookup"><span data-stu-id="8f8a4-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f8a4-129">String</span><span class="sxs-lookup"><span data-stu-id="8f8a4-129">String</span></span>|<span data-ttu-id="8f8a4-130">Określa nazwę typu i zestaw oraz inne dane używane do znajdowania typu.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-130">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="8f8a4-131">Minimalna nazwa przestrzeni nazw i typ są wymagane.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-131">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="8f8a4-132">Informacje opcjonalne obejmują: nazwę zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-132">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="8f8a4-133">certificateValidationMode — atrybut</span><span class="sxs-lookup"><span data-stu-id="8f8a4-133">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="8f8a4-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="8f8a4-134">Value</span></span>|<span data-ttu-id="8f8a4-135">Opis</span><span class="sxs-lookup"><span data-stu-id="8f8a4-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f8a4-136">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8f8a4-136">Enumeration</span></span>|<span data-ttu-id="8f8a4-137">Jedna z następujących wartości: `None` , `PeerTrust` ,, `ChainTrust` `PeerOrChainTrust` , `Custom` .</span><span class="sxs-lookup"><span data-stu-id="8f8a4-137">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="8f8a4-138">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-138">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="8f8a4-139">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8f8a4-139">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="8f8a4-140">Atrybut odwołania</span><span class="sxs-lookup"><span data-stu-id="8f8a4-140">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="8f8a4-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="8f8a4-141">Value</span></span>|<span data-ttu-id="8f8a4-142">Opis</span><span class="sxs-lookup"><span data-stu-id="8f8a4-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f8a4-143">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8f8a4-143">Enumeration</span></span>|<span data-ttu-id="8f8a4-144">Jedna z następujących wartości: `NoCheck` , `Online` , `Offline` .</span><span class="sxs-lookup"><span data-stu-id="8f8a4-144">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="8f8a4-145">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-145">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="8f8a4-146">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8f8a4-146">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="8f8a4-147">trustedStoreLocation — atrybut</span><span class="sxs-lookup"><span data-stu-id="8f8a4-147">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="8f8a4-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="8f8a4-148">Value</span></span>|<span data-ttu-id="8f8a4-149">Opis</span><span class="sxs-lookup"><span data-stu-id="8f8a4-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f8a4-150">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8f8a4-150">Enumeration</span></span>|<span data-ttu-id="8f8a4-151">Jedna z następujących wartości: `LocalMachine` lub `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="8f8a4-151">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="8f8a4-152">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-152">The default is `CurrentUser`.</span></span> <span data-ttu-id="8f8a4-153">Jeśli aplikacja kliencka jest uruchomiona na koncie systemowym, zwykle jest to certyfikat `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="8f8a4-153">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="8f8a4-154">Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, certyfikat zazwyczaj znajduje się w temacie `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="8f8a4-154">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f8a4-155">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8f8a4-155">Child Elements</span></span>  
 <span data-ttu-id="8f8a4-156">Brak.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f8a4-157">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8f8a4-157">Parent Elements</span></span>  
  
|<span data-ttu-id="8f8a4-158">Element</span><span class="sxs-lookup"><span data-stu-id="8f8a4-158">Element</span></span>|<span data-ttu-id="8f8a4-159">Opis</span><span class="sxs-lookup"><span data-stu-id="8f8a4-159">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="8f8a4-160">Określa poświadczenie używane do uwierzytelniania klienta w usłudze równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-160">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f8a4-161">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f8a4-161">Remarks</span></span>  
 <span data-ttu-id="8f8a4-162">`<authentication>`Element odnosi się do <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> klasy.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-162">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="8f8a4-163">Ten element określa moduł sprawdzania poprawności, który jest wywoływany podczas uwierzytelniania sąsiada-sąsiada w sieci.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-163">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="8f8a4-164">Gdy nowy element równorzędny podejmie próbę nawiązania połączenia sąsiada, przekazuje własne poświadczenie do elementu równorzędnego odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-164">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="8f8a4-165">Moduł sprawdzania poprawności jest wywoływany w celu zweryfikowania poświadczeń strony zdalnej.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-165">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="8f8a4-166">Za każdym razem, gdy połączenie równorzędne jest nawiązane w sieci, oba elementy równorzędne są uwierzytelniane wzajemnie, co oznacza, że są wywoływane walidacje na obu końcach.</span><span class="sxs-lookup"><span data-stu-id="8f8a4-166">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f8a4-167">Przykład</span><span class="sxs-lookup"><span data-stu-id="8f8a4-167">Example</span></span>  
 <span data-ttu-id="8f8a4-168">Poniższy kod ustawia tryb walidacji certyfikatu `PeerOrChainTrust` .</span><span class="sxs-lookup"><span data-stu-id="8f8a4-168">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8f8a4-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f8a4-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="8f8a4-170">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="8f8a4-170">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="8f8a4-171">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="8f8a4-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="8f8a4-172">[Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="8f8a4-172">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="8f8a4-173">[Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="8f8a4-173">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="8f8a4-174">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="8f8a4-174">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
