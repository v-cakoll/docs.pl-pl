---
title: <transport> dla <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 08be5d752f8422ebe6442b295195f21b16a274c0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399313"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="26992-102">\<Transport > \<NetPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="26992-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="26992-103">Określa ustawienia zabezpieczeń na poziomie transportu podczas korzystania z [ \<> NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="26992-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
<span data-ttu-id="26992-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="26992-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="26992-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="26992-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="26992-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="26992-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="26992-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="26992-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="26992-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="26992-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="26992-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-netpeerbinding.md)</span><span class="sxs-lookup"><span data-stu-id="26992-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)</span></span>\
<span data-ttu-id="26992-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> transportu**</span><span class="sxs-lookup"><span data-stu-id="26992-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26992-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="26992-111">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26992-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="26992-112">Attributes and Elements</span></span>  
 <span data-ttu-id="26992-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="26992-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26992-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="26992-114">Attributes</span></span>  
  
|<span data-ttu-id="26992-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="26992-115">Attribute</span></span>|<span data-ttu-id="26992-116">Opis</span><span class="sxs-lookup"><span data-stu-id="26992-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26992-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="26992-117">credentialType</span></span>|<span data-ttu-id="26992-118">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="26992-118">Optional.</span></span> <span data-ttu-id="26992-119">Określa typ poświadczeń używanych do weryfikowania komunikatów wysyłanych z transportem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="26992-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="26992-120">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="26992-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="26992-121">CredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="26992-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="26992-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="26992-122">Value</span></span>|<span data-ttu-id="26992-123">Opis</span><span class="sxs-lookup"><span data-stu-id="26992-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="26992-124">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="26992-124">Certificate</span></span>|<span data-ttu-id="26992-125">Uwierzytelnianie w ramach transportu kanału równorzędnego wymaga certyfikatu x509.</span><span class="sxs-lookup"><span data-stu-id="26992-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="26992-126">Hasło</span><span class="sxs-lookup"><span data-stu-id="26992-126">Password</span></span>|<span data-ttu-id="26992-127">Uwierzytelnianie transportu kanału równorzędnego wymaga poprawnego hasła.</span><span class="sxs-lookup"><span data-stu-id="26992-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26992-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="26992-128">Child Elements</span></span>  
 <span data-ttu-id="26992-129">Brak</span><span class="sxs-lookup"><span data-stu-id="26992-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26992-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="26992-130">Parent Elements</span></span>  
  
|<span data-ttu-id="26992-131">Element</span><span class="sxs-lookup"><span data-stu-id="26992-131">Element</span></span>|<span data-ttu-id="26992-132">Opis</span><span class="sxs-lookup"><span data-stu-id="26992-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26992-133">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="26992-133">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="26992-134">Definiuje ustawienia [ \<zabezpieczeń > NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="26992-134">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26992-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26992-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="26992-136">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="26992-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="26992-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="26992-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="26992-138">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="26992-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="26992-139">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="26992-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="26992-140">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="26992-140">\<binding></span></span>](../../../misc/binding.md)
