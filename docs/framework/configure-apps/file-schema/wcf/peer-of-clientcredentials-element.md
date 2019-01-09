---
title: '&lt;peer&gt; w &lt;clientCredentials&gt;, element'
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 9846a25a8df165f51290aa8a26f907d40b6b159f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150568"
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="8e97a-102">&lt;peer&gt; w &lt;clientCredentials&gt;, element</span><span class="sxs-lookup"><span data-stu-id="8e97a-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="8e97a-103">Określa poświadczenia używane podczas uwierzytelniania klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="8e97a-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="8e97a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8e97a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8e97a-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="8e97a-105">\<behaviors></span></span>  
<span data-ttu-id="8e97a-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="8e97a-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="8e97a-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="8e97a-107">\<behavior></span></span>  
<span data-ttu-id="8e97a-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="8e97a-108">\<clientCredentials></span></span>  
<span data-ttu-id="8e97a-109">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="8e97a-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e97a-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e97a-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e97a-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8e97a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8e97a-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8e97a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e97a-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8e97a-113">Attributes</span></span>  
 <span data-ttu-id="8e97a-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="8e97a-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8e97a-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8e97a-115">Child Elements</span></span>  
  
|<span data-ttu-id="8e97a-116">Element</span><span class="sxs-lookup"><span data-stu-id="8e97a-116">Element</span></span>|<span data-ttu-id="8e97a-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8e97a-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e97a-118">\<certyfikat ></span><span class="sxs-lookup"><span data-stu-id="8e97a-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="8e97a-119">Określa certyfikat X.509 do podpisywania i szyfrowania wiadomości dla klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="8e97a-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="8e97a-120">.</span><span class="sxs-lookup"><span data-stu-id="8e97a-120">.</span></span>|  
|[<span data-ttu-id="8e97a-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="8e97a-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="8e97a-122">Określa opcje uwierzytelniania dla klientów typu peer.</span><span class="sxs-lookup"><span data-stu-id="8e97a-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="8e97a-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="8e97a-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="8e97a-124">Określa opcje uwierzytelnienia dla nadawców wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8e97a-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e97a-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8e97a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="8e97a-126">Element</span><span class="sxs-lookup"><span data-stu-id="8e97a-126">Element</span></span>|<span data-ttu-id="8e97a-127">Opis</span><span class="sxs-lookup"><span data-stu-id="8e97a-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e97a-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="8e97a-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="8e97a-129">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="8e97a-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e97a-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e97a-130">Remarks</span></span>  
 <span data-ttu-id="8e97a-131">Ten element konfiguracji Określa poświadczenia używane przez węzeł równorzędny uwierzytelnienie na innych węzłach w sieci, a także ustawienia uwierzytelniania, używanych przez węzeł równorzędny do uwierzytelniania innych węzłów elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="8e97a-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="8e97a-132">Aby uzyskać więcej informacji, zobacz [uwierzytelniania wiadomości kanał elementu równorzędnego](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) i [zabezpieczanie aplikacji kanałów równorzędnych](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="8e97a-132">For more information, see [Peer Channel Message Authentication](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e97a-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e97a-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="8e97a-134">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="8e97a-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="8e97a-135">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="8e97a-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="8e97a-136">Uwierzytelnianie wiadomości z kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="8e97a-136">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="8e97a-137">Kanał elementu równorzędnego uwierzytelniania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="8e97a-137">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="8e97a-138">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="8e97a-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="8e97a-139">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="8e97a-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
