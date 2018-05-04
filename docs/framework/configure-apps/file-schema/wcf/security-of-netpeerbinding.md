---
title: '&lt;security&gt; w &lt;netPeerBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7413820f1a1f38b3d533573715267df3b85c9d9a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a>&lt;security&gt; w &lt;netPeerBinding&gt;
Definiuje ustawienia zabezpieczeń [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), takich jak typ uwierzytelniania używany i zabezpieczenia używany do transportu wiadomości.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netPeerBinding>  
\<Powiązanie >  
\<Zabezpieczenia >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|tryb|Opcjonalna. Określa typ zabezpieczeń używanych przez elementy równorzędne skonfigurowane dla tego wiązania. Wartość domyślna to `Message`. Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Tryb atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Komunikat|Zabezpieczenia protokołu SOAP oferuje uwierzytelniania, integralności i poufności.|  
|Brak|Zabezpieczenia są wyłączone.|  
|Transportu|Zabezpieczenia przy użyciu protokołu HTTPS.|  
|TransportWithMessageCredential|Protokół HTTPS oferuje uwierzytelnianie i poufności. Wiadomości SOAP Podaj sformatowanego poświadczeń.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<transport >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|Definiuje typ transportu zabezpieczonych wiadomości wysyłanych przez elementy równorzędne skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Uwagi  
 Zabezpieczeń może być albo wiadomości - lub specyficznych dla transportu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Wybieranie typu poświadczeń](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
