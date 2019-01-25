---
title: '&lt;ws2007FederationHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 7869737f1e3d8c7a9ba569991ead6f7f759e6c58
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616891"
---
# <a name="ltws2007federationhttpbindinggt"></a>&lt;ws2007FederationHttpBinding&gt;
Bezpieczne i interoperacyjne powiązanie pochodzi od klasy [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i obsługuje federacyjnego zabezpieczenia.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<ws2007FederationHttpBinding>  
  
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
|`bypassProxyOnLocal`|Wartość, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.|  
|`closeTimeout`|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`hostnameComparisonMode`|Określa tryb porównywania nazwy hosta HTTP używany do analizowania identyfikatorów URI. Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje hostname dopasowania.|  
|`maxBufferPoolSize`|Maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 524,288 bajtów (512 * 1024). Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów. Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe. Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.|  
|`maxReceivedMessageSize`|Maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, które może zostać odebrany w kanale skonfigurowany tym wiązaniem. Nadawca wiadomości, która przekracza ten limit otrzyma błąd protokołu SOAP. Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|`messageEncoding`|Definiuje encoder umożliwia kodowanie wiadomości. Prawidłowe wartości są następujące:<br /><br /> -Tekst: Za pomocą kodera komunikatów tekstu.<br />-Mtom: Za pomocą kodera komunikatów transmisji organizacji mechanizm 1.0 (MTOM).<br /><br /> Wartość domyślna to Text.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Nazwa konfiguracji powiązania. Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`privactyNoticeAt`|Identyfikator URI, w której znajduje się powiadomienie dotyczące prywatności.|  
|`privactyNoticeVersion`|Wersja bieżąca powiadomienie dotyczące prywatności.|  
|`proxyAddress`|Identyfikator URI, który określa adres serwera proxy HTTP. Jeśli `useDefaultWebProxy` jest `true`, to ustawienie musi być `null`. Wartość domyślna to `null`.|  
|`receiveTimeout`|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|  
|`sendTimeout`|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`textEncoding`|Określa kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków. Prawidłowe wartości są następujące:<br /><br /> -BigEndianUnicode: Big Endian kodowanie Unicode.<br />-Unicode: 16-bitowego kodowania.<br />-   UTF8: 8-bitowego kodowania.<br /><br /> Wartość domyślna to UTF8. Ten atrybut jest typu <xref:System.Text.Encoding>.|  
|`transactionFlow`|Wartość, która określa, czy powiązanie obsługuje płynące WS-transakcji. Wartość domyślna to `false`.|  
|`useDefaultWebProxy`|Wartość, która wskazuje, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie. Adres serwera proxy musi być `null` (czyli nie ustawiono) Jeśli ten atrybut jest `true`. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|Definiuje ustawienia zabezpieczeń dla wiadomości. Ten element jest typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Określa, czy niezawodnej sesji są ustanawiane między punktami końcowymi kanału.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 Federacja znajduje się możliwość udostępniania tożsamości w wielu przedsiębiorstwach lub zaufania domen do uwierzytelniania i autoryzacji. Używa protokołu WS-Trust do mapowania reprezentacji tożsamości z jednej relacji zaufania domeny do innego. Federacyjnego powiązania HTTP obsługuje zabezpieczenia protokołu SOAP, a także trybu mieszanego zabezpieczeń, ale nie obsługuje zabezpieczeń transportu. Skonfigurowano z tym powiązaniem usług, należy użyć protokołu HTTP. Aby uzyskać więcej informacji, zobacz [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
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
- [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
