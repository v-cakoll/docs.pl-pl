---
title: <security> dla <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: be5ebacec466caf8d8a77bf552f42da1861e77a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936627"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="9e2aa-102">\<> \<zabezpieczeń elementu webpeerbinding ></span><span class="sxs-lookup"><span data-stu-id="9e2aa-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="9e2aa-103">Definiuje ustawienia [ \<zabezpieczeń > NetPeerTcpBinding](netpeertcpbinding.md), włącznie z typem używanego uwierzytelniania i zabezpieczeniami używanymi do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9e2aa-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="9e2aa-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9e2aa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9e2aa-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="9e2aa-105">\<bindings></span></span>  
<span data-ttu-id="9e2aa-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="9e2aa-106">\<netPeerBinding></span></span>  
<span data-ttu-id="9e2aa-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="9e2aa-107">\<binding></span></span>  
<span data-ttu-id="9e2aa-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="9e2aa-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e2aa-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e2aa-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e2aa-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9e2aa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9e2aa-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9e2aa-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e2aa-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9e2aa-112">Attributes</span></span>  
  
|<span data-ttu-id="9e2aa-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9e2aa-113">Attribute</span></span>|<span data-ttu-id="9e2aa-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9e2aa-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e2aa-115">tryb</span><span class="sxs-lookup"><span data-stu-id="9e2aa-115">mode</span></span>|<span data-ttu-id="9e2aa-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9e2aa-116">Optional.</span></span> <span data-ttu-id="9e2aa-117">Określa typ zabezpieczeń używanych przez elementy równorzędne skonfigurowane przy użyciu tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9e2aa-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="9e2aa-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="9e2aa-118">The default value is `Message`.</span></span> <span data-ttu-id="9e2aa-119">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="9e2aa-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="9e2aa-120">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="9e2aa-120">mode Attribute</span></span>  
  
|<span data-ttu-id="9e2aa-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="9e2aa-121">Value</span></span>|<span data-ttu-id="9e2aa-122">Opis</span><span class="sxs-lookup"><span data-stu-id="9e2aa-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9e2aa-123">Message</span><span class="sxs-lookup"><span data-stu-id="9e2aa-123">Message</span></span>|<span data-ttu-id="9e2aa-124">Zabezpieczenia protokołu SOAP zapewniają uwierzytelnianie, integralność i poufność.</span><span class="sxs-lookup"><span data-stu-id="9e2aa-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="9e2aa-125">Brak</span><span class="sxs-lookup"><span data-stu-id="9e2aa-125">None</span></span>|<span data-ttu-id="9e2aa-126">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="9e2aa-126">Security is disabled.</span></span>|  
|<span data-ttu-id="9e2aa-127">Transportu</span><span class="sxs-lookup"><span data-stu-id="9e2aa-127">Transport</span></span>|<span data-ttu-id="9e2aa-128">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9e2aa-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="9e2aa-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="9e2aa-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="9e2aa-130">Protokół HTTPS zapewnia uwierzytelnianie i poufność.</span><span class="sxs-lookup"><span data-stu-id="9e2aa-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="9e2aa-131">Komunikaty protokołu SOAP zapewniają zaawansowane typy poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="9e2aa-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e2aa-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9e2aa-132">Child Elements</span></span>  
  
|<span data-ttu-id="9e2aa-133">Element</span><span class="sxs-lookup"><span data-stu-id="9e2aa-133">Element</span></span>|<span data-ttu-id="9e2aa-134">Opis</span><span class="sxs-lookup"><span data-stu-id="9e2aa-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e2aa-135">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="9e2aa-135">\<transport></span></span>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="9e2aa-136">Definiuje typ transportu dla zabezpieczonych komunikatów wysyłanych przez elementy równorzędne skonfigurowane przy użyciu tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9e2aa-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="9e2aa-137">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="9e2aa-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9e2aa-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9e2aa-138">Parent Elements</span></span>  
  
|<span data-ttu-id="9e2aa-139">Element</span><span class="sxs-lookup"><span data-stu-id="9e2aa-139">Element</span></span>|<span data-ttu-id="9e2aa-140">Opis</span><span class="sxs-lookup"><span data-stu-id="9e2aa-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e2aa-141">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="9e2aa-141">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="9e2aa-142">Definiuje wszystkie możliwości [ \<powiązań NetPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9e2aa-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e2aa-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e2aa-143">Remarks</span></span>  
 <span data-ttu-id="9e2aa-144">Zabezpieczenia mogą dotyczyć zarówno komunikatów, jak i związanych z transportem.</span><span class="sxs-lookup"><span data-stu-id="9e2aa-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e2aa-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e2aa-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="9e2aa-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="9e2aa-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9e2aa-147">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="9e2aa-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="9e2aa-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="9e2aa-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9e2aa-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="9e2aa-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9e2aa-150">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="9e2aa-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9e2aa-151">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="9e2aa-151">\<binding></span></span>](../../../misc/binding.md)
