---
title: <peer> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: ca97be7b1ab562382895fea4f1d1fc716151b70b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397645"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="ffd51-102">\<> elementów równorzędnych w \<usłudze ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="ffd51-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="ffd51-103">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="ffd51-103">Specifies the current credentials for a peer node.</span></span>  
  
<span data-ttu-id="ffd51-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ffd51-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ffd51-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ffd51-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ffd51-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ffd51-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ffd51-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ffd51-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="ffd51-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ffd51-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="ffd51-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ServiceCredentials**](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="ffd51-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="ffd51-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> elementów równorzędnych**</span><span class="sxs-lookup"><span data-stu-id="ffd51-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffd51-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffd51-111">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffd51-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ffd51-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ffd51-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ffd51-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffd51-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ffd51-114">Attributes</span></span>  
 <span data-ttu-id="ffd51-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="ffd51-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ffd51-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ffd51-116">Child Elements</span></span>  
  
|<span data-ttu-id="ffd51-117">Element</span><span class="sxs-lookup"><span data-stu-id="ffd51-117">Element</span></span>|<span data-ttu-id="ffd51-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ffd51-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ffd51-119">\<> certyfikatów</span><span class="sxs-lookup"><span data-stu-id="ffd51-119">\<certificate></span></span>](certificate-of-peer.md)|<span data-ttu-id="ffd51-120">Określa certyfikat X. 509 używany do podpisywania i szyfrowania komunikatów dla usług peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="ffd51-120">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="ffd51-121">.</span><span class="sxs-lookup"><span data-stu-id="ffd51-121">.</span></span>|  
|[<span data-ttu-id="ffd51-122">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="ffd51-122">\<messageSenderAuthentication></span></span>](messagesenderauthentication.md)|<span data-ttu-id="ffd51-123">Określa opcje uwierzytelniania dla nadawców wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ffd51-123">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="ffd51-124">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="ffd51-124">\<peerAuthentication></span></span>](peerauthentication.md)|<span data-ttu-id="ffd51-125">Określa opcje uwierzytelniania dla usług równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="ffd51-125">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ffd51-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ffd51-126">Parent Elements</span></span>  
  
|<span data-ttu-id="ffd51-127">Element</span><span class="sxs-lookup"><span data-stu-id="ffd51-127">Element</span></span>|<span data-ttu-id="ffd51-128">Opis</span><span class="sxs-lookup"><span data-stu-id="ffd51-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ffd51-129">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="ffd51-129">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="ffd51-130">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="ffd51-130">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ffd51-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffd51-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="ffd51-132">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="ffd51-132">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="ffd51-133">[Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ffd51-133">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="ffd51-134">[Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ffd51-134">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="ffd51-135">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="ffd51-135">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="ffd51-136">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ffd51-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
