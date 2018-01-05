---
title: '&lt;security&gt; w &lt;netPeerBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b9228ccbed2b0f612986d59b72c920d57f38f69a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="0e357-102">&lt;security&gt; w &lt;netPeerBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="0e357-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="0e357-103">Definiuje ustawienia zabezpieczeń [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), takich jak typ uwierzytelniania używany i zabezpieczenia używany do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0e357-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="0e357-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0e357-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0e357-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="0e357-105">\<bindings></span></span>  
<span data-ttu-id="0e357-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="0e357-106">\<netPeerBinding></span></span>  
<span data-ttu-id="0e357-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0e357-107">\<binding></span></span>  
<span data-ttu-id="0e357-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="0e357-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e357-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e357-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e357-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0e357-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0e357-111">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0e357-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e357-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0e357-112">Attributes</span></span>  
  
|<span data-ttu-id="0e357-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0e357-113">Attribute</span></span>|<span data-ttu-id="0e357-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0e357-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0e357-115">tryb</span><span class="sxs-lookup"><span data-stu-id="0e357-115">mode</span></span>|<span data-ttu-id="0e357-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0e357-116">Optional.</span></span> <span data-ttu-id="0e357-117">Określa typ zabezpieczeń używanych przez elementy równorzędne skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="0e357-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="0e357-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="0e357-118">The default value is `Message`.</span></span> <span data-ttu-id="0e357-119">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="0e357-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0e357-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="0e357-120">mode Attribute</span></span>  
  
|<span data-ttu-id="0e357-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="0e357-121">Value</span></span>|<span data-ttu-id="0e357-122">Opis</span><span class="sxs-lookup"><span data-stu-id="0e357-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e357-123">Komunikat</span><span class="sxs-lookup"><span data-stu-id="0e357-123">Message</span></span>|<span data-ttu-id="0e357-124">Zabezpieczenia protokołu SOAP oferuje uwierzytelniania, integralności i poufności.</span><span class="sxs-lookup"><span data-stu-id="0e357-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="0e357-125">Brak</span><span class="sxs-lookup"><span data-stu-id="0e357-125">None</span></span>|<span data-ttu-id="0e357-126">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="0e357-126">Security is disabled.</span></span>|  
|<span data-ttu-id="0e357-127">Transportu</span><span class="sxs-lookup"><span data-stu-id="0e357-127">Transport</span></span>|<span data-ttu-id="0e357-128">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0e357-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="0e357-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="0e357-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="0e357-130">Protokół HTTPS oferuje uwierzytelnianie i poufności.</span><span class="sxs-lookup"><span data-stu-id="0e357-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="0e357-131">Wiadomości SOAP Podaj sformatowanego poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="0e357-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e357-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0e357-132">Child Elements</span></span>  
  
|<span data-ttu-id="0e357-133">Element</span><span class="sxs-lookup"><span data-stu-id="0e357-133">Element</span></span>|<span data-ttu-id="0e357-134">Opis</span><span class="sxs-lookup"><span data-stu-id="0e357-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e357-135">\<transport ></span><span class="sxs-lookup"><span data-stu-id="0e357-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="0e357-136">Definiuje typ transportu zabezpieczonych wiadomości wysyłanych przez elementy równorzędne skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="0e357-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="0e357-137">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="0e357-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e357-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0e357-138">Parent Elements</span></span>  
  
|<span data-ttu-id="0e357-139">Element</span><span class="sxs-lookup"><span data-stu-id="0e357-139">Element</span></span>|<span data-ttu-id="0e357-140">Opis</span><span class="sxs-lookup"><span data-stu-id="0e357-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e357-141">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0e357-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0e357-142">Definiuje wszystkie możliwości powiązania [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0e357-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e357-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e357-143">Remarks</span></span>  
 <span data-ttu-id="0e357-144">Zabezpieczeń może być albo wiadomości - lub specyficznych dla transportu.</span><span class="sxs-lookup"><span data-stu-id="0e357-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e357-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e357-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="0e357-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="0e357-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="0e357-147">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="0e357-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="0e357-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="0e357-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0e357-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="0e357-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0e357-150">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="0e357-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="0e357-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0e357-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
