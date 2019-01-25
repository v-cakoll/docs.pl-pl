---
title: '&lt;peer&gt; w &lt;clientCredentials&gt;, element'
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: f933e4c6719437d530e0cf90e3aa1da3a8143060
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616215"
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="4bcfe-102">&lt;peer&gt; w &lt;clientCredentials&gt;, element</span><span class="sxs-lookup"><span data-stu-id="4bcfe-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="4bcfe-103">Określa poświadczenia używane podczas uwierzytelniania klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="4bcfe-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="4bcfe-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4bcfe-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4bcfe-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="4bcfe-105">\<behaviors></span></span>  
<span data-ttu-id="4bcfe-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="4bcfe-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="4bcfe-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="4bcfe-107">\<behavior></span></span>  
<span data-ttu-id="4bcfe-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="4bcfe-108">\<clientCredentials></span></span>  
<span data-ttu-id="4bcfe-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="4bcfe-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bcfe-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bcfe-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4bcfe-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4bcfe-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4bcfe-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4bcfe-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4bcfe-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4bcfe-113">Attributes</span></span>  
 <span data-ttu-id="4bcfe-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="4bcfe-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4bcfe-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4bcfe-115">Child Elements</span></span>  
  
|<span data-ttu-id="4bcfe-116">Element</span><span class="sxs-lookup"><span data-stu-id="4bcfe-116">Element</span></span>|<span data-ttu-id="4bcfe-117">Opis</span><span class="sxs-lookup"><span data-stu-id="4bcfe-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4bcfe-118">\<certyfikat ></span><span class="sxs-lookup"><span data-stu-id="4bcfe-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="4bcfe-119">Określa certyfikat X.509 do podpisywania i szyfrowania wiadomości dla klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="4bcfe-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="4bcfe-120">.</span><span class="sxs-lookup"><span data-stu-id="4bcfe-120">.</span></span>|  
|[<span data-ttu-id="4bcfe-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="4bcfe-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="4bcfe-122">Określa opcje uwierzytelniania dla klientów typu peer.</span><span class="sxs-lookup"><span data-stu-id="4bcfe-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="4bcfe-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="4bcfe-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="4bcfe-124">Określa opcje uwierzytelnienia dla nadawców wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4bcfe-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4bcfe-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4bcfe-125">Parent Elements</span></span>  
  
|<span data-ttu-id="4bcfe-126">Element</span><span class="sxs-lookup"><span data-stu-id="4bcfe-126">Element</span></span>|<span data-ttu-id="4bcfe-127">Opis</span><span class="sxs-lookup"><span data-stu-id="4bcfe-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4bcfe-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="4bcfe-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="4bcfe-129">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="4bcfe-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bcfe-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4bcfe-130">Remarks</span></span>  
 <span data-ttu-id="4bcfe-131">Ten element konfiguracji Określa poświadczenia używane przez węzeł równorzędny uwierzytelnienie na innych węzłach w sieci, a także ustawienia uwierzytelniania, używanych przez węzeł równorzędny do uwierzytelniania innych węzłów elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="4bcfe-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="4bcfe-132">Aby uzyskać więcej informacji, zobacz [uwierzytelniania wiadomości kanał elementu równorzędnego](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) i [zabezpieczanie aplikacji kanałów równorzędnych](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="4bcfe-132">For more information, see [Peer Channel Message Authentication](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bcfe-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bcfe-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="4bcfe-134">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="4bcfe-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="4bcfe-135">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="4bcfe-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="4bcfe-136">Uwierzytelnianie wiadomości z kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="4bcfe-136">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)
- [<span data-ttu-id="4bcfe-137">Kanał elementu równorzędnego uwierzytelniania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="4bcfe-137">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)
- [<span data-ttu-id="4bcfe-138">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="4bcfe-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="4bcfe-139">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="4bcfe-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
