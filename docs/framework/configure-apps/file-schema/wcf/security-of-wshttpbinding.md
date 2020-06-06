---
title: <security> dla <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: b66b5228cab9dbc35502a13a2d0fe56ce4c6a18d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738581"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="83c2e-102">\<security> dla \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="83c2e-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="83c2e-103">Reprezentuje możliwości zabezpieczeń [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="83c2e-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="83c2e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83c2e-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83c2e-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="83c2e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="83c2e-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="83c2e-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83c2e-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="83c2e-107">Attributes</span></span>  
  
|<span data-ttu-id="83c2e-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="83c2e-108">Attribute</span></span>|<span data-ttu-id="83c2e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="83c2e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83c2e-110">tryb</span><span class="sxs-lookup"><span data-stu-id="83c2e-110">mode</span></span>|<span data-ttu-id="83c2e-111">Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="83c2e-111">-   Optional.</span></span> <span data-ttu-id="83c2e-112">Określa typ stosowanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="83c2e-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="83c2e-113">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="83c2e-113">The default is `Message`.</span></span><br /><span data-ttu-id="83c2e-114">-Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="83c2e-114">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="83c2e-115">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="83c2e-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="83c2e-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="83c2e-116">Value</span></span>|<span data-ttu-id="83c2e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="83c2e-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="83c2e-118">Brak</span><span class="sxs-lookup"><span data-stu-id="83c2e-118">None</span></span>|<span data-ttu-id="83c2e-119">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="83c2e-119">Security is disabled.</span></span>|  
|<span data-ttu-id="83c2e-120">Transport</span><span class="sxs-lookup"><span data-stu-id="83c2e-120">Transport</span></span>|<span data-ttu-id="83c2e-121">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="83c2e-121">Security is provided using HTTPS.</span></span> <span data-ttu-id="83c2e-122">Usługa musi być skonfigurowana przy użyciu certyfikatów SSL.</span><span class="sxs-lookup"><span data-stu-id="83c2e-122">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="83c2e-123">Komunikat jest całkowicie zabezpieczony przy użyciu protokołu HTTPS i uwierzytelniany przez klienta przy użyciu certyfikatu SSL usługi.</span><span class="sxs-lookup"><span data-stu-id="83c2e-123">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="83c2e-124">Uwierzytelnianie klienta jest kontrolowane przez `ClientCredentials` atrybut.</span><span class="sxs-lookup"><span data-stu-id="83c2e-124">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="83c2e-125">z [\<transport>](transport-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="83c2e-125">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="83c2e-126">Komunikat</span><span class="sxs-lookup"><span data-stu-id="83c2e-126">Message</span></span>|<span data-ttu-id="83c2e-127">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="83c2e-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="83c2e-128">Domyślnie treść protokołu SOAP jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="83c2e-128">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="83c2e-129">Ten tryb oferuje różne funkcje, takie jak to, czy poświadczenia usługi są dostępne na klientach poza pasmem, z którego korzysta pakiet algorytmów, oraz jaki poziom ochrony ma być stosowany do treści wiadomości za pomocą właściwości Security. Message.</span><span class="sxs-lookup"><span data-stu-id="83c2e-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="83c2e-130">Uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="83c2e-130">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="83c2e-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="83c2e-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="83c2e-132">W tym trybie protokół HTTPS zapewnia integralność, poufność i uwierzytelnianie serwera, a zabezpieczenia komunikatów protokołu SOAP zapewniają uwierzytelnianie klienta.</span><span class="sxs-lookup"><span data-stu-id="83c2e-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="83c2e-133">Domyślnie uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane przez czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="83c2e-133">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83c2e-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="83c2e-134">Child Elements</span></span>  
  
|<span data-ttu-id="83c2e-135">Element</span><span class="sxs-lookup"><span data-stu-id="83c2e-135">Element</span></span>|<span data-ttu-id="83c2e-136">Opis</span><span class="sxs-lookup"><span data-stu-id="83c2e-136">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-wshttpbinding.md)|<span data-ttu-id="83c2e-137">Definiuje ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="83c2e-137">Defines the transport security settings.</span></span> <span data-ttu-id="83c2e-138">Ten element odnosi się do <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="83c2e-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[\<message>](message-of-wshttpbinding.md)|<span data-ttu-id="83c2e-139">Definiuje ustawienia zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="83c2e-139">Defines the security settings for the message.</span></span> <span data-ttu-id="83c2e-140">Ten element odnosi się do <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="83c2e-140">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="83c2e-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="83c2e-141">Parent Elements</span></span>  
  
|<span data-ttu-id="83c2e-142">Element</span><span class="sxs-lookup"><span data-stu-id="83c2e-142">Element</span></span>|<span data-ttu-id="83c2e-143">Opis</span><span class="sxs-lookup"><span data-stu-id="83c2e-143">Description</span></span>|  
|-------------|-----------------|  
|[\<wsHttpBinding>](wshttpbinding.md)|<span data-ttu-id="83c2e-144">Bezpieczne powiązanie dla aplikacji transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="83c2e-144">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83c2e-145">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83c2e-145">Remarks</span></span>  
 <span data-ttu-id="83c2e-146">Klasa WSHttpBinding została zaprojektowana na potrzeby współdziałania z usługami, które implementują specyfikacje WS-\*.</span><span class="sxs-lookup"><span data-stu-id="83c2e-146">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="83c2e-147">Zabezpieczenia transportu dla tego powiązania są SSL (SSL) za pośrednictwem protokołu HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="83c2e-147">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c2e-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83c2e-148">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="83c2e-149">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="83c2e-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="83c2e-150">Powiązania</span><span class="sxs-lookup"><span data-stu-id="83c2e-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="83c2e-151">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="83c2e-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="83c2e-152">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="83c2e-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
