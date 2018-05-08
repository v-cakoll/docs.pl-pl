---
title: 'Instrukcje: Tworzenie dwukierunkowego powiązania federacyjnego'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: d736d0119f3e938d81a15d57bb6d97ca2a1990fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Instrukcje: Tworzenie dwukierunkowego powiązania federacyjnego
<xref:System.ServiceModel.WSFederationHttpBinding> obsługuje tylko kontraktami wymiany wiadomość datagramu i żądanie/odpowiedź. Aby użyć kontraktu dwustronnego wiadomości programu exchange, należy utworzyć niestandardowego powiązania. Poniższe procedury pokazują, jak to zrobić w konfiguracji przy użyciu wiadomości tryb zabezpieczeń dla transportu HTTP i TCP i zabezpieczeń w trybie mieszanym dla transportu TCP. Przykładowy kod, przedstawiający wszystkie powiązania 3 znajduje się na końcu tego tematu.  
  
 Można również utworzyć powiązanie w kodzie. Opis stosu powiązania elementów do tworzenia, zobacz [porady: Tworzenie powiązań niestandardowych za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Aby utworzyć dwukierunkowego powiązania federacyjnego niestandardowych za pomocą protokołu HTTP  
  
1.  W [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) węzła pliku konfiguracji, Utwórz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu.  
  
2.  Wewnątrz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) element z `name` ustawić atrybutu `FederationDuplexHttpMessageSecurityBinding`.  
  
3.  Wewnątrz [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu, Utwórz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` ustawić atrybutu `SecureConversation`.  
  
4.  Wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` ustawić atrybutu `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.  
  
5.  Po [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz pustą [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) elementu.  
  
6.  Po [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) elementu, Utwórz pustą [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) elementu.  
  
7.  Po [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) elementu, Utwórz pustą [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) elementu.  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Aby utworzyć dwukierunkowego powiązania federacyjnego niestandardowych za pomocą trybu zabezpieczenia wiadomości TCP  
  
1.  W [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) węzła pliku konfiguracji, Utwórz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu.   
  
2.  Wewnątrz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) element z `name` ustawić atrybutu `FederationDuplexTcpMessageSecurityBinding`.  
  
3.  Wewnątrz [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu, Utwórz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` ustawić atrybutu `SecureConversation`.  
  
4.  Wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` ustawić atrybutu `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.  
  
5.  Po [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz pustą [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) elementu.  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Aby utworzyć dupleks federacyjnych niestandardowego powiązania protokołu TCP w trybie mieszanym zabezpieczeń  
  
1.  W [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) węzła pliku konfiguracji, Utwórz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu.   
  
2.  Wewnątrz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) element z `name` ustawić atrybutu `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.  
  
3.  Wewnątrz [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu, Utwórz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` ustawić atrybutu `SecureConversation`.  
  
4.  Wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` ustawić atrybutu `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.  
  
5.  Po [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz pustą [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) elementu.  
  
6.  Po [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) elementu, Utwórz pustą [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) elementu.  
  
## <a name="code-sample"></a>Przykładowy kod  
  
#### <a name="sample-with-3-bindings"></a>Przykładowe z powiązaniami 3  
  
1.  Wstaw następujący kod do pliku konfiguracji.  
  
## <a name="example"></a>Przykład  
  
```xml  
<bindings>  
   <customBinding>  
      <binding name="FederationDuplexHttpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <httpTransport />  
       </binding>  
<!-- duplex over https is not supported -->  
       <binding name="FederationDuplexTcpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <tcpTransport />  
       </binding>              
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />  
          </security>  
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->  
          <sslStreamSecurity />  
          <tcpTransport />  
       </binding>              
    </customBinding>  
</bindings>  
```
