---
title: '&lt;security&gt; w &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: f552e12e98e1fd760a9b36f6984a41a32f96533f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192528"
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a><span data-ttu-id="0b84d-102">&lt;security&gt; w &lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="0b84d-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="0b84d-103">Reprezentuje możliwości zabezpieczeń [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0b84d-103">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="0b84d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0b84d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0b84d-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="0b84d-105">\<bindings></span></span>  
<span data-ttu-id="0b84d-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0b84d-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="0b84d-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0b84d-107">\<binding></span></span>  
<span data-ttu-id="0b84d-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="0b84d-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b84d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b84d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b84d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0b84d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0b84d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0b84d-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b84d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0b84d-112">Attributes</span></span>  
  
|<span data-ttu-id="0b84d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0b84d-113">Attribute</span></span>|<span data-ttu-id="0b84d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0b84d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0b84d-115">tryb</span><span class="sxs-lookup"><span data-stu-id="0b84d-115">mode</span></span>|<span data-ttu-id="0b84d-116">— Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="0b84d-116">-   Optional.</span></span> <span data-ttu-id="0b84d-117">Określa typ zabezpieczeń, która jest stosowana.</span><span class="sxs-lookup"><span data-stu-id="0b84d-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="0b84d-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="0b84d-118">The default is `Message`.</span></span><br /><span data-ttu-id="0b84d-119">— Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="0b84d-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0b84d-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="0b84d-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="0b84d-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="0b84d-121">Value</span></span>|<span data-ttu-id="0b84d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="0b84d-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0b84d-123">Brak</span><span class="sxs-lookup"><span data-stu-id="0b84d-123">None</span></span>|<span data-ttu-id="0b84d-124">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="0b84d-124">Security is disabled.</span></span>|  
|<span data-ttu-id="0b84d-125">Transportu</span><span class="sxs-lookup"><span data-stu-id="0b84d-125">Transport</span></span>|<span data-ttu-id="0b84d-126">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0b84d-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="0b84d-127">Usługa musi zostać skonfigurowane przy użyciu certyfikatów SSL.</span><span class="sxs-lookup"><span data-stu-id="0b84d-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="0b84d-128">Komunikat jest całkowicie zabezpieczony przy użyciu protokołu HTTPS i jest uwierzytelniany przez klienta za pomocą certyfikatu SSL usługi.</span><span class="sxs-lookup"><span data-stu-id="0b84d-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="0b84d-129">Uwierzytelnianie klienta jest kontrolowany za pośrednictwem `ClientCredentials` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0b84d-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="0b84d-130">z [ \<transportu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0b84d-130">of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="0b84d-131">Komunikat</span><span class="sxs-lookup"><span data-stu-id="0b84d-131">Message</span></span>|<span data-ttu-id="0b84d-132">Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="0b84d-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="0b84d-133">Domyślnie treści protokołu SOAP jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="0b84d-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="0b84d-134">Ten tryb zapewnia szeroką gamę funkcji, takich jak tego, czy poświadczenia usługi są dostępne pod adresem klientem poza pasmem, pakiet algorytmów, używać oraz poziom ochrony do zastosowania do treści wiadomości za pomocą właściwości Security.Message.</span><span class="sxs-lookup"><span data-stu-id="0b84d-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="0b84d-135">Uwierzytelnianie klienta jest wykonywane raz na sesji i wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="0b84d-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="0b84d-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="0b84d-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="0b84d-137">W tym trybie HTTPS zapewnia integralność, poufność i uwierzytelniania serwera i zabezpieczenia wiadomości protokołu SOAP zapewnia uwierzytelnianie klienta.</span><span class="sxs-lookup"><span data-stu-id="0b84d-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="0b84d-138">Domyślnie uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="0b84d-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b84d-139">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0b84d-139">Child Elements</span></span>  
  
|<span data-ttu-id="0b84d-140">Element</span><span class="sxs-lookup"><span data-stu-id="0b84d-140">Element</span></span>|<span data-ttu-id="0b84d-141">Opis</span><span class="sxs-lookup"><span data-stu-id="0b84d-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b84d-142">\<transport ></span><span class="sxs-lookup"><span data-stu-id="0b84d-142">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|<span data-ttu-id="0b84d-143">Określa ustawienia zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="0b84d-143">Defines the transport security settings.</span></span> <span data-ttu-id="0b84d-144">Ten element odnosi się do <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="0b84d-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="0b84d-145">\<message></span><span class="sxs-lookup"><span data-stu-id="0b84d-145">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|<span data-ttu-id="0b84d-146">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0b84d-146">Defines the security settings for the message.</span></span> <span data-ttu-id="0b84d-147">Ten element odnosi się do <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="0b84d-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0b84d-148">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0b84d-148">Parent Elements</span></span>  
  
|<span data-ttu-id="0b84d-149">Element</span><span class="sxs-lookup"><span data-stu-id="0b84d-149">Element</span></span>|<span data-ttu-id="0b84d-150">Opis</span><span class="sxs-lookup"><span data-stu-id="0b84d-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b84d-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0b84d-151">\<wsHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="0b84d-152">Bezpiecznego powiązania aplikacji transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="0b84d-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b84d-153">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b84d-153">Remarks</span></span>  
 <span data-ttu-id="0b84d-154">Klasa WSHttpBinding zaprojektowano pod kątem współdziałanie z usługami, które implementują WS-\* specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="0b84d-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="0b84d-155">Zabezpieczenia transportu dla tego powiązania jest Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0b84d-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b84d-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b84d-156">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [<span data-ttu-id="0b84d-157">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="0b84d-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="0b84d-158">Powiązania</span><span class="sxs-lookup"><span data-stu-id="0b84d-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0b84d-159">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="0b84d-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0b84d-160">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="0b84d-160">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="0b84d-161">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0b84d-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
