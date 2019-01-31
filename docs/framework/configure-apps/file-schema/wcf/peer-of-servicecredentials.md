---
title: <peer> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 2090e79e6affe8ade6e2e52b94d2c4e1dafe8fa1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266029"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="63c4b-102">\<elementu równorzędnego > z \<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="63c4b-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="63c4b-103">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="63c4b-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="63c4b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="63c4b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="63c4b-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="63c4b-105">\<behaviors></span></span>  
<span data-ttu-id="63c4b-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="63c4b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="63c4b-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="63c4b-107">\<behavior></span></span>  
<span data-ttu-id="63c4b-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="63c4b-108">\<serviceCredentials></span></span>  
<span data-ttu-id="63c4b-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="63c4b-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63c4b-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="63c4b-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63c4b-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="63c4b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="63c4b-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="63c4b-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63c4b-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="63c4b-113">Attributes</span></span>  
 <span data-ttu-id="63c4b-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="63c4b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="63c4b-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="63c4b-115">Child Elements</span></span>  
  
|<span data-ttu-id="63c4b-116">Element</span><span class="sxs-lookup"><span data-stu-id="63c4b-116">Element</span></span>|<span data-ttu-id="63c4b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="63c4b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63c4b-118">\<certyfikat ></span><span class="sxs-lookup"><span data-stu-id="63c4b-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="63c4b-119">Określa certyfikat X.509 do podpisywania i szyfrowanie wiadomości usługi peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="63c4b-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="63c4b-120">.</span><span class="sxs-lookup"><span data-stu-id="63c4b-120">.</span></span>|  
|[<span data-ttu-id="63c4b-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="63c4b-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="63c4b-122">Określa opcje uwierzytelnienia dla nadawców wiadomości.</span><span class="sxs-lookup"><span data-stu-id="63c4b-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="63c4b-123">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="63c4b-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="63c4b-124">Określa opcje uwierzytelniania dla elementów równorzędnych usługi.</span><span class="sxs-lookup"><span data-stu-id="63c4b-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63c4b-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="63c4b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="63c4b-126">Element</span><span class="sxs-lookup"><span data-stu-id="63c4b-126">Element</span></span>|<span data-ttu-id="63c4b-127">Opis</span><span class="sxs-lookup"><span data-stu-id="63c4b-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63c4b-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="63c4b-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="63c4b-129">Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="63c4b-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63c4b-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63c4b-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="63c4b-131">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="63c4b-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="63c4b-132">Uwierzytelnianie wiadomości z kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="63c4b-132">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)
- [<span data-ttu-id="63c4b-133">Kanał elementu równorzędnego uwierzytelniania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="63c4b-133">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)
- [<span data-ttu-id="63c4b-134">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="63c4b-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="63c4b-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="63c4b-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
