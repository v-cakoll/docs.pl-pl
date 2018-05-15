---
title: '&lt;security&gt; w &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 836e920ef7c95d4a7a2b752c2f76f29d8c880e7c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a><span data-ttu-id="11a58-102">&lt;security&gt; w &lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="11a58-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="11a58-103">Reprezentuje możliwości zabezpieczeń [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="11a58-103">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="11a58-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="11a58-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="11a58-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="11a58-105">\<bindings></span></span>  
<span data-ttu-id="11a58-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="11a58-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="11a58-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="11a58-107">\<binding></span></span>  
<span data-ttu-id="11a58-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="11a58-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a58-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="11a58-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">  
   <transport  
         clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string"   
      defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      defaultRealm="string" />  
   <message  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
       establishSecurityContext="Boolean"   
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11a58-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="11a58-110">Attributes and Elements</span></span>  
 <span data-ttu-id="11a58-111">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="11a58-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11a58-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="11a58-112">Attributes</span></span>  
  
|<span data-ttu-id="11a58-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="11a58-113">Attribute</span></span>|<span data-ttu-id="11a58-114">Opis</span><span class="sxs-lookup"><span data-stu-id="11a58-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11a58-115">tryb</span><span class="sxs-lookup"><span data-stu-id="11a58-115">mode</span></span>|<span data-ttu-id="11a58-116">-Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="11a58-116">-   Optional.</span></span> <span data-ttu-id="11a58-117">Określa typ zabezpieczeń, która została zastosowana.</span><span class="sxs-lookup"><span data-stu-id="11a58-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="11a58-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="11a58-118">The default is `Message`.</span></span><br /><span data-ttu-id="11a58-119">— Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="11a58-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="11a58-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="11a58-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="11a58-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="11a58-121">Value</span></span>|<span data-ttu-id="11a58-122">Opis</span><span class="sxs-lookup"><span data-stu-id="11a58-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="11a58-123">Brak</span><span class="sxs-lookup"><span data-stu-id="11a58-123">None</span></span>|<span data-ttu-id="11a58-124">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="11a58-124">Security is disabled.</span></span>|  
|<span data-ttu-id="11a58-125">Transportu</span><span class="sxs-lookup"><span data-stu-id="11a58-125">Transport</span></span>|<span data-ttu-id="11a58-126">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="11a58-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="11a58-127">Usługa musi być skonfigurowany z certyfikatów SSL.</span><span class="sxs-lookup"><span data-stu-id="11a58-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="11a58-128">Komunikat jest zabezpieczony całkowicie przy użyciu protokołu HTTPS i zostanie uwierzytelniony przez klienta przy użyciu certyfikatu SSL usługi.</span><span class="sxs-lookup"><span data-stu-id="11a58-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="11a58-129">Uwierzytelnianie klienta są kontrolowane poprzez `ClientCredentials` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="11a58-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="11a58-130">z [ \<transportu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="11a58-130">of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="11a58-131">Komunikat</span><span class="sxs-lookup"><span data-stu-id="11a58-131">Message</span></span>|<span data-ttu-id="11a58-132">Zabezpieczenia korzystanie z zabezpieczeń komunikatów SOAP.</span><span class="sxs-lookup"><span data-stu-id="11a58-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="11a58-133">Domyślnie treści protokołu SOAP jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="11a58-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="11a58-134">W tym trybie oferuje wiele funkcji, takich jak określa, czy poświadczenia usługi są dostępne pod adresem klientem poza pasmem, pakiet algorytmów do użycia, a poziom ochrony do zastosowania do treści komunikatu za pośrednictwem właściwości Security.Message.</span><span class="sxs-lookup"><span data-stu-id="11a58-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="11a58-135">Uwierzytelnianie klienta jest wykonywane raz na sesji i wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="11a58-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="11a58-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="11a58-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="11a58-137">W tym trybie HTTPS zapewnia integralność, poufność i uwierzytelnianie serwera i uwierzytelnianie klienta zawiera zabezpieczenia wiadomości SOAP.</span><span class="sxs-lookup"><span data-stu-id="11a58-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="11a58-138">Domyślnie uwierzytelnianie klienta jest wykonywane raz na sesji i wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="11a58-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11a58-139">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="11a58-139">Child Elements</span></span>  
  
|<span data-ttu-id="11a58-140">Element</span><span class="sxs-lookup"><span data-stu-id="11a58-140">Element</span></span>|<span data-ttu-id="11a58-141">Opis</span><span class="sxs-lookup"><span data-stu-id="11a58-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11a58-142">\<transport ></span><span class="sxs-lookup"><span data-stu-id="11a58-142">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|<span data-ttu-id="11a58-143">Określa ustawienia zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="11a58-143">Defines the transport security settings.</span></span> <span data-ttu-id="11a58-144">Ten element odpowiada <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="11a58-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="11a58-145">\<message></span><span class="sxs-lookup"><span data-stu-id="11a58-145">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|<span data-ttu-id="11a58-146">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="11a58-146">Defines the security settings for the message.</span></span> <span data-ttu-id="11a58-147">Ten element odpowiada <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="11a58-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11a58-148">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="11a58-148">Parent Elements</span></span>  
  
|<span data-ttu-id="11a58-149">Element</span><span class="sxs-lookup"><span data-stu-id="11a58-149">Element</span></span>|<span data-ttu-id="11a58-150">Opis</span><span class="sxs-lookup"><span data-stu-id="11a58-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11a58-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="11a58-151">\<wsHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="11a58-152">Bezpiecznego powiązania dla aplikacji transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="11a58-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11a58-153">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11a58-153">Remarks</span></span>  
 <span data-ttu-id="11a58-154">Klasy WSHttpBinding zaprojektowano pod kątem współpracy z usługami, które implementują WS-\* specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="11a58-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="11a58-155">Zabezpieczenia transportu dla tego powiązania jest Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="11a58-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a58-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11a58-156">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [<span data-ttu-id="11a58-157">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="11a58-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="11a58-158">Powiązania</span><span class="sxs-lookup"><span data-stu-id="11a58-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="11a58-159">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="11a58-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="11a58-160">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="11a58-160">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="11a58-161">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="11a58-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
