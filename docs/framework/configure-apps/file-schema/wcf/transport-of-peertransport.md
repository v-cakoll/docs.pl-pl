---
title: <transport> dla <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 5dbc55db25c0c49d72ec2cd8dd1041a3f8705d8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940646"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="017c4-102">\<Transport > \<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="017c4-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="017c4-103">Określa typ transportu zabezpieczonych komunikatów wysyłanych przez elementy równorzędne skonfigurowane przy użyciu tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="017c4-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="017c4-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="017c4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="017c4-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="017c4-105">\<bindings></span></span>  
<span data-ttu-id="017c4-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="017c4-106">\<customBinding></span></span>  
<span data-ttu-id="017c4-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="017c4-107">\<binding></span></span>  
<span data-ttu-id="017c4-108">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="017c4-108">\<peerTransport></span></span>  
<span data-ttu-id="017c4-109">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="017c4-109">\<security></span></span>  
<span data-ttu-id="017c4-110">\<transport></span><span class="sxs-lookup"><span data-stu-id="017c4-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="017c4-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="017c4-111">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="017c4-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="017c4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="017c4-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="017c4-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="017c4-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="017c4-114">Attributes</span></span>  
  
|<span data-ttu-id="017c4-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="017c4-115">Attribute</span></span>|<span data-ttu-id="017c4-116">Opis</span><span class="sxs-lookup"><span data-stu-id="017c4-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="017c4-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="017c4-117">credentialType</span></span>|<span data-ttu-id="017c4-118">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="017c4-118">Optional.</span></span> <span data-ttu-id="017c4-119">Określa typ poświadczeń używanych do weryfikowania komunikatów wysyłanych z transportem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="017c4-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="017c4-120">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="017c4-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="017c4-121">CredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="017c4-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="017c4-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="017c4-122">Value</span></span>|<span data-ttu-id="017c4-123">Opis</span><span class="sxs-lookup"><span data-stu-id="017c4-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="017c4-124">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="017c4-124">Certificate</span></span>|<span data-ttu-id="017c4-125">Uwierzytelnianie w ramach transportu kanału równorzędnego wymaga certyfikatu x509.</span><span class="sxs-lookup"><span data-stu-id="017c4-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="017c4-126">Hasło</span><span class="sxs-lookup"><span data-stu-id="017c4-126">Password</span></span>|<span data-ttu-id="017c4-127">Uwierzytelnianie transportu kanału równorzędnego wymaga poprawnego hasła.</span><span class="sxs-lookup"><span data-stu-id="017c4-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="017c4-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="017c4-128">Child Elements</span></span>  
 <span data-ttu-id="017c4-129">Brak</span><span class="sxs-lookup"><span data-stu-id="017c4-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="017c4-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="017c4-130">Parent Elements</span></span>  
  
|<span data-ttu-id="017c4-131">Element</span><span class="sxs-lookup"><span data-stu-id="017c4-131">Element</span></span>|<span data-ttu-id="017c4-132">Opis</span><span class="sxs-lookup"><span data-stu-id="017c4-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="017c4-133">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="017c4-133">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="017c4-134">Definiuje ustawienia zabezpieczeń dla transportu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="017c4-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="017c4-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="017c4-135">Remarks</span></span>  
 <span data-ttu-id="017c4-136">Ten element jest ustawiany tylko wtedy, gdy atrybut `Transport` `TransportWithMessageCredential` [ \<Mode > zabezpieczeń](security-of-peertransport.md) jest ustawiony na lub.</span><span class="sxs-lookup"><span data-stu-id="017c4-136">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="017c4-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="017c4-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="017c4-138">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="017c4-138">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="017c4-139">Transporty</span><span class="sxs-lookup"><span data-stu-id="017c4-139">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="017c4-140">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="017c4-140">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="017c4-141">Powiązania</span><span class="sxs-lookup"><span data-stu-id="017c4-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="017c4-142">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="017c4-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="017c4-143">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="017c4-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="017c4-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="017c4-144">\<customBinding></span></span>](custombinding.md)
