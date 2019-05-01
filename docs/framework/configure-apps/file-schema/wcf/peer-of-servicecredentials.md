---
title: <peer> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: d726ab460141b1e373a1cabf770b8958f50319eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783399"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="c3c2d-102">\<elementu równorzędnego > z \<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="c3c2d-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="c3c2d-103">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="c3c2d-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="c3c2d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c3c2d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c3c2d-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="c3c2d-105">\<behaviors></span></span>  
<span data-ttu-id="c3c2d-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c3c2d-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c3c2d-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="c3c2d-107">\<behavior></span></span>  
<span data-ttu-id="c3c2d-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c3c2d-108">\<serviceCredentials></span></span>  
<span data-ttu-id="c3c2d-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="c3c2d-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3c2d-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3c2d-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3c2d-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c3c2d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c3c2d-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c3c2d-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3c2d-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3c2d-113">Attributes</span></span>  
 <span data-ttu-id="c3c2d-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="c3c2d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c3c2d-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c3c2d-115">Child Elements</span></span>  
  
|<span data-ttu-id="c3c2d-116">Element</span><span class="sxs-lookup"><span data-stu-id="c3c2d-116">Element</span></span>|<span data-ttu-id="c3c2d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="c3c2d-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3c2d-118">\<certyfikat ></span><span class="sxs-lookup"><span data-stu-id="c3c2d-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="c3c2d-119">Określa certyfikat X.509 do podpisywania i szyfrowanie wiadomości usługi peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="c3c2d-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="c3c2d-120">.</span><span class="sxs-lookup"><span data-stu-id="c3c2d-120">.</span></span>|  
|[<span data-ttu-id="c3c2d-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="c3c2d-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="c3c2d-122">Określa opcje uwierzytelnienia dla nadawców wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c3c2d-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="c3c2d-123">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="c3c2d-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="c3c2d-124">Określa opcje uwierzytelniania dla elementów równorzędnych usługi.</span><span class="sxs-lookup"><span data-stu-id="c3c2d-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c3c2d-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c3c2d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c3c2d-126">Element</span><span class="sxs-lookup"><span data-stu-id="c3c2d-126">Element</span></span>|<span data-ttu-id="c3c2d-127">Opis</span><span class="sxs-lookup"><span data-stu-id="c3c2d-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3c2d-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c3c2d-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="c3c2d-129">Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="c3c2d-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3c2d-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3c2d-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="c3c2d-131">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="c3c2d-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="c3c2d-132">[Uwierzytelnianie wiadomości z kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c3c2d-132">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="c3c2d-133">[Kanał elementu równorzędnego uwierzytelniania niestandardowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c3c2d-133">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="c3c2d-134">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="c3c2d-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="c3c2d-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="c3c2d-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
