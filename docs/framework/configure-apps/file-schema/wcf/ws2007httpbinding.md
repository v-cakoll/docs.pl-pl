---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 2fb9f7a16a360ddd61e6f8b935f928ddfdeb6cc3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915255"
---
# <a name="ws2007httpbinding"></a>\<ws2007HttpBinding>
Definiuje powiązanie interoperacyjne, które zapewnia obsługę prawidłowych wersji <xref:System.ServiceModel.WSHttpBinding.Security%2A>elementów, <xref:System.ServiceModel.ReliableSession>i <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> .  
  
 \<system.serviceModel>  
\<> powiązań  
\<ws2007HttpBinding>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<ws2007HttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
        <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"
                 negotiateServiceCredential="Boolean"
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
                 establishSecurityContext="Boolean"
                 negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`allowCookies`|Wartość wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań. Wartość domyślna to `false`.<br /><br /> Tej właściwości można użyć podczas korzystania z usług sieci Web ASP.NET (ASMX), które używają plików cookie. Dzięki temu pliki cookie zwracane przez serwer są automatycznie kopiowane do wszystkich przyszłych żądań klientów dla tej usługi.|  
|`bypassProxyOnLocal`|Wartość wskazująca, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.|  
|`closeTimeout`|<xref:System.TimeSpan> Wartość, która określa przedział czasu na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`hostNameComparisonMode`|Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI (Uniform Resource Identifier). Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, co powoduje ignorowanie nazwy hosta w dopasowaniu.|  
|`maxBufferPoolSize`|Maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 524 288 bajtów (512 × 1 024). Wiele części Windows Communication Foundation (WCF) używa buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne, ponieważ wyrzucanie elementów bezużytecznych dla buforów. W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu. Pozwala to uniknąć nakładu pracy podczas tworzenia i niszczenia buforów.|  
|`maxReceivedMessageSize`|Może zostać wyświetlony maksymalny rozmiar komunikatu (w bajtach), łącznie z nagłówkami, które zostały skonfigurowane przy użyciu tego powiązania. Nadawca komunikatu przekraczającego ten limit odbiera błąd protokołu SOAP. Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|`messageEncoding`|Definiuje koder używany do kodowania wiadomości. Prawidłowe wartości to:<br /><br /> -   `Text`: Użyj kodera wiadomości tekstowych.<br />-   `Mtom`: Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.<br /><br /> Wartość domyślna to `Text`.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Nazwa konfiguracji powiązania. Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|<xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`proxyAddress`|Identyfikator URI, który określa adres serwera proxy HTTP. Jeśli `useSystemWebProxy` `null`jest `true`, to ustawienie musi być. Wartość domyślna to `null`.|  
|`receiveTimeout`|<xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`sendTimeout`|<xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`textEncoding`|Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu. Prawidłowe wartości to:<br /><br /> -   `UnicodeFffeTextEncoding`: Kodowanie Unicode big endian.<br />-   `Utf16TextEncoding`: kodowanie 16-bitowe.<br />-   `Utf8TextEncoding`: kodowanie 8-bitowe.<br /><br /> Wartość domyślna to `Utf8TextEncoding`.<br /><br /> Ten atrybut jest typu <xref:System.Text.Encoding>.|  
|`transactionFlow`|Wartość określająca, czy powiązanie obsługuje przepływy WS-Transactions. Wartość domyślna to `false`.|  
|`useDefaultWebProxy`|Wartość określająca, czy jest używany konfigurowany przez system serwer proxy HTTP. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> zabezpieczeń](security-of-wshttpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które można przetwarzać za pomocą punktów końcowych skonfigurowanych dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|Określa, czy niezawodne sesje są nawiązywane między punktami końcowymi kanałów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> powiązań](bindings.md)|Ten element zawiera kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 Dodaje do programu powiązanie dostarczone z systemem, które `WSHttpBinding` jest podobne do programu, ale używa organizacji do rozwoju standardowych wersji standardu języka Oasis (Structured Information Standards) ReliableSession, Security i TransactionFlow Protocols. `WS2007HttpBinding` W przypadku korzystania z tego powiązania nie są wymagane żadne zmiany w modelu obiektu ani w ustawieniach domyślnych.  
  
## <a name="example"></a>Przykład  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007HttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </ws2007HttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> powiązania](../../../misc/binding.md)
