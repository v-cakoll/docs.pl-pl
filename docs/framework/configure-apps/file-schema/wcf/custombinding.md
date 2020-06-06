---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: cdaaacf0dfa75209d001f6e8d6ac7175816048aa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140793"
---
# \<customBinding>

Zapewnia pełną kontrolę nad stosem obsługi komunikatów dla użytkownika.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customBinding>**  

## <a name="syntax"></a>Składnia

```xml
<customBinding>
  <binding name="String"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
    <compositeDuplex clientBaseAddress="Uri" />
    <reliableSession acknowledgementInterval="TimeSpan"
                     advancedFlowControl="Boolean"
                     bufferedMessagesQuota="Integer"
                     inactivityTimeout="TimeSpan"
                     maxPendingChannels="Integer"
                     maxRetryCount="Integer"
                     ordered="Boolean" />
    <pnrpPeerResolver />
    <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
    <sslStreamSecurity requireClientCertificate="Boolean" />
    <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              contextMode="Cookie"
              defaultProtectionLevel="Sign"
              enableKeyDerivation="false"
              keyEntropyMode="ClientEntropy"
              messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"
              securityVersion="WSSecurityXXX2005">
      <localClientSettings cacheCookies="false"
                           detectReplays="false"
                           maxCookieCachingTime="00:07:24" />
      <localServiceSettings replayCacheSize="9"
                            maxClockSkew="00:00:03"
                            replayWindow="00:07:22.2190000" />
    </security>
    <binaryMessageEncoding maxReadPoolSize="Integer"
                           maxWritePoolSize="Integer"
                           maxSessionSize="Integer" />
    <httpsTransport manualAddressing="Boolean"
                    maxMessageSize="Integer"
                    authenticationScheme="Negotiate"
                    bypassProxyOnLocal="Boolean"
                    hostNameComparisonMode="Exact"
                    mapAddressingHeadersToHttpHeaders="Boolean"
                    proxyaddress="Uri"
                    realm="String"
                    requireClientCertificate="Boolean" />
    <peerTransport manualAddressing="false"
                   maxMessageSize="20002"
                   listenIPAddress="202.10.1.9"
                   messageAuthentication="false"
                   peerNodeAuthenticationMode="None"
                   port="1000" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean">
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                            issuedCookieLifeTime="TimeSpan"
                            maxStatefulNegotiations="Integer"
                            replayCacheSize="Integer"
                            maxClockSkew="TimeSpan"
                            negotiationTimeout="TimeSpan"
                            replayWindow="TimeSpan"
                            inactivityTimeout="TimeSpan"
                            sessionKeyRenewalInterval="TimeSpan"
                            sessionKeyRolloverInterval="TimeSpan"
                            reconnectOnTransportFailure="Boolean"
                            maxConcurrentSessions="Integer"
                            timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
    </security>
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean" >
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                           issuedCookieLifeTime="TimeSpan"
                           maxStatefulNegotiations="Integer"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           negotiationTimeout="TimeSpan"
                           replayWindow="TimeSpan"
                           inactivityTimeout="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           maxConcurrentSessions="Integer"
                           timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
      <genericIssuedTokenParameters>
        <localIssuerIssuedTokenParameters keyType="SymmetricKey/PublicKey"
                                          keySize="Integer"
                                          tokenType="String" />
        <issuedTokenParametersEndpointAddress address="URI"
                                              bindingConfiguration="String"
                                              binding="String" />
        <issuedTokenClient localIssuerChannelBehaviors="String"
                           cacheIssuedTokens="Boolean"
                           maxIssuedTokenCachingTime="TimeSpan"
                           keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />
        <issuedTokenClientBehavior issuerAddress="String"
                                   behaviorConfiguration="String" />
        <issuedTokenClientBehavior address="URI"
                                   bindingConfiguration="String"
                                   binding="String" />
      </genericIssuedTokenParameters>
    </security>
  </binding>
</customBinding>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|closeTimeout|<xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|
|name|Ciąg zawierający nazwę konfiguracji powiązania. Ta wartość jest ciągiem zdefiniowanym przez użytkownika, który działa jako ciąg identyfikacyjny dla niestandardowego powiązania. Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|
|openTimeout|<xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|
|receiveTimeout|Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|
|Właściwości SendTimeout|<xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<compositeDuplex>](compositeduplex.md)|Określa komunikat dwukierunkowy dla niestandardowego powiązania. Jest on używany z transportami, które nie zezwalają na natywną komunikację bezstronną, na przykład HTTP. Protokół TCP, w przeciwieństwie, umożliwia natywną komunikację bezstronną i nie wymaga użycia tego elementu powiązania dla usługi do wysyłania komunikatów z powrotem do klienta.<br /><br /> Klient musi uwidocznić adres usługi, aby nawiązać kontakt i nawiązać połączenie. Ten adres klienta jest dostarczany przez `ClientBaseAddress` atrybut.<br /><br /> Ten element jest typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement> .|
|[\<pnrpPeerResolver>](pnrppeerresolver.md)|Określa program rozpoznawania nazw elementów równorzędnych protokołu PNRP (Peer Name Resolution Protocol). Ten element jest typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement> .|
|[\<reliableSession>](reliablesession.md)|Określa ustawienie dla obsługi komunikatów w usłudze WS-niezawodny. Gdy ten element zostanie dodany do niestandardowego powiązania, otrzymany kanał może obsługiwać tylko jednokrotne gwarancje dostarczania. Ten element jest typu <xref:System.ServiceModel.Configuration.ReliableSessionElement> .|
|[\<security>](security-of-custombinding.md)|Określa opcje zabezpieczeń niestandardowego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.SecurityElement> .|
|[\<sslStreamSecurity>](sslstreamsecurity.md)|Określa ustawienia zabezpieczeń dla powiązania strumienia SSL. Ten element jest typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement> .|
|[\<transactionFlow>](transactionflow.md)|Określa, że powiązanie obsługuje przepływ transakcji, oraz protokołu, który ma być używany przez `transactionProtocol` atrybut. Ten element jest typu <xref:System.ServiceModel.Configuration.TransactionFlowElement> .|
|[\<windowsStreamSecurity>](windowsstreamsecurity.md)|Określa opcje zabezpieczeń przesyłania strumieniowego dla niestandardowego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement> .|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|powiązania|Zawiera wszystkie powiązania dla Windows Communication Foundation aplikacji.|

## <a name="remarks"></a>Uwagi

Niestandardowe powiązania zapewniają pełną kontrolę nad stosem obsługi komunikatów WCF. Można utworzyć specjalne powiązania dostosowane, dodając elementy konfiguracji dla określonych jednostek. Na przykład użytkownik może połączyć `httpsTransport` sekcję, `reliableSession` sekcję i `security` sekcję, aby utworzyć niezawodne i bezpieczne powiązanie https.

Pojedyncze powiązanie definiuje stos komunikatów przez określenie elementów konfiguracji dla elementów stosu w kolejności, w jakiej występują na stosie. Każdy element definiuje i konfiguruje jeden element stosu. W każdym powiązaniu niestandardowym musi istnieć jeden i tylko jeden element transportu. Bez tego elementu stos komunikatów jest niekompletny.

Kolejność, w której elementy pojawiają się w kwestiach stosu, ponieważ jest to kolejność, w której operacje są stosowane do wiadomości. Zalecana kolejność elementów stosu jest następująca:

1. Transakcje (opcjonalnie)

2. Niezawodna obsługa komunikatów (opcjonalnie)

3. Zabezpieczenia (opcjonalnie)

4. Transport

5. Koder (opcjonalnie)

Użyj niestandardowego powiązania, gdy jedno z powiązań dostarczonych przez system nie spełnia wymagań usługi. Można na przykład użyć niestandardowego powiązania, aby umożliwić korzystanie z nowego lub nowego kodera w punkcie końcowym usługi.

Niestandardowe powiązanie jest konstruowane przy użyciu jednej z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> kolekcji elementów powiązania, które są "ułożone" w określonej kolejności:

- U góry jest opcjonalne <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> , które umożliwia przepływ transakcji.

- Następnie jest opcjonalne <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> , które udostępnia mechanizm sesji i kolejności, zgodnie z definicją w specyfikacji WS-ReliableMessaging. To pojęcie sesji może przekroczyć pośredniki SOAP i transportu.

- Dalej jest opcjonalny element powiązania zabezpieczeń, który zapewnia funkcje zabezpieczeń, takie jak autoryzacja, uwierzytelnianie, ochrona i poufność. Następujące elementy powiązań zabezpieczeń są udostępniane przez Windows Communication Foundation (WCF):

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- Następnie są opcjonalne wzorce komunikatów określone przez elementy powiązania:

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- Poniżej przedstawiono opcjonalne elementy powiązania uaktualnienia/pomocnika transportu:

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- Następnie jest wymagany element powiązania kodowania komunikatów. Możesz użyć własnego transportu lub użyć jednego z następujących powiązań kodowania komunikatów:

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- U dołu jest wymagany element transportu. Możesz użyć własnego transportu lub użyć jednego z elementów powiązania transportowego dostarczonych przez Windows Communication Foundation (WCF):

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

Poniższa tabela zawiera podsumowanie opcji dla każdej warstwy.

|Warstwa|Opcje|Wymagane|
|-----------|-------------|--------------|
|Przepływ transakcji|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Nie|
|Niezawodność|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Nie|
|Zabezpieczenia|Symetryczne, asymetryczne, na poziomie transportu|Nie|
|Zmiana kształtu|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|Nie|
|Uaktualnienia transportu|Strumień SSL, strumień systemu Windows, program rozpoznawania elementów równorzędnych|Nie|
|Kodowanie|Tekst, dane binarne, MTOM, niestandardowe|Tak|
|Transport|TCP, nazwane potoki, HTTP, HTTPS, typy usługi MSMQ, niestandardowe|Tak|

Ponadto można definiować własne elementy powiązania i wstawiać je między wszystkimi wcześniej zdefiniowanymi warstwami.

Aby uzyskać informacje na temat sposobu użycia niestandardowego powiązania do modyfikacji powiązania dostarczonego przez system, zobacz [How to: Dostosowywanie podanego przez system powiązania](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<binding>](bindings.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [CustomBinding — element](custombinding.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
