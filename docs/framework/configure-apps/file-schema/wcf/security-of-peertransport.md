---
title: <security> dla <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: bdd3b236c9bae198f8027c4ca0c0fa5b70d30342
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936636"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="d387f-102">\<zabezpieczenia > \<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="d387f-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="d387f-103">Zawiera ustawienia zabezpieczeń skojarzone z kanałem równorzędnym, w tym typ używanego uwierzytelniania i zabezpieczenia używane do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d387f-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="d387f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d387f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d387f-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="d387f-105">\<bindings></span></span>  
<span data-ttu-id="d387f-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d387f-106">\<customBinding></span></span>  
<span data-ttu-id="d387f-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="d387f-107">\<binding></span></span>  
<span data-ttu-id="d387f-108">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="d387f-108">\<peerTransport></span></span>  
<span data-ttu-id="d387f-109">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d387f-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d387f-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d387f-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d387f-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d387f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d387f-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d387f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d387f-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d387f-113">Attributes</span></span>  
  
|<span data-ttu-id="d387f-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d387f-114">Attribute</span></span>|<span data-ttu-id="d387f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d387f-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="d387f-116">Określa typ zabezpieczenia do zastosowania.</span><span class="sxs-lookup"><span data-stu-id="d387f-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="d387f-117">Wartość domyślna to Message.</span><span class="sxs-lookup"><span data-stu-id="d387f-117">The default value is Message.</span></span> <span data-ttu-id="d387f-118">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d387f-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d387f-119">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="d387f-119">mode Attribute</span></span>  
  
|<span data-ttu-id="d387f-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="d387f-120">Value</span></span>|<span data-ttu-id="d387f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="d387f-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="d387f-122">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="d387f-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="d387f-123">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d387f-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="d387f-124">Zabezpieczenia protokołu SOAP zapewniają uwierzytelnianie, integralność i poufność.</span><span class="sxs-lookup"><span data-stu-id="d387f-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="d387f-125">Protokół HTTPS zapewnia uwierzytelnianie i poufność.</span><span class="sxs-lookup"><span data-stu-id="d387f-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="d387f-126">Komunikaty protokołu SOAP zapewniają zaawansowane typy poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="d387f-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d387f-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d387f-127">Child Elements</span></span>  
  
|<span data-ttu-id="d387f-128">Element</span><span class="sxs-lookup"><span data-stu-id="d387f-128">Element</span></span>|<span data-ttu-id="d387f-129">Opis</span><span class="sxs-lookup"><span data-stu-id="d387f-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d387f-130">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="d387f-130">\<transport></span></span>](transport-of-peertransport.md)|<span data-ttu-id="d387f-131">Definiuje transport równorzędny dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d387f-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="d387f-132">Ten element ma `clientCredentialType` atrybut, który określa poświadczenia, które mają być używane podczas korzystania z usługi.</span><span class="sxs-lookup"><span data-stu-id="d387f-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="d387f-133">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d387f-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="d387f-134">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="d387f-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d387f-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d387f-135">Parent Elements</span></span>  
  
|<span data-ttu-id="d387f-136">Element</span><span class="sxs-lookup"><span data-stu-id="d387f-136">Element</span></span>|<span data-ttu-id="d387f-137">Opis</span><span class="sxs-lookup"><span data-stu-id="d387f-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d387f-138">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="d387f-138">\<peerTransport></span></span>](peertransport.md)|<span data-ttu-id="d387f-139">Definiuje transport równorzędny dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d387f-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d387f-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d387f-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d387f-141">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="d387f-141">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="d387f-142">Transporty</span><span class="sxs-lookup"><span data-stu-id="d387f-142">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="d387f-143">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="d387f-143">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="d387f-144">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d387f-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d387f-145">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="d387f-145">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d387f-146">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="d387f-146">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d387f-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d387f-147">\<customBinding></span></span>](custombinding.md)
