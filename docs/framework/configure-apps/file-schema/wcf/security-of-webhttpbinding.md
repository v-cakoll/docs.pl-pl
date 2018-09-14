---
title: '&lt;security&gt; w &lt;webHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 52146fa08ec63ef63fa996cdc09f9185b9f42e02
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45515304"
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a><span data-ttu-id="032d0-102">&lt;security&gt; w &lt;webHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="032d0-102">&lt;security&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="032d0-103">Określa wymagania dotyczące zabezpieczeń dla punktu końcowego skonfigurowano [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="032d0-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="032d0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="032d0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="032d0-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="032d0-105">\<bindings></span></span>  
<span data-ttu-id="032d0-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="032d0-106">\<webHttpBinding></span></span>  
<span data-ttu-id="032d0-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="032d0-107">\<binding></span></span>  
<span data-ttu-id="032d0-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="032d0-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="032d0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="032d0-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="032d0-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="032d0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="032d0-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="032d0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="032d0-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="032d0-112">Attributes</span></span>  
  
|<span data-ttu-id="032d0-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="032d0-113">Attribute</span></span>|<span data-ttu-id="032d0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="032d0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="032d0-115">tryb</span><span class="sxs-lookup"><span data-stu-id="032d0-115">mode</span></span>|<span data-ttu-id="032d0-116">Określa, czy zabezpieczenia na poziomie transportu lub zabezpieczeń nie jest używany przez punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="032d0-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="032d0-117">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="032d0-117">The default is `None`.</span></span> <span data-ttu-id="032d0-118">Ten atrybut jest typu <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="032d0-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="032d0-119">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="032d0-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="032d0-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="032d0-120">Value</span></span>|<span data-ttu-id="032d0-121">Opis</span><span class="sxs-lookup"><span data-stu-id="032d0-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="032d0-122">Brak</span><span class="sxs-lookup"><span data-stu-id="032d0-122">None</span></span>|<span data-ttu-id="032d0-123">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="032d0-123">Security is disabled.</span></span>|  
|<span data-ttu-id="032d0-124">Transportu</span><span class="sxs-lookup"><span data-stu-id="032d0-124">Transport</span></span>|<span data-ttu-id="032d0-125">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="032d0-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="032d0-126">Usługa musi zostać skonfigurowane przy użyciu certyfikatów SSL.</span><span class="sxs-lookup"><span data-stu-id="032d0-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="032d0-127">Komunikat jest całkowicie zabezpieczony przy użyciu protokołu HTTPS, a usługa jest uwierzytelniany przez klienta za pomocą certyfikatu SSL usługi.</span><span class="sxs-lookup"><span data-stu-id="032d0-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="032d0-128">Uwierzytelnianie klienta jest kontrolowany za pośrednictwem `ClientCredentialType` atrybutu [ \<transportu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="032d0-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="032d0-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="032d0-129">TransportCredentialOnly</span></span>|<span data-ttu-id="032d0-130">Ten tryb nie zapewnia integralność komunikatów i poufność.</span><span class="sxs-lookup"><span data-stu-id="032d0-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="032d0-131">Zapewnia uwierzytelnianie oparte na protokole HTTP klienta.</span><span class="sxs-lookup"><span data-stu-id="032d0-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="032d0-132">W tym trybie, należy używać ostrożnie.</span><span class="sxs-lookup"><span data-stu-id="032d0-132">This mode should be used with caution.</span></span> <span data-ttu-id="032d0-133">Należy używać w środowiskach, gdzie zabezpieczenia transportu jest świadczona w inny sposób (takich jak IPSec), a tylko uwierzytelnianie klientów jest świadczona przez infrastrukturę usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="032d0-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="032d0-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="032d0-134">Child Elements</span></span>  
  
|<span data-ttu-id="032d0-135">Element</span><span class="sxs-lookup"><span data-stu-id="032d0-135">Element</span></span>|<span data-ttu-id="032d0-136">Opis</span><span class="sxs-lookup"><span data-stu-id="032d0-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="032d0-137">\<transport ></span><span class="sxs-lookup"><span data-stu-id="032d0-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="032d0-138">Określa ustawienia zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="032d0-138">Defines the transport security settings.</span></span> <span data-ttu-id="032d0-139">Ten element odnosi się do <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="032d0-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="032d0-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="032d0-140">Parent Elements</span></span>  
  
|<span data-ttu-id="032d0-141">Element</span><span class="sxs-lookup"><span data-stu-id="032d0-141">Element</span></span>|<span data-ttu-id="032d0-142">Opis</span><span class="sxs-lookup"><span data-stu-id="032d0-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="032d0-143">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="032d0-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="032d0-144">Element powiązania, który jest używany do konfigurowania punktów końcowych dla tego odpowiadanie na żądania HTTP zamiast na wiadomości SOAP usług sieci Web Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="032d0-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="032d0-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="032d0-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [<span data-ttu-id="032d0-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="032d0-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="032d0-147">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="032d0-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="032d0-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="032d0-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="032d0-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="032d0-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="032d0-150">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="032d0-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="032d0-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="032d0-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="032d0-152">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="032d0-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
