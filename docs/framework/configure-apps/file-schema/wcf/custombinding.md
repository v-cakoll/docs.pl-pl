---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 9ed5f25a9297edc5f921305edc009edf5076672b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159747"
---
# <a name="custombinding"></a>\<customBinding>

Zapewnia użytkownikowi pełną kontrolę nad stosem obsługi wiadomości.

\<system.serviceModel>\
\<powiązania > \
\<customBinding>

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

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|closeTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|
|nazwa|Ciąg, który zawiera nazwę konfiguracji powiązania. Ta wartość jest ciągu zdefiniowany przez użytkownika, który działa jako ciąg identyfikacyjny dla niestandardowego powiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|
|openTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|
|receiveTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|
|sendTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<compositeDuplex>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|Określa dwukierunkowej wiadomości do niestandardowego powiązania. Jest używany przy użyciu transportu, które nie zezwalają na komunikację dwukierunkowego natywnie, na przykład HTTP. TCP, z drugiej strony, natywnie umożliwia dwukierunkowe komunikacji i nie wymaga użycia tego elementu powiązania usługi można wysłać wiadomości zwrotnie do klienta.<br /><br /> Klient musi ujawniać adres korespondencyjny upewnić się, skontaktuj się z pomocą i nawiązania połączenia. Ten adres klienta są dostarczane przez `ClientBaseAddress` atrybutu.<br /><br /> Ten element jest typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.|
|[\<pnrpPeerResolver>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|Określa nazwę elementu równorzędnego protokołu Instrumentacji zarządzania Windows (PNRP, Peer Name Resolution Protocol) program rozpoznawania nazw. Ten element jest typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.|
|[\<reliableSession >](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|Określa ustawienie dla WS-Reliable Messaging. Gdy ten element jest dodawany do niestandardowego powiązania, dokładnie obsługuje wynikowy kanału — gdy gwarancje dostarczenia. Ten element jest typu <xref:System.ServiceModel.Configuration.ReliableSessionElement>.|
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Określa opcje zabezpieczeń niestandardowego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.SecurityElement>.|
|[\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|Określa ustawienia zabezpieczeń dla powiązania strumienia SSL. Ten element jest typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.|
|[\<transactionFlow >](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|Określa, że powiązanie obsługuje przepływu transakcji i protokół, który będzie używany przez `transactionProtocol` atrybutu. Ten element jest typu <xref:System.ServiceModel.Configuration.TransactionFlowElement>.|
|[\<windowsStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|Określa opcje do przesyłania strumieniowego zabezpieczeń niestandardowego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|powiązania|Zawiera wszystkie powiązania dla aplikacji Windows Communication Foundation.|

## <a name="remarks"></a>Uwagi

Powiązania niestandardowe zapewniają pełną kontrolę nad stosem obsługi wiadomości usługi WCF. Moje Dodawanie elementów konfiguracji dla konkretnych jednostek można tworzyć specjalne powiązania dostosowanych do potrzeb. Na przykład użytkownik może łączyć `httpsTransport` sekcji `reliableSession` sekcji i `security` sekcję, aby utworzyć niezawodną i bezpieczną protokołu https na podstawie powiązania.

Powiązanie poszczególnych definiuje stosu wiadomości, określając elementów konfiguracji dla elementów stosu w kolejności, w jakiej znajdują się na stosie. Każdy element definiuje i konfiguruje jeden element stosu. W każdym niestandardowego powiązania musi istnieć jeden i tylko jeden element transportu. Bez tego elementu stosem obsługi wiadomości jest niekompletna.

Kolejność wyświetlania elementów w stosie ma znaczenie, ponieważ jest on kolejność, w której operacje są stosowane do wiadomości. Zalecana kolejność elementów stosu jest następująca:

1. Transakcje (opcjonalnie)

2. Niezawodna obsługa komunikatów (opcjonalnie)

3. Zabezpieczenia (opcjonalnie)

4. Transport

5. Koder (opcjonalnie)

Użyj niestandardowego powiązania, gdy jedno z powiązań dostarczanych przez system nie spełnia wymagania dotyczące usługi. Powiązanie niestandardowe może służyć, na przykład, aby umożliwić użycie nowego transportu lub Nowa usługa encoder w punkcie końcowym usługi.

Powiązanie niestandardowe jest konstruowany przy użyciu jednej z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> z kolekcji elementów, które są "skumulowany" w określonej kolejności wiązania:

- U góry to opcjonalna <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> umożliwiająca przepływu transakcji.

- Następnie to opcjonalna <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> zapewniający sesji i kolejność mechanizmu, zgodnie z definicją w specyfikacji WS-ReliableMessaging. Pojęcie to sesji mogą przechodzić pośredników SOAP i mechanizm transportu.

- Następnym ekranem jest elementu powiązania zabezpieczeń opcjonalne, która zapewnia funkcje zabezpieczeń, takich jak autoryzacja, uwierzytelnianie, ochrony i poufności. Następujące elementy powiązania zabezpieczeń są dostarczane przez Windows Communication Foundation (WCF):

    - <xref:System.ServiceModel.Channels.SecurityBindingElement>

    - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

    - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

    - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- Następnie opcjonalne wzorce wiadomości są określone przez powiązanie elementów:

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- Następnie są uaktualnienia opcjonalne transportu/pomocników elementy powiązania:

    - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

    - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

    - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- Następnym ekranem jest element powiązania z kodowania komunikatu wymagane. Możesz użyć własnego transportu lub użyj jednej z następującym komunikatem kodowanie powiązań:

    - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

    - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

    - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- W dolnej części jest element wymagany transportu. Można używać własnego transportu lub użyj jednego z dostarczonych przez Windows Communication Foundation (WCF) elementów powiązania transportu:

    - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

    - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

    - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

    - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

    - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

    - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

    - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

Poniższa tabela podsumowuje opcje dla każdej warstwy.

|Warstwa|Opcje|Wymagane|
|-----------|-------------|--------------|
|Przepływ transakcji|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Nie|
|Niezawodność|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Nie|
|Zabezpieczenia|Symetryczne, asymetryczne i Transport niskiego poziomu|Nie|
|Zmiana kształtu|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|Nie|
|Transport uaktualnień|Strumień protokołu SSL, strumienia Windows elementu równorzędnego programu rozpoznawania nazw|Nie|
|Kodowanie|Tekst, Binary MTOM, niestandardowe|Tak|
|Transport|Odmian HTTP, HTTPS, TCP i nazwane potoki usługi MSMQ, niestandardowe|Tak|

Ponadto można zdefiniować własne elementy powiązania i wstawione między dowolnymi poprzedniej warstwy zdefiniowanej przez użytkownika.

Aby uzyskać informacje dotyczące sposobu używania niestandardowego powiązania, aby zmodyfikować powiązania dostarczane przez system, zobacz [jak: Dostosuj powiązania dostarczane przez System](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [customBinding — Element](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą wiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
