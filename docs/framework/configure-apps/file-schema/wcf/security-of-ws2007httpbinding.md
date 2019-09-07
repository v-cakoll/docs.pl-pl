---
title: <security> dla <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: ab5969da6a2d7cb59c057fd5bb909add6b6398a4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399786"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="ed2d6-102">\<zabezpieczenia > \<WS2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ed2d6-102">\<security> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="ed2d6-103">Reprezentuje ustawienia zabezpieczeń używane z [ \<WS2007HttpBinding elementu >](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ed2d6-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
<span data-ttu-id="ed2d6-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed2d6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ed2d6-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ed2d6-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ed2d6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="ed2d6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ed2d6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ed2d6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="ed2d6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="ed2d6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="ed2d6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpieczeń**</span><span class="sxs-lookup"><span data-stu-id="ed2d6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed2d6-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed2d6-110">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed2d6-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ed2d6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ed2d6-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed2d6-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ed2d6-113">Attributes</span></span>  
  
|<span data-ttu-id="ed2d6-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ed2d6-114">Attribute</span></span>|<span data-ttu-id="ed2d6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ed2d6-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="ed2d6-116">Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-116">-   Optional.</span></span> <span data-ttu-id="ed2d6-117">Określa typ stosowanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="ed2d6-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-118">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="ed2d6-119">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="ed2d6-120">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="ed2d6-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="ed2d6-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="ed2d6-121">Value</span></span>|<span data-ttu-id="ed2d6-122">Opis</span><span class="sxs-lookup"><span data-stu-id="ed2d6-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="ed2d6-123">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="ed2d6-124">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-124">Security is provided using HTTPS.</span></span> <span data-ttu-id="ed2d6-125">Usługa musi być skonfigurowana z certyfikatami SSL (SSL).</span><span class="sxs-lookup"><span data-stu-id="ed2d6-125">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="ed2d6-126">Wiadomość jest całkowicie zabezpieczona przy użyciu protokołu HTTPS, a usługa jest uwierzytelniana przez klienta przy użyciu certyfikatu SSL usługi.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-126">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="ed2d6-127">Uwierzytelnianie klienta jest kontrolowane przez `ClientCredentials` atrybut [ \<elementu > transportu](transport-of-ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ed2d6-127">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="ed2d6-128">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="ed2d6-129">Domyślnie treść protokołu SOAP jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-129">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="ed2d6-130">Ten tryb oferuje różne funkcje, takie jak to, czy poświadczenia usługi są dostępne na klientach poza pasmem, z którego korzysta pakiet algorytmów, oraz jaki poziom ochrony ma być stosowany do treści wiadomości za pomocą <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-130">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="ed2d6-131">Uwierzytelnianie klienta jest wykonywane raz dla każdej sesji, a wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-131">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="ed2d6-132">W tym trybie protokół HTTPS zapewnia integralność, poufność i uwierzytelnianie serwera, a zabezpieczenia komunikatów protokołu SOAP zapewniają uwierzytelnianie klienta.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="ed2d6-133">Domyślnie uwierzytelnianie klienta jest wykonywane raz dla każdej sesji, a wyniki uwierzytelniania są buforowane przez czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-133">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed2d6-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ed2d6-134">Child Elements</span></span>  
  
|<span data-ttu-id="ed2d6-135">Element</span><span class="sxs-lookup"><span data-stu-id="ed2d6-135">Element</span></span>|<span data-ttu-id="ed2d6-136">Opis</span><span class="sxs-lookup"><span data-stu-id="ed2d6-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed2d6-137">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="ed2d6-137">\<transport></span></span>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="ed2d6-138">Definiuje ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-138">Defines the transport security settings.</span></span> <span data-ttu-id="ed2d6-139">Ten element odnosi się do <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="ed2d6-140">Te ustawienia są stosowane tylko wtedy, gdy tryb jest ustawiony na transport.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-140">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="ed2d6-141">\<message></span><span class="sxs-lookup"><span data-stu-id="ed2d6-141">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="ed2d6-142">Definiuje ustawienia zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-142">Defines the security settings for the message.</span></span> <span data-ttu-id="ed2d6-143">Ten element odnosi się do <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-143">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="ed2d6-144">Te ustawienia nie są stosowane, gdy tryb jest ustawiony na transport.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-144">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ed2d6-145">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ed2d6-145">Parent Elements</span></span>  
  
|<span data-ttu-id="ed2d6-146">Element</span><span class="sxs-lookup"><span data-stu-id="ed2d6-146">Element</span></span>|<span data-ttu-id="ed2d6-147">Opis</span><span class="sxs-lookup"><span data-stu-id="ed2d6-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed2d6-148">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="ed2d6-148">\<ws2007HttpBinding></span></span>](ws2007httpbinding.md)|<span data-ttu-id="ed2d6-149">Bezpieczne powiązanie dla aplikacji transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-149">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed2d6-150">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed2d6-150">Remarks</span></span>  
 <span data-ttu-id="ed2d6-151">Ten element jest przeznaczony do współdziałania z usługami, które implementują specyfikacje WS-\*.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-151">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="ed2d6-152">Zabezpieczenia transportu dla tego powiązania są SSL (SSL) za pośrednictwem protokołu HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ed2d6-152">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed2d6-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed2d6-153">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="ed2d6-154">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ed2d6-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ed2d6-155">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ed2d6-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ed2d6-156">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="ed2d6-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ed2d6-157">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="ed2d6-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ed2d6-158">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="ed2d6-158">\<binding></span></span>](../../../misc/binding.md)
