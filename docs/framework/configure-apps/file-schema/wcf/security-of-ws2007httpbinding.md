---
title: <security> dla <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: a895df027bee7430e51e76c480136a49b6b2a0be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936572"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="15bb2-102">\<zabezpieczenia > \<WS2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="15bb2-102">\<security> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="15bb2-103">Reprezentuje ustawienia zabezpieczeń używane z [ \<WS2007HttpBinding elementu >](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="15bb2-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="15bb2-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="15bb2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="15bb2-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="15bb2-105">\<bindings></span></span>  
<span data-ttu-id="15bb2-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="15bb2-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="15bb2-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="15bb2-107">\<binding></span></span>  
<span data-ttu-id="15bb2-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="15bb2-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15bb2-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="15bb2-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15bb2-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="15bb2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="15bb2-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="15bb2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15bb2-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="15bb2-112">Attributes</span></span>  
  
|<span data-ttu-id="15bb2-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="15bb2-113">Attribute</span></span>|<span data-ttu-id="15bb2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="15bb2-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="15bb2-115">Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="15bb2-115">-   Optional.</span></span> <span data-ttu-id="15bb2-116">Określa typ stosowanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="15bb2-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="15bb2-117">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="15bb2-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="15bb2-118">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="15bb2-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="15bb2-119">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="15bb2-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="15bb2-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="15bb2-120">Value</span></span>|<span data-ttu-id="15bb2-121">Opis</span><span class="sxs-lookup"><span data-stu-id="15bb2-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="15bb2-122">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="15bb2-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="15bb2-123">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="15bb2-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="15bb2-124">Usługa musi być skonfigurowana z certyfikatami SSL (SSL).</span><span class="sxs-lookup"><span data-stu-id="15bb2-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="15bb2-125">Wiadomość jest całkowicie zabezpieczona przy użyciu protokołu HTTPS, a usługa jest uwierzytelniana przez klienta przy użyciu certyfikatu SSL usługi.</span><span class="sxs-lookup"><span data-stu-id="15bb2-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="15bb2-126">Uwierzytelnianie klienta jest kontrolowane przez `ClientCredentials` atrybut [ \<elementu > transportu](transport-of-ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="15bb2-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="15bb2-127">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="15bb2-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="15bb2-128">Domyślnie treść protokołu SOAP jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="15bb2-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="15bb2-129">Ten tryb oferuje różne funkcje, takie jak to, czy poświadczenia usługi są dostępne na klientach poza pasmem, z którego korzysta pakiet algorytmów, oraz jaki poziom ochrony ma być stosowany do treści wiadomości za pomocą <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="15bb2-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="15bb2-130">Uwierzytelnianie klienta jest wykonywane raz dla każdej sesji, a wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="15bb2-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="15bb2-131">W tym trybie protokół HTTPS zapewnia integralność, poufność i uwierzytelnianie serwera, a zabezpieczenia komunikatów protokołu SOAP zapewniają uwierzytelnianie klienta.</span><span class="sxs-lookup"><span data-stu-id="15bb2-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="15bb2-132">Domyślnie uwierzytelnianie klienta jest wykonywane raz dla każdej sesji, a wyniki uwierzytelniania są buforowane przez czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="15bb2-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15bb2-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="15bb2-133">Child Elements</span></span>  
  
|<span data-ttu-id="15bb2-134">Element</span><span class="sxs-lookup"><span data-stu-id="15bb2-134">Element</span></span>|<span data-ttu-id="15bb2-135">Opis</span><span class="sxs-lookup"><span data-stu-id="15bb2-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15bb2-136">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="15bb2-136">\<transport></span></span>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="15bb2-137">Definiuje ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="15bb2-137">Defines the transport security settings.</span></span> <span data-ttu-id="15bb2-138">Ten element odnosi się do <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="15bb2-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="15bb2-139">Te ustawienia są stosowane tylko wtedy, gdy tryb jest ustawiony na transport.</span><span class="sxs-lookup"><span data-stu-id="15bb2-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="15bb2-140">\<message></span><span class="sxs-lookup"><span data-stu-id="15bb2-140">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="15bb2-141">Definiuje ustawienia zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="15bb2-141">Defines the security settings for the message.</span></span> <span data-ttu-id="15bb2-142">Ten element odnosi się do <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="15bb2-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="15bb2-143">Te ustawienia nie są stosowane, gdy tryb jest ustawiony na transport.</span><span class="sxs-lookup"><span data-stu-id="15bb2-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15bb2-144">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="15bb2-144">Parent Elements</span></span>  
  
|<span data-ttu-id="15bb2-145">Element</span><span class="sxs-lookup"><span data-stu-id="15bb2-145">Element</span></span>|<span data-ttu-id="15bb2-146">Opis</span><span class="sxs-lookup"><span data-stu-id="15bb2-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15bb2-147">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="15bb2-147">\<ws2007HttpBinding></span></span>](ws2007httpbinding.md)|<span data-ttu-id="15bb2-148">Bezpieczne powiązanie dla aplikacji transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="15bb2-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15bb2-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15bb2-149">Remarks</span></span>  
 <span data-ttu-id="15bb2-150">Ten element jest przeznaczony do współdziałania z usługami, które implementują specyfikacje WS-\*.</span><span class="sxs-lookup"><span data-stu-id="15bb2-150">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="15bb2-151">Zabezpieczenia transportu dla tego powiązania są SSL (SSL) za pośrednictwem protokołu HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="15bb2-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15bb2-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15bb2-152">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="15bb2-153">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="15bb2-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="15bb2-154">Powiązania</span><span class="sxs-lookup"><span data-stu-id="15bb2-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="15bb2-155">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="15bb2-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="15bb2-156">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="15bb2-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="15bb2-157">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="15bb2-157">\<binding></span></span>](../../../misc/binding.md)
