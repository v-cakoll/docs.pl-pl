---
title: <security> dla <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: bdd3b236c9bae198f8027c4ca0c0fa5b70d30342
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936636"
---
# <a name="security-of-peertransport"></a>\<zabezpieczenia > \<peerTransport >
Zawiera ustawienia zabezpieczeń skojarzone z kanałem równorzędnym, w tym typ używanego uwierzytelniania i zabezpieczenia używane do transportu wiadomości.  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<peerTransport>  
\<> zabezpieczeń  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`mode`|Określa typ zabezpieczenia do zastosowania. Wartość domyślna to Message. Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Atrybut Mode  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`None`|Zabezpieczenia są wyłączone.|  
|`Transport`|Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.|  
|`Message`|Zabezpieczenia protokołu SOAP zapewniają uwierzytelnianie, integralność i poufność.|  
|`TransportWithMessageCredential`|Protokół HTTPS zapewnia uwierzytelnianie i poufność. Komunikaty protokołu SOAP zapewniają zaawansowane typy poświadczeń.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> transportu](transport-of-peertransport.md)|Definiuje transport równorzędny dla niestandardowego powiązania. Ten element ma `clientCredentialType` atrybut, który określa poświadczenia, które mają być używane podczas korzystania z usługi. Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.<br /><br /> Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<peerTransport >](peertransport.md)|Definiuje transport równorzędny dla niestandardowego powiązania.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Zabezpieczenia transportu](../../../wcf/feature-details/transport-security.md)
- [Transporty](../../../wcf/feature-details/transports.md)
- [Wybieranie transportu](../../../wcf/feature-details/choosing-a-transport.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
