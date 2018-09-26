---
title: '&lt;security&gt; w &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
author: BrucePerlerMS
ms.openlocfilehash: 6eb7497990abb29693921d601b222a3b7e87bf6c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196593"
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a><span data-ttu-id="4b346-102">&lt;security&gt; w &lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="4b346-102">&lt;security&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="4b346-103">Reprezentuje ustawienia zabezpieczeń używane dla [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="4b346-103">Represents the security settings used with the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="4b346-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4b346-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4b346-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="4b346-105">\<bindings></span></span>  
<span data-ttu-id="4b346-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="4b346-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="4b346-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4b346-107">\<binding></span></span>  
<span data-ttu-id="4b346-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="4b346-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b346-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b346-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <bindings>  
        <ws2007HttpBinding>  
            <binding name = "string">  
              <security mode="None/Message/Transport/TransportWithMessageCredential">  
                  <transport>  
                  </transport>  
                  <message>  
                  </message>  
              </security  
        </ws2007HttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b346-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4b346-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4b346-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4b346-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b346-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4b346-112">Attributes</span></span>  
  
|<span data-ttu-id="4b346-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4b346-113">Attribute</span></span>|<span data-ttu-id="4b346-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4b346-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="4b346-115">— Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="4b346-115">-   Optional.</span></span> <span data-ttu-id="4b346-116">Określa typ zabezpieczeń, która jest stosowana.</span><span class="sxs-lookup"><span data-stu-id="4b346-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="4b346-117">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="4b346-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="4b346-118">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="4b346-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="4b346-119">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="4b346-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="4b346-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="4b346-120">Value</span></span>|<span data-ttu-id="4b346-121">Opis</span><span class="sxs-lookup"><span data-stu-id="4b346-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="4b346-122">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="4b346-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="4b346-123">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4b346-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="4b346-124">Usługa musi być skonfigurowany przy użyciu certyfikatów Secure Sockets Layer (SSL).</span><span class="sxs-lookup"><span data-stu-id="4b346-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="4b346-125">Komunikat jest całkowicie zabezpieczony przy użyciu protokołu HTTPS, a usługa jest uwierzytelniany przez klienta za pomocą certyfikatu SSL usługi.</span><span class="sxs-lookup"><span data-stu-id="4b346-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="4b346-126">Uwierzytelnianie klienta jest kontrolowany za pośrednictwem `ClientCredentials` atrybutu [ \<transportu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="4b346-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="4b346-127">Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4b346-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="4b346-128">Domyślnie treści protokołu SOAP jest zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="4b346-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="4b346-129">Ten tryb zapewnia szeroką gamę funkcji, takich jak tego, czy poświadczenia usługi są dostępne pod adresem klientem poza pasmem, pakiet algorytmów, używać oraz poziom ochrony do zastosowania do treści wiadomości, za pośrednictwem <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="4b346-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="4b346-130">Uwierzytelnianie klienta jest wykonywana raz dla każdej sesji i wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="4b346-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="4b346-131">W tym trybie HTTPS zapewnia integralność, poufność i uwierzytelniania serwera i zabezpieczenia wiadomości protokołu SOAP zapewnia uwierzytelnianie klienta.</span><span class="sxs-lookup"><span data-stu-id="4b346-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="4b346-132">Domyślnie uwierzytelnianie klienta jest wykonywana raz dla każdej sesji, a wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="4b346-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b346-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4b346-133">Child Elements</span></span>  
  
|<span data-ttu-id="4b346-134">Element</span><span class="sxs-lookup"><span data-stu-id="4b346-134">Element</span></span>|<span data-ttu-id="4b346-135">Opis</span><span class="sxs-lookup"><span data-stu-id="4b346-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b346-136">\<transport ></span><span class="sxs-lookup"><span data-stu-id="4b346-136">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|<span data-ttu-id="4b346-137">Określa ustawienia zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="4b346-137">Defines the transport security settings.</span></span> <span data-ttu-id="4b346-138">Ten element odnosi się do <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="4b346-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="4b346-139">Te ustawienia są stosowane tylko wtedy, gdy tryb jest ustawiony na Transport.</span><span class="sxs-lookup"><span data-stu-id="4b346-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="4b346-140">\<message></span><span class="sxs-lookup"><span data-stu-id="4b346-140">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="4b346-141">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4b346-141">Defines the security settings for the message.</span></span> <span data-ttu-id="4b346-142">Ten element odnosi się do <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="4b346-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="4b346-143">Te ustawienia nie są stosowane, gdy tryb jest ustawiony jako transportu.</span><span class="sxs-lookup"><span data-stu-id="4b346-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b346-144">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4b346-144">Parent Elements</span></span>  
  
|<span data-ttu-id="4b346-145">Element</span><span class="sxs-lookup"><span data-stu-id="4b346-145">Element</span></span>|<span data-ttu-id="4b346-146">Opis</span><span class="sxs-lookup"><span data-stu-id="4b346-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b346-147">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="4b346-147">\<ws2007HttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|<span data-ttu-id="4b346-148">Bezpiecznego powiązania aplikacji transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4b346-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b346-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b346-149">Remarks</span></span>  
 <span data-ttu-id="4b346-150">Ten element jest przeznaczona dla współdziałanie z usługami, które implementują WS-\* specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="4b346-150">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="4b346-151">Zabezpieczenia transportu dla tego powiązania jest Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4b346-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b346-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b346-152">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="4b346-153">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="4b346-153">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="4b346-154">Powiązania</span><span class="sxs-lookup"><span data-stu-id="4b346-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4b346-155">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="4b346-155">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="4b346-156">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="4b346-156">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="4b346-157">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4b346-157">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
