---
title: '&lt;security&gt; w &lt;netPeerBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 45000554226fcde753041fca283bfc8b1eeba5ce
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45561126"
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="d304c-102">&lt;security&gt; w &lt;netPeerBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="d304c-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="d304c-103">Definiuje ustawienia zabezpieczeń [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), takie jak typ uwierzytelniania używany i zabezpieczenia używany do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d304c-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="d304c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d304c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d304c-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="d304c-105">\<bindings></span></span>  
<span data-ttu-id="d304c-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="d304c-106">\<netPeerBinding></span></span>  
<span data-ttu-id="d304c-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d304c-107">\<binding></span></span>  
<span data-ttu-id="d304c-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="d304c-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d304c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d304c-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d304c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d304c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d304c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d304c-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d304c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d304c-112">Attributes</span></span>  
  
|<span data-ttu-id="d304c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d304c-113">Attribute</span></span>|<span data-ttu-id="d304c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d304c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d304c-115">tryb</span><span class="sxs-lookup"><span data-stu-id="d304c-115">mode</span></span>|<span data-ttu-id="d304c-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d304c-116">Optional.</span></span> <span data-ttu-id="d304c-117">Określa typ zabezpieczeń używanych przez elementy równorzędne skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="d304c-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="d304c-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="d304c-118">The default value is `Message`.</span></span> <span data-ttu-id="d304c-119">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d304c-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d304c-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="d304c-120">mode Attribute</span></span>  
  
|<span data-ttu-id="d304c-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="d304c-121">Value</span></span>|<span data-ttu-id="d304c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="d304c-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d304c-123">Komunikat</span><span class="sxs-lookup"><span data-stu-id="d304c-123">Message</span></span>|<span data-ttu-id="d304c-124">Zabezpieczenia protokołu SOAP zapewnia uwierzytelnianie, integralności i poufności.</span><span class="sxs-lookup"><span data-stu-id="d304c-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="d304c-125">Brak</span><span class="sxs-lookup"><span data-stu-id="d304c-125">None</span></span>|<span data-ttu-id="d304c-126">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="d304c-126">Security is disabled.</span></span>|  
|<span data-ttu-id="d304c-127">Transportu</span><span class="sxs-lookup"><span data-stu-id="d304c-127">Transport</span></span>|<span data-ttu-id="d304c-128">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d304c-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="d304c-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d304c-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="d304c-130">Protokół HTTPS zapewnia uwierzytelnianie i poufności.</span><span class="sxs-lookup"><span data-stu-id="d304c-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="d304c-131">Komunikaty protokołu SOAP zawierają typy zaawansowane poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="d304c-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d304c-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d304c-132">Child Elements</span></span>  
  
|<span data-ttu-id="d304c-133">Element</span><span class="sxs-lookup"><span data-stu-id="d304c-133">Element</span></span>|<span data-ttu-id="d304c-134">Opis</span><span class="sxs-lookup"><span data-stu-id="d304c-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d304c-135">\<transport ></span><span class="sxs-lookup"><span data-stu-id="d304c-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="d304c-136">Definiuje typ transportu dla zabezpieczonych wiadomości wysłanych przez elementy równorzędne skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="d304c-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="d304c-137">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="d304c-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d304c-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d304c-138">Parent Elements</span></span>  
  
|<span data-ttu-id="d304c-139">Element</span><span class="sxs-lookup"><span data-stu-id="d304c-139">Element</span></span>|<span data-ttu-id="d304c-140">Opis</span><span class="sxs-lookup"><span data-stu-id="d304c-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d304c-141">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d304c-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d304c-142">Definiuje wszystkie możliwości wiązania [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d304c-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d304c-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d304c-143">Remarks</span></span>  
 <span data-ttu-id="d304c-144">Zabezpieczeń może być albo lub transportu specyficzne dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d304c-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d304c-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d304c-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="d304c-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="d304c-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="d304c-147">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="d304c-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="d304c-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d304c-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d304c-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="d304c-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d304c-150">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="d304c-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="d304c-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d304c-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
