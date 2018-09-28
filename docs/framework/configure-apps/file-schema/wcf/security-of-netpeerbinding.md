---
title: '&lt;security&gt; w &lt;netPeerBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
ms.openlocfilehash: d17d063ffdd354327c2523415b7d9394e723135a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47436300"
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="831b3-102">&lt;security&gt; w &lt;netPeerBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="831b3-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="831b3-103">Definiuje ustawienia zabezpieczeń [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), takie jak typ uwierzytelniania używany i zabezpieczenia używany do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="831b3-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="831b3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="831b3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="831b3-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="831b3-105">\<bindings></span></span>  
<span data-ttu-id="831b3-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="831b3-106">\<netPeerBinding></span></span>  
<span data-ttu-id="831b3-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="831b3-107">\<binding></span></span>  
<span data-ttu-id="831b3-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="831b3-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="831b3-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="831b3-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="831b3-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="831b3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="831b3-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="831b3-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="831b3-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="831b3-112">Attributes</span></span>  
  
|<span data-ttu-id="831b3-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="831b3-113">Attribute</span></span>|<span data-ttu-id="831b3-114">Opis</span><span class="sxs-lookup"><span data-stu-id="831b3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="831b3-115">tryb</span><span class="sxs-lookup"><span data-stu-id="831b3-115">mode</span></span>|<span data-ttu-id="831b3-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="831b3-116">Optional.</span></span> <span data-ttu-id="831b3-117">Określa typ zabezpieczeń używanych przez elementy równorzędne skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="831b3-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="831b3-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="831b3-118">The default value is `Message`.</span></span> <span data-ttu-id="831b3-119">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="831b3-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="831b3-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="831b3-120">mode Attribute</span></span>  
  
|<span data-ttu-id="831b3-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="831b3-121">Value</span></span>|<span data-ttu-id="831b3-122">Opis</span><span class="sxs-lookup"><span data-stu-id="831b3-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="831b3-123">Komunikat</span><span class="sxs-lookup"><span data-stu-id="831b3-123">Message</span></span>|<span data-ttu-id="831b3-124">Zabezpieczenia protokołu SOAP zapewnia uwierzytelnianie, integralności i poufności.</span><span class="sxs-lookup"><span data-stu-id="831b3-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="831b3-125">Brak</span><span class="sxs-lookup"><span data-stu-id="831b3-125">None</span></span>|<span data-ttu-id="831b3-126">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="831b3-126">Security is disabled.</span></span>|  
|<span data-ttu-id="831b3-127">Transportu</span><span class="sxs-lookup"><span data-stu-id="831b3-127">Transport</span></span>|<span data-ttu-id="831b3-128">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="831b3-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="831b3-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="831b3-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="831b3-130">Protokół HTTPS zapewnia uwierzytelnianie i poufności.</span><span class="sxs-lookup"><span data-stu-id="831b3-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="831b3-131">Komunikaty protokołu SOAP zawierają typy zaawansowane poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="831b3-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="831b3-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="831b3-132">Child Elements</span></span>  
  
|<span data-ttu-id="831b3-133">Element</span><span class="sxs-lookup"><span data-stu-id="831b3-133">Element</span></span>|<span data-ttu-id="831b3-134">Opis</span><span class="sxs-lookup"><span data-stu-id="831b3-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="831b3-135">\<transport ></span><span class="sxs-lookup"><span data-stu-id="831b3-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="831b3-136">Definiuje typ transportu dla zabezpieczonych wiadomości wysłanych przez elementy równorzędne skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="831b3-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="831b3-137">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="831b3-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="831b3-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="831b3-138">Parent Elements</span></span>  
  
|<span data-ttu-id="831b3-139">Element</span><span class="sxs-lookup"><span data-stu-id="831b3-139">Element</span></span>|<span data-ttu-id="831b3-140">Opis</span><span class="sxs-lookup"><span data-stu-id="831b3-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="831b3-141">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="831b3-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="831b3-142">Definiuje wszystkie możliwości wiązania [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="831b3-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="831b3-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="831b3-143">Remarks</span></span>  
 <span data-ttu-id="831b3-144">Zabezpieczeń może być albo lub transportu specyficzne dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="831b3-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="831b3-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="831b3-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="831b3-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="831b3-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="831b3-147">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="831b3-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="831b3-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="831b3-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="831b3-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="831b3-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="831b3-150">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="831b3-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="831b3-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="831b3-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
