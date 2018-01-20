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
ms.openlocfilehash: c8e979768bdc9a8f78fb97c6c7838e44e81b52ac
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="04e9a-102">&lt;security&gt; w &lt;netPeerBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="04e9a-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="04e9a-103">Definiuje ustawienia zabezpieczeń [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), takich jak typ uwierzytelniania używany i zabezpieczenia używany do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="04e9a-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="04e9a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="04e9a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="04e9a-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="04e9a-105">\<bindings></span></span>  
<span data-ttu-id="04e9a-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="04e9a-106">\<netPeerBinding></span></span>  
<span data-ttu-id="04e9a-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="04e9a-107">\<binding></span></span>  
<span data-ttu-id="04e9a-108">\<security></span><span class="sxs-lookup"><span data-stu-id="04e9a-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e9a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="04e9a-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04e9a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="04e9a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="04e9a-111">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="04e9a-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04e9a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="04e9a-112">Attributes</span></span>  
  
|<span data-ttu-id="04e9a-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="04e9a-113">Attribute</span></span>|<span data-ttu-id="04e9a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="04e9a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04e9a-115">tryb</span><span class="sxs-lookup"><span data-stu-id="04e9a-115">mode</span></span>|<span data-ttu-id="04e9a-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="04e9a-116">Optional.</span></span> <span data-ttu-id="04e9a-117">Określa typ zabezpieczeń używanych przez elementy równorzędne skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="04e9a-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="04e9a-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="04e9a-118">The default value is `Message`.</span></span> <span data-ttu-id="04e9a-119">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="04e9a-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="04e9a-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="04e9a-120">mode Attribute</span></span>  
  
|<span data-ttu-id="04e9a-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="04e9a-121">Value</span></span>|<span data-ttu-id="04e9a-122">Opis</span><span class="sxs-lookup"><span data-stu-id="04e9a-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04e9a-123">Komunikat</span><span class="sxs-lookup"><span data-stu-id="04e9a-123">Message</span></span>|<span data-ttu-id="04e9a-124">Zabezpieczenia protokołu SOAP oferuje uwierzytelniania, integralności i poufności.</span><span class="sxs-lookup"><span data-stu-id="04e9a-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="04e9a-125">Brak</span><span class="sxs-lookup"><span data-stu-id="04e9a-125">None</span></span>|<span data-ttu-id="04e9a-126">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="04e9a-126">Security is disabled.</span></span>|  
|<span data-ttu-id="04e9a-127">Transportu</span><span class="sxs-lookup"><span data-stu-id="04e9a-127">Transport</span></span>|<span data-ttu-id="04e9a-128">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="04e9a-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="04e9a-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="04e9a-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="04e9a-130">Protokół HTTPS oferuje uwierzytelnianie i poufności.</span><span class="sxs-lookup"><span data-stu-id="04e9a-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="04e9a-131">Wiadomości SOAP Podaj sformatowanego poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="04e9a-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04e9a-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="04e9a-132">Child Elements</span></span>  
  
|<span data-ttu-id="04e9a-133">Element</span><span class="sxs-lookup"><span data-stu-id="04e9a-133">Element</span></span>|<span data-ttu-id="04e9a-134">Opis</span><span class="sxs-lookup"><span data-stu-id="04e9a-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04e9a-135">\<transport ></span><span class="sxs-lookup"><span data-stu-id="04e9a-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="04e9a-136">Definiuje typ transportu zabezpieczonych wiadomości wysyłanych przez elementy równorzędne skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="04e9a-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="04e9a-137">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="04e9a-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="04e9a-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="04e9a-138">Parent Elements</span></span>  
  
|<span data-ttu-id="04e9a-139">Element</span><span class="sxs-lookup"><span data-stu-id="04e9a-139">Element</span></span>|<span data-ttu-id="04e9a-140">Opis</span><span class="sxs-lookup"><span data-stu-id="04e9a-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04e9a-141">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="04e9a-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="04e9a-142">Definiuje wszystkie możliwości powiązania [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="04e9a-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04e9a-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04e9a-143">Remarks</span></span>  
 <span data-ttu-id="04e9a-144">Zabezpieczeń może być albo wiadomości - lub specyficznych dla transportu.</span><span class="sxs-lookup"><span data-stu-id="04e9a-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e9a-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04e9a-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="04e9a-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="04e9a-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="04e9a-147">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="04e9a-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="04e9a-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="04e9a-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="04e9a-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="04e9a-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="04e9a-150">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="04e9a-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="04e9a-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="04e9a-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
