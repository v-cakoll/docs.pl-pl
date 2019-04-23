---
title: <peer> z <clientCredentials> — Element
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 7074ee992755557d7e5503035c89bdbefd678792
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107240"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="e948c-102">\<elementu równorzędnego > z \<clientCredentials > Element</span><span class="sxs-lookup"><span data-stu-id="e948c-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="e948c-103">Określa poświadczenia używane podczas uwierzytelniania klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="e948c-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="e948c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e948c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e948c-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="e948c-105">\<behaviors></span></span>  
<span data-ttu-id="e948c-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="e948c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="e948c-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="e948c-107">\<behavior></span></span>  
<span data-ttu-id="e948c-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e948c-108">\<clientCredentials></span></span>  
<span data-ttu-id="e948c-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="e948c-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e948c-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e948c-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e948c-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e948c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e948c-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e948c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e948c-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e948c-113">Attributes</span></span>  
 <span data-ttu-id="e948c-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="e948c-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e948c-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e948c-115">Child Elements</span></span>  
  
|<span data-ttu-id="e948c-116">Element</span><span class="sxs-lookup"><span data-stu-id="e948c-116">Element</span></span>|<span data-ttu-id="e948c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e948c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e948c-118">\<certyfikat ></span><span class="sxs-lookup"><span data-stu-id="e948c-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="e948c-119">Określa certyfikat X.509 do podpisywania i szyfrowania wiadomości dla klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="e948c-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="e948c-120">.</span><span class="sxs-lookup"><span data-stu-id="e948c-120">.</span></span>|  
|[<span data-ttu-id="e948c-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="e948c-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="e948c-122">Określa opcje uwierzytelniania dla klientów typu peer.</span><span class="sxs-lookup"><span data-stu-id="e948c-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="e948c-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="e948c-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="e948c-124">Określa opcje uwierzytelnienia dla nadawców wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e948c-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e948c-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e948c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e948c-126">Element</span><span class="sxs-lookup"><span data-stu-id="e948c-126">Element</span></span>|<span data-ttu-id="e948c-127">Opis</span><span class="sxs-lookup"><span data-stu-id="e948c-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e948c-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e948c-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="e948c-129">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="e948c-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e948c-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e948c-130">Remarks</span></span>  
 <span data-ttu-id="e948c-131">Ten element konfiguracji Określa poświadczenia używane przez węzeł równorzędny uwierzytelnienie na innych węzłach w sieci, a także ustawienia uwierzytelniania, używanych przez węzeł równorzędny do uwierzytelniania innych węzłów elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="e948c-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="e948c-132">Aby uzyskać więcej informacji, zobacz [uwierzytelniania wiadomości kanał elementu równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) i [zabezpieczanie aplikacji kanałów równorzędnych](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="e948c-132">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e948c-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e948c-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="e948c-134">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="e948c-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="e948c-135">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="e948c-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- <span data-ttu-id="e948c-136">[Uwierzytelnianie wiadomości z kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e948c-136">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="e948c-137">[Kanał elementu równorzędnego uwierzytelniania niestandardowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e948c-137">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="e948c-138">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="e948c-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="e948c-139">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="e948c-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
