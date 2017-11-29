---
title: '&lt;security&gt; w &lt;webHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: b3d5d00dcc79a746818975a6a8b125d3dc33933b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a><span data-ttu-id="1cc4d-102">&lt;security&gt; w &lt;webHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="1cc4d-102">&lt;security&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="1cc4d-103">Określa wymagań zabezpieczeń dotyczących punkt końcowy skonfigurowany [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1cc4d-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="1cc4d-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1cc4d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1cc4d-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="1cc4d-105">\<bindings></span></span>  
<span data-ttu-id="1cc4d-106">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="1cc4d-106">\<webHttpBinding></span></span>  
<span data-ttu-id="1cc4d-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1cc4d-107">\<binding></span></span>  
<span data-ttu-id="1cc4d-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="1cc4d-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cc4d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="1cc4d-109">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
    <bindings>  
        <webHttpBinding>  
            <binding name = "string">  
              <security mode="None/Transport/TransportCredentialOnly">  
                                    <transport clientCredentialType =   
                                     "Basic/Certificate/Digest/None/Ntlm/Windows"  
                                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                                     realm="string" />  
              </security>  
        </webHttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1cc4d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1cc4d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1cc4d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1cc4d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1cc4d-112">Attributes</span></span>  
  
|<span data-ttu-id="1cc4d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1cc4d-113">Attribute</span></span>|<span data-ttu-id="1cc4d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1cc4d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1cc4d-115">tryb</span><span class="sxs-lookup"><span data-stu-id="1cc4d-115">mode</span></span>|<span data-ttu-id="1cc4d-116">Określa, czy zabezpieczenia na poziomie transportu lub zabezpieczeń nie jest używany przez punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="1cc4d-117">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-117">The default is `None`.</span></span> <span data-ttu-id="1cc4d-118">Ten atrybut jest typu <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="1cc4d-119">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="1cc4d-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="1cc4d-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="1cc4d-120">Value</span></span>|<span data-ttu-id="1cc4d-121">Opis</span><span class="sxs-lookup"><span data-stu-id="1cc4d-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1cc4d-122">Brak</span><span class="sxs-lookup"><span data-stu-id="1cc4d-122">None</span></span>|<span data-ttu-id="1cc4d-123">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-123">Security is disabled.</span></span>|  
|<span data-ttu-id="1cc4d-124">Transportu</span><span class="sxs-lookup"><span data-stu-id="1cc4d-124">Transport</span></span>|<span data-ttu-id="1cc4d-125">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="1cc4d-126">Usługa musi być skonfigurowany z certyfikatów SSL.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="1cc4d-127">Komunikat jest całkowicie zabezpieczone przy użyciu protokołu HTTPS, a usługa jest uwierzytelniany przez klienta przy użyciu certyfikatu SSL usługi.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="1cc4d-128">Uwierzytelnianie klienta są kontrolowane poprzez `ClientCredentialType` atrybutu [ \<transportu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1cc4d-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="1cc4d-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="1cc4d-129">TransportCredentialOnly</span></span>|<span data-ttu-id="1cc4d-130">W tym trybie nie zapewnia integralności i poufności.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="1cc4d-131">Zapewnia uwierzytelnianie oparte na protokole HTTP klienta.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="1cc4d-132">Tego trybu należy używać ostrożnie.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-132">This mode should be used with caution.</span></span> <span data-ttu-id="1cc4d-133">Tej opcji należy używać w środowiskach, gdzie zabezpieczeń transportu jest świadczona w inny sposób (na przykład IPSec), a tylko uwierzytelnianie klienta jest zapewniana przez [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1cc4d-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1cc4d-134">Child Elements</span></span>  
  
|<span data-ttu-id="1cc4d-135">Element</span><span class="sxs-lookup"><span data-stu-id="1cc4d-135">Element</span></span>|<span data-ttu-id="1cc4d-136">Opis</span><span class="sxs-lookup"><span data-stu-id="1cc4d-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1cc4d-137">\<transport ></span><span class="sxs-lookup"><span data-stu-id="1cc4d-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="1cc4d-138">Określa ustawienia zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-138">Defines the transport security settings.</span></span> <span data-ttu-id="1cc4d-139">Ten element odpowiada <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1cc4d-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1cc4d-140">Parent Elements</span></span>  
  
|<span data-ttu-id="1cc4d-141">Element</span><span class="sxs-lookup"><span data-stu-id="1cc4d-141">Element</span></span>|<span data-ttu-id="1cc4d-142">Opis</span><span class="sxs-lookup"><span data-stu-id="1cc4d-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1cc4d-143">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="1cc4d-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="1cc4d-144">Element powiązania, który jest używany do konfigurowania punktów końcowych dla [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tego odpowiada na żądania HTTP zamiast na wiadomości SOAP usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1cc4d-144">A binding element that is used to configure endpoints for [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1cc4d-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1cc4d-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [<span data-ttu-id="1cc4d-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="1cc4d-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="1cc4d-147">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="1cc4d-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="1cc4d-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1cc4d-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1cc4d-149">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="1cc4d-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="1cc4d-150">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="1cc4d-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="1cc4d-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1cc4d-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="1cc4d-152">Model programowania protokołu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="1cc4d-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
