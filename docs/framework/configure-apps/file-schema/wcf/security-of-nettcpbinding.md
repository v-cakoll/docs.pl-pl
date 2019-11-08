---
title: <security> dla <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: aa01e906ddd2f15007c72bfc2a45122cfb15ba2c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736373"
---
# <a name="security-of-nettcpbinding"></a>\<> zabezpieczeń \<netTcpBinding >
Definiuje ustawienia zabezpieczeń dla powiązania.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<NetTcpBinding**](nettcpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpieczenia >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|tryb|Opcjonalny. Określa typ stosowanego zabezpieczenia. Poniżej przedstawiono prawidłowe wartości. Wartość domyślna to `Transport`.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Atrybut Mode  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Zabezpieczenia są wyłączone.|  
|Transportu|Zabezpieczenia transportu są udostępniane przy użyciu protokołu TLS przez TCP lub SPNego. Może być konieczne skonfigurowanie usługi przy użyciu certyfikatów SSL. Istnieje możliwość kontrolowania poziomu ochrony w tym trybie.|  
|Komunikat|Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP. Domyślnie treść protokołu SOAP jest zaszyfrowana i podpisana. Ten tryb oferuje różne funkcje, takie jak to, czy poświadczenia usługi są dostępne na kliencie poza pasmem, pakiet algorytmów do użycia oraz jaki poziom ochrony ma być stosowany do treści wiadomości. Uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane na czas trwania sesji.|  
|TransportWithMessageCredential|Zabezpieczenia transportu są powiązane z zabezpieczeniami komunikatów. Zabezpieczenia transportu są udostępniane przez protokół TLS przez TCP lub SPNego oraz zapewniają integralność, poufność i uwierzytelnianie serwera. Zabezpieczenia komunikatów protokołu SOAP zapewniają uwierzytelnianie klienta. Domyślnie uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane przez czas trwania sesji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[> transportu \<](transport-of-nettcpbinding.md)|Definiuje ustawienia zabezpieczeń transportu. Ten element jest typu <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.|  
|[\<> komunikatów](message-element-of-nettcpbinding.md)|Definiuje ustawienia zabezpieczeń wiadomości. Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|powiązanie|Element powiązania [\<netTcpBinding >](nettcpbinding.md).|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie powiązania standardowe zawierają parametry służące do kontrolowania wymagań dotyczących zabezpieczeń transferu. Parametry te zazwyczaj obejmują tryb zabezpieczeń, który określa, czy używane są zabezpieczenia na poziomie wiadomości lub transportu oraz wybór typu poświadczeń klienta. Na podstawie wyboru opcji tych parametrów istnieje stos kanału z odpowiednimi zabezpieczeniami.  
  
 Powiązania dostarczone przez system Windows Communication Foundation (WCF) są zestawem zaprojektowanym pod kątem spełnienia niektórych typowych wymagań scenariusza. Każde z tych powiązań umożliwia określenie wymagań dotyczących zabezpieczeń dla niektórych konkretnych scenariuszy.  
  
 Ten element konfiguracji zawiera specyfikacje zabezpieczeń dla `netTcpBinding`. Jest to bezpieczne, niezawodne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami. Domyślnie generuje stos komunikacji środowiska uruchomieniowego obsługujący protokół TCP na potrzeby dostarczania komunikatów i zabezpieczenia systemu Windows w celu zapewnienia bezpieczeństwa i uwierzytelniania komunikatów oraz szyfrowania wiadomości binarnych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [> powiązań \<](bindings.md)
