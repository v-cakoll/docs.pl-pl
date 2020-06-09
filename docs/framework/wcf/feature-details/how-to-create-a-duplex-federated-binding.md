---
title: 'Instrukcje: Tworzenie dwukierunkowego powiązania federacyjnego'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: e93651ce9fe9dae55c299fcb061da6bdc4b6bc5e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598973"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Instrukcje: Tworzenie dwukierunkowego powiązania federacyjnego

<xref:System.ServiceModel.WSFederationHttpBinding>obsługuje tylko kontrakty wymiany dla komunikatów datagram i Request/Reply. Aby można było korzystać z kontraktu programu Exchange z wiadomościami dwustronnymi, należy utworzyć niestandardowe powiązanie. Poniższe procedury pokazują, jak to zrobić w konfiguracji, przy użyciu zabezpieczeń trybu komunikatów dla transportów HTTP i TCP oraz przy użyciu zabezpieczeń w trybie mieszanym do transportu TCP. Przykładowy kod pokazujący wszystkie 3 powiązania znajduje się na końcu tego tematu.

Możesz również utworzyć powiązanie w kodzie. Opis stosu elementów powiązania do utworzenia znajduje się w temacie [How to: Create a Custom Binding using the elementu SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Aby utworzyć niestandardowe powiązanie federacyjne z protokołem HTTP

1. W [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) węźle pliku konfiguracji Utwórz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.

2. Wewnątrz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elementu Utwórz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element z `name` atrybutem ustawionym na `FederationDuplexHttpMessageSecurityBinding` .

3. Wewnątrz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu Utwórz [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` atrybutem ustawionym na `SecureConversation` .

4. Wewnątrz [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu Utwórz [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` atrybutem ustawionym na `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated` .

5. Po [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemencie Utwórz pusty [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element.

6. Po [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) elemencie Utwórz pusty [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element.

7. Po [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) elemencie Utwórz pusty [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) element.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Aby utworzyć niestandardowe powiązanie federacyjne z trybem zabezpieczeń wiadomości TCP

1. W [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) węźle pliku konfiguracji Utwórz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.

2. Wewnątrz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elementu Utwórz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element z `name` atrybutem ustawionym na `FederationDuplexTcpMessageSecurityBinding` .

3. Wewnątrz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu Utwórz [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` atrybutem ustawionym na `SecureConversation` .

4. Wewnątrz [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu Utwórz [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` atrybutem ustawionym na `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated` .

5. Po [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemencie Utwórz pusty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Aby utworzyć niestandardowe powiązanie federacyjne z trybem mieszanym protokołu TCP

1. W [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) węźle pliku konfiguracji Utwórz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.

2. Wewnątrz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elementu Utwórz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element z `name` atrybutem ustawionym na `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` .

3. Wewnątrz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu Utwórz [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` atrybutem ustawionym na `SecureConversation` .

4. Wewnątrz [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu Utwórz [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` atrybutem ustawionym na `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated` .

5. Po [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemencie Utwórz pusty [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element.

6. Po [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) elemencie Utwórz pusty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.

## <a name="code-sample"></a>Przykładowy kod

### <a name="sample-with-3-bindings"></a>Przykład z 3 powiązaniami

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
