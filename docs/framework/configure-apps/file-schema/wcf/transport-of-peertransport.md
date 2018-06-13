---
title: '&lt;transport&gt; w &lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: aeadf23b4ae6b4b0be18755c43585cbfea418567
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756426"
---
# <a name="lttransportgt-of-ltpeertransportgt"></a><span data-ttu-id="f6a20-102">&lt;transport&gt; w &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="f6a20-102">&lt;transport&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="f6a20-103">Określa typ transportu zabezpieczonych wiadomości wysyłanych przez elementy równorzędne skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="f6a20-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="f6a20-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f6a20-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f6a20-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="f6a20-105">\<bindings></span></span>  
<span data-ttu-id="f6a20-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f6a20-106">\<customBinding></span></span>  
<span data-ttu-id="f6a20-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f6a20-107">\<binding></span></span>  
<span data-ttu-id="f6a20-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="f6a20-108">\<peerTransport></span></span>  
<span data-ttu-id="f6a20-109">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="f6a20-109">\<security></span></span>  
<span data-ttu-id="f6a20-110">\<transport></span><span class="sxs-lookup"><span data-stu-id="f6a20-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6a20-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6a20-111">Syntax</span></span>  
  
```xml  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6a20-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f6a20-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f6a20-113">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f6a20-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6a20-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f6a20-114">Attributes</span></span>  
  
|<span data-ttu-id="f6a20-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f6a20-115">Attribute</span></span>|<span data-ttu-id="f6a20-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f6a20-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6a20-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="f6a20-117">credentialType</span></span>|<span data-ttu-id="f6a20-118">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f6a20-118">Optional.</span></span> <span data-ttu-id="f6a20-119">Określa poświadczenia używane do weryfikowania wiadomości wysyłane z transportu elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="f6a20-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="f6a20-120">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="f6a20-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="f6a20-121">credentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="f6a20-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="f6a20-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="f6a20-122">Value</span></span>|<span data-ttu-id="f6a20-123">Opis</span><span class="sxs-lookup"><span data-stu-id="f6a20-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f6a20-124">certyfikat</span><span class="sxs-lookup"><span data-stu-id="f6a20-124">Certificate</span></span>|<span data-ttu-id="f6a20-125">Uwierzytelnianie kanał transportowy peer wymaga X509 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="f6a20-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="f6a20-126">Hasło</span><span class="sxs-lookup"><span data-stu-id="f6a20-126">Password</span></span>|<span data-ttu-id="f6a20-127">Uwierzytelnianie kanał transportowy peer wymaga poprawne hasło.</span><span class="sxs-lookup"><span data-stu-id="f6a20-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6a20-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f6a20-128">Child Elements</span></span>  
 <span data-ttu-id="f6a20-129">Brak</span><span class="sxs-lookup"><span data-stu-id="f6a20-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6a20-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f6a20-130">Parent Elements</span></span>  
  
|<span data-ttu-id="f6a20-131">Element</span><span class="sxs-lookup"><span data-stu-id="f6a20-131">Element</span></span>|<span data-ttu-id="f6a20-132">Opis</span><span class="sxs-lookup"><span data-stu-id="f6a20-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6a20-133">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="f6a20-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="f6a20-134">Definiuje ustawienia zabezpieczeń transportu elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="f6a20-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6a20-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6a20-135">Remarks</span></span>  
 <span data-ttu-id="f6a20-136">Ten element jest ustawiona tylko wtedy, gdy atrybut tryb [ \<zabezpieczeń >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) ustawiono `Transport` lub `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="f6a20-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6a20-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6a20-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="f6a20-138">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="f6a20-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="f6a20-139">Transporty</span><span class="sxs-lookup"><span data-stu-id="f6a20-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="f6a20-140">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="f6a20-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="f6a20-141">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f6a20-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f6a20-142">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f6a20-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f6a20-143">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f6a20-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f6a20-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f6a20-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
