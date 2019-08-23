---
title: <security> dla <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: e627a63221d0013c89495d7ff81e02047a03df89
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936507"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="d0294-102">\<zabezpieczenia > \<WSHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d0294-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="d0294-103">Reprezentuje możliwości [ \<zabezpieczeń > WSHttpBinding](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d0294-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="d0294-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d0294-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d0294-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="d0294-105">\<bindings></span></span>  
<span data-ttu-id="d0294-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d0294-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="d0294-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="d0294-107">\<binding></span></span>  
<span data-ttu-id="d0294-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d0294-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0294-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0294-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0294-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d0294-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d0294-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d0294-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0294-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d0294-112">Attributes</span></span>  
  
|<span data-ttu-id="d0294-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d0294-113">Attribute</span></span>|<span data-ttu-id="d0294-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d0294-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0294-115">tryb</span><span class="sxs-lookup"><span data-stu-id="d0294-115">mode</span></span>|<span data-ttu-id="d0294-116">Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="d0294-116">-   Optional.</span></span> <span data-ttu-id="d0294-117">Określa typ stosowanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="d0294-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="d0294-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="d0294-118">The default is `Message`.</span></span><br /><span data-ttu-id="d0294-119">-Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d0294-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d0294-120">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="d0294-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="d0294-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="d0294-121">Value</span></span>|<span data-ttu-id="d0294-122">Opis</span><span class="sxs-lookup"><span data-stu-id="d0294-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d0294-123">Brak</span><span class="sxs-lookup"><span data-stu-id="d0294-123">None</span></span>|<span data-ttu-id="d0294-124">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="d0294-124">Security is disabled.</span></span>|  
|<span data-ttu-id="d0294-125">Transportu</span><span class="sxs-lookup"><span data-stu-id="d0294-125">Transport</span></span>|<span data-ttu-id="d0294-126">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d0294-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="d0294-127">Usługa musi być skonfigurowana przy użyciu certyfikatów SSL.</span><span class="sxs-lookup"><span data-stu-id="d0294-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="d0294-128">Komunikat jest całkowicie zabezpieczony przy użyciu protokołu HTTPS i uwierzytelniany przez klienta przy użyciu certyfikatu SSL usługi.</span><span class="sxs-lookup"><span data-stu-id="d0294-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="d0294-129">Uwierzytelnianie klienta jest kontrolowane przez `ClientCredentials` atrybut.</span><span class="sxs-lookup"><span data-stu-id="d0294-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="d0294-130">> transportu. [ \<](transport-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d0294-130">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="d0294-131">Message</span><span class="sxs-lookup"><span data-stu-id="d0294-131">Message</span></span>|<span data-ttu-id="d0294-132">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d0294-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="d0294-133">Domyślnie treść protokołu SOAP jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="d0294-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="d0294-134">Ten tryb oferuje różne funkcje, takie jak to, czy poświadczenia usługi są dostępne na klientach poza pasmem, z którego korzysta pakiet algorytmów, oraz jaki poziom ochrony ma być stosowany do treści wiadomości za pomocą właściwości Security. Message.</span><span class="sxs-lookup"><span data-stu-id="d0294-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="d0294-135">Uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="d0294-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="d0294-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d0294-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="d0294-137">W tym trybie protokół HTTPS zapewnia integralność, poufność i uwierzytelnianie serwera, a zabezpieczenia komunikatów protokołu SOAP zapewniają uwierzytelnianie klienta.</span><span class="sxs-lookup"><span data-stu-id="d0294-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="d0294-138">Domyślnie uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane przez czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="d0294-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0294-139">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d0294-139">Child Elements</span></span>  
  
|<span data-ttu-id="d0294-140">Element</span><span class="sxs-lookup"><span data-stu-id="d0294-140">Element</span></span>|<span data-ttu-id="d0294-141">Opis</span><span class="sxs-lookup"><span data-stu-id="d0294-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0294-142">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="d0294-142">\<transport></span></span>](transport-of-wshttpbinding.md)|<span data-ttu-id="d0294-143">Definiuje ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="d0294-143">Defines the transport security settings.</span></span> <span data-ttu-id="d0294-144">Ten element odnosi się do <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="d0294-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="d0294-145">\<message></span><span class="sxs-lookup"><span data-stu-id="d0294-145">\<message></span></span>](message-of-wshttpbinding.md)|<span data-ttu-id="d0294-146">Definiuje ustawienia zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d0294-146">Defines the security settings for the message.</span></span> <span data-ttu-id="d0294-147">Ten element odnosi się do <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="d0294-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0294-148">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d0294-148">Parent Elements</span></span>  
  
|<span data-ttu-id="d0294-149">Element</span><span class="sxs-lookup"><span data-stu-id="d0294-149">Element</span></span>|<span data-ttu-id="d0294-150">Opis</span><span class="sxs-lookup"><span data-stu-id="d0294-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0294-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d0294-151">\<wsHttpBinding></span></span>](wshttpbinding.md)|<span data-ttu-id="d0294-152">Bezpieczne powiązanie dla aplikacji transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="d0294-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0294-153">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d0294-153">Remarks</span></span>  
 <span data-ttu-id="d0294-154">Klasa WSHttpBinding została zaprojektowana na potrzeby współdziałania z usługami, które implementują specyfikacje WS-\*.</span><span class="sxs-lookup"><span data-stu-id="d0294-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="d0294-155">Zabezpieczenia transportu dla tego powiązania są SSL (SSL) za pośrednictwem protokołu HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d0294-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0294-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0294-156">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="d0294-157">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="d0294-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d0294-158">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d0294-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d0294-159">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="d0294-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d0294-160">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="d0294-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d0294-161">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="d0294-161">\<binding></span></span>](../../../misc/binding.md)
