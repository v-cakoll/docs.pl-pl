---
title: <security> dla <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 97c52fa4f062ed0c65d5b1a8ca47a1439ab04cf5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736481"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="6553d-102">> zabezpieczeń \<\<protokołu HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6553d-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="6553d-103">Definiuje możliwości zabezpieczeń [\<> protokołu HttpBinding](nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6553d-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

<span data-ttu-id="6553d-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6553d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6553d-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6553d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6553d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="6553d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6553d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<protokół HttpBinding**](nethttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="6553d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="6553d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="6553d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6553d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpieczenia >**</span><span class="sxs-lookup"><span data-stu-id="6553d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="6553d-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="6553d-110">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6553d-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6553d-111">Attributes and elements</span></span>

<span data-ttu-id="6553d-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6553d-112">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6553d-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6553d-113">Attributes</span></span>

|<span data-ttu-id="6553d-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6553d-114">Attribute</span></span>|<span data-ttu-id="6553d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6553d-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="6553d-116">tryb</span><span class="sxs-lookup"><span data-stu-id="6553d-116">mode</span></span>|<span data-ttu-id="6553d-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6553d-117">Optional.</span></span> <span data-ttu-id="6553d-118">Określa typ używanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="6553d-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="6553d-119">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="6553d-119">The default is `None`.</span></span> <span data-ttu-id="6553d-120">Ten atrybut jest typu <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="6553d-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="6553d-121">atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="6553d-121">mode attribute</span></span>

|<span data-ttu-id="6553d-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="6553d-122">Value</span></span>|<span data-ttu-id="6553d-123">Opis</span><span class="sxs-lookup"><span data-stu-id="6553d-123">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="6553d-124">Brak</span><span class="sxs-lookup"><span data-stu-id="6553d-124">None</span></span>|<span data-ttu-id="6553d-125">-Komunikaty nie są zabezpieczane podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="6553d-125">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="6553d-126">Transportu</span><span class="sxs-lookup"><span data-stu-id="6553d-126">Transport</span></span>|<span data-ttu-id="6553d-127">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6553d-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="6553d-128">Komunikaty protokołu SOAP są zabezpieczone przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6553d-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="6553d-129">Usługa jest uwierzytelniana na kliencie przy użyciu certyfikatu X. 509 usługi.</span><span class="sxs-lookup"><span data-stu-id="6553d-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="6553d-130">Klient jest uwierzytelniany przy użyciu dostarczonego obiekt ClientCredentialtype.</span><span class="sxs-lookup"><span data-stu-id="6553d-130">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="6553d-131">Komunikat</span><span class="sxs-lookup"><span data-stu-id="6553d-131">Message</span></span>|<span data-ttu-id="6553d-132">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="6553d-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="6553d-133">Domyślnie treść jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="6553d-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="6553d-134">W przypadku tego powiązania system wymaga, aby certyfikat serwera został dostarczony do klienta poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="6553d-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="6553d-135">Jedynym prawidłowym `ClientCredentialType` dla tego powiązania jest `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="6553d-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="6553d-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="6553d-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="6553d-137">Integralność, poufność i uwierzytelnianie serwera są udostępniane przez zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="6553d-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="6553d-138">Uwierzytelnianie klienta jest zapewniane przez zabezpieczenia komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="6553d-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="6553d-139">Ten tryb jest istotny, gdy użytkownik jest uwierzytelniany przy użyciu nazwy użytkownika/hasła i istnieje wdrożenie HTTP na potrzeby zabezpieczania transferu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6553d-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="6553d-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="6553d-140">TransportCredentialOnly</span></span>|<span data-ttu-id="6553d-141">Ten tryb nie zapewnia integralności i poufności komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6553d-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="6553d-142">Zapewnia uwierzytelnianie klienta oparte na protokole HTTP.</span><span class="sxs-lookup"><span data-stu-id="6553d-142">It provides http-based client authentication.</span></span> <span data-ttu-id="6553d-143">Ten tryb powinien być używany z zachowaniem ostrożności.</span><span class="sxs-lookup"><span data-stu-id="6553d-143">This mode should be used with caution.</span></span> <span data-ttu-id="6553d-144">Powinna być używana w środowiskach, w których zabezpieczenia transportu są dostarczane przy użyciu innych metod (takich jak IPSec) i tylko uwierzytelnianie klienta jest udostępniane przez infrastrukturę WCF.</span><span class="sxs-lookup"><span data-stu-id="6553d-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6553d-145">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6553d-145">Child elements</span></span>

|<span data-ttu-id="6553d-146">Element</span><span class="sxs-lookup"><span data-stu-id="6553d-146">Element</span></span>|<span data-ttu-id="6553d-147">Opis</span><span class="sxs-lookup"><span data-stu-id="6553d-147">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6553d-148">> transportu \<</span><span class="sxs-lookup"><span data-stu-id="6553d-148">\<transport></span></span>](transport-of-nethttpbinding.md)|<span data-ttu-id="6553d-149">Definiuje ustawienia zabezpieczeń transportu dla podstawowej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="6553d-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="6553d-150">Ten element odnosi się do <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="6553d-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[<span data-ttu-id="6553d-151">\<> komunikatów</span><span class="sxs-lookup"><span data-stu-id="6553d-151">\<message></span></span>](message-of-nethttpbinding.md)|<span data-ttu-id="6553d-152">Definiuje ustawienia zabezpieczeń wiadomości dla podstawowej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="6553d-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="6553d-153">Ten element odnosi się do <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="6553d-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6553d-154">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6553d-154">Parent elements</span></span>

|<span data-ttu-id="6553d-155">Element</span><span class="sxs-lookup"><span data-stu-id="6553d-155">Element</span></span>|<span data-ttu-id="6553d-156">Opis</span><span class="sxs-lookup"><span data-stu-id="6553d-156">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="6553d-157">powiązanie</span><span class="sxs-lookup"><span data-stu-id="6553d-157">binding</span></span>|<span data-ttu-id="6553d-158">Element powiązania [\<basicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6553d-158">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="6553d-159">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6553d-159">Remarks</span></span>

 <span data-ttu-id="6553d-160">Domyślnie komunikat protokołu SOAP nie jest zabezpieczony i klient nie jest uwierzytelniany.</span><span class="sxs-lookup"><span data-stu-id="6553d-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="6553d-161">Ten element umożliwia skonfigurowanie dodatkowych ustawień zabezpieczeń dla elementu `netHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="6553d-161">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="6553d-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6553d-162">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="6553d-163">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="6553d-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6553d-164">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="6553d-164">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="6553d-165">Powiązania</span><span class="sxs-lookup"><span data-stu-id="6553d-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6553d-166">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="6553d-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6553d-167">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="6553d-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6553d-168">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="6553d-168">\<binding></span></span>](bindings.md)
