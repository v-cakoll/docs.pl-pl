---
title: <peer><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 2f1cb5689125e2483a74dcac515beb07abbb7c70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934034"
---
# <a name="peer-of-clientcredentials-element"></a>\<> elementów równorzędnych obiektu \<ClientCredentials >
Określa poświadczenia używane podczas uwierzytelniania klientów równorzędnych.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<endpointBehaviors>  
\<> zachowania  
\<clientCredentials>  
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
|[\<> certyfikatów](certificate-element.md)|Określa certyfikat X. 509 używany do podpisywania i szyfrowania komunikatów dla klientów równorzędnych. .|  
|[\<peerAuthentication >](peerauthentication-element.md)|Określa opcje uwierzytelniania dla klientów równorzędnych.|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|Określa opcje uwierzytelniania dla nadawców wiadomości.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Określa poświadczenia używane do uwierzytelniania klienta w usłudze.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji określa poświadczenia używane przez węzeł równorzędny do samodzielnego uwierzytelnienia w innych węzłach w sieci, a także ustawień uwierzytelniania używanych przez węzeł równorzędny do uwierzytelniania innych węzłów równorzędnych. Aby uzyskać więcej informacji, zobacz [uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) i [Zabezpieczanie aplikacji kanału równorzędnego](../../../wcf/feature-details/securing-peer-channel-applications.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [Sieci równorzędne](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Zabezpieczanie klientów](../../../wcf/securing-clients.md)
- [Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Zabezpieczanie aplikacji kanałów równorzędnych](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
