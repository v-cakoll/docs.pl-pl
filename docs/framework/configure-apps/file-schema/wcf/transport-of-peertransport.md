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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 787d4569416203364e04898c6adcd57fb5a7aec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltpeertransportgt"></a><span data-ttu-id="49cbf-102">&lt;transport&gt; w &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="49cbf-102">&lt;transport&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="49cbf-103">Określa typ transportu zabezpieczonych wiadomości wysyłanych przez elementy równorzędne skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="49cbf-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="49cbf-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="49cbf-104">\<system.serviceModel></span></span>  
<span data-ttu-id="49cbf-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="49cbf-105">\<bindings></span></span>  
<span data-ttu-id="49cbf-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="49cbf-106">\<customBinding></span></span>  
<span data-ttu-id="49cbf-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="49cbf-107">\<binding></span></span>  
<span data-ttu-id="49cbf-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="49cbf-108">\<peerTransport></span></span>  
<span data-ttu-id="49cbf-109">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="49cbf-109">\<security></span></span>  
<span data-ttu-id="49cbf-110">\<transport ></span><span class="sxs-lookup"><span data-stu-id="49cbf-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49cbf-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="49cbf-111">Syntax</span></span>  
  
```xml  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49cbf-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="49cbf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="49cbf-113">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="49cbf-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49cbf-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="49cbf-114">Attributes</span></span>  
  
|<span data-ttu-id="49cbf-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="49cbf-115">Attribute</span></span>|<span data-ttu-id="49cbf-116">Opis</span><span class="sxs-lookup"><span data-stu-id="49cbf-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49cbf-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="49cbf-117">credentialType</span></span>|<span data-ttu-id="49cbf-118">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="49cbf-118">Optional.</span></span> <span data-ttu-id="49cbf-119">Określa poświadczenia używane do weryfikowania wiadomości wysyłane z transportu elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="49cbf-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="49cbf-120">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="49cbf-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="49cbf-121">credentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="49cbf-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="49cbf-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="49cbf-122">Value</span></span>|<span data-ttu-id="49cbf-123">Opis</span><span class="sxs-lookup"><span data-stu-id="49cbf-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="49cbf-124">certyfikat</span><span class="sxs-lookup"><span data-stu-id="49cbf-124">Certificate</span></span>|<span data-ttu-id="49cbf-125">Uwierzytelnianie kanał transportowy peer wymaga X509 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="49cbf-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="49cbf-126">Hasło</span><span class="sxs-lookup"><span data-stu-id="49cbf-126">Password</span></span>|<span data-ttu-id="49cbf-127">Uwierzytelnianie kanał transportowy peer wymaga poprawne hasło.</span><span class="sxs-lookup"><span data-stu-id="49cbf-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49cbf-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="49cbf-128">Child Elements</span></span>  
 <span data-ttu-id="49cbf-129">Brak</span><span class="sxs-lookup"><span data-stu-id="49cbf-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="49cbf-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="49cbf-130">Parent Elements</span></span>  
  
|<span data-ttu-id="49cbf-131">Element</span><span class="sxs-lookup"><span data-stu-id="49cbf-131">Element</span></span>|<span data-ttu-id="49cbf-132">Opis</span><span class="sxs-lookup"><span data-stu-id="49cbf-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49cbf-133">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="49cbf-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="49cbf-134">Definiuje ustawienia zabezpieczeń transportu elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="49cbf-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49cbf-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49cbf-135">Remarks</span></span>  
 <span data-ttu-id="49cbf-136">Ten element jest ustawiona tylko wtedy, gdy atrybut tryb [ \<zabezpieczeń >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) ustawiono `Transport` lub `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="49cbf-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49cbf-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49cbf-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="49cbf-138">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="49cbf-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="49cbf-139">Transporty</span><span class="sxs-lookup"><span data-stu-id="49cbf-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="49cbf-140">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="49cbf-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="49cbf-141">Powiązania</span><span class="sxs-lookup"><span data-stu-id="49cbf-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="49cbf-142">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="49cbf-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="49cbf-143">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="49cbf-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="49cbf-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="49cbf-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
