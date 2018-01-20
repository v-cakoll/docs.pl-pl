---
title: '&lt;peer&gt; w &lt;clientCredentials&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3479b52c6e06b7b9ebd69d46780e8dca70d2ef7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a>&lt;peer&gt; w &lt;clientCredentials&gt;, element
Określa poświadczenia używane podczas uwierzytelniania klientów peer-to-peer.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<endpointBehaviors>  
\<behavior>  
\<clientCredentials>  
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
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<certyfikat >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|Określa certyfikat X.509 do użycia podczas podpisywania i szyfrowania wiadomości dla klientów peer-to-peer. .|  
|[\<peerAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|Określa opcje uwierzytelniania dla klientów typu peer.|  
|[\<messageSenderAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|Określa opcje uwierzytelnienia dla nadawców wiadomości.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Określa poświadczenia używane do uwierzytelniania klienta do usługi.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji Określa poświadczenia używane przez węzeł elementu równorzędnego do samodzielnego uwierzytelnienia w innych węzłach w sieci, a także ustawienia uwierzytelniania, używane do uwierzytelniania innych węzłów równorzędnych węzła równorzędnego. Aby uzyskać więcej informacji, zobacz [uwierzytelniania wiadomości kanał elementu równorzędnego](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) i [zabezpieczanie aplikacji kanałów równorzędnych](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [Sieci równorzędne](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Zabezpieczanie klientów](../../../../../docs/framework/wcf/securing-clients.md)  
 [Uwierzytelnianie wiadomości kanału równorzędnego](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Niestandardowe uwierzytelnianie kanału równorzędnego](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Zabezpieczanie aplikacji kanałów równorzędnych](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
