---
title: '&lt;peer&gt; w &lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3754964d07dd80442fbffd7c632304ef9d83ab1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltpeergt-of-ltservicecredentialsgt"></a><span data-ttu-id="1a5ee-102">&lt;peer&gt; w &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="1a5ee-102">&lt;peer&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="1a5ee-103">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="1a5ee-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="1a5ee-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1a5ee-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1a5ee-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="1a5ee-105">\<behaviors></span></span>  
<span data-ttu-id="1a5ee-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1a5ee-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1a5ee-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="1a5ee-107">\<behavior></span></span>  
<span data-ttu-id="1a5ee-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="1a5ee-108">\<serviceCredentials></span></span>  
<span data-ttu-id="1a5ee-109">\<peer ></span><span class="sxs-lookup"><span data-stu-id="1a5ee-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a5ee-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a5ee-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a5ee-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1a5ee-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1a5ee-112">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1a5ee-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a5ee-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1a5ee-113">Attributes</span></span>  
 <span data-ttu-id="1a5ee-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="1a5ee-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1a5ee-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1a5ee-115">Child Elements</span></span>  
  
|<span data-ttu-id="1a5ee-116">Element</span><span class="sxs-lookup"><span data-stu-id="1a5ee-116">Element</span></span>|<span data-ttu-id="1a5ee-117">Opis</span><span class="sxs-lookup"><span data-stu-id="1a5ee-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a5ee-118">\<certyfikat ></span><span class="sxs-lookup"><span data-stu-id="1a5ee-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="1a5ee-119">Określa certyfikat X.509 do użycia podczas podpisywania i szyfrowania wiadomości dla usług peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="1a5ee-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="1a5ee-120">.</span><span class="sxs-lookup"><span data-stu-id="1a5ee-120">.</span></span>|  
|[<span data-ttu-id="1a5ee-121">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1a5ee-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="1a5ee-122">Określa opcje uwierzytelnienia dla nadawców wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a5ee-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="1a5ee-123">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1a5ee-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="1a5ee-124">Określa opcje uwierzytelniania dla usług elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="1a5ee-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a5ee-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1a5ee-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1a5ee-126">Element</span><span class="sxs-lookup"><span data-stu-id="1a5ee-126">Element</span></span>|<span data-ttu-id="1a5ee-127">Opis</span><span class="sxs-lookup"><span data-stu-id="1a5ee-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a5ee-128">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="1a5ee-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="1a5ee-129">Określa poświadczenia do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="1a5ee-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a5ee-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a5ee-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="1a5ee-131">Sieci peer-to-Peer</span><span class="sxs-lookup"><span data-stu-id="1a5ee-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="1a5ee-132">Uwierzytelnianie wiadomości kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="1a5ee-132">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="1a5ee-133">Niestandardowe uwierzytelnianie kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="1a5ee-133">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="1a5ee-134">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="1a5ee-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="1a5ee-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="1a5ee-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
