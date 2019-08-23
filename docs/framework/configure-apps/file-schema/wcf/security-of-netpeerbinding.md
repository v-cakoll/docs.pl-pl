---
title: <security> dla <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: be5ebacec466caf8d8a77bf552f42da1861e77a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936627"
---
# <a name="security-of-netpeerbinding"></a>\<> \<zabezpieczeń elementu webpeerbinding >
Definiuje ustawienia [ \<zabezpieczeń > NetPeerTcpBinding](netpeertcpbinding.md), włącznie z typem używanego uwierzytelniania i zabezpieczeniami używanymi do transportu wiadomości.  
  
 \<system.ServiceModel>  
\<> powiązań  
\<netPeerBinding>  
\<> powiązania  
\<> zabezpieczeń  
  
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
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|tryb|Opcjonalny. Określa typ zabezpieczeń używanych przez elementy równorzędne skonfigurowane przy użyciu tego powiązania. Wartość domyślna to `Message`. Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Atrybut Mode  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Message|Zabezpieczenia protokołu SOAP zapewniają uwierzytelnianie, integralność i poufność.|  
|Brak|Zabezpieczenia są wyłączone.|  
|Transportu|Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.|  
|TransportWithMessageCredential|Protokół HTTPS zapewnia uwierzytelnianie i poufność. Komunikaty protokołu SOAP zapewniają zaawansowane typy poświadczeń.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> transportu](transport-of-netpeertcpbinding.md)|Definiuje typ transportu dla zabezpieczonych komunikatów wysyłanych przez elementy równorzędne skonfigurowane przy użyciu tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> powiązania](../../../misc/binding.md)|Definiuje wszystkie możliwości [ \<powiązań NetPeerTcpBinding >](netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Uwagi  
 Zabezpieczenia mogą dotyczyć zarówno komunikatów, jak i związanych z transportem.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Wybieranie typu poświadczeń](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> powiązania](../../../misc/binding.md)
