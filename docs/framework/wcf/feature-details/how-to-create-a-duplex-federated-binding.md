---
title: 'Instrukcje: Tworzenie dwukierunkowego powiązania federacyjnego'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 3ecd9e2dbeb30bb255cbf66488b50a9b20219431
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141721"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Instrukcje: Tworzenie dwukierunkowego powiązania federacyjnego

<xref:System.ServiceModel.WSFederationHttpBinding> obsługuje tylko kontrakty wymiany dla komunikatów datagram i Request/Reply. Aby można było korzystać z kontraktu programu Exchange z wiadomościami dwustronnymi, należy utworzyć niestandardowe powiązanie. Poniższe procedury pokazują, jak to zrobić w konfiguracji, przy użyciu zabezpieczeń trybu komunikatów dla transportów HTTP i TCP oraz przy użyciu zabezpieczeń w trybie mieszanym do transportu TCP. Przykładowy kod pokazujący wszystkie 3 powiązania znajduje się na końcu tego tematu.

Możesz również utworzyć powiązanie w kodzie. Opis stosu elementów powiązania do utworzenia znajduje się w temacie [How to: Create a Custom Binding using the elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Aby utworzyć niestandardowe powiązanie federacyjne z protokołem HTTP

1. W węźle [\<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji utwórz element [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. Wewnątrz elementu [\<custombinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) utwórz element [> powiązania\<](../../configure-apps/file-schema/wcf/bindings.md) z atrybutem `name` ustawionym na `FederationDuplexHttpMessageSecurityBinding`.

3. Wewnątrz elementu [\<binding >](../../configure-apps/file-schema/wcf/bindings.md) utwórz element [\<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) z atrybutem `authenticationMode` ustawionym na `SecureConversation`.

4. Wewnątrz elementu [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) utwórz element [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) z atrybutem `authenticationMode` ustawionym na `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.

5. Po elemencie [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) utwórz pusty [\<elementu > compositeDuplex](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) .

6. Po elemencie [\<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) utwórz pusty [\<element > oneWay](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) .

7. Po elemencie [\<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) utwórz pusty [\<elementu > httpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) .

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Aby utworzyć niestandardowe powiązanie federacyjne z trybem zabezpieczeń wiadomości TCP

1. W węźle [\<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji utwórz element [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. Wewnątrz elementu [\<custombinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) utwórz element [> powiązania\<](../../configure-apps/file-schema/wcf/bindings.md) z atrybutem `name` ustawionym na `FederationDuplexTcpMessageSecurityBinding`.

3. Wewnątrz elementu [\<binding >](../../configure-apps/file-schema/wcf/bindings.md) utwórz element [\<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) z atrybutem `authenticationMode` ustawionym na `SecureConversation`.

4. Wewnątrz elementu [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) utwórz element [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) z atrybutem `authenticationMode` ustawionym na `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.

5. Po elemencie [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) utwórz pusty [\<elementu > tcpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) .

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Aby utworzyć niestandardowe powiązanie federacyjne z trybem mieszanym protokołu TCP

1. W węźle [\<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji utwórz element [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. Wewnątrz elementu [\<custombinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) utwórz element [> powiązania\<](../../configure-apps/file-schema/wcf/bindings.md) z atrybutem `name` ustawionym na `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.

3. Wewnątrz elementu [\<binding >](../../configure-apps/file-schema/wcf/bindings.md) utwórz element [\<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) z atrybutem `authenticationMode` ustawionym na `SecureConversation`.

4. Wewnątrz elementu [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) utwórz element [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) z atrybutem `authenticationMode` ustawionym na `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.

5. Po elemencie [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) utwórz pusty [\<elementu > sslStreamSecurity](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) .

6. Po elemencie [\<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) Utwórz pusty element [\<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) .

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
