---
title: <security> dla <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 77009dc950a608da9e0db3a7d09be67e1ed46137
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738637"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="3756f-102">> zabezpieczeń \<\<WebHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="3756f-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="3756f-103">Określa wymagania dotyczące zabezpieczeń punktu końcowego skonfigurowanego za pomocą [\<WebHttpBinding](webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3756f-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
<span data-ttu-id="3756f-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3756f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3756f-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="3756f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3756f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="3756f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="3756f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WebHttpBinding**](webhttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="3756f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="3756f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="3756f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="3756f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpieczenia >**</span><span class="sxs-lookup"><span data-stu-id="3756f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3756f-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="3756f-110">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <bindings>
    <webHttpBinding>
      <binding name = "String">
        <security mode="None/Transport/TransportCredentialOnly">
          <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                     realm="String" />
        </security>
      </binding>
    </webHttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3756f-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3756f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3756f-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3756f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3756f-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3756f-113">Attributes</span></span>  
  
|<span data-ttu-id="3756f-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3756f-114">Attribute</span></span>|<span data-ttu-id="3756f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="3756f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3756f-116">tryb</span><span class="sxs-lookup"><span data-stu-id="3756f-116">mode</span></span>|<span data-ttu-id="3756f-117">Określa, czy w punkcie końcowym nie są używane zabezpieczenia na poziomie transportu, czy żadne zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="3756f-117">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="3756f-118">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="3756f-118">The default is `None`.</span></span> <span data-ttu-id="3756f-119">Ten atrybut jest typu <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="3756f-119">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="3756f-120">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="3756f-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="3756f-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="3756f-121">Value</span></span>|<span data-ttu-id="3756f-122">Opis</span><span class="sxs-lookup"><span data-stu-id="3756f-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3756f-123">Brak</span><span class="sxs-lookup"><span data-stu-id="3756f-123">None</span></span>|<span data-ttu-id="3756f-124">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="3756f-124">Security is disabled.</span></span>|  
|<span data-ttu-id="3756f-125">Transportu</span><span class="sxs-lookup"><span data-stu-id="3756f-125">Transport</span></span>|<span data-ttu-id="3756f-126">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3756f-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="3756f-127">Usługa musi być skonfigurowana przy użyciu certyfikatów SSL.</span><span class="sxs-lookup"><span data-stu-id="3756f-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="3756f-128">Wiadomość jest całkowicie zabezpieczona przy użyciu protokołu HTTPS, a usługa jest uwierzytelniana przez klienta przy użyciu certyfikatu SSL usługi.</span><span class="sxs-lookup"><span data-stu-id="3756f-128">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="3756f-129">Uwierzytelnianie klienta jest kontrolowane przez `ClientCredentialType` atrybutu [> transportu\<](transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3756f-129">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="3756f-130">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="3756f-130">TransportCredentialOnly</span></span>|<span data-ttu-id="3756f-131">Ten tryb nie zapewnia integralności i poufności komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3756f-131">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="3756f-132">Zapewnia uwierzytelnianie klienta oparte na protokole HTTP.</span><span class="sxs-lookup"><span data-stu-id="3756f-132">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="3756f-133">Ten tryb powinien być używany z zachowaniem ostrożności.</span><span class="sxs-lookup"><span data-stu-id="3756f-133">This mode should be used with caution.</span></span> <span data-ttu-id="3756f-134">Powinna być używana w środowiskach, w których zabezpieczenia transportu są dostarczane przy użyciu innych metod (takich jak IPSec) i tylko uwierzytelnianie klienta jest udostępniane przez infrastrukturę WCF.</span><span class="sxs-lookup"><span data-stu-id="3756f-134">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3756f-135">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3756f-135">Child Elements</span></span>  
  
|<span data-ttu-id="3756f-136">Element</span><span class="sxs-lookup"><span data-stu-id="3756f-136">Element</span></span>|<span data-ttu-id="3756f-137">Opis</span><span class="sxs-lookup"><span data-stu-id="3756f-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3756f-138">> transportu \<</span><span class="sxs-lookup"><span data-stu-id="3756f-138">\<transport></span></span>](transport-of-webhttpbinding.md)|<span data-ttu-id="3756f-139">Definiuje ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="3756f-139">Defines the transport security settings.</span></span> <span data-ttu-id="3756f-140">Ten element odnosi się do typu <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="3756f-140">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3756f-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3756f-141">Parent Elements</span></span>  
  
|<span data-ttu-id="3756f-142">Element</span><span class="sxs-lookup"><span data-stu-id="3756f-142">Element</span></span>|<span data-ttu-id="3756f-143">Opis</span><span class="sxs-lookup"><span data-stu-id="3756f-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3756f-144">\<WebHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="3756f-144">\<webHttpBinding></span></span>](webhttpbinding.md)|<span data-ttu-id="3756f-145">Element powiązania, który jest używany do konfigurowania punktów końcowych dla usług sieci Web Windows Communication Foundation (WCF), które odpowiadają na żądania HTTP zamiast komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="3756f-145">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3756f-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3756f-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="3756f-147">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="3756f-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3756f-148">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="3756f-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="3756f-149">Powiązania</span><span class="sxs-lookup"><span data-stu-id="3756f-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3756f-150">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="3756f-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3756f-151">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="3756f-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3756f-152">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="3756f-152">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="3756f-153">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="3756f-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
