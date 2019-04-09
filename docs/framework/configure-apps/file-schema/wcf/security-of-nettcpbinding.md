---
title: <security> z <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: 3fd850862172ad2b9bd58cd01d332028ff76462a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199079"
---
# <a name="security-of-nettcpbinding"></a>\<Zabezpieczenia > z \<netTcpBinding >
Definiuje ustawienia zabezpieczeń dla powiązania.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netTcpBinding>  
\<Powiązanie >  
\<security>  
  
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
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|tryb|Opcjonalna. Określa typ zabezpieczeń, która jest stosowana. Poniżej przedstawiono prawidłowe wartości. Wartość domyślna to `Transport`.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Tryb atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Zabezpieczenia są wyłączone.|  
|Transport|Zabezpieczenia transportu znajduje się za pośrednictwem protokołu TCP lub SPNego przy użyciu protokołu TLS. Usługa może być konieczne można skonfigurować za pomocą certyfikatów SSL. Istnieje możliwość kontrolować poziom ochrony w tym trybie.|  
|Komunikat|Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP. Domyślnie treści protokołu SOAP jest zaszyfrowany i podpisany. Ten tryb zapewnia szeroką gamę funkcji, takich jak tego, czy poświadczenia usługi są dostępne pod adresem klientem poza pasmem, pakiet algorytmów, używać oraz poziom ochrony w celu zastosowania do treści wiadomości. Uwierzytelnianie klienta jest wykonywane raz na sesji i wyniki uwierzytelniania są buforowane na czas trwania sesji.|  
|TransportWithMessageCredential|Zabezpieczenia transportu jest sprzężona z zabezpieczeń komunikatów. Zabezpieczenia transportu znajduje się przez protokół TLS za pośrednictwem protokołu TCP lub SPNego i zapewnia integralność, poufności i uwierzytelniania serwera. Zabezpieczenia komunikatów SOAP zapewnia uwierzytelnianie klienta. Domyślnie uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane na czas trwania sesji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|Definiuje ustawienia zabezpieczeń dla transportu. Ten element jest typu <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|Definiuje ustawienia zabezpieczeń dla wiadomości. Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|powiązanie|Element powiązania [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Uwagi  
 Każda standardowa powiązania udostępnia parametry do kontrolowania wymagania w zakresie zabezpieczeń transferu. Te parametry obejmują zazwyczaj tryb zabezpieczeń, który określono, czy zabezpieczeń na poziomie transportu lub poziomie wiadomości jest używany i wybór typu poświadczeń klienta. Na podstawie wybranego opcji Parametry te obecny, stos kanał jest zbudowany z odpowiednie zabezpieczenia.  
  
 Powiązania dostarczane przez system, dostarczonych przez Windows Communication Foundation (WCF) to zestaw zaprojektowanych do spełniania niektóre z najczęściej stawianych wymagań scenariusza. Każda z tych powiązań umożliwia określenie wymagań dotyczących zabezpieczeń w niektórych określonych scenariuszach docelowych.  
  
 Ten element konfiguracji zawiera specyfikacje zabezpieczeń `netTcpBinding`. Jest to bezpieczne, niezawodne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami. Domyślnie generuje stosu komunikacji środowiska uruchomieniowego obsługi protokołu TCP dla dostarczania wiadomości i zabezpieczeń Windows dla zabezpieczenia wiadomości i każde uwierzytelnienie, WS-ReliableMessaging, niezawodność i kodowania komunikatu binarnego.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą wiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
