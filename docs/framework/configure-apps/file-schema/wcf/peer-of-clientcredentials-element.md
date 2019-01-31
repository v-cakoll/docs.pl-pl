---
title: <peer> z <clientCredentials> — Element
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 8970100b1ad3019ff4a639d835d1db1430968008
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275148"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="6b850-102">\<elementu równorzędnego > z \<clientCredentials > Element</span><span class="sxs-lookup"><span data-stu-id="6b850-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="6b850-103">Określa poświadczenia używane podczas uwierzytelniania klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="6b850-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="6b850-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6b850-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6b850-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="6b850-105">\<behaviors></span></span>  
<span data-ttu-id="6b850-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="6b850-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="6b850-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="6b850-107">\<behavior></span></span>  
<span data-ttu-id="6b850-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="6b850-108">\<clientCredentials></span></span>  
<span data-ttu-id="6b850-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="6b850-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b850-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b850-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b850-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6b850-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6b850-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6b850-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b850-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6b850-113">Attributes</span></span>  
 <span data-ttu-id="6b850-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="6b850-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6b850-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6b850-115">Child Elements</span></span>  
  
|<span data-ttu-id="6b850-116">Element</span><span class="sxs-lookup"><span data-stu-id="6b850-116">Element</span></span>|<span data-ttu-id="6b850-117">Opis</span><span class="sxs-lookup"><span data-stu-id="6b850-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b850-118">\<certyfikat ></span><span class="sxs-lookup"><span data-stu-id="6b850-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="6b850-119">Określa certyfikat X.509 do podpisywania i szyfrowania wiadomości dla klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="6b850-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="6b850-120">.</span><span class="sxs-lookup"><span data-stu-id="6b850-120">.</span></span>|  
|[<span data-ttu-id="6b850-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="6b850-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="6b850-122">Określa opcje uwierzytelniania dla klientów typu peer.</span><span class="sxs-lookup"><span data-stu-id="6b850-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="6b850-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="6b850-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="6b850-124">Określa opcje uwierzytelnienia dla nadawców wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6b850-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b850-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6b850-125">Parent Elements</span></span>  
  
|<span data-ttu-id="6b850-126">Element</span><span class="sxs-lookup"><span data-stu-id="6b850-126">Element</span></span>|<span data-ttu-id="6b850-127">Opis</span><span class="sxs-lookup"><span data-stu-id="6b850-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b850-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="6b850-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="6b850-129">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="6b850-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b850-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b850-130">Remarks</span></span>  
 <span data-ttu-id="6b850-131">Ten element konfiguracji Określa poświadczenia używane przez węzeł równorzędny uwierzytelnienie na innych węzłach w sieci, a także ustawienia uwierzytelniania, używanych przez węzeł równorzędny do uwierzytelniania innych węzłów elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="6b850-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="6b850-132">Aby uzyskać więcej informacji, zobacz [uwierzytelniania wiadomości kanał elementu równorzędnego](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) i [zabezpieczanie aplikacji kanałów równorzędnych](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="6b850-132">For more information, see [Peer Channel Message Authentication](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b850-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b850-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="6b850-134">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="6b850-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="6b850-135">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="6b850-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="6b850-136">Uwierzytelnianie wiadomości z kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="6b850-136">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)
- [<span data-ttu-id="6b850-137">Kanał elementu równorzędnego uwierzytelniania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="6b850-137">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)
- [<span data-ttu-id="6b850-138">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="6b850-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="6b850-139">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="6b850-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
