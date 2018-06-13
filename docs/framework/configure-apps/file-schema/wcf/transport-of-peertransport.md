---
title: '&lt;transport&gt; w &lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: aeadf23b4ae6b4b0be18755c43585cbfea418567
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756426"
---
# <a name="lttransportgt-of-ltpeertransportgt"></a>&lt;transport&gt; w &lt;peerTransport&gt;
Określa typ transportu zabezpieczonych wiadomości wysyłanych przez elementy równorzędne skonfigurowane dla tego wiązania.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<peerTransport >  
\<Zabezpieczenia >  
\<transport>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|credentialType|Opcjonalna. Określa poświadczenia używane do weryfikowania wiadomości wysyłane z transportu elementów równorzędnych. Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.|  
  
## <a name="credentialtype-attribute"></a>credentialType atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|certyfikat|Uwierzytelnianie kanał transportowy peer wymaga X509 certyfikatu.|  
|Hasło|Uwierzytelnianie kanał transportowy peer wymaga poprawne hasło.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|Definiuje ustawienia zabezpieczeń transportu elementów równorzędnych.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element jest ustawiona tylko wtedy, gdy atrybut tryb [ \<zabezpieczeń >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) ustawiono `Transport` lub `TransportWithMessageCredential`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Zabezpieczenia transportu](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Transporty](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Wybieranie transportu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
