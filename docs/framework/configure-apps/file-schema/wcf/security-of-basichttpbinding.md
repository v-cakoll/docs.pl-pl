---
title: <security> dla <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: c8e4f2d000a155eecd2a6c7faaaf4af525b24ca3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738713"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="322d5-102">\<> zabezpieczeń \<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="322d5-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="322d5-103">Definiuje możliwości zabezpieczeń [\<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="322d5-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
<span data-ttu-id="322d5-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="322d5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="322d5-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="322d5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="322d5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="322d5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="322d5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<BasicHttpBinding**](basichttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="322d5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="322d5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="322d5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="322d5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpieczenia >**</span><span class="sxs-lookup"><span data-stu-id="322d5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="322d5-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="322d5-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="322d5-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="322d5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="322d5-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="322d5-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="322d5-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="322d5-113">Attributes</span></span>  
  
|<span data-ttu-id="322d5-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="322d5-114">Attribute</span></span>|<span data-ttu-id="322d5-115">Opis</span><span class="sxs-lookup"><span data-stu-id="322d5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="322d5-116">tryb</span><span class="sxs-lookup"><span data-stu-id="322d5-116">mode</span></span>|<span data-ttu-id="322d5-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="322d5-117">Optional.</span></span> <span data-ttu-id="322d5-118">Określa typ używanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="322d5-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="322d5-119">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="322d5-119">The default is `None`.</span></span> <span data-ttu-id="322d5-120">Ten atrybut jest typu <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="322d5-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="322d5-121">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="322d5-121">mode Attribute</span></span>  
  
|<span data-ttu-id="322d5-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="322d5-122">Value</span></span>|<span data-ttu-id="322d5-123">Opis</span><span class="sxs-lookup"><span data-stu-id="322d5-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="322d5-124">Brak</span><span class="sxs-lookup"><span data-stu-id="322d5-124">None</span></span>|<span data-ttu-id="322d5-125">-Komunikaty nie są zabezpieczane podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="322d5-125">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="322d5-126">Transportu</span><span class="sxs-lookup"><span data-stu-id="322d5-126">Transport</span></span>|<span data-ttu-id="322d5-127">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="322d5-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="322d5-128">Komunikaty protokołu SOAP są zabezpieczone przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="322d5-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="322d5-129">Usługa jest uwierzytelniana na kliencie przy użyciu certyfikatu X. 509 usługi.</span><span class="sxs-lookup"><span data-stu-id="322d5-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="322d5-130">Klient jest uwierzytelniany przy użyciu dostarczonego obiekt ClientCredentialtype.</span><span class="sxs-lookup"><span data-stu-id="322d5-130">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="322d5-131">Zobacz [\<transport](transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="322d5-131">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="322d5-132">Komunikat</span><span class="sxs-lookup"><span data-stu-id="322d5-132">Message</span></span>|<span data-ttu-id="322d5-133">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="322d5-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="322d5-134">Domyślnie treść jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="322d5-134">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="322d5-135">W przypadku tego powiązania system wymaga, aby certyfikat serwera został dostarczony do klienta poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="322d5-135">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="322d5-136">Jedynym prawidłowym `ClientCredentialType` dla tego powiązania jest `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="322d5-136">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="322d5-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="322d5-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="322d5-138">Integralność, poufność i uwierzytelnianie serwera są udostępniane przez zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="322d5-138">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="322d5-139">Uwierzytelnianie klienta jest zapewniane przez zabezpieczenia komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="322d5-139">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="322d5-140">Ten tryb jest istotny, gdy użytkownik jest uwierzytelniany przy użyciu nazwy użytkownika/hasła i istnieje wdrożenie HTTP na potrzeby zabezpieczania transferu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="322d5-140">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="322d5-141">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="322d5-141">TransportCredentialOnly</span></span>|<span data-ttu-id="322d5-142">Ten tryb nie zapewnia integralności i poufności komunikatów.</span><span class="sxs-lookup"><span data-stu-id="322d5-142">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="322d5-143">Zapewnia uwierzytelnianie klienta oparte na protokole HTTP.</span><span class="sxs-lookup"><span data-stu-id="322d5-143">It provides http-based client authentication.</span></span> <span data-ttu-id="322d5-144">Ten tryb powinien być używany z zachowaniem ostrożności.</span><span class="sxs-lookup"><span data-stu-id="322d5-144">This mode should be used with caution.</span></span> <span data-ttu-id="322d5-145">Powinna być używana w środowiskach, w których zabezpieczenia transportu są dostarczane przy użyciu innych metod (takich jak IPSec) i tylko uwierzytelnianie klienta jest udostępniane przez infrastrukturę WCF.</span><span class="sxs-lookup"><span data-stu-id="322d5-145">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="322d5-146">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="322d5-146">Child Elements</span></span>  
  
|<span data-ttu-id="322d5-147">Element</span><span class="sxs-lookup"><span data-stu-id="322d5-147">Element</span></span>|<span data-ttu-id="322d5-148">Opis</span><span class="sxs-lookup"><span data-stu-id="322d5-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="322d5-149">> transportu \<</span><span class="sxs-lookup"><span data-stu-id="322d5-149">\<transport></span></span>](transport-of-basichttpbinding.md)|<span data-ttu-id="322d5-150">Definiuje ustawienia zabezpieczeń transportu dla podstawowej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="322d5-150">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="322d5-151">Ten element odnosi się do <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="322d5-151">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="322d5-152">\<> komunikatów</span><span class="sxs-lookup"><span data-stu-id="322d5-152">\<message></span></span>](message-of-basichttpbinding.md)|<span data-ttu-id="322d5-153">Definiuje ustawienia zabezpieczeń wiadomości dla podstawowej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="322d5-153">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="322d5-154">Ten element odnosi się do <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="322d5-154">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="322d5-155">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="322d5-155">Parent Elements</span></span>  
  
|<span data-ttu-id="322d5-156">Element</span><span class="sxs-lookup"><span data-stu-id="322d5-156">Element</span></span>|<span data-ttu-id="322d5-157">Opis</span><span class="sxs-lookup"><span data-stu-id="322d5-157">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="322d5-158">powiązanie</span><span class="sxs-lookup"><span data-stu-id="322d5-158">binding</span></span>|<span data-ttu-id="322d5-159">Element powiązania [\<basicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="322d5-159">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="322d5-160">Uwagi</span><span class="sxs-lookup"><span data-stu-id="322d5-160">Remarks</span></span>  
 <span data-ttu-id="322d5-161">Domyślnie komunikat protokołu SOAP nie jest zabezpieczony i klient nie jest uwierzytelniany.</span><span class="sxs-lookup"><span data-stu-id="322d5-161">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="322d5-162">Ten element umożliwia skonfigurowanie dodatkowych ustawień zabezpieczeń dla elementu `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="322d5-162">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="322d5-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="322d5-163">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="322d5-164">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="322d5-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="322d5-165">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="322d5-165">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="322d5-166">Powiązania</span><span class="sxs-lookup"><span data-stu-id="322d5-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="322d5-167">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="322d5-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="322d5-168">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="322d5-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="322d5-169">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="322d5-169">\<binding></span></span>](bindings.md)
