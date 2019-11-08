---
title: <transport> dla <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 49b31a889d192d190125214e89ba09305114eb7f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735976"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="20082-102">\<Transport > \<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="20082-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="20082-103">Określa ustawienia zabezpieczeń na poziomie transportu przy użyciu [\<netPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="20082-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
<span data-ttu-id="20082-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="20082-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="20082-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="20082-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="20082-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="20082-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="20082-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<NetPeerTcpBinding**](netpeertcpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="20082-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="20082-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="20082-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="20082-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpieczeń**](security-of-netpeerbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="20082-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)</span></span>\
<span data-ttu-id="20082-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**</span><span class="sxs-lookup"><span data-stu-id="20082-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20082-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="20082-111">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20082-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="20082-112">Attributes and Elements</span></span>  
 <span data-ttu-id="20082-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="20082-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20082-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="20082-114">Attributes</span></span>  
  
|<span data-ttu-id="20082-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="20082-115">Attribute</span></span>|<span data-ttu-id="20082-116">Opis</span><span class="sxs-lookup"><span data-stu-id="20082-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20082-117">CredentialType</span><span class="sxs-lookup"><span data-stu-id="20082-117">credentialType</span></span>|<span data-ttu-id="20082-118">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="20082-118">Optional.</span></span> <span data-ttu-id="20082-119">Określa typ poświadczeń używanych do weryfikowania komunikatów wysyłanych z transportem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="20082-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="20082-120">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="20082-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="20082-121">CredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="20082-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="20082-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="20082-122">Value</span></span>|<span data-ttu-id="20082-123">Opis</span><span class="sxs-lookup"><span data-stu-id="20082-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="20082-124">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="20082-124">Certificate</span></span>|<span data-ttu-id="20082-125">Uwierzytelnianie w ramach transportu kanału równorzędnego wymaga certyfikatu x509.</span><span class="sxs-lookup"><span data-stu-id="20082-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="20082-126">Hasło</span><span class="sxs-lookup"><span data-stu-id="20082-126">Password</span></span>|<span data-ttu-id="20082-127">Uwierzytelnianie transportu kanału równorzędnego wymaga poprawnego hasła.</span><span class="sxs-lookup"><span data-stu-id="20082-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20082-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="20082-128">Child Elements</span></span>  
 <span data-ttu-id="20082-129">Brak</span><span class="sxs-lookup"><span data-stu-id="20082-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20082-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="20082-130">Parent Elements</span></span>  
  
|<span data-ttu-id="20082-131">Element</span><span class="sxs-lookup"><span data-stu-id="20082-131">Element</span></span>|<span data-ttu-id="20082-132">Opis</span><span class="sxs-lookup"><span data-stu-id="20082-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20082-133">> zabezpieczeń \<</span><span class="sxs-lookup"><span data-stu-id="20082-133">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="20082-134">Definiuje ustawienia zabezpieczeń [\<netPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="20082-134">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20082-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20082-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="20082-136">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="20082-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="20082-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="20082-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="20082-138">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="20082-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="20082-139">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="20082-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="20082-140">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="20082-140">\<binding></span></span>](bindings.md)
