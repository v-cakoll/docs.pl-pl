---
title: '&lt;security&gt; w &lt;netPeerBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 45000554226fcde753041fca283bfc8b1eeba5ce
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776919"
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="2d895-102">&lt;security&gt; w &lt;netPeerBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="2d895-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="2d895-103">Definiuje ustawienia zabezpieczeń [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), takie jak typ uwierzytelniania używany i zabezpieczenia używany do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2d895-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="2d895-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2d895-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2d895-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="2d895-105">\<bindings></span></span>  
<span data-ttu-id="2d895-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="2d895-106">\<netPeerBinding></span></span>  
<span data-ttu-id="2d895-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="2d895-107">\<binding></span></span>  
<span data-ttu-id="2d895-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="2d895-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d895-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d895-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d895-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2d895-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2d895-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2d895-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d895-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2d895-112">Attributes</span></span>  
  
|<span data-ttu-id="2d895-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2d895-113">Attribute</span></span>|<span data-ttu-id="2d895-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2d895-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d895-115">tryb</span><span class="sxs-lookup"><span data-stu-id="2d895-115">mode</span></span>|<span data-ttu-id="2d895-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="2d895-116">Optional.</span></span> <span data-ttu-id="2d895-117">Określa typ zabezpieczeń używanych przez elementy równorzędne skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="2d895-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="2d895-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="2d895-118">The default value is `Message`.</span></span> <span data-ttu-id="2d895-119">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="2d895-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="2d895-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="2d895-120">mode Attribute</span></span>  
  
|<span data-ttu-id="2d895-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="2d895-121">Value</span></span>|<span data-ttu-id="2d895-122">Opis</span><span class="sxs-lookup"><span data-stu-id="2d895-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2d895-123">Komunikat</span><span class="sxs-lookup"><span data-stu-id="2d895-123">Message</span></span>|<span data-ttu-id="2d895-124">Zabezpieczenia protokołu SOAP zapewnia uwierzytelnianie, integralności i poufności.</span><span class="sxs-lookup"><span data-stu-id="2d895-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="2d895-125">Brak</span><span class="sxs-lookup"><span data-stu-id="2d895-125">None</span></span>|<span data-ttu-id="2d895-126">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="2d895-126">Security is disabled.</span></span>|  
|<span data-ttu-id="2d895-127">Transportu</span><span class="sxs-lookup"><span data-stu-id="2d895-127">Transport</span></span>|<span data-ttu-id="2d895-128">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2d895-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="2d895-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="2d895-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="2d895-130">Protokół HTTPS zapewnia uwierzytelnianie i poufności.</span><span class="sxs-lookup"><span data-stu-id="2d895-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="2d895-131">Komunikaty protokołu SOAP zawierają typy zaawansowane poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="2d895-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d895-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2d895-132">Child Elements</span></span>  
  
|<span data-ttu-id="2d895-133">Element</span><span class="sxs-lookup"><span data-stu-id="2d895-133">Element</span></span>|<span data-ttu-id="2d895-134">Opis</span><span class="sxs-lookup"><span data-stu-id="2d895-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d895-135">\<transport ></span><span class="sxs-lookup"><span data-stu-id="2d895-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="2d895-136">Definiuje typ transportu dla zabezpieczonych wiadomości wysłanych przez elementy równorzędne skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="2d895-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="2d895-137">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2d895-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2d895-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2d895-138">Parent Elements</span></span>  
  
|<span data-ttu-id="2d895-139">Element</span><span class="sxs-lookup"><span data-stu-id="2d895-139">Element</span></span>|<span data-ttu-id="2d895-140">Opis</span><span class="sxs-lookup"><span data-stu-id="2d895-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d895-141">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="2d895-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2d895-142">Definiuje wszystkie możliwości wiązania [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="2d895-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d895-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d895-143">Remarks</span></span>  
 <span data-ttu-id="2d895-144">Zabezpieczeń może być albo lub transportu specyficzne dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2d895-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d895-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d895-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="2d895-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="2d895-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="2d895-147">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="2d895-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="2d895-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="2d895-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2d895-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="2d895-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="2d895-150">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="2d895-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="2d895-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="2d895-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
