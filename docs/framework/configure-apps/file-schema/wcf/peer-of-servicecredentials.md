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
# <a name="peer-of-servicecredentials"></a>\<> elementów równorzędnych w \<usłudze ServiceCredentials >
Określa bieżące poświadczenia dla węzła równorzędnego.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<serviceBehaviors>  
\<> zachowania  
\<serviceCredentials>  
\<> elementów równorzędnych  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> certyfikatów](certificate-of-peer.md)|Określa certyfikat X. 509 używany do podpisywania i szyfrowania komunikatów dla usług peer-to-peer. .|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|Określa opcje uwierzytelniania dla nadawców wiadomości.|  
|[\<peerAuthentication >](peerauthentication.md)|Określa opcje uwierzytelniania dla usług równorzędnych.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [Sieci równorzędne](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Zabezpieczanie aplikacji kanałów równorzędnych](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
