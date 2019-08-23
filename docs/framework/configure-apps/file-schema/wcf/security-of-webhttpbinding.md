---
title: <security> dla <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 806cf8524ed1a1439ca85a4b918e8e486e5dc94b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936590"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="80e06-102">\<> zabezpieczeń elementu \<WebHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="80e06-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="80e06-103">Określa wymagania dotyczące zabezpieczeń dla punktu końcowego skonfigurowanego za [ \<](webhttpbinding.md)pomocą elementu WebHttpBinding >.</span><span class="sxs-lookup"><span data-stu-id="80e06-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
 <span data-ttu-id="80e06-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="80e06-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="80e06-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="80e06-105">\<bindings></span></span>  
<span data-ttu-id="80e06-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="80e06-106">\<webHttpBinding></span></span>  
<span data-ttu-id="80e06-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="80e06-107">\<binding></span></span>  
<span data-ttu-id="80e06-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="80e06-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e06-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="80e06-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80e06-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="80e06-110">Attributes and Elements</span></span>  
 <span data-ttu-id="80e06-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="80e06-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80e06-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="80e06-112">Attributes</span></span>  
  
|<span data-ttu-id="80e06-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="80e06-113">Attribute</span></span>|<span data-ttu-id="80e06-114">Opis</span><span class="sxs-lookup"><span data-stu-id="80e06-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80e06-115">tryb</span><span class="sxs-lookup"><span data-stu-id="80e06-115">mode</span></span>|<span data-ttu-id="80e06-116">Określa, czy w punkcie końcowym nie są używane zabezpieczenia na poziomie transportu, czy żadne zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="80e06-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="80e06-117">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="80e06-117">The default is `None`.</span></span> <span data-ttu-id="80e06-118">Ten atrybut jest typu <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="80e06-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="80e06-119">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="80e06-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="80e06-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="80e06-120">Value</span></span>|<span data-ttu-id="80e06-121">Opis</span><span class="sxs-lookup"><span data-stu-id="80e06-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="80e06-122">Brak</span><span class="sxs-lookup"><span data-stu-id="80e06-122">None</span></span>|<span data-ttu-id="80e06-123">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="80e06-123">Security is disabled.</span></span>|  
|<span data-ttu-id="80e06-124">Transportu</span><span class="sxs-lookup"><span data-stu-id="80e06-124">Transport</span></span>|<span data-ttu-id="80e06-125">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="80e06-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="80e06-126">Usługa musi być skonfigurowana przy użyciu certyfikatów SSL.</span><span class="sxs-lookup"><span data-stu-id="80e06-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="80e06-127">Wiadomość jest całkowicie zabezpieczona przy użyciu protokołu HTTPS, a usługa jest uwierzytelniana przez klienta przy użyciu certyfikatu SSL usługi.</span><span class="sxs-lookup"><span data-stu-id="80e06-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="80e06-128">Uwierzytelnianie klienta jest kontrolowane przez `ClientCredentialType` atrybut [ \<> transportu](transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="80e06-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="80e06-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="80e06-129">TransportCredentialOnly</span></span>|<span data-ttu-id="80e06-130">Ten tryb nie zapewnia integralności i poufności komunikatów.</span><span class="sxs-lookup"><span data-stu-id="80e06-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="80e06-131">Zapewnia uwierzytelnianie klienta oparte na protokole HTTP.</span><span class="sxs-lookup"><span data-stu-id="80e06-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="80e06-132">Ten tryb powinien być używany z zachowaniem ostrożności.</span><span class="sxs-lookup"><span data-stu-id="80e06-132">This mode should be used with caution.</span></span> <span data-ttu-id="80e06-133">Powinna być używana w środowiskach, w których zabezpieczenia transportu są dostarczane przy użyciu innych metod (takich jak IPSec) i tylko uwierzytelnianie klienta jest udostępniane przez infrastrukturę WCF.</span><span class="sxs-lookup"><span data-stu-id="80e06-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80e06-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="80e06-134">Child Elements</span></span>  
  
|<span data-ttu-id="80e06-135">Element</span><span class="sxs-lookup"><span data-stu-id="80e06-135">Element</span></span>|<span data-ttu-id="80e06-136">Opis</span><span class="sxs-lookup"><span data-stu-id="80e06-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80e06-137">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="80e06-137">\<transport></span></span>](transport-of-webhttpbinding.md)|<span data-ttu-id="80e06-138">Definiuje ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="80e06-138">Defines the transport security settings.</span></span> <span data-ttu-id="80e06-139">Ten element odnosi się do <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="80e06-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80e06-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="80e06-140">Parent Elements</span></span>  
  
|<span data-ttu-id="80e06-141">Element</span><span class="sxs-lookup"><span data-stu-id="80e06-141">Element</span></span>|<span data-ttu-id="80e06-142">Opis</span><span class="sxs-lookup"><span data-stu-id="80e06-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80e06-143">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="80e06-143">\<webHttpBinding></span></span>](webhttpbinding.md)|<span data-ttu-id="80e06-144">Element powiązania, który jest używany do konfigurowania punktów końcowych dla usług sieci Web Windows Communication Foundation (WCF), które odpowiadają na żądania HTTP zamiast komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="80e06-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80e06-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80e06-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="80e06-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="80e06-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="80e06-147">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="80e06-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="80e06-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="80e06-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="80e06-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="80e06-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="80e06-150">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="80e06-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="80e06-151">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="80e06-151">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="80e06-152">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="80e06-152">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
