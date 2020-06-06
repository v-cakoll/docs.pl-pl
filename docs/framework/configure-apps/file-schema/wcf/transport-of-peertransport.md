---
title: <transport> dla <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3b2c7716727f58abb81bf4d58b13189ac170cf7c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399286"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="0440c-102">\<transport> dla \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="0440c-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="0440c-103">Określa typ transportu zabezpieczonych komunikatów wysyłanych przez elementy równorzędne skonfigurowane przy użyciu tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="0440c-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="0440c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0440c-104">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0440c-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0440c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0440c-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0440c-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0440c-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0440c-107">Attributes</span></span>  
  
|<span data-ttu-id="0440c-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0440c-108">Attribute</span></span>|<span data-ttu-id="0440c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="0440c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0440c-110">CredentialType</span><span class="sxs-lookup"><span data-stu-id="0440c-110">credentialType</span></span>|<span data-ttu-id="0440c-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0440c-111">Optional.</span></span> <span data-ttu-id="0440c-112">Określa typ poświadczeń używanych do weryfikowania komunikatów wysyłanych z transportem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="0440c-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="0440c-113">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="0440c-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="0440c-114">CredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="0440c-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="0440c-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="0440c-115">Value</span></span>|<span data-ttu-id="0440c-116">Opis</span><span class="sxs-lookup"><span data-stu-id="0440c-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0440c-117">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="0440c-117">Certificate</span></span>|<span data-ttu-id="0440c-118">Uwierzytelnianie w ramach transportu kanału równorzędnego wymaga certyfikatu x509.</span><span class="sxs-lookup"><span data-stu-id="0440c-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="0440c-119">Hasło</span><span class="sxs-lookup"><span data-stu-id="0440c-119">Password</span></span>|<span data-ttu-id="0440c-120">Uwierzytelnianie transportu kanału równorzędnego wymaga poprawnego hasła.</span><span class="sxs-lookup"><span data-stu-id="0440c-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0440c-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0440c-121">Child Elements</span></span>  
 <span data-ttu-id="0440c-122">Brak</span><span class="sxs-lookup"><span data-stu-id="0440c-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0440c-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0440c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0440c-124">Element</span><span class="sxs-lookup"><span data-stu-id="0440c-124">Element</span></span>|<span data-ttu-id="0440c-125">Opis</span><span class="sxs-lookup"><span data-stu-id="0440c-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="0440c-126">Definiuje ustawienia zabezpieczeń dla transportu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="0440c-126">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0440c-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0440c-127">Remarks</span></span>  
 <span data-ttu-id="0440c-128">Ten element jest ustawiany tylko wtedy, gdy atrybut mode [\<security>](security-of-peertransport.md) jest ustawiony na `Transport` lub `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="0440c-128">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0440c-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0440c-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0440c-130">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="0440c-130">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="0440c-131">Transporty</span><span class="sxs-lookup"><span data-stu-id="0440c-131">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="0440c-132">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="0440c-132">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="0440c-133">Powiązania</span><span class="sxs-lookup"><span data-stu-id="0440c-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0440c-134">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="0440c-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0440c-135">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="0440c-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
