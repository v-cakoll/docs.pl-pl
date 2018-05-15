---
title: '&lt;security&gt; w &lt;netPeerBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7413820f1a1f38b3d533573715267df3b85c9d9a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="0135d-102">&lt;security&gt; w &lt;netPeerBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="0135d-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="0135d-103">Definiuje ustawienia zabezpieczeń [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), takich jak typ uwierzytelniania używany i zabezpieczenia używany do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0135d-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="0135d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0135d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0135d-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="0135d-105">\<bindings></span></span>  
<span data-ttu-id="0135d-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="0135d-106">\<netPeerBinding></span></span>  
<span data-ttu-id="0135d-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0135d-107">\<binding></span></span>  
<span data-ttu-id="0135d-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="0135d-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0135d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0135d-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0135d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0135d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0135d-111">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0135d-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0135d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0135d-112">Attributes</span></span>  
  
|<span data-ttu-id="0135d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0135d-113">Attribute</span></span>|<span data-ttu-id="0135d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0135d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0135d-115">tryb</span><span class="sxs-lookup"><span data-stu-id="0135d-115">mode</span></span>|<span data-ttu-id="0135d-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0135d-116">Optional.</span></span> <span data-ttu-id="0135d-117">Określa typ zabezpieczeń używanych przez elementy równorzędne skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="0135d-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="0135d-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="0135d-118">The default value is `Message`.</span></span> <span data-ttu-id="0135d-119">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="0135d-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0135d-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="0135d-120">mode Attribute</span></span>  
  
|<span data-ttu-id="0135d-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="0135d-121">Value</span></span>|<span data-ttu-id="0135d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="0135d-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0135d-123">Komunikat</span><span class="sxs-lookup"><span data-stu-id="0135d-123">Message</span></span>|<span data-ttu-id="0135d-124">Zabezpieczenia protokołu SOAP oferuje uwierzytelniania, integralności i poufności.</span><span class="sxs-lookup"><span data-stu-id="0135d-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="0135d-125">Brak</span><span class="sxs-lookup"><span data-stu-id="0135d-125">None</span></span>|<span data-ttu-id="0135d-126">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="0135d-126">Security is disabled.</span></span>|  
|<span data-ttu-id="0135d-127">Transportu</span><span class="sxs-lookup"><span data-stu-id="0135d-127">Transport</span></span>|<span data-ttu-id="0135d-128">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0135d-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="0135d-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="0135d-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="0135d-130">Protokół HTTPS oferuje uwierzytelnianie i poufności.</span><span class="sxs-lookup"><span data-stu-id="0135d-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="0135d-131">Wiadomości SOAP Podaj sformatowanego poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="0135d-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0135d-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0135d-132">Child Elements</span></span>  
  
|<span data-ttu-id="0135d-133">Element</span><span class="sxs-lookup"><span data-stu-id="0135d-133">Element</span></span>|<span data-ttu-id="0135d-134">Opis</span><span class="sxs-lookup"><span data-stu-id="0135d-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0135d-135">\<transport ></span><span class="sxs-lookup"><span data-stu-id="0135d-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="0135d-136">Definiuje typ transportu zabezpieczonych wiadomości wysyłanych przez elementy równorzędne skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="0135d-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="0135d-137">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="0135d-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0135d-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0135d-138">Parent Elements</span></span>  
  
|<span data-ttu-id="0135d-139">Element</span><span class="sxs-lookup"><span data-stu-id="0135d-139">Element</span></span>|<span data-ttu-id="0135d-140">Opis</span><span class="sxs-lookup"><span data-stu-id="0135d-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0135d-141">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0135d-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0135d-142">Definiuje wszystkie możliwości powiązania [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0135d-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0135d-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0135d-143">Remarks</span></span>  
 <span data-ttu-id="0135d-144">Zabezpieczeń może być albo wiadomości - lub specyficznych dla transportu.</span><span class="sxs-lookup"><span data-stu-id="0135d-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0135d-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0135d-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="0135d-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="0135d-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="0135d-147">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="0135d-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="0135d-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="0135d-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0135d-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="0135d-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0135d-150">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="0135d-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="0135d-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0135d-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
