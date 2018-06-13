---
title: '&lt;security&gt; w &lt;netTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f58dd0ee1b00785e82628e5442c736866ffe7db5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751236"
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a>&lt;security&gt; w &lt;netTcpBinding&gt;
Definiuje ustawienia zabezpieczeń dla powiązania.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netTcpBinding>  
\<Powiązanie >  
\<Zabezpieczenia >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|tryb|Opcjonalna. Określa typ zabezpieczeń, która została zastosowana. Poniżej przedstawiono prawidłowe wartości. Wartość domyślna to `Transport`.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Tryb atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Zabezpieczenia są wyłączone.|  
|Transportu|Zabezpieczenia transportu są udostępniane za pośrednictwem protokołu TCP lub SPNego przy użyciu protokołu TLS. Usługa może być konieczne można skonfigurować za pomocą certyfikatów SSL. Jest możliwe kontrolowanie poziomu ochrony, w tym trybie.|  
|Komunikat|Zabezpieczenia korzystanie z zabezpieczeń komunikatów SOAP. Domyślnie treści protokołu SOAP zostaje zaszyfrowany i podpisany. W tym trybie oferuje wiele funkcji, takich jak określa, czy poświadczenia usługi są dostępne pod adresem klientem poza pasmem, pakiet algorytmów do użycia, a poziom ochrony do zastosowania do treści wiadomości. Uwierzytelnianie klienta jest wykonywane raz na sesji i wyniki uwierzytelniania są buforowane na czas trwania sesji.|  
|TransportWithMessageCredential|Zabezpieczenia transportu jest sprzężona z zabezpieczeń wiadomości. Zabezpieczenia transportu są dostarczane przez TLS za pośrednictwem protokołu TCP lub SPNego i zapewnia integralność, poufności i uwierzytelniania serwera. Zabezpieczenia komunikatów SOAP zapewnia uwierzytelnianie klienta. Domyślnie uwierzytelnianie klienta jest wykonywane raz na sesji i wyniki uwierzytelniania są buforowane na czas trwania sesji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<transport >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|Definiuje ustawienia zabezpieczeń dla transportu. Ten element jest typu <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|Definiuje ustawienia zabezpieczeń dla wiadomości. Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|powiązanie|Element powiązania [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Uwagi  
 Każdy powiązań standardowych zawiera parametry kontrolowanie wymagania dotyczące zabezpieczeń transferu. Te parametry obejmują zazwyczaj tryb zabezpieczeń, które określone, czy używany jest zabezpieczeń na poziomie transportu lub poziom wiadomości i wybór typu poświadczeń klienta. Na podstawie wyboru opcji parametrów nie istnieje stosu kanał jest tworzony z odpowiednich ustawień zabezpieczeń.  
  
 Powiązania dostarczane przez system dostarczane przez Windows Communication Foundation (WCF) są zestawem zaprojektowane pod kątem niektórych wymagań najbardziej typowych scenariuszy. Każdy z tych powiązań umożliwia określenie wymagań dotyczących zabezpieczeń dla niektórych konkretnych scenariuszy docelowych.  
  
 Ten element konfiguracji zawiera specyfikacji zabezpieczenia dla `netTcpBinding`. Jest to bezpieczne, niezawodne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami. Domyślnie generuje stosu komunikacji środowiska uruchomieniowego obsługi protokołu TCP dla dostarczanie komunikatów i zabezpieczenia systemu Windows dla komunikatów zabezpieczeń i uwierzytelniania, WS-ReliableMessaging, niezawodności i kodowanie komunikatu binarnego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
