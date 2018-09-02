---
title: '&lt;peer&gt; w &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 94f93a7955af3bff1c17e59a11af3fad85c9134d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399846"
---
# <a name="ltpeergt-of-ltservicecredentialsgt"></a><span data-ttu-id="3e3f9-102">&lt;peer&gt; w &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="3e3f9-102">&lt;peer&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="3e3f9-103">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="3e3f9-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="3e3f9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3e3f9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3e3f9-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="3e3f9-105">\<behaviors></span></span>  
<span data-ttu-id="3e3f9-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3e3f9-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="3e3f9-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="3e3f9-107">\<behavior></span></span>  
<span data-ttu-id="3e3f9-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="3e3f9-108">\<serviceCredentials></span></span>  
<span data-ttu-id="3e3f9-109">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="3e3f9-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e3f9-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e3f9-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e3f9-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3e3f9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3e3f9-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3e3f9-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e3f9-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3e3f9-113">Attributes</span></span>  
 <span data-ttu-id="3e3f9-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="3e3f9-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3e3f9-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3e3f9-115">Child Elements</span></span>  
  
|<span data-ttu-id="3e3f9-116">Element</span><span class="sxs-lookup"><span data-stu-id="3e3f9-116">Element</span></span>|<span data-ttu-id="3e3f9-117">Opis</span><span class="sxs-lookup"><span data-stu-id="3e3f9-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e3f9-118">\<certyfikat ></span><span class="sxs-lookup"><span data-stu-id="3e3f9-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="3e3f9-119">Określa certyfikat X.509 do podpisywania i szyfrowanie wiadomości usługi peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="3e3f9-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="3e3f9-120">.</span><span class="sxs-lookup"><span data-stu-id="3e3f9-120">.</span></span>|  
|[<span data-ttu-id="3e3f9-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="3e3f9-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="3e3f9-122">Określa opcje uwierzytelnienia dla nadawców wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3e3f9-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="3e3f9-123">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="3e3f9-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="3e3f9-124">Określa opcje uwierzytelniania dla elementów równorzędnych usługi.</span><span class="sxs-lookup"><span data-stu-id="3e3f9-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e3f9-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3e3f9-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3e3f9-126">Element</span><span class="sxs-lookup"><span data-stu-id="3e3f9-126">Element</span></span>|<span data-ttu-id="3e3f9-127">Opis</span><span class="sxs-lookup"><span data-stu-id="3e3f9-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e3f9-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="3e3f9-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="3e3f9-129">Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="3e3f9-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e3f9-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e3f9-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="3e3f9-131">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="3e3f9-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="3e3f9-132">Uwierzytelnianie wiadomości z kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="3e3f9-132">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="3e3f9-133">Kanał elementu równorzędnego uwierzytelniania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="3e3f9-133">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="3e3f9-134">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="3e3f9-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="3e3f9-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="3e3f9-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
