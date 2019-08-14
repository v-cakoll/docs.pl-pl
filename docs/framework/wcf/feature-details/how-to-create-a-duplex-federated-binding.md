---
title: 'Instrukcje: tworzenie dwukierunkowego wiązania federacyjnego'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 71c970fa45d7d4ccd55fceddb2360d0aa0a768f8
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972060"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Instrukcje: tworzenie dwukierunkowego wiązania federacyjnego

<xref:System.ServiceModel.WSFederationHttpBinding>obsługuje tylko kontrakty wymiany dla komunikatów datagram i Request/Reply. Aby można było korzystać z kontraktu programu Exchange z wiadomościami dwustronnymi, należy utworzyć niestandardowe powiązanie. Poniższe procedury pokazują, jak to zrobić w konfiguracji, przy użyciu zabezpieczeń trybu komunikatów dla transportów HTTP i TCP oraz przy użyciu zabezpieczeń w trybie mieszanym do transportu TCP. Przykładowy kod pokazujący wszystkie 3 powiązania znajduje się na końcu tego tematu.

Możesz również utworzyć powiązanie w kodzie. Opis stosu elementów powiązania do utworzenia znajduje się w temacie [How to: Utwórz niestandardowe powiązanie przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Aby utworzyć niestandardowe powiązanie federacyjne z protokołem HTTP

1. W węźle powiązania > [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) pliku konfiguracji Utwórz niestandardowy element >Binding. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

2. W elemencie CustomBinding `name` > Utwórz element `FederationDuplexHttpMessageSecurityBinding` [ >powiązaniazatrybutemustawionymna.\<](../../../../docs/framework/misc/binding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

3. `authenticationMode` `SecureConversation` [ Wewnątrz\<elementu](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ Binding>Utwórzelement>zabezpieczeńz\<](../../../../docs/framework/misc/binding.md) atrybutem ustawionym na.

4. `IssuedTokenForCertificate` `authenticationMode` `IssuedTokenForSslNegotiated` [ Wewnątrz\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ elementu>zabezpieczeńUtwórzelement>secureConversationBootstrapzatrybutem\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) ustawionym na lub.

5. Po elemencie [> zabezpieczeńUtwórzpustyelement>compositeDuplex.\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)

6. Po elemencie [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) compositeDuplex > Utwórz pusty element > oneWay. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)

7. Po elemencie [> oneWayUtwórzpustyelement>httpTransport.\<](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Aby utworzyć niestandardowe powiązanie federacyjne z trybem zabezpieczeń wiadomości TCP

1. W węźle powiązania > [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) pliku konfiguracji Utwórz niestandardowy element >Binding. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

2. W elemencie CustomBinding `name` > Utwórz element `FederationDuplexTcpMessageSecurityBinding` [ >powiązaniazatrybutemustawionymna.\<](../../../../docs/framework/misc/binding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

3. `authenticationMode` `SecureConversation` [ Wewnątrz\<elementu](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ Binding>Utwórzelement>zabezpieczeńz\<](../../../../docs/framework/misc/binding.md) atrybutem ustawionym na.

4. `IssuedTokenForCertificate` `authenticationMode` `IssuedTokenForSslNegotiated` [ Wewnątrz\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ elementu>zabezpieczeńUtwórzelement>secureConversationBootstrapzatrybutem\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) ustawionym na lub.

5. Po elemencie [> zabezpieczeńUtwórzpustyelement>tcpTransport.\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Aby utworzyć niestandardowe powiązanie federacyjne z trybem mieszanym protokołu TCP

1. W węźle powiązania > [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) pliku konfiguracji Utwórz niestandardowy element >Binding. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

2. W elemencie CustomBinding `name` > Utwórz element `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` [ >powiązaniazatrybutemustawionymna.\<](../../../../docs/framework/misc/binding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

3. `authenticationMode` `SecureConversation` [ Wewnątrz\<elementu](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ Binding>Utwórzelement>zabezpieczeńz\<](../../../../docs/framework/misc/binding.md) atrybutem ustawionym na.

4. `IssuedTokenForCertificate` `authenticationMode` `IssuedTokenForSslNegotiated` [ Wewnątrz\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ elementu>zabezpieczeńUtwórzelement>secureConversationBootstrapzatrybutem\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) ustawionym na lub.

5. Po elemencie [> zabezpieczeńUtwórzpustyelement>sslStreamSecurity.\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)

6. Po sslStreamSecurity elementu > Utwórz pusty [ \<element tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) . [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)

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
