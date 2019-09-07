---
title: <security> dla <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 270ca844f586be256b6483653c868d1cc4396657
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399762"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="ff993-102">\<zabezpieczenia > \<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="ff993-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="ff993-103">Zawiera ustawienia zabezpieczeń skojarzone z kanałem równorzędnym, w tym typ używanego uwierzytelniania i zabezpieczenia używane do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ff993-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
<span data-ttu-id="ff993-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ff993-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ff993-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ff993-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ff993-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="ff993-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ff993-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="ff993-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="ff993-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="ff993-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="ff993-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<peerTransport >** ](peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="ff993-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)</span></span>\
<span data-ttu-id="ff993-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpieczeń**</span><span class="sxs-lookup"><span data-stu-id="ff993-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff993-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff993-111">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff993-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ff993-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ff993-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ff993-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff993-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ff993-114">Attributes</span></span>  
  
|<span data-ttu-id="ff993-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ff993-115">Attribute</span></span>|<span data-ttu-id="ff993-116">Opis</span><span class="sxs-lookup"><span data-stu-id="ff993-116">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="ff993-117">Określa typ zabezpieczenia do zastosowania.</span><span class="sxs-lookup"><span data-stu-id="ff993-117">Specifies the type of security to be applied.</span></span> <span data-ttu-id="ff993-118">Wartość domyślna to Message.</span><span class="sxs-lookup"><span data-stu-id="ff993-118">The default value is Message.</span></span> <span data-ttu-id="ff993-119">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ff993-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="ff993-120">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="ff993-120">mode Attribute</span></span>  
  
|<span data-ttu-id="ff993-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="ff993-121">Value</span></span>|<span data-ttu-id="ff993-122">Opis</span><span class="sxs-lookup"><span data-stu-id="ff993-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="ff993-123">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ff993-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="ff993-124">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ff993-124">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="ff993-125">Zabezpieczenia protokołu SOAP zapewniają uwierzytelnianie, integralność i poufność.</span><span class="sxs-lookup"><span data-stu-id="ff993-125">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="ff993-126">Protokół HTTPS zapewnia uwierzytelnianie i poufność.</span><span class="sxs-lookup"><span data-stu-id="ff993-126">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="ff993-127">Komunikaty protokołu SOAP zapewniają zaawansowane typy poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="ff993-127">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff993-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ff993-128">Child Elements</span></span>  
  
|<span data-ttu-id="ff993-129">Element</span><span class="sxs-lookup"><span data-stu-id="ff993-129">Element</span></span>|<span data-ttu-id="ff993-130">Opis</span><span class="sxs-lookup"><span data-stu-id="ff993-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff993-131">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="ff993-131">\<transport></span></span>](transport-of-peertransport.md)|<span data-ttu-id="ff993-132">Definiuje transport równorzędny dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ff993-132">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="ff993-133">Ten element ma `clientCredentialType` atrybut, który określa poświadczenia, które mają być używane podczas korzystania z usługi.</span><span class="sxs-lookup"><span data-stu-id="ff993-133">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="ff993-134">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="ff993-134">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="ff993-135">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="ff993-135">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff993-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ff993-136">Parent Elements</span></span>  
  
|<span data-ttu-id="ff993-137">Element</span><span class="sxs-lookup"><span data-stu-id="ff993-137">Element</span></span>|<span data-ttu-id="ff993-138">Opis</span><span class="sxs-lookup"><span data-stu-id="ff993-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff993-139">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="ff993-139">\<peerTransport></span></span>](peertransport.md)|<span data-ttu-id="ff993-140">Definiuje transport równorzędny dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ff993-140">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff993-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff993-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ff993-142">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="ff993-142">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="ff993-143">Transporty</span><span class="sxs-lookup"><span data-stu-id="ff993-143">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="ff993-144">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="ff993-144">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="ff993-145">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ff993-145">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ff993-146">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="ff993-146">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ff993-147">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ff993-147">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="ff993-148">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ff993-148">\<customBinding></span></span>](custombinding.md)
