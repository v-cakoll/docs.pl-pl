---
title: '&lt;peer&gt; w &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: f50c192639df7b7ed35e863821d5b7a8d62f29bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747684"
---
# <a name="ltpeergt-of-ltservicecredentialsgt"></a>&lt;peer&gt; w &lt;serviceCredentials&gt;
Określa bieżące poświadczenia dla węzła równorzędnego.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<peer >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<certyfikat >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|Określa certyfikat X.509 do użycia podczas podpisywania i szyfrowania wiadomości dla usług peer-to-peer. .|  
|[\<messageSenderAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|Określa opcje uwierzytelnienia dla nadawców wiadomości.|  
|[\<peerAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|Określa opcje uwierzytelniania dla usług elementów równorzędnych.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Określa poświadczenia do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [Sieci równorzędne](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Uwierzytelnianie wiadomości kanału równorzędnego](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Niestandardowe uwierzytelnianie kanału równorzędnego](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Zabezpieczanie aplikacji kanałów równorzędnych](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
