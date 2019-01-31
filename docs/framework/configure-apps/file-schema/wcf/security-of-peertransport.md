---
title: <security> z <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: aadf2058c66cea4919d5dc9aa5aeab7850fcc395
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283767"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="291e7-102">\<Zabezpieczenia > z \<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="291e7-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="291e7-103">Zawiera ustawienia zabezpieczenia skojarzone z równorzędnym kanałem, takie jak typ uwierzytelniania i zabezpieczenia używany do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="291e7-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="291e7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="291e7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="291e7-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="291e7-105">\<bindings></span></span>  
<span data-ttu-id="291e7-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="291e7-106">\<customBinding></span></span>  
<span data-ttu-id="291e7-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="291e7-107">\<binding></span></span>  
<span data-ttu-id="291e7-108">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="291e7-108">\<peerTransport></span></span>  
<span data-ttu-id="291e7-109">\<security></span><span class="sxs-lookup"><span data-stu-id="291e7-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="291e7-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="291e7-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="291e7-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="291e7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="291e7-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="291e7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="291e7-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="291e7-113">Attributes</span></span>  
  
|<span data-ttu-id="291e7-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="291e7-114">Attribute</span></span>|<span data-ttu-id="291e7-115">Opis</span><span class="sxs-lookup"><span data-stu-id="291e7-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="291e7-116">Określa typ zabezpieczenia do zastosowania.</span><span class="sxs-lookup"><span data-stu-id="291e7-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="291e7-117">Wartość domyślna to wiadomość.</span><span class="sxs-lookup"><span data-stu-id="291e7-117">The default value is Message.</span></span> <span data-ttu-id="291e7-118">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="291e7-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="291e7-119">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="291e7-119">mode Attribute</span></span>  
  
|<span data-ttu-id="291e7-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="291e7-120">Value</span></span>|<span data-ttu-id="291e7-121">Opis</span><span class="sxs-lookup"><span data-stu-id="291e7-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="291e7-122">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="291e7-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="291e7-123">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="291e7-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="291e7-124">Zabezpieczenia protokołu SOAP zapewnia uwierzytelnianie, integralności i poufności.</span><span class="sxs-lookup"><span data-stu-id="291e7-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="291e7-125">Protokół HTTPS zapewnia uwierzytelnianie i poufności.</span><span class="sxs-lookup"><span data-stu-id="291e7-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="291e7-126">Komunikaty protokołu SOAP zawierają typy zaawansowane poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="291e7-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="291e7-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="291e7-127">Child Elements</span></span>  
  
|<span data-ttu-id="291e7-128">Element</span><span class="sxs-lookup"><span data-stu-id="291e7-128">Element</span></span>|<span data-ttu-id="291e7-129">Opis</span><span class="sxs-lookup"><span data-stu-id="291e7-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="291e7-130">\<transport></span><span class="sxs-lookup"><span data-stu-id="291e7-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="291e7-131">Definiuje transport elementu równorzędnego dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="291e7-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="291e7-132">Ten element ma `clientCredentialType` atrybut, który określa poświadczenia, które mają być używane podczas interakcji z usługą.</span><span class="sxs-lookup"><span data-stu-id="291e7-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="291e7-133">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="291e7-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="291e7-134">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="291e7-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="291e7-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="291e7-135">Parent Elements</span></span>  
  
|<span data-ttu-id="291e7-136">Element</span><span class="sxs-lookup"><span data-stu-id="291e7-136">Element</span></span>|<span data-ttu-id="291e7-137">Opis</span><span class="sxs-lookup"><span data-stu-id="291e7-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="291e7-138">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="291e7-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="291e7-139">Definiuje transport elementu równorzędnego dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="291e7-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="291e7-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="291e7-140">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="291e7-141">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="291e7-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="291e7-142">Transporty</span><span class="sxs-lookup"><span data-stu-id="291e7-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="291e7-143">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="291e7-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="291e7-144">Powiązania</span><span class="sxs-lookup"><span data-stu-id="291e7-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="291e7-145">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="291e7-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="291e7-146">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="291e7-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="291e7-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="291e7-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
