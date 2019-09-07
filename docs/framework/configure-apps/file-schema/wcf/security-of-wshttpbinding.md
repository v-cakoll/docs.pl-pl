---
title: <security> dla <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: f7a4ef98637a7c966665fdd02ad26929bd4ba6ac
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399726"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="cf243-102">\<zabezpieczenia > \<WSHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="cf243-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="cf243-103">Reprezentuje możliwości [ \<zabezpieczeń > WSHttpBinding](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="cf243-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
<span data-ttu-id="cf243-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cf243-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cf243-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cf243-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cf243-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="cf243-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="cf243-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="cf243-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="cf243-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="cf243-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="cf243-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpieczeń**</span><span class="sxs-lookup"><span data-stu-id="cf243-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf243-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf243-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="String"
             defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             defaultRealm="String" />
  <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           establishSecurityContext="Boolean"
           negotiateServiceCredential="Boolean" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf243-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cf243-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cf243-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cf243-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf243-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cf243-113">Attributes</span></span>  
  
|<span data-ttu-id="cf243-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cf243-114">Attribute</span></span>|<span data-ttu-id="cf243-115">Opis</span><span class="sxs-lookup"><span data-stu-id="cf243-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf243-116">tryb</span><span class="sxs-lookup"><span data-stu-id="cf243-116">mode</span></span>|<span data-ttu-id="cf243-117">Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="cf243-117">-   Optional.</span></span> <span data-ttu-id="cf243-118">Określa typ stosowanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="cf243-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="cf243-119">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="cf243-119">The default is `Message`.</span></span><br /><span data-ttu-id="cf243-120">-Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="cf243-120">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="cf243-121">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="cf243-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="cf243-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="cf243-122">Value</span></span>|<span data-ttu-id="cf243-123">Opis</span><span class="sxs-lookup"><span data-stu-id="cf243-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cf243-124">Brak</span><span class="sxs-lookup"><span data-stu-id="cf243-124">None</span></span>|<span data-ttu-id="cf243-125">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="cf243-125">Security is disabled.</span></span>|  
|<span data-ttu-id="cf243-126">Transportu</span><span class="sxs-lookup"><span data-stu-id="cf243-126">Transport</span></span>|<span data-ttu-id="cf243-127">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cf243-127">Security is provided using HTTPS.</span></span> <span data-ttu-id="cf243-128">Usługa musi być skonfigurowana przy użyciu certyfikatów SSL.</span><span class="sxs-lookup"><span data-stu-id="cf243-128">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="cf243-129">Komunikat jest całkowicie zabezpieczony przy użyciu protokołu HTTPS i uwierzytelniany przez klienta przy użyciu certyfikatu SSL usługi.</span><span class="sxs-lookup"><span data-stu-id="cf243-129">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="cf243-130">Uwierzytelnianie klienta jest kontrolowane przez `ClientCredentials` atrybut.</span><span class="sxs-lookup"><span data-stu-id="cf243-130">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="cf243-131">> transportu. [ \<](transport-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="cf243-131">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="cf243-132">Message</span><span class="sxs-lookup"><span data-stu-id="cf243-132">Message</span></span>|<span data-ttu-id="cf243-133">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="cf243-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="cf243-134">Domyślnie treść protokołu SOAP jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="cf243-134">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="cf243-135">Ten tryb oferuje różne funkcje, takie jak to, czy poświadczenia usługi są dostępne na klientach poza pasmem, z którego korzysta pakiet algorytmów, oraz jaki poziom ochrony ma być stosowany do treści wiadomości za pomocą właściwości Security. Message.</span><span class="sxs-lookup"><span data-stu-id="cf243-135">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="cf243-136">Uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="cf243-136">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="cf243-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="cf243-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="cf243-138">W tym trybie protokół HTTPS zapewnia integralność, poufność i uwierzytelnianie serwera, a zabezpieczenia komunikatów protokołu SOAP zapewniają uwierzytelnianie klienta.</span><span class="sxs-lookup"><span data-stu-id="cf243-138">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="cf243-139">Domyślnie uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane przez czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="cf243-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf243-140">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cf243-140">Child Elements</span></span>  
  
|<span data-ttu-id="cf243-141">Element</span><span class="sxs-lookup"><span data-stu-id="cf243-141">Element</span></span>|<span data-ttu-id="cf243-142">Opis</span><span class="sxs-lookup"><span data-stu-id="cf243-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf243-143">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="cf243-143">\<transport></span></span>](transport-of-wshttpbinding.md)|<span data-ttu-id="cf243-144">Definiuje ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="cf243-144">Defines the transport security settings.</span></span> <span data-ttu-id="cf243-145">Ten element odnosi się do <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="cf243-145">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="cf243-146">\<message></span><span class="sxs-lookup"><span data-stu-id="cf243-146">\<message></span></span>](message-of-wshttpbinding.md)|<span data-ttu-id="cf243-147">Definiuje ustawienia zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="cf243-147">Defines the security settings for the message.</span></span> <span data-ttu-id="cf243-148">Ten element odnosi się do <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="cf243-148">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf243-149">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cf243-149">Parent Elements</span></span>  
  
|<span data-ttu-id="cf243-150">Element</span><span class="sxs-lookup"><span data-stu-id="cf243-150">Element</span></span>|<span data-ttu-id="cf243-151">Opis</span><span class="sxs-lookup"><span data-stu-id="cf243-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf243-152">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="cf243-152">\<wsHttpBinding></span></span>](wshttpbinding.md)|<span data-ttu-id="cf243-153">Bezpieczne powiązanie dla aplikacji transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="cf243-153">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf243-154">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf243-154">Remarks</span></span>  
 <span data-ttu-id="cf243-155">Klasa WSHttpBinding została zaprojektowana na potrzeby współdziałania z usługami, które implementują specyfikacje WS-\*.</span><span class="sxs-lookup"><span data-stu-id="cf243-155">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="cf243-156">Zabezpieczenia transportu dla tego powiązania są SSL (SSL) za pośrednictwem protokołu HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cf243-156">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf243-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf243-157">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="cf243-158">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="cf243-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cf243-159">Powiązania</span><span class="sxs-lookup"><span data-stu-id="cf243-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cf243-160">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="cf243-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cf243-161">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="cf243-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="cf243-162">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="cf243-162">\<binding></span></span>](../../../misc/binding.md)
