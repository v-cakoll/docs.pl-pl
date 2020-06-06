---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 20ba643fddbac8a488e5457f0195cc253d4d23f7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139313"
---
# \<ws2007FederationHttpBinding>

Bezpieczne i interoperacyjne powiązanie, które wynika z [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) i obsługuje zabezpieczenia federacyjne.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**  
  
## <a name="syntax"></a>Składnia

```xml
<ws2007FederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           privacyNoticeAt="Uri"
           privacyNoticeVersion="Integer"
           proxyAddress="Uri"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007FederationHttpBinding>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`bypassProxyOnLocal`|Wartość wskazująca, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.|
|`closeTimeout`|<xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|
|`hostNameComparisonMode`|Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI. Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode> , który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , co powoduje ignorowanie nazwy hosta w dopasowaniu.|
|`maxBufferPoolSize`|Maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 524 288 bajtów (512 * 1024). Wiele części Windows Communication Foundation (WCF) używa buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne. W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu. W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.|
|`maxReceivedMessageSize`|Maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, które można odbierać w kanale skonfigurowanym za pomocą tego powiązania. Nadawca komunikatu, który przekracza ten limit, odbiera błąd protokołu SOAP. Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|
|`messageEncoding`|Definiuje koder używany do kodowania wiadomości. Prawidłowe wartości to:<br /><br /> -Text: Użyj kodera wiadomości tekstowej.<br />-MTOM: Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.<br /><br /> Wartość domyślna to Text.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding> .|
|`name`|Nazwa konfiguracji powiązania. Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania. Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|
|`openTimeout`|<xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|
|`privacyNoticeAt`|Identyfikator URI, w którym znajduje się powiadomienie dotyczące zachowania poufności informacji.|
|`privacyNoticeVersion`|Wersja bieżącego powiadomienia o ochronie prywatności.|
|`proxyAddress`|Identyfikator URI, który określa adres serwera proxy HTTP. Jeśli `useDefaultWebProxy` jest `true` , to ustawienie musi być `null` . Wartość domyślna to `null`.|
|`receiveTimeout`|Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:10:00.|
|`sendTimeout`|<xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|
|`textEncoding`|Ustawia kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu. Prawidłowe wartości to:<br /><br /> -BigEndianUnicode: kodowanie Unicode big endian.<br />-Unicode: kodowanie 16-bitowe.<br />-UTF8: kodowanie 8-bitowe.<br /><br /> Wartość domyślna to UTF8. Ten atrybut jest typu <xref:System.Text.Encoding> .|
|`transactionFlow`|Wartość określająca, czy powiązanie obsługuje przepływy WS-Transactions. Wartość domyślna to `false`.|
|`useDefaultWebProxy`|Wartość wskazująca, czy jest używany konfigurowany przez system serwer proxy HTTP. Jeśli ten atrybut ma wartość, adres serwera proxy musi mieć `null` wartość (czyli nie jest ustawiony) `true` . Wartość domyślna to `true`.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|Definiuje ustawienia zabezpieczeń wiadomości. Ten element jest typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> .|
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .|
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|Określa, czy niezawodne sesje są nawiązywane między punktami końcowymi kanałów.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<bindings>](bindings.md)|Ten element zawiera kolekcję powiązań standardowych i niestandardowych.|

## <a name="remarks"></a>Uwagi

Federacja jest możliwością udostępniania tożsamości w wielu przedsiębiorstwach lub domenach zaufania na potrzeby uwierzytelniania i autoryzacji. Używa protokołu WS-Trust, aby zamapować reprezentację tożsamości z jednej domeny zaufania na inną. Federacyjne powiązanie HTTP obsługuje zabezpieczenia protokołu SOAP oraz zabezpieczenia w trybie mieszanym, ale nie obsługuje zabezpieczeń transportu. Usługi skonfigurowane przy użyciu tego powiązania muszą korzystać z transportu HTTP. Aby uzyskać więcej informacji, zobacz [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .

## <a name="example"></a>Przykład

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </ws2007FederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [\<wsFederationHttpBinding>](wsfederationhttpbinding.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
