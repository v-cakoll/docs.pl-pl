---
title: <security> dla <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 270ca844f586be256b6483653c868d1cc4396657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399762"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="64b13-102">\<security> dla \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="64b13-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="64b13-103">Zawiera ustawienia zabezpieczeń skojarzone z kanałem równorzędnym, w tym typ używanego uwierzytelniania i zabezpieczenia używane do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="64b13-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="64b13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="64b13-104">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64b13-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="64b13-105">Attributes and Elements</span></span>  
 <span data-ttu-id="64b13-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="64b13-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64b13-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="64b13-107">Attributes</span></span>  
  
|<span data-ttu-id="64b13-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="64b13-108">Attribute</span></span>|<span data-ttu-id="64b13-109">Opis</span><span class="sxs-lookup"><span data-stu-id="64b13-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="64b13-110">Określa typ zabezpieczenia do zastosowania.</span><span class="sxs-lookup"><span data-stu-id="64b13-110">Specifies the type of security to be applied.</span></span> <span data-ttu-id="64b13-111">Wartość domyślna to Message.</span><span class="sxs-lookup"><span data-stu-id="64b13-111">The default value is Message.</span></span> <span data-ttu-id="64b13-112">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="64b13-112">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="64b13-113">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="64b13-113">mode Attribute</span></span>  
  
|<span data-ttu-id="64b13-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="64b13-114">Value</span></span>|<span data-ttu-id="64b13-115">Opis</span><span class="sxs-lookup"><span data-stu-id="64b13-115">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="64b13-116">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="64b13-116">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="64b13-117">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="64b13-117">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="64b13-118">Zabezpieczenia protokołu SOAP zapewniają uwierzytelnianie, integralność i poufność.</span><span class="sxs-lookup"><span data-stu-id="64b13-118">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="64b13-119">Protokół HTTPS zapewnia uwierzytelnianie i poufność.</span><span class="sxs-lookup"><span data-stu-id="64b13-119">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="64b13-120">Komunikaty protokołu SOAP zapewniają zaawansowane typy poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="64b13-120">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64b13-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="64b13-121">Child Elements</span></span>  
  
|<span data-ttu-id="64b13-122">Element</span><span class="sxs-lookup"><span data-stu-id="64b13-122">Element</span></span>|<span data-ttu-id="64b13-123">Opis</span><span class="sxs-lookup"><span data-stu-id="64b13-123">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-peertransport.md)|<span data-ttu-id="64b13-124">Definiuje transport równorzędny dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="64b13-124">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="64b13-125">Ten element ma `clientCredentialType` atrybut, który określa poświadczenia, które mają być używane podczas korzystania z usługi.</span><span class="sxs-lookup"><span data-stu-id="64b13-125">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="64b13-126">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="64b13-126">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="64b13-127">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="64b13-127">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="64b13-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="64b13-128">Parent Elements</span></span>  
  
|<span data-ttu-id="64b13-129">Element</span><span class="sxs-lookup"><span data-stu-id="64b13-129">Element</span></span>|<span data-ttu-id="64b13-130">Opis</span><span class="sxs-lookup"><span data-stu-id="64b13-130">Description</span></span>|  
|-------------|-----------------|  
|[\<peerTransport>](peertransport.md)|<span data-ttu-id="64b13-131">Definiuje transport równorzędny dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="64b13-131">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64b13-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64b13-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="64b13-133">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="64b13-133">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="64b13-134">Transporty</span><span class="sxs-lookup"><span data-stu-id="64b13-134">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="64b13-135">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="64b13-135">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="64b13-136">Powiązania</span><span class="sxs-lookup"><span data-stu-id="64b13-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="64b13-137">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="64b13-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="64b13-138">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="64b13-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
