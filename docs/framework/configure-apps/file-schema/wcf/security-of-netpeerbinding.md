---
title: '&lt;security&gt; w &lt;netPeerBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
ms.openlocfilehash: 1d7ffaf72e34b700f4702b2e531afbf7e842de09
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844569"
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="c9757-102">&lt;security&gt; w &lt;netPeerBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="c9757-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="c9757-103">Definiuje ustawienia zabezpieczeń [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), takie jak typ uwierzytelniania używany i zabezpieczenia używany do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c9757-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="c9757-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c9757-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c9757-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c9757-105">\<bindings></span></span>  
<span data-ttu-id="c9757-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="c9757-106">\<netPeerBinding></span></span>  
<span data-ttu-id="c9757-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c9757-107">\<binding></span></span>  
<span data-ttu-id="c9757-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="c9757-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9757-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9757-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9757-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c9757-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c9757-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c9757-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9757-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c9757-112">Attributes</span></span>  
  
|<span data-ttu-id="c9757-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c9757-113">Attribute</span></span>|<span data-ttu-id="c9757-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c9757-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9757-115">tryb</span><span class="sxs-lookup"><span data-stu-id="c9757-115">mode</span></span>|<span data-ttu-id="c9757-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="c9757-116">Optional.</span></span> <span data-ttu-id="c9757-117">Określa typ zabezpieczeń używanych przez elementy równorzędne skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="c9757-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="c9757-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="c9757-118">The default value is `Message`.</span></span> <span data-ttu-id="c9757-119">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="c9757-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="c9757-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="c9757-120">mode Attribute</span></span>  
  
|<span data-ttu-id="c9757-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="c9757-121">Value</span></span>|<span data-ttu-id="c9757-122">Opis</span><span class="sxs-lookup"><span data-stu-id="c9757-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9757-123">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c9757-123">Message</span></span>|<span data-ttu-id="c9757-124">Zabezpieczenia protokołu SOAP zapewnia uwierzytelnianie, integralności i poufności.</span><span class="sxs-lookup"><span data-stu-id="c9757-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="c9757-125">Brak</span><span class="sxs-lookup"><span data-stu-id="c9757-125">None</span></span>|<span data-ttu-id="c9757-126">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="c9757-126">Security is disabled.</span></span>|  
|<span data-ttu-id="c9757-127">Transportu</span><span class="sxs-lookup"><span data-stu-id="c9757-127">Transport</span></span>|<span data-ttu-id="c9757-128">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c9757-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="c9757-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="c9757-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="c9757-130">Protokół HTTPS zapewnia uwierzytelnianie i poufności.</span><span class="sxs-lookup"><span data-stu-id="c9757-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="c9757-131">Komunikaty protokołu SOAP zawierają typy zaawansowane poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="c9757-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9757-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c9757-132">Child Elements</span></span>  
  
|<span data-ttu-id="c9757-133">Element</span><span class="sxs-lookup"><span data-stu-id="c9757-133">Element</span></span>|<span data-ttu-id="c9757-134">Opis</span><span class="sxs-lookup"><span data-stu-id="c9757-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9757-135">\<transport ></span><span class="sxs-lookup"><span data-stu-id="c9757-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="c9757-136">Definiuje typ transportu dla zabezpieczonych wiadomości wysłanych przez elementy równorzędne skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="c9757-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="c9757-137">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="c9757-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c9757-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c9757-138">Parent Elements</span></span>  
  
|<span data-ttu-id="c9757-139">Element</span><span class="sxs-lookup"><span data-stu-id="c9757-139">Element</span></span>|<span data-ttu-id="c9757-140">Opis</span><span class="sxs-lookup"><span data-stu-id="c9757-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9757-141">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c9757-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c9757-142">Definiuje wszystkie możliwości wiązania [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c9757-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9757-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9757-143">Remarks</span></span>  
 <span data-ttu-id="c9757-144">Zabezpieczeń może być albo lub transportu specyficzne dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c9757-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9757-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9757-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="c9757-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="c9757-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="c9757-147">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="c9757-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="c9757-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c9757-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c9757-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="c9757-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="c9757-150">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="c9757-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="c9757-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c9757-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
