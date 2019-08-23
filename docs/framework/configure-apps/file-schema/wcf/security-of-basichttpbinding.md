---
title: <security> dla <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: f84f6c0f9988dd2d07377bf694286922db9d8364
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936802"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="353e0-102">\<zabezpieczenia > \<BasicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="353e0-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="353e0-103">Definiuje możliwości [ \<zabezpieczeń > BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="353e0-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="353e0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="353e0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="353e0-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="353e0-105">\<bindings></span></span>  
<span data-ttu-id="353e0-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="353e0-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="353e0-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="353e0-107">\<binding></span></span>  
<span data-ttu-id="353e0-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="353e0-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="353e0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="353e0-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="353e0-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="353e0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="353e0-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="353e0-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="353e0-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="353e0-112">Attributes</span></span>  
  
|<span data-ttu-id="353e0-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="353e0-113">Attribute</span></span>|<span data-ttu-id="353e0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="353e0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="353e0-115">tryb</span><span class="sxs-lookup"><span data-stu-id="353e0-115">mode</span></span>|<span data-ttu-id="353e0-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="353e0-116">Optional.</span></span> <span data-ttu-id="353e0-117">Określa typ używanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="353e0-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="353e0-118">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="353e0-118">The default is `None`.</span></span> <span data-ttu-id="353e0-119">Ten atrybut jest typu <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="353e0-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="353e0-120">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="353e0-120">mode Attribute</span></span>  
  
|<span data-ttu-id="353e0-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="353e0-121">Value</span></span>|<span data-ttu-id="353e0-122">Opis</span><span class="sxs-lookup"><span data-stu-id="353e0-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="353e0-123">Brak</span><span class="sxs-lookup"><span data-stu-id="353e0-123">None</span></span>|<span data-ttu-id="353e0-124">-Komunikaty nie są zabezpieczane podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="353e0-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="353e0-125">Transportu</span><span class="sxs-lookup"><span data-stu-id="353e0-125">Transport</span></span>|<span data-ttu-id="353e0-126">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="353e0-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="353e0-127">Komunikaty protokołu SOAP są zabezpieczone przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="353e0-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="353e0-128">Usługa jest uwierzytelniana na kliencie przy użyciu certyfikatu X. 509 usługi.</span><span class="sxs-lookup"><span data-stu-id="353e0-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="353e0-129">Klient jest uwierzytelniany przy użyciu dostarczonego obiekt ClientCredentialtype.</span><span class="sxs-lookup"><span data-stu-id="353e0-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="353e0-130">Zobacz transport [ >\<](transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="353e0-130">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="353e0-131">Message</span><span class="sxs-lookup"><span data-stu-id="353e0-131">Message</span></span>|<span data-ttu-id="353e0-132">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="353e0-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="353e0-133">Domyślnie treść jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="353e0-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="353e0-134">W przypadku tego powiązania system wymaga, aby certyfikat serwera został dostarczony do klienta poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="353e0-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="353e0-135">Jedyna prawidłowa `ClientCredentialType` dla tego powiązania to `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="353e0-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="353e0-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="353e0-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="353e0-137">Integralność, poufność i uwierzytelnianie serwera są udostępniane przez zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="353e0-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="353e0-138">Uwierzytelnianie klienta jest zapewniane przez zabezpieczenia komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="353e0-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="353e0-139">Ten tryb jest istotny, gdy użytkownik jest uwierzytelniany przy użyciu nazwy użytkownika/hasła i istnieje wdrożenie HTTP na potrzeby zabezpieczania transferu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="353e0-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="353e0-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="353e0-140">TransportCredentialOnly</span></span>|<span data-ttu-id="353e0-141">Ten tryb nie zapewnia integralności i poufności komunikatów.</span><span class="sxs-lookup"><span data-stu-id="353e0-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="353e0-142">Zapewnia uwierzytelnianie klienta oparte na protokole HTTP.</span><span class="sxs-lookup"><span data-stu-id="353e0-142">It provides http-based client authentication.</span></span> <span data-ttu-id="353e0-143">Ten tryb powinien być używany z zachowaniem ostrożności.</span><span class="sxs-lookup"><span data-stu-id="353e0-143">This mode should be used with caution.</span></span> <span data-ttu-id="353e0-144">Powinna być używana w środowiskach, w których zabezpieczenia transportu są dostarczane przy użyciu innych metod (takich jak IPSec) i tylko uwierzytelnianie klienta jest udostępniane przez infrastrukturę WCF.</span><span class="sxs-lookup"><span data-stu-id="353e0-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="353e0-145">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="353e0-145">Child Elements</span></span>  
  
|<span data-ttu-id="353e0-146">Element</span><span class="sxs-lookup"><span data-stu-id="353e0-146">Element</span></span>|<span data-ttu-id="353e0-147">Opis</span><span class="sxs-lookup"><span data-stu-id="353e0-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="353e0-148">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="353e0-148">\<transport></span></span>](transport-of-basichttpbinding.md)|<span data-ttu-id="353e0-149">Definiuje ustawienia zabezpieczeń transportu dla podstawowej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="353e0-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="353e0-150">Ten element odnosi się <xref:System.ServiceModel.HttpTransportSecurity>do.</span><span class="sxs-lookup"><span data-stu-id="353e0-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="353e0-151">\<message></span><span class="sxs-lookup"><span data-stu-id="353e0-151">\<message></span></span>](message-of-basichttpbinding.md)|<span data-ttu-id="353e0-152">Definiuje ustawienia zabezpieczeń wiadomości dla podstawowej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="353e0-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="353e0-153">Ten element odnosi się <xref:System.ServiceModel.BasicHttpMessageSecurity>do.</span><span class="sxs-lookup"><span data-stu-id="353e0-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="353e0-154">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="353e0-154">Parent Elements</span></span>  
  
|<span data-ttu-id="353e0-155">Element</span><span class="sxs-lookup"><span data-stu-id="353e0-155">Element</span></span>|<span data-ttu-id="353e0-156">Opis</span><span class="sxs-lookup"><span data-stu-id="353e0-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="353e0-157">powiązanie</span><span class="sxs-lookup"><span data-stu-id="353e0-157">binding</span></span>|<span data-ttu-id="353e0-158">Element Binding elementu [ \<BasicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="353e0-158">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="353e0-159">Uwagi</span><span class="sxs-lookup"><span data-stu-id="353e0-159">Remarks</span></span>  
 <span data-ttu-id="353e0-160">Domyślnie komunikat protokołu SOAP nie jest zabezpieczony i klient nie jest uwierzytelniany.</span><span class="sxs-lookup"><span data-stu-id="353e0-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="353e0-161">Ten element umożliwia skonfigurowanie dodatkowych ustawień zabezpieczeń dla `basicHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="353e0-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="353e0-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="353e0-162">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="353e0-163">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="353e0-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="353e0-164">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="353e0-164">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="353e0-165">Powiązania</span><span class="sxs-lookup"><span data-stu-id="353e0-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="353e0-166">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="353e0-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="353e0-167">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="353e0-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="353e0-168">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="353e0-168">\<binding></span></span>](../../../misc/binding.md)
