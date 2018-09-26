---
title: '&lt;security&gt; w &lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
author: BrucePerlerMS
ms.openlocfilehash: 152087550d3fa881a7a88271d9c91dfcc5c894c8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176763"
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a><span data-ttu-id="bc614-102">&lt;security&gt; w &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="bc614-102">&lt;security&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="bc614-103">Zawiera ustawienia zabezpieczenia skojarzone z równorzędnym kanałem, takie jak typ uwierzytelniania i zabezpieczenia używany do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bc614-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="bc614-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bc614-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bc614-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="bc614-105">\<bindings></span></span>  
<span data-ttu-id="bc614-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bc614-106">\<customBinding></span></span>  
<span data-ttu-id="bc614-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="bc614-107">\<binding></span></span>  
<span data-ttu-id="bc614-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="bc614-108">\<peerTransport></span></span>  
<span data-ttu-id="bc614-109">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="bc614-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc614-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc614-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">  
    <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
</security  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc614-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bc614-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bc614-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bc614-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc614-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bc614-113">Attributes</span></span>  
  
|<span data-ttu-id="bc614-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bc614-114">Attribute</span></span>|<span data-ttu-id="bc614-115">Opis</span><span class="sxs-lookup"><span data-stu-id="bc614-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="bc614-116">Określa typ zabezpieczenia do zastosowania.</span><span class="sxs-lookup"><span data-stu-id="bc614-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="bc614-117">Wartość domyślna to wiadomość.</span><span class="sxs-lookup"><span data-stu-id="bc614-117">The default value is Message.</span></span> <span data-ttu-id="bc614-118">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="bc614-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="bc614-119">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="bc614-119">mode Attribute</span></span>  
  
|<span data-ttu-id="bc614-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="bc614-120">Value</span></span>|<span data-ttu-id="bc614-121">Opis</span><span class="sxs-lookup"><span data-stu-id="bc614-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="bc614-122">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="bc614-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="bc614-123">Zabezpieczenia przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bc614-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="bc614-124">Zabezpieczenia protokołu SOAP zapewnia uwierzytelnianie, integralności i poufności.</span><span class="sxs-lookup"><span data-stu-id="bc614-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="bc614-125">Protokół HTTPS zapewnia uwierzytelnianie i poufności.</span><span class="sxs-lookup"><span data-stu-id="bc614-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="bc614-126">Komunikaty protokołu SOAP zawierają typy zaawansowane poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="bc614-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc614-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bc614-127">Child Elements</span></span>  
  
|<span data-ttu-id="bc614-128">Element</span><span class="sxs-lookup"><span data-stu-id="bc614-128">Element</span></span>|<span data-ttu-id="bc614-129">Opis</span><span class="sxs-lookup"><span data-stu-id="bc614-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc614-130">\<transport ></span><span class="sxs-lookup"><span data-stu-id="bc614-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="bc614-131">Definiuje transport elementu równorzędnego dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="bc614-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="bc614-132">Ten element ma `clientCredentialType` atrybut, który określa poświadczenia, które mają być używane podczas interakcji z usługą.</span><span class="sxs-lookup"><span data-stu-id="bc614-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="bc614-133">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="bc614-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="bc614-134">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="bc614-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bc614-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bc614-135">Parent Elements</span></span>  
  
|<span data-ttu-id="bc614-136">Element</span><span class="sxs-lookup"><span data-stu-id="bc614-136">Element</span></span>|<span data-ttu-id="bc614-137">Opis</span><span class="sxs-lookup"><span data-stu-id="bc614-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc614-138">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="bc614-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="bc614-139">Definiuje transport elementu równorzędnego dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="bc614-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc614-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc614-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="bc614-141">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="bc614-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="bc614-142">Transporty</span><span class="sxs-lookup"><span data-stu-id="bc614-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="bc614-143">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="bc614-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="bc614-144">Powiązania</span><span class="sxs-lookup"><span data-stu-id="bc614-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bc614-145">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="bc614-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="bc614-146">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="bc614-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="bc614-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bc614-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
