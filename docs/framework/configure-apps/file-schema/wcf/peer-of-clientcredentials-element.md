---
title: <peer><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 2f1cb5689125e2483a74dcac515beb07abbb7c70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934034"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="ee1c6-102">\<> elementów równorzędnych obiektu \<ClientCredentials ></span><span class="sxs-lookup"><span data-stu-id="ee1c6-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="ee1c6-103">Określa poświadczenia używane podczas uwierzytelniania klientów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="ee1c6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ee1c6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ee1c6-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="ee1c6-105">\<behaviors></span></span>  
<span data-ttu-id="ee1c6-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="ee1c6-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="ee1c6-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="ee1c6-107">\<behavior></span></span>  
<span data-ttu-id="ee1c6-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="ee1c6-108">\<clientCredentials></span></span>  
<span data-ttu-id="ee1c6-109">\<> elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="ee1c6-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee1c6-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee1c6-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee1c6-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ee1c6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ee1c6-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee1c6-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ee1c6-113">Attributes</span></span>  
 <span data-ttu-id="ee1c6-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ee1c6-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ee1c6-115">Child Elements</span></span>  
  
|<span data-ttu-id="ee1c6-116">Element</span><span class="sxs-lookup"><span data-stu-id="ee1c6-116">Element</span></span>|<span data-ttu-id="ee1c6-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ee1c6-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee1c6-118">\<> certyfikatów</span><span class="sxs-lookup"><span data-stu-id="ee1c6-118">\<certificate></span></span>](certificate-element.md)|<span data-ttu-id="ee1c6-119">Określa certyfikat X. 509 używany do podpisywania i szyfrowania komunikatów dla klientów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="ee1c6-120">.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-120">.</span></span>|  
|[<span data-ttu-id="ee1c6-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="ee1c6-121">\<peerAuthentication></span></span>](peerauthentication-element.md)|<span data-ttu-id="ee1c6-122">Określa opcje uwierzytelniania dla klientów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="ee1c6-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="ee1c6-123">\<messageSenderAuthentication></span></span>](messagesenderauthentication-element.md)|<span data-ttu-id="ee1c6-124">Określa opcje uwierzytelniania dla nadawców wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee1c6-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ee1c6-125">Parent Elements</span></span>  
  
|<span data-ttu-id="ee1c6-126">Element</span><span class="sxs-lookup"><span data-stu-id="ee1c6-126">Element</span></span>|<span data-ttu-id="ee1c6-127">Opis</span><span class="sxs-lookup"><span data-stu-id="ee1c6-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee1c6-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="ee1c6-128">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="ee1c6-129">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee1c6-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee1c6-130">Remarks</span></span>  
 <span data-ttu-id="ee1c6-131">Ten element konfiguracji określa poświadczenia używane przez węzeł równorzędny do samodzielnego uwierzytelnienia w innych węzłach w sieci, a także ustawień uwierzytelniania używanych przez węzeł równorzędny do uwierzytelniania innych węzłów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="ee1c6-132">Aby uzyskać więcej informacji, zobacz [uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) i [Zabezpieczanie aplikacji kanału równorzędnego](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="ee1c6-132">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee1c6-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee1c6-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="ee1c6-134">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="ee1c6-134">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="ee1c6-135">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="ee1c6-135">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="ee1c6-136">[Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ee1c6-136">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="ee1c6-137">[Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ee1c6-137">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="ee1c6-138">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="ee1c6-138">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="ee1c6-139">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ee1c6-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
