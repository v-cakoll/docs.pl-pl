---
title: <security> dla <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 3d1ac85073c44f683fe0c054737c5ec7ed1cbf52
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738659"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="b9578-102">> zabezpieczeń \<\<sieci równorzędnej ></span><span class="sxs-lookup"><span data-stu-id="b9578-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="b9578-103">Definiuje ustawienia zabezpieczeń [\<netPeerTcpBinding >](netpeertcpbinding.md), włącznie z typem używanego uwierzytelniania i zabezpieczeniami używanymi do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b9578-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
<span data-ttu-id="b9578-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b9578-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b9578-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="b9578-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b9578-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="b9578-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b9578-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<NetPeerTcpBinding**](netpeertcpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="b9578-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="b9578-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="b9578-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b9578-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpieczenia >**</span><span class="sxs-lookup"><span data-stu-id="b9578-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9578-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9578-110">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9578-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b9578-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b9578-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b9578-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9578-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b9578-113">Attributes</span></span>  
  
|<span data-ttu-id="b9578-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b9578-114">Attribute</span></span>|<span data-ttu-id="b9578-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b9578-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b9578-116">tryb</span><span class="sxs-lookup"><span data-stu-id="b9578-116">mode</span></span>|<span data-ttu-id="b9578-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b9578-117">Optional.</span></span> <span data-ttu-id="b9578-118">Określa typ zabezpieczeń używanych przez elementy równorzędne skonfigurowane przy użyciu tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b9578-118">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="b9578-119">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="b9578-119">The default value is `Message`.</span></span> <span data-ttu-id="b9578-120">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="b9578-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="b9578-121">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="b9578-121">mode Attribute</span></span>  
  
|<span data-ttu-id="b9578-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="b9578-122">Value</span></span>|<span data-ttu-id="b9578-123">Opis</span><span class="sxs-lookup"><span data-stu-id="b9578-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b9578-124">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b9578-124">Message</span></span>|<span data-ttu-id="b9578-125">Zabezpieczenia protokołu SOAP zapewniają uwierzytelnianie, integralność i poufność.</span><span class="sxs-lookup"><span data-stu-id="b9578-125">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="b9578-126">Brak</span><span class="sxs-lookup"><span data-stu-id="b9578-126">None</span></span>|<span data-ttu-id="b9578-127">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="b9578-127">Security is disabled.</span></span>|  
|<span data-ttu-id="b9578-128">Transportu</span><span class="sxs-lookup"><span data-stu-id="b9578-128">Transport</span></span>|<span data-ttu-id="b9578-129">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b9578-129">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="b9578-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="b9578-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="b9578-131">Protokół HTTPS zapewnia uwierzytelnianie i poufność.</span><span class="sxs-lookup"><span data-stu-id="b9578-131">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="b9578-132">Komunikaty protokołu SOAP zapewniają zaawansowane typy poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="b9578-132">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9578-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b9578-133">Child Elements</span></span>  
  
|<span data-ttu-id="b9578-134">Element</span><span class="sxs-lookup"><span data-stu-id="b9578-134">Element</span></span>|<span data-ttu-id="b9578-135">Opis</span><span class="sxs-lookup"><span data-stu-id="b9578-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9578-136">> transportu \<</span><span class="sxs-lookup"><span data-stu-id="b9578-136">\<transport></span></span>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="b9578-137">Definiuje typ transportu dla zabezpieczonych komunikatów wysyłanych przez elementy równorzędne skonfigurowane przy użyciu tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b9578-137">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="b9578-138">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="b9578-138">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b9578-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b9578-139">Parent Elements</span></span>  
  
|<span data-ttu-id="b9578-140">Element</span><span class="sxs-lookup"><span data-stu-id="b9578-140">Element</span></span>|<span data-ttu-id="b9578-141">Opis</span><span class="sxs-lookup"><span data-stu-id="b9578-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9578-142">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="b9578-142">\<binding></span></span>](bindings.md)|<span data-ttu-id="b9578-143">Definiuje wszystkie możliwości powiązań [\<netPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b9578-143">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9578-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9578-144">Remarks</span></span>  
 <span data-ttu-id="b9578-145">Zabezpieczenia mogą dotyczyć zarówno komunikatów, jak i związanych z transportem.</span><span class="sxs-lookup"><span data-stu-id="b9578-145">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9578-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9578-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="b9578-147">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="b9578-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b9578-148">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="b9578-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="b9578-149">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b9578-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b9578-150">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="b9578-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b9578-151">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="b9578-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b9578-152">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="b9578-152">\<binding></span></span>](bindings.md)
