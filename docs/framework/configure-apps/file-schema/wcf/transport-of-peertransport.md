---
title: <transport> dla <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3b2c7716727f58abb81bf4d58b13189ac170cf7c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399286"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="e14ce-102">\<Transport > \<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="e14ce-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="e14ce-103">Określa typ transportu zabezpieczonych komunikatów wysyłanych przez elementy równorzędne skonfigurowane przy użyciu tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e14ce-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
<span data-ttu-id="e14ce-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e14ce-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e14ce-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e14ce-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e14ce-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e14ce-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e14ce-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="e14ce-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="e14ce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="e14ce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e14ce-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<peerTransport >** ](peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="e14ce-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)</span></span>\
<span data-ttu-id="e14ce-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="e14ce-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)</span></span>\
<span data-ttu-id="e14ce-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> transportu**</span><span class="sxs-lookup"><span data-stu-id="e14ce-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e14ce-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="e14ce-112">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e14ce-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e14ce-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e14ce-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e14ce-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e14ce-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e14ce-115">Attributes</span></span>  
  
|<span data-ttu-id="e14ce-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e14ce-116">Attribute</span></span>|<span data-ttu-id="e14ce-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e14ce-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e14ce-118">credentialType</span><span class="sxs-lookup"><span data-stu-id="e14ce-118">credentialType</span></span>|<span data-ttu-id="e14ce-119">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e14ce-119">Optional.</span></span> <span data-ttu-id="e14ce-120">Określa typ poświadczeń używanych do weryfikowania komunikatów wysyłanych z transportem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="e14ce-120">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="e14ce-121">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="e14ce-121">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="e14ce-122">CredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="e14ce-122">credentialType Attribute</span></span>  
  
|<span data-ttu-id="e14ce-123">Wartość</span><span class="sxs-lookup"><span data-stu-id="e14ce-123">Value</span></span>|<span data-ttu-id="e14ce-124">Opis</span><span class="sxs-lookup"><span data-stu-id="e14ce-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e14ce-125">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e14ce-125">Certificate</span></span>|<span data-ttu-id="e14ce-126">Uwierzytelnianie w ramach transportu kanału równorzędnego wymaga certyfikatu x509.</span><span class="sxs-lookup"><span data-stu-id="e14ce-126">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="e14ce-127">Hasło</span><span class="sxs-lookup"><span data-stu-id="e14ce-127">Password</span></span>|<span data-ttu-id="e14ce-128">Uwierzytelnianie transportu kanału równorzędnego wymaga poprawnego hasła.</span><span class="sxs-lookup"><span data-stu-id="e14ce-128">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e14ce-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e14ce-129">Child Elements</span></span>  
 <span data-ttu-id="e14ce-130">Brak</span><span class="sxs-lookup"><span data-stu-id="e14ce-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e14ce-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e14ce-131">Parent Elements</span></span>  
  
|<span data-ttu-id="e14ce-132">Element</span><span class="sxs-lookup"><span data-stu-id="e14ce-132">Element</span></span>|<span data-ttu-id="e14ce-133">Opis</span><span class="sxs-lookup"><span data-stu-id="e14ce-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e14ce-134">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e14ce-134">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="e14ce-135">Definiuje ustawienia zabezpieczeń dla transportu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="e14ce-135">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e14ce-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e14ce-136">Remarks</span></span>  
 <span data-ttu-id="e14ce-137">Ten element jest ustawiany tylko wtedy, gdy atrybut `Transport` `TransportWithMessageCredential` [ \<Mode > zabezpieczeń](security-of-peertransport.md) jest ustawiony na lub.</span><span class="sxs-lookup"><span data-stu-id="e14ce-137">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e14ce-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e14ce-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e14ce-139">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="e14ce-139">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="e14ce-140">Transporty</span><span class="sxs-lookup"><span data-stu-id="e14ce-140">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="e14ce-141">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="e14ce-141">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="e14ce-142">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e14ce-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e14ce-143">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="e14ce-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e14ce-144">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="e14ce-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e14ce-145">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e14ce-145">\<customBinding></span></span>](custombinding.md)
