---
title: <security> dla <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: e88f55f3651d1ccd55631dce13a0349ac2772624
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736389"
---
# <a name="security-of-ws2007httpbinding"></a>\<> zabezpieczeń \<ws2007HttpBinding >
Reprezentuje ustawienia zabezpieczeń używane z\<elementu [> WS2007HttpBinding](ws2007httpbinding.md) .  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WS2007HttpBinding**](ws2007httpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpieczenia >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`mode`|Obowiązkowe. Określa typ stosowanego zabezpieczenia. Wartość domyślna to `Message`.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Atrybut Mode  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`None`|Zabezpieczenia są wyłączone.|  
|`Transport`|Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS. Usługa musi być skonfigurowana z certyfikatami SSL (SSL). Wiadomość jest całkowicie zabezpieczona przy użyciu protokołu HTTPS, a usługa jest uwierzytelniana przez klienta przy użyciu certyfikatu SSL usługi. Uwierzytelnianie klienta jest kontrolowane przez atrybut `ClientCredentials` elementu [\<transport](transport-of-ws2007httpbinding.md) .|  
|`Message`|Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP. Domyślnie treść protokołu SOAP jest zaszyfrowana i podpisana. Ten tryb oferuje różne funkcje, takie jak to, czy poświadczenia usługi są dostępne na klientach poza pasmem, z którego korzysta pakiet algorytmów, oraz jaki poziom ochrony ma być stosowany do treści wiadomości za pomocą <xref:System.ServiceModel.Security.SecurityMessageProperty>. Uwierzytelnianie klienta jest wykonywane raz dla każdej sesji, a wyniki uwierzytelniania są buforowane na czas trwania sesji.|  
|`TransportWithMessageCredential`|W tym trybie protokół HTTPS zapewnia integralność, poufność i uwierzytelnianie serwera, a zabezpieczenia komunikatów protokołu SOAP zapewniają uwierzytelnianie klienta. Domyślnie uwierzytelnianie klienta jest wykonywane raz dla każdej sesji, a wyniki uwierzytelniania są buforowane przez czas trwania sesji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[> transportu \<](transport-of-ws2007httpbinding.md)|Definiuje ustawienia zabezpieczeń transportu. Ten element odnosi się do typu <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>. Te ustawienia są stosowane tylko wtedy, gdy tryb jest ustawiony na transport.|  
|[\<> komunikatów](message-of-ws2007httpbinding.md)|Definiuje ustawienia zabezpieczeń wiadomości. Ten element odnosi się do typu <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>. Te ustawienia nie są stosowane, gdy tryb jest ustawiony na transport.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<ws2007HttpBinding >](ws2007httpbinding.md)|Bezpieczne powiązanie dla aplikacji transportu HTTP.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element jest przeznaczony do współdziałania z usługami, które implementują specyfikacje WS-*. Zabezpieczenia transportu dla tego powiązania są SSL (SSL) za pośrednictwem protokołu HTTP lub HTTPS.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [> powiązań \<](bindings.md)
