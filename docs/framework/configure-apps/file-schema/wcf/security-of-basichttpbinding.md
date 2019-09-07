---
title: <security> dla <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: 00a933892376c2dc9771752beaf76d4994554968
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399892"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="8ae4c-102">\<zabezpieczenia > \<BasicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="8ae4c-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="8ae4c-103">Definiuje możliwości [ \<zabezpieczeń > BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8ae4c-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
<span data-ttu-id="8ae4c-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8ae4c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8ae4c-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8ae4c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8ae4c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="8ae4c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="8ae4c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="8ae4c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="8ae4c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="8ae4c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="8ae4c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpieczeń**</span><span class="sxs-lookup"><span data-stu-id="8ae4c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ae4c-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ae4c-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ae4c-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8ae4c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8ae4c-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ae4c-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8ae4c-113">Attributes</span></span>  
  
|<span data-ttu-id="8ae4c-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8ae4c-114">Attribute</span></span>|<span data-ttu-id="8ae4c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="8ae4c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8ae4c-116">tryb</span><span class="sxs-lookup"><span data-stu-id="8ae4c-116">mode</span></span>|<span data-ttu-id="8ae4c-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-117">Optional.</span></span> <span data-ttu-id="8ae4c-118">Określa typ używanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="8ae4c-119">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-119">The default is `None`.</span></span> <span data-ttu-id="8ae4c-120">Ten atrybut jest typu <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="8ae4c-121">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="8ae4c-121">mode Attribute</span></span>  
  
|<span data-ttu-id="8ae4c-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="8ae4c-122">Value</span></span>|<span data-ttu-id="8ae4c-123">Opis</span><span class="sxs-lookup"><span data-stu-id="8ae4c-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8ae4c-124">Brak</span><span class="sxs-lookup"><span data-stu-id="8ae4c-124">None</span></span>|<span data-ttu-id="8ae4c-125">-Komunikaty nie są zabezpieczane podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-125">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="8ae4c-126">Transportu</span><span class="sxs-lookup"><span data-stu-id="8ae4c-126">Transport</span></span>|<span data-ttu-id="8ae4c-127">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="8ae4c-128">Komunikaty protokołu SOAP są zabezpieczone przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="8ae4c-129">Usługa jest uwierzytelniana na kliencie przy użyciu certyfikatu X. 509 usługi.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="8ae4c-130">Klient jest uwierzytelniany przy użyciu dostarczonego obiekt ClientCredentialtype.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-130">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="8ae4c-131">Zobacz transport [ >\<](transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8ae4c-131">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="8ae4c-132">Message</span><span class="sxs-lookup"><span data-stu-id="8ae4c-132">Message</span></span>|<span data-ttu-id="8ae4c-133">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="8ae4c-134">Domyślnie treść jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-134">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="8ae4c-135">W przypadku tego powiązania system wymaga, aby certyfikat serwera został dostarczony do klienta poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-135">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="8ae4c-136">Jedyna prawidłowa `ClientCredentialType` dla tego powiązania to `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-136">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="8ae4c-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="8ae4c-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="8ae4c-138">Integralność, poufność i uwierzytelnianie serwera są udostępniane przez zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-138">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="8ae4c-139">Uwierzytelnianie klienta jest zapewniane przez zabezpieczenia komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-139">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="8ae4c-140">Ten tryb jest istotny, gdy użytkownik jest uwierzytelniany przy użyciu nazwy użytkownika/hasła i istnieje wdrożenie HTTP na potrzeby zabezpieczania transferu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-140">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="8ae4c-141">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="8ae4c-141">TransportCredentialOnly</span></span>|<span data-ttu-id="8ae4c-142">Ten tryb nie zapewnia integralności i poufności komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-142">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="8ae4c-143">Zapewnia uwierzytelnianie klienta oparte na protokole HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-143">It provides http-based client authentication.</span></span> <span data-ttu-id="8ae4c-144">Ten tryb powinien być używany z zachowaniem ostrożności.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-144">This mode should be used with caution.</span></span> <span data-ttu-id="8ae4c-145">Powinna być używana w środowiskach, w których zabezpieczenia transportu są dostarczane przy użyciu innych metod (takich jak IPSec) i tylko uwierzytelnianie klienta jest udostępniane przez infrastrukturę WCF.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-145">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ae4c-146">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8ae4c-146">Child Elements</span></span>  
  
|<span data-ttu-id="8ae4c-147">Element</span><span class="sxs-lookup"><span data-stu-id="8ae4c-147">Element</span></span>|<span data-ttu-id="8ae4c-148">Opis</span><span class="sxs-lookup"><span data-stu-id="8ae4c-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ae4c-149">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="8ae4c-149">\<transport></span></span>](transport-of-basichttpbinding.md)|<span data-ttu-id="8ae4c-150">Definiuje ustawienia zabezpieczeń transportu dla podstawowej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-150">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="8ae4c-151">Ten element odnosi się <xref:System.ServiceModel.HttpTransportSecurity>do.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-151">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="8ae4c-152">\<message></span><span class="sxs-lookup"><span data-stu-id="8ae4c-152">\<message></span></span>](message-of-basichttpbinding.md)|<span data-ttu-id="8ae4c-153">Definiuje ustawienia zabezpieczeń wiadomości dla podstawowej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-153">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="8ae4c-154">Ten element odnosi się <xref:System.ServiceModel.BasicHttpMessageSecurity>do.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-154">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ae4c-155">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8ae4c-155">Parent Elements</span></span>  
  
|<span data-ttu-id="8ae4c-156">Element</span><span class="sxs-lookup"><span data-stu-id="8ae4c-156">Element</span></span>|<span data-ttu-id="8ae4c-157">Opis</span><span class="sxs-lookup"><span data-stu-id="8ae4c-157">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ae4c-158">powiązanie</span><span class="sxs-lookup"><span data-stu-id="8ae4c-158">binding</span></span>|<span data-ttu-id="8ae4c-159">Element Binding elementu [ \<BasicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8ae4c-159">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ae4c-160">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ae4c-160">Remarks</span></span>  
 <span data-ttu-id="8ae4c-161">Domyślnie komunikat protokołu SOAP nie jest zabezpieczony i klient nie jest uwierzytelniany.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-161">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="8ae4c-162">Ten element umożliwia skonfigurowanie dodatkowych ustawień zabezpieczeń dla `basicHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="8ae4c-162">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae4c-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ae4c-163">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="8ae4c-164">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="8ae4c-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8ae4c-165">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="8ae4c-165">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="8ae4c-166">Powiązania</span><span class="sxs-lookup"><span data-stu-id="8ae4c-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8ae4c-167">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="8ae4c-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8ae4c-168">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="8ae4c-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8ae4c-169">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="8ae4c-169">\<binding></span></span>](../../../misc/binding.md)
