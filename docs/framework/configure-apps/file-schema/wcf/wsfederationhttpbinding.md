---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 011a46c15785b7ffa832db57925c7e7b5f76c67a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732501"
---
# <a name="wsfederationhttpbinding"></a>\<wsFederationHttpBinding >

Definiuje powiązanie, które obsługuje WS-Federation.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<wsFederationHttpBinding >**  

## <a name="syntax"></a>Składnia

```xml
<wsFederationHttpBinding>
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
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/ Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
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
</wsFederationBinding>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|bypassProxyOnLocal|Wartość logiczna wskazująca, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.|
|closeTimeout|Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|
|hostnameComparisonMode|Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI. Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, co powoduje ignorowanie nazwy hosta w dopasowaniu.|
|maxBufferPoolSize|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 524 288 bajtów (512 * 1024). Wiele części Windows Communication Foundation (WCF) używa buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne. W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu. W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.|
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości (w bajtach), w tym nagłówki, które można odbierać w kanale skonfigurowanym dla tego powiązania. Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP. Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|
|messageEncoding|Definiuje koder używany do kodowania wiadomości. Prawidłowe wartości to:<br /><br /> -Text: Użyj kodera wiadomości tekstowej.<br />-MTOM: Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.<br /><br /> Wartość domyślna to Text.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.|
|nazwa|Ciąg zawierający nazwę konfiguracji powiązania. Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|
|openTimeout|Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji otwierania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|
|privacyNoticeAt|Ciąg określający identyfikator URI, w którym znajduje się powiadomienie o prywatności.|
|privacyNoticeVersion|Liczba całkowita, która określa wersję bieżącego powiadomienia o ochronie prywatności.|
|proxyAddress|Identyfikator URI, który określa adres serwera proxy HTTP. Jeśli `useDefaultWebProxy` jest `true`, to ustawienie musi być `null`. Wartość domyślna to `null`.|
|receiveTimeout|Wartość <xref:System.TimeSpan>, która określa przedział czasu podanego na zakończenie operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|
|Właściwości SendTimeout|Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|
|TextEncoding|Ustawia kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu. Prawidłowe wartości to:<br /><br /> -BigEndianUnicode: kodowanie Unicode BigEndian.<br />-Unicode: kodowanie 16-bitowe.<br />-UTF8: kodowanie 8-bitowe<br /><br /> Wartość domyślna to UTF8. Ten atrybut jest typu <xref:System.Text.Encoding>..|
|transactionFlow|Wartość logiczna określająca, czy powiązanie obsługuje przepływy WS-Transactions. Wartość domyślna to `false`.|
|useDefaultWebProxy|Wartość logiczna wskazująca, czy jest używany konfigurowany przez system serwer proxy HTTP. Jeśli ten atrybut jest `true`, adres serwera proxy musi być `null` (to nie jest ustawione). Wartość domyślna to `true`.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[> zabezpieczeń \<](security-of-wsfederationhttpbinding.md)|Definiuje ustawienia zabezpieczeń wiadomości. Ten element jest typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.|
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|
|[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|Określa, czy niezawodne sesje są nawiązywane między punktami końcowymi kanałów.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[> powiązań\<](bindings.md)|Ten element zawiera kolekcję powiązań standardowych i niestandardowych.|

## <a name="remarks"></a>Uwagi

Federacja jest możliwością udostępniania tożsamości w wielu systemach na potrzeby uwierzytelniania i autoryzacji. Te tożsamości mogą odwoływać się do użytkowników lub do maszyn. Federacyjny protokół HTTP obsługuje zabezpieczenia protokołu SOAP, a także zabezpieczenia w trybie mieszanym, ale nie obsługuje wyłącznie zabezpieczeń transportu. To powiązanie zapewnia obsługę Windows Communication Foundation (WCF) dla protokołu WS-Federation. Usługi skonfigurowane przy użyciu tego powiązania muszą korzystać z transportu HTTP.

Powiązania składają się ze stosu elementów powiązania. Stos elementów powiązania w

`wsFederationHttpBinding` jest taka sama jak zawarte w `wsHttpBinding`

gdy [\<> zabezpieczeń](security-of-wsfederationhttpbinding.md) ma ustawioną wartość domyślną <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.

`wsFederationHttpBinding` kontroluje szczegóły ustawień zabezpieczeń wiadomości w [> komunikat\<](message-element-of-wsfederationhttpbinding.md). Należy zauważyć, że element [\<security >](security-of-wsfederationhttpbinding.md) zapewnia dostęp tylko wtedy, gdy nie można zmienić zabezpieczeń używanych przez powiązanie w momencie utworzenia powiązania.

`wsFederationHttpBinding` udostępnia również atrybut privacyNoticeAt do ustawiania i pobierania identyfikatora URI, w którym znajduje się powiadomienie o prywatności.

Ochrona zasad jest szczególnie ważna w scenariuszach federacyjnych. Zalecenie polega na użyciu jakiejś formy zabezpieczeń, na przykład protokołu HTTPS, w celu ochrony zasad przed złośliwymi użytkownikami.

W scenariuszach federacyjnych przy użyciu tego powiązania zasady usługi mogą mieć ważne informacje, takie jak klucz używany do szyfrowania tokenu wystawionego (SAML), typ oświadczeń do umieszczenia w tokenie i tak dalej. Jeśli te zasady zostaną naruszone, osoba atakująca może odnaleźć klucz wystawionego tokenu prowadzący do dalszej manipulacji, ujawnienia informacji i innych złośliwych zachowań. Aby temu zapobiec, zasady muszą być pobierane bezpiecznie (na przykład przy użyciu protokołu HTTPS) z usługi.

Aby uzyskać więcej informacji na temat tego powiązania, zobacz [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).

## <a name="example"></a>Przykład

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsFederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="saml"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </wsFederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [Instrukcje: tworzenie elementu WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [> powiązań \<](bindings.md)
