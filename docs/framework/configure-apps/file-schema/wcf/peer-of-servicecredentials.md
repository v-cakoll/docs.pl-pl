---
title: <peer> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 50415cb9b35d2a2053efa3313a415de518b7e36e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933777"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="f08f3-102">\<> elementów równorzędnych w \<usłudze ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="f08f3-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="f08f3-103">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="f08f3-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="f08f3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f08f3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f08f3-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="f08f3-105">\<behaviors></span></span>  
<span data-ttu-id="f08f3-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f08f3-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f08f3-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="f08f3-107">\<behavior></span></span>  
<span data-ttu-id="f08f3-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="f08f3-108">\<serviceCredentials></span></span>  
<span data-ttu-id="f08f3-109">\<> elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="f08f3-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f08f3-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f08f3-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f08f3-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f08f3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f08f3-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f08f3-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f08f3-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f08f3-113">Attributes</span></span>  
 <span data-ttu-id="f08f3-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="f08f3-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f08f3-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f08f3-115">Child Elements</span></span>  
  
|<span data-ttu-id="f08f3-116">Element</span><span class="sxs-lookup"><span data-stu-id="f08f3-116">Element</span></span>|<span data-ttu-id="f08f3-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f08f3-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f08f3-118">\<> certyfikatów</span><span class="sxs-lookup"><span data-stu-id="f08f3-118">\<certificate></span></span>](certificate-of-peer.md)|<span data-ttu-id="f08f3-119">Określa certyfikat X. 509 używany do podpisywania i szyfrowania komunikatów dla usług peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="f08f3-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="f08f3-120">.</span><span class="sxs-lookup"><span data-stu-id="f08f3-120">.</span></span>|  
|[<span data-ttu-id="f08f3-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="f08f3-121">\<messageSenderAuthentication></span></span>](messagesenderauthentication.md)|<span data-ttu-id="f08f3-122">Określa opcje uwierzytelniania dla nadawców wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f08f3-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="f08f3-123">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="f08f3-123">\<peerAuthentication></span></span>](peerauthentication.md)|<span data-ttu-id="f08f3-124">Określa opcje uwierzytelniania dla usług równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="f08f3-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f08f3-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f08f3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f08f3-126">Element</span><span class="sxs-lookup"><span data-stu-id="f08f3-126">Element</span></span>|<span data-ttu-id="f08f3-127">Opis</span><span class="sxs-lookup"><span data-stu-id="f08f3-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f08f3-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="f08f3-128">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="f08f3-129">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="f08f3-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f08f3-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f08f3-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="f08f3-131">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="f08f3-131">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="f08f3-132">[Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f08f3-132">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="f08f3-133">[Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f08f3-133">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="f08f3-134">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="f08f3-134">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="f08f3-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="f08f3-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
