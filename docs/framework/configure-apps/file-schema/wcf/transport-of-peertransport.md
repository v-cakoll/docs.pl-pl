---
title: <transport> z <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 9b6f548515afbba5068659bd5c6f7f2b33f80cda
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076006"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="87bfc-102">\<transport > z \<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="87bfc-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="87bfc-103">Określa typ transportu dla zabezpieczonych wiadomości wysłanych przez elementy równorzędne skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="87bfc-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="87bfc-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="87bfc-104">\<system.serviceModel></span></span>  
<span data-ttu-id="87bfc-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="87bfc-105">\<bindings></span></span>  
<span data-ttu-id="87bfc-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="87bfc-106">\<customBinding></span></span>  
<span data-ttu-id="87bfc-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="87bfc-107">\<binding></span></span>  
<span data-ttu-id="87bfc-108">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="87bfc-108">\<peerTransport></span></span>  
<span data-ttu-id="87bfc-109">\<security></span><span class="sxs-lookup"><span data-stu-id="87bfc-109">\<security></span></span>  
<span data-ttu-id="87bfc-110">\<transport></span><span class="sxs-lookup"><span data-stu-id="87bfc-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87bfc-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="87bfc-111">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87bfc-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="87bfc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="87bfc-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="87bfc-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87bfc-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="87bfc-114">Attributes</span></span>  
  
|<span data-ttu-id="87bfc-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="87bfc-115">Attribute</span></span>|<span data-ttu-id="87bfc-116">Opis</span><span class="sxs-lookup"><span data-stu-id="87bfc-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87bfc-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="87bfc-117">credentialType</span></span>|<span data-ttu-id="87bfc-118">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="87bfc-118">Optional.</span></span> <span data-ttu-id="87bfc-119">Określa typ poświadczenia używane do weryfikowania komunikaty wysyłane za pomocą transportu elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="87bfc-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="87bfc-120">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="87bfc-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="87bfc-121">credentialType Attribute</span><span class="sxs-lookup"><span data-stu-id="87bfc-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="87bfc-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="87bfc-122">Value</span></span>|<span data-ttu-id="87bfc-123">Opis</span><span class="sxs-lookup"><span data-stu-id="87bfc-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="87bfc-124">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="87bfc-124">Certificate</span></span>|<span data-ttu-id="87bfc-125">Uwierzytelnianie transportu kanał elementu równorzędnego wymaga X509 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="87bfc-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="87bfc-126">Hasło</span><span class="sxs-lookup"><span data-stu-id="87bfc-126">Password</span></span>|<span data-ttu-id="87bfc-127">Uwierzytelnianie transportu kanał elementu równorzędnego wymaga prawidłowego hasła.</span><span class="sxs-lookup"><span data-stu-id="87bfc-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87bfc-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="87bfc-128">Child Elements</span></span>  
 <span data-ttu-id="87bfc-129">Brak</span><span class="sxs-lookup"><span data-stu-id="87bfc-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87bfc-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="87bfc-130">Parent Elements</span></span>  
  
|<span data-ttu-id="87bfc-131">Element</span><span class="sxs-lookup"><span data-stu-id="87bfc-131">Element</span></span>|<span data-ttu-id="87bfc-132">Opis</span><span class="sxs-lookup"><span data-stu-id="87bfc-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87bfc-133">\<security></span><span class="sxs-lookup"><span data-stu-id="87bfc-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="87bfc-134">Definiuje ustawienia zabezpieczeń transport elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="87bfc-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87bfc-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87bfc-135">Remarks</span></span>  
 <span data-ttu-id="87bfc-136">Ten element jest ustawiona tylko wtedy, gdy atrybut tryb [ \<zabezpieczeń >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) ustawiono `Transport` lub `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="87bfc-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87bfc-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87bfc-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="87bfc-138">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="87bfc-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="87bfc-139">Transporty</span><span class="sxs-lookup"><span data-stu-id="87bfc-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="87bfc-140">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="87bfc-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="87bfc-141">Powiązania</span><span class="sxs-lookup"><span data-stu-id="87bfc-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="87bfc-142">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="87bfc-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="87bfc-143">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="87bfc-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="87bfc-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="87bfc-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
