---
title: <peer> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: ca97be7b1ab562382895fea4f1d1fc716151b70b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397645"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="73a3d-102">\<peer> dla \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="73a3d-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="73a3d-103">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="73a3d-103">Specifies the current credentials for a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="73a3d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73a3d-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73a3d-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="73a3d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="73a3d-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="73a3d-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73a3d-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="73a3d-107">Attributes</span></span>  
 <span data-ttu-id="73a3d-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="73a3d-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="73a3d-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="73a3d-109">Child Elements</span></span>  
  
|<span data-ttu-id="73a3d-110">Element</span><span class="sxs-lookup"><span data-stu-id="73a3d-110">Element</span></span>|<span data-ttu-id="73a3d-111">Opis</span><span class="sxs-lookup"><span data-stu-id="73a3d-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|<span data-ttu-id="73a3d-112">Określa certyfikat X. 509 używany do podpisywania i szyfrowania komunikatów dla usług peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="73a3d-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="73a3d-113">.</span><span class="sxs-lookup"><span data-stu-id="73a3d-113">.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|<span data-ttu-id="73a3d-114">Określa opcje uwierzytelniania dla nadawców wiadomości.</span><span class="sxs-lookup"><span data-stu-id="73a3d-114">Specifies authentication options for message senders.</span></span>|  
|[\<peerAuthentication>](peerauthentication.md)|<span data-ttu-id="73a3d-115">Określa opcje uwierzytelniania dla usług równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="73a3d-115">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73a3d-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="73a3d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="73a3d-117">Element</span><span class="sxs-lookup"><span data-stu-id="73a3d-117">Element</span></span>|<span data-ttu-id="73a3d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="73a3d-118">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="73a3d-119">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="73a3d-119">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73a3d-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73a3d-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="73a3d-121">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="73a3d-121">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="73a3d-122">[Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="73a3d-122">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="73a3d-123">[Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="73a3d-123">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="73a3d-124">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="73a3d-124">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="73a3d-125">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="73a3d-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
