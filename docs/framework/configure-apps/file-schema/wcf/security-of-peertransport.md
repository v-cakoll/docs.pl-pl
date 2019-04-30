---
title: <security> dla <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 1aff79bf5867a3a1ebe05e3f812475dac4b413e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670498"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="ead54-102">\<Zabezpieczenia > z \<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="ead54-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="ead54-103">Zawiera ustawienia zabezpieczenia skojarzone z równorzędnym kanałem, takie jak typ uwierzytelniania i zabezpieczenia używany do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ead54-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="ead54-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ead54-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ead54-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="ead54-105">\<bindings></span></span>  
<span data-ttu-id="ead54-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ead54-106">\<customBinding></span></span>  
<span data-ttu-id="ead54-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="ead54-107">\<binding></span></span>  
<span data-ttu-id="ead54-108">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="ead54-108">\<peerTransport></span></span>  
<span data-ttu-id="ead54-109">\<security></span><span class="sxs-lookup"><span data-stu-id="ead54-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ead54-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ead54-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ead54-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ead54-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ead54-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ead54-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ead54-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ead54-113">Attributes</span></span>  
  
|<span data-ttu-id="ead54-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ead54-114">Attribute</span></span>|<span data-ttu-id="ead54-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ead54-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="ead54-116">Określa typ zabezpieczenia do zastosowania.</span><span class="sxs-lookup"><span data-stu-id="ead54-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="ead54-117">Wartość domyślna to wiadomość.</span><span class="sxs-lookup"><span data-stu-id="ead54-117">The default value is Message.</span></span> <span data-ttu-id="ead54-118">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ead54-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="ead54-119">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="ead54-119">mode Attribute</span></span>  
  
|<span data-ttu-id="ead54-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="ead54-120">Value</span></span>|<span data-ttu-id="ead54-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ead54-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="ead54-122">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ead54-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="ead54-123">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ead54-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="ead54-124">Zabezpieczenia protokołu SOAP zapewnia uwierzytelnianie, integralności i poufności.</span><span class="sxs-lookup"><span data-stu-id="ead54-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="ead54-125">Protokół HTTPS zapewnia uwierzytelnianie i poufności.</span><span class="sxs-lookup"><span data-stu-id="ead54-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="ead54-126">Komunikaty protokołu SOAP zawierają typy zaawansowane poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="ead54-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ead54-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ead54-127">Child Elements</span></span>  
  
|<span data-ttu-id="ead54-128">Element</span><span class="sxs-lookup"><span data-stu-id="ead54-128">Element</span></span>|<span data-ttu-id="ead54-129">Opis</span><span class="sxs-lookup"><span data-stu-id="ead54-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ead54-130">\<transport></span><span class="sxs-lookup"><span data-stu-id="ead54-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="ead54-131">Definiuje transport elementu równorzędnego dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ead54-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="ead54-132">Ten element ma `clientCredentialType` atrybut, który określa poświadczenia, które mają być używane podczas interakcji z usługą.</span><span class="sxs-lookup"><span data-stu-id="ead54-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="ead54-133">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="ead54-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="ead54-134">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="ead54-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ead54-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ead54-135">Parent Elements</span></span>  
  
|<span data-ttu-id="ead54-136">Element</span><span class="sxs-lookup"><span data-stu-id="ead54-136">Element</span></span>|<span data-ttu-id="ead54-137">Opis</span><span class="sxs-lookup"><span data-stu-id="ead54-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ead54-138">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="ead54-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="ead54-139">Definiuje transport elementu równorzędnego dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ead54-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ead54-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ead54-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ead54-141">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="ead54-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="ead54-142">Transporty</span><span class="sxs-lookup"><span data-stu-id="ead54-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="ead54-143">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="ead54-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="ead54-144">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ead54-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="ead54-145">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="ead54-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ead54-146">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ead54-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="ead54-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ead54-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
