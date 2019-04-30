---
title: 'Instrukcje: tworzenie dwukierunkowego wiązania federacyjnego'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 510faa0b1d791b1d164c55e9fa32daafa559d56c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696213"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Instrukcje: tworzenie dwukierunkowego wiązania federacyjnego
<xref:System.ServiceModel.WSFederationHttpBinding> obsługuje tylko kontraktami wymiany komunikatów datagram i żądanie/nietypizowana odpowiedź. Aby użyć kontrakt wymiany komunikatów dupleksowy, należy utworzyć niestandardowego powiązania. Poniższe procedury pokazują, jak to zrobić w konfiguracji, za pomocą komunikatu tryb zabezpieczeń dla transportu HTTP i TCP i korzystanie z zabezpieczeń w trybie mieszanym dla warstwy transportowej TCP. Przykładowy kod, przedstawiający wszystkie powiązania 3 znajduje się na końcu tego tematu.  
  
 Można również utworzyć powiązanie w kodzie. Aby uzyskać opis stosie elementów powiązania, aby utworzyć, zobacz [jak: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Aby utworzyć niestandardowe dwukierunkowego powiązania federacyjnego za pośrednictwem protokołu HTTP  
  
1. W [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) węzeł pliku konfiguracji, tworzenia [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu.  
  
2. Wewnątrz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) element z `name` ustawioną wartość atrybutu `FederationDuplexHttpMessageSecurityBinding`.  
  
3. Wewnątrz [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu, Utwórz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` ustawioną wartość atrybutu `SecureConversation`.  
  
4. Wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` ustawioną wartość atrybutu `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.  
  
5. Następujące [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz pustą [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) elementu.  
  
6. Następujące [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) elementu, Utwórz pustą [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) elementu.  
  
7. Następujące [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) elementu, Utwórz pustą [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) elementu.  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Aby utworzyć niestandardowe dwukierunkowego powiązania federacyjnego przy użyciu trybu zabezpieczenia wiadomości TCP  
  
1. W [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) węzeł pliku konfiguracji, tworzenia [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu.   
  
2. Wewnątrz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) element z `name` ustawioną wartość atrybutu `FederationDuplexTcpMessageSecurityBinding`.  
  
3. Wewnątrz [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu, Utwórz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` ustawioną wartość atrybutu `SecureConversation`.  
  
4. Wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` ustawioną wartość atrybutu `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.  
  
5. Następujące [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz pustą [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) elementu.  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Aby utworzyć dupleks federacyjnych niestandardowego powiązania za pomocą trybu mieszanego zabezpieczeń protokołu TCP  
  
1. W [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) węzeł pliku konfiguracji, tworzenia [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu.   
  
2. Wewnątrz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) element z `name` ustawioną wartość atrybutu `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.  
  
3. Wewnątrz [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu, Utwórz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` ustawioną wartość atrybutu `SecureConversation`.  
  
4. Wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` ustawioną wartość atrybutu `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.  
  
5. Następujące [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz pustą [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) elementu.  
  
6. Następujące [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) elementu, Utwórz pustą [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) elementu.  
  
## <a name="code-sample"></a>Przykładowy kod  
  
#### <a name="sample-with-3-bindings"></a>Oto przykład z 3 powiązania  
  
1. Wstaw następujący kod do pliku konfiguracji.  
  
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
