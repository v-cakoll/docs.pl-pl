---
title: '&lt;security&gt; w &lt;ws2007HttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 355fa3a7031c9650d52d258b9d5ef67b291e6e17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a><span data-ttu-id="01e66-102">&lt;security&gt; w &lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="01e66-102">&lt;security&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="01e66-103">Reprezentuje ustawienia zabezpieczeń używane dla [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="01e66-103">Represents the security settings used with the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="01e66-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="01e66-104">\<system.serviceModel></span></span>  
<span data-ttu-id="01e66-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="01e66-105">\<bindings></span></span>  
<span data-ttu-id="01e66-106">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="01e66-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="01e66-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="01e66-107">\<binding></span></span>  
<span data-ttu-id="01e66-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="01e66-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01e66-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="01e66-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01e66-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="01e66-110">Attributes and Elements</span></span>  
 <span data-ttu-id="01e66-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="01e66-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01e66-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="01e66-112">Attributes</span></span>  
  
|<span data-ttu-id="01e66-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="01e66-113">Attribute</span></span>|<span data-ttu-id="01e66-114">Opis</span><span class="sxs-lookup"><span data-stu-id="01e66-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="01e66-115">-Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="01e66-115">-   Optional.</span></span> <span data-ttu-id="01e66-116">Określa typ zabezpieczeń, która została zastosowana.</span><span class="sxs-lookup"><span data-stu-id="01e66-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="01e66-117">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="01e66-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="01e66-118">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="01e66-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="01e66-119">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="01e66-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="01e66-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="01e66-120">Value</span></span>|<span data-ttu-id="01e66-121">Opis</span><span class="sxs-lookup"><span data-stu-id="01e66-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="01e66-122">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="01e66-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="01e66-123">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="01e66-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="01e66-124">Usługa musi być skonfigurowana za pomocą certyfikatów Secure Sockets Layer (SSL).</span><span class="sxs-lookup"><span data-stu-id="01e66-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="01e66-125">Komunikat jest całkowicie zabezpieczone przy użyciu protokołu HTTPS, a usługa jest uwierzytelniany przez klienta przy użyciu certyfikatu SSL usługi.</span><span class="sxs-lookup"><span data-stu-id="01e66-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="01e66-126">Uwierzytelnianie klienta są kontrolowane poprzez `ClientCredentials` atrybutu [ \<transportu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="01e66-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="01e66-127">Zabezpieczenia korzystanie z zabezpieczeń komunikatów SOAP.</span><span class="sxs-lookup"><span data-stu-id="01e66-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="01e66-128">Domyślnie treści protokołu SOAP zostaje zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="01e66-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="01e66-129">W tym trybie oferuje wiele funkcji, takich jak określa, czy poświadczenia usługi są dostępne pod adresem klientem poza pasmem, pakiet algorytmów do użycia, a poziom ochrony do zastosowania do treści komunikatu za pośrednictwem <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="01e66-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="01e66-130">Uwierzytelnianie klienta jest wykonywana raz dla każdej sesji i wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="01e66-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="01e66-131">W tym trybie HTTPS zapewnia integralność, poufność i uwierzytelnianie serwera i uwierzytelnianie klienta zawiera zabezpieczenia wiadomości SOAP.</span><span class="sxs-lookup"><span data-stu-id="01e66-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="01e66-132">Domyślnie uwierzytelnianie klienta jest wykonywana raz dla każdej sesji i wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="01e66-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01e66-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="01e66-133">Child Elements</span></span>  
  
|<span data-ttu-id="01e66-134">Element</span><span class="sxs-lookup"><span data-stu-id="01e66-134">Element</span></span>|<span data-ttu-id="01e66-135">Opis</span><span class="sxs-lookup"><span data-stu-id="01e66-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01e66-136">\<transport ></span><span class="sxs-lookup"><span data-stu-id="01e66-136">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|<span data-ttu-id="01e66-137">Określa ustawienia zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="01e66-137">Defines the transport security settings.</span></span> <span data-ttu-id="01e66-138">Ten element odpowiada <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="01e66-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="01e66-139">Te ustawienia są stosowane tylko wtedy, gdy jest tryb transportu.</span><span class="sxs-lookup"><span data-stu-id="01e66-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="01e66-140">\<komunikat ></span><span class="sxs-lookup"><span data-stu-id="01e66-140">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="01e66-141">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="01e66-141">Defines the security settings for the message.</span></span> <span data-ttu-id="01e66-142">Ten element odpowiada <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="01e66-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="01e66-143">Te ustawienia nie są stosowane, gdy tryb ustawiono transportu.</span><span class="sxs-lookup"><span data-stu-id="01e66-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="01e66-144">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="01e66-144">Parent Elements</span></span>  
  
|<span data-ttu-id="01e66-145">Element</span><span class="sxs-lookup"><span data-stu-id="01e66-145">Element</span></span>|<span data-ttu-id="01e66-146">Opis</span><span class="sxs-lookup"><span data-stu-id="01e66-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01e66-147">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="01e66-147">\<ws2007HttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|<span data-ttu-id="01e66-148">Bezpiecznego powiązania dla aplikacji transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="01e66-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01e66-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01e66-149">Remarks</span></span>  
 <span data-ttu-id="01e66-150">Ten element jest przeznaczona dla współdziałanie z usługami, które implementują WS-* specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="01e66-150">This element is designed for interoperation with services that implement WS-* specifications.</span></span> <span data-ttu-id="01e66-151">Zabezpieczenia transportu dla tego powiązania jest Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="01e66-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e66-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01e66-152">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="01e66-153">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="01e66-153">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="01e66-154">Powiązania</span><span class="sxs-lookup"><span data-stu-id="01e66-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="01e66-155">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="01e66-155">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="01e66-156">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="01e66-156">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="01e66-157">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="01e66-157">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
