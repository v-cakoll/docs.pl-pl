---
title: <basicHttpContextBinding>
ms.date: 03/30/2017
ms.assetid: 39b16b82-4ec6-4eff-8031-67e026870961
ms.openlocfilehash: 05c863cf7649546745db270a4b3ac0c638083a85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919862"
---
# <a name="basichttpcontextbinding"></a>\<basicHttpContextBinding>
Określanie powiązania, które dostarcza kontekst <xref:System.ServiceModel.BasicHttpBinding> do wymiany przez włączenie plików cookie protokołu HTTP jako mechanizm wymiany.  
  
 \<system.ServiceModel>  
\<> powiązań  
\<basicHttpContextBinding>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<basicHttpContextBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           envelopeVersion="None/Soap11/Soap12"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="String"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="String" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpContextBinding>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`allowCookies`|Wartość logiczna wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań. Wartość domyślna to `false`.<br /><br /> Tej właściwości można użyć podczas współpracy z usługami sieci Web ASMX, które korzystają z plików cookie. W ten sposób można mieć pewność, że pliki cookie zwrócone z serwera są automatycznie kopiowane do wszystkich przyszłych żądań klientów dla tej usługi.|  
|`bypassProxyOnLocal`|Wartość logiczna wskazująca, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.<br /><br /> Zasób internetowy jest lokalny, jeśli ma adres lokalny. Lokalny adres jest taki, który znajduje się na tym samym komputerze, lokalnej sieci LAN lub intranet i jest identyfikowany, składniowo, brak kropki (.) jak identyfikatory URI "http://webserver/" i "http://localhost/".<br /><br /> Ustawienie tego atrybutu określa, czy punkty końcowe skonfigurowane za pomocą BasicHttpBinding używają serwera proxy podczas uzyskiwania dostępu do zasobów lokalnych. Jeśli ten atrybut jest `true`, żądania do lokalnych zasobów internetowych nie korzystają z serwera proxy. Jeśli klient ma przechodzić przez serwer proxy podczas rozmowy z usługami na tym samym komputerze, gdy ten atrybut jest ustawiony na `true`, należy użyć nazwy hosta (zamiast hosta lokalnego).<br /><br /> Gdy ten atrybut ma `false`wartość, wszystkie żądania internetowe są nawiązywane za pomocą serwera proxy.|  
|`closeTimeout`|<xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`envelopeVersion`|Określa wersję protokołu SOAP używaną dla komunikatów przetwarzanych przez to powiązanie. Jedyną prawidłową wartością jest Soap11.|  
|`hostNameComparisonMode`|Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI. Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, co powoduje ignorowanie nazwy hosta w dopasowaniu.|  
|`maxBufferPoolSize`|Wartość całkowita określająca maksymalną ilość pamięci przydzieloną do użytku przez Menedżera buforów komunikatów, które odbierają komunikaty z kanału. Wartość domyślna to 524288 (0x80000) b.<br /><br /> Menedżer buforów minimalizuje koszt używania buforów przy użyciu puli buforów. Bufory są wymagane do przetwarzania komunikatów przez usługę, gdy wychodzą z kanału. Jeśli w puli buforów nie ma wystarczającej ilości pamięci do przetworzenia ładowania komunikatów, Menedżer buforów musi przydzielić dodatkową pamięć ze sterty CLR, co spowoduje zwiększenie nakładu wyrzucania elementów bezużytecznych. Rozbudowana alokacja ze sterty elementów bezużytecznych CLR wskazuje, że rozmiar puli buforów jest zbyt mały i można zwiększyć wydajność z większą alokacją przez zwiększenie limitu określonego przez ten atrybut.|  
|`maxBufferSize`|Wartość całkowita, która określa maksymalny rozmiar bufora, w bajtach, który przechowuje komunikaty podczas przetwarzania dla punktu końcowego skonfigurowanego za pomocą tego powiązania. Wartość domyślna to 65 536 bajtów.|  
|`maxReceivedMessageSize`|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości w bajtach, w tym nagłówki, dla wiadomości, które można odbierać w kanale skonfigurowanym za pomocą tego powiązania. Nadawca odbiera błąd protokołu SOAP, jeśli komunikat jest zbyt duży dla odbiornika. Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65 536 bajtów.|  
|`messageEncoding`|Definiuje koder używany do kodowania komunikatu protokołu SOAP. Prawidłowe wartości to:<br /><br /> Opis Użyj kodera wiadomości tekstowych.<br />MTOM Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.<br /><br /> Wartość domyślna to Text. Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|`messageVersion`|Określa wersję wiadomości używaną przez klientów i usługi skonfigurowane przy użyciu powiązania. Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.|  
|`name`|Ciąg zawierający nazwę konfiguracji powiązania. Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania. Każde powiązanie ma `name` atrybut i `namespace` , który jednoznacznie identyfikuje go w metadanych usługi. Ponadto ta nazwa jest unikatowa wśród powiązań tego samego typu. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`namespace`|Określa przestrzeń nazw XML powiązania. Wartość domyślna to "http://tempuri.org/Bindings". Każde powiązanie ma `name` atrybut i `namespace` , który jednoznacznie identyfikuje go w metadanych usługi.|  
|`openTimeout`|<xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`proxyAddress`|Identyfikator URI, który zawiera adres serwera proxy HTTP. Jeśli `useSystemWebProxy` jest ustawiona na `true`, to ustawienie musi być `null`. Wartość domyślna to `null`.|  
|`receiveTimeout`|<xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|  
|`sendTimeout`|<xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`textEncoding`|Ustawia kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu. Prawidłowe wartości to:<br /><br /> - BigEndianUnicode: Kodowanie Unicode BigEndian.<br />Unicode kodowanie 16-bitowe.<br />-   UTF8: kodowanie 8-bitowe<br /><br /> Wartość domyślna to UTF8. Ten atrybut jest typu <xref:System.Text.Encoding>.|  
|`transferMode`|Prawidłowa <xref:System.ServiceModel.TransferMode> wartość określająca, czy komunikaty są buforowane, czy przesyłane strumieniowo na żądanie lub odpowiedź.|  
|`useDefaultWebProxy`|Wartość logiczna określająca, czy ma być używany autokonfigurowany serwer proxy HTTP systemu, jeśli jest dostępny. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> zabezpieczeń](security-of-basichttpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> powiązań](bindings.md)|Ten element zawiera kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element powiązania zapewnia poziom ochrony i mechanizm wymiany w ramach kontekstu dla `BasicHttpBinding`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.BasicHttpContextBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpContextBindingElement>
- <xref:System.ServiceModel.Channels.ContextBindingElement>
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> powiązania](../../../misc/binding.md)
- [\<basicHttpBinding >](basichttpbinding.md)
