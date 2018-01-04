---
title: '&lt;transport&gt; w &lt;peerTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8bb0fbce0d7b45fd051db187cd6d7e920b08cab3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltpeertransportgt"></a><span data-ttu-id="b70ce-102">&lt;transport&gt; w &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="b70ce-102">&lt;transport&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="b70ce-103">Określa typ transportu zabezpieczonych wiadomości wysyłanych przez elementy równorzędne skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="b70ce-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="b70ce-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b70ce-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b70ce-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b70ce-105">\<bindings></span></span>  
<span data-ttu-id="b70ce-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b70ce-106">\<customBinding></span></span>  
<span data-ttu-id="b70ce-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b70ce-107">\<binding></span></span>  
<span data-ttu-id="b70ce-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="b70ce-108">\<peerTransport></span></span>  
<span data-ttu-id="b70ce-109">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="b70ce-109">\<security></span></span>  
<span data-ttu-id="b70ce-110">\<transport ></span><span class="sxs-lookup"><span data-stu-id="b70ce-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b70ce-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="b70ce-111">Syntax</span></span>  
  
```xml  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b70ce-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b70ce-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b70ce-113">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b70ce-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b70ce-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b70ce-114">Attributes</span></span>  
  
|<span data-ttu-id="b70ce-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b70ce-115">Attribute</span></span>|<span data-ttu-id="b70ce-116">Opis</span><span class="sxs-lookup"><span data-stu-id="b70ce-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b70ce-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="b70ce-117">credentialType</span></span>|<span data-ttu-id="b70ce-118">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b70ce-118">Optional.</span></span> <span data-ttu-id="b70ce-119">Określa poświadczenia używane do weryfikowania wiadomości wysyłane z transportu elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="b70ce-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="b70ce-120">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="b70ce-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="b70ce-121">credentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="b70ce-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="b70ce-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="b70ce-122">Value</span></span>|<span data-ttu-id="b70ce-123">Opis</span><span class="sxs-lookup"><span data-stu-id="b70ce-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b70ce-124">certyfikat</span><span class="sxs-lookup"><span data-stu-id="b70ce-124">Certificate</span></span>|<span data-ttu-id="b70ce-125">Uwierzytelnianie kanał transportowy peer wymaga X509 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="b70ce-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="b70ce-126">Hasło</span><span class="sxs-lookup"><span data-stu-id="b70ce-126">Password</span></span>|<span data-ttu-id="b70ce-127">Uwierzytelnianie kanał transportowy peer wymaga poprawne hasło.</span><span class="sxs-lookup"><span data-stu-id="b70ce-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b70ce-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b70ce-128">Child Elements</span></span>  
 <span data-ttu-id="b70ce-129">Brak</span><span class="sxs-lookup"><span data-stu-id="b70ce-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b70ce-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b70ce-130">Parent Elements</span></span>  
  
|<span data-ttu-id="b70ce-131">Element</span><span class="sxs-lookup"><span data-stu-id="b70ce-131">Element</span></span>|<span data-ttu-id="b70ce-132">Opis</span><span class="sxs-lookup"><span data-stu-id="b70ce-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b70ce-133">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="b70ce-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="b70ce-134">Definiuje ustawienia zabezpieczeń transportu elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="b70ce-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b70ce-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b70ce-135">Remarks</span></span>  
 <span data-ttu-id="b70ce-136">Ten element jest ustawiona tylko wtedy, gdy atrybut tryb [ \<zabezpieczeń >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) ustawiono `Transport` lub `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="b70ce-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b70ce-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b70ce-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="b70ce-138">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="b70ce-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="b70ce-139">Transporty</span><span class="sxs-lookup"><span data-stu-id="b70ce-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="b70ce-140">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="b70ce-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="b70ce-141">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b70ce-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b70ce-142">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b70ce-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b70ce-143">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b70ce-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b70ce-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b70ce-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
