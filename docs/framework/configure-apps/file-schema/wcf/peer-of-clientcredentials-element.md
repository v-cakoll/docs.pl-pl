---
title: <peer><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: dce7ef64de1e3eb248e3553c97cbce8e9b205b4c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400099"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="b3765-102">\<> elementów równorzędnych obiektu \<ClientCredentials ></span><span class="sxs-lookup"><span data-stu-id="b3765-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="b3765-103">Określa poświadczenia używane podczas uwierzytelniania klientów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="b3765-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
<span data-ttu-id="b3765-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b3765-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b3765-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b3765-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b3765-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b3765-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="b3765-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b3765-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="b3765-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b3765-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="b3765-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Obiekt clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="b3765-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="b3765-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> elementów równorzędnych**</span><span class="sxs-lookup"><span data-stu-id="b3765-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3765-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3765-111">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3765-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b3765-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b3765-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b3765-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3765-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b3765-114">Attributes</span></span>  
 <span data-ttu-id="b3765-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="b3765-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b3765-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b3765-116">Child Elements</span></span>  
  
|<span data-ttu-id="b3765-117">Element</span><span class="sxs-lookup"><span data-stu-id="b3765-117">Element</span></span>|<span data-ttu-id="b3765-118">Opis</span><span class="sxs-lookup"><span data-stu-id="b3765-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3765-119">\<> certyfikatów</span><span class="sxs-lookup"><span data-stu-id="b3765-119">\<certificate></span></span>](certificate-element.md)|<span data-ttu-id="b3765-120">Określa certyfikat X. 509 używany do podpisywania i szyfrowania komunikatów dla klientów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="b3765-120">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="b3765-121">.</span><span class="sxs-lookup"><span data-stu-id="b3765-121">.</span></span>|  
|[<span data-ttu-id="b3765-122">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="b3765-122">\<peerAuthentication></span></span>](peerauthentication-element.md)|<span data-ttu-id="b3765-123">Określa opcje uwierzytelniania dla klientów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="b3765-123">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="b3765-124">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="b3765-124">\<messageSenderAuthentication></span></span>](messagesenderauthentication-element.md)|<span data-ttu-id="b3765-125">Określa opcje uwierzytelniania dla nadawców wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b3765-125">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b3765-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b3765-126">Parent Elements</span></span>  
  
|<span data-ttu-id="b3765-127">Element</span><span class="sxs-lookup"><span data-stu-id="b3765-127">Element</span></span>|<span data-ttu-id="b3765-128">Opis</span><span class="sxs-lookup"><span data-stu-id="b3765-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3765-129">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="b3765-129">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="b3765-130">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="b3765-130">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3765-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3765-131">Remarks</span></span>  
 <span data-ttu-id="b3765-132">Ten element konfiguracji określa poświadczenia używane przez węzeł równorzędny do samodzielnego uwierzytelnienia w innych węzłach w sieci, a także ustawień uwierzytelniania używanych przez węzeł równorzędny do uwierzytelniania innych węzłów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="b3765-132">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="b3765-133">Aby uzyskać więcej informacji, zobacz [uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) i [Zabezpieczanie aplikacji kanału równorzędnego](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="b3765-133">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3765-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3765-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="b3765-135">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="b3765-135">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="b3765-136">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="b3765-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="b3765-137">[Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b3765-137">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="b3765-138">[Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b3765-138">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="b3765-139">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="b3765-139">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="b3765-140">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="b3765-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
