---
title: '&lt;basicHttpContextBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 39b16b82-4ec6-4eff-8031-67e026870961
ms.openlocfilehash: fb6388244ea0bfb583c9a0d3ee5a4843727e45a0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltbasichttpcontextbindinggt"></a>&lt;basicHttpContextBinding&gt;
Określanie powiązania, które dostarcza kontekst dla <xref:System.ServiceModel.BasicHttpBinding> Aby wymienić przez włączenie plików cookie protokołu HTTP jako mechanizm wymiany.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<basicHttpContextBinding>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<basicHttpContextBinding>  
   <binding   
       allowCookies="Boolean"  
       bypassProxyOnLocal="Boolean"  
       closeTimeout="TimeSpan"   
       envelopeVersion="None/Soap11/Soap12"  
       hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"  
       maxReceivedMessageSize="Integer"  
       messageEncoding="Text/Mtom"  
       name="string"   
       openTimeout="TimeSpan"   
       proxyAddress="URI"  
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
       textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
       transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
       useDefaultWebProxy="Boolean"  
       <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
           <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                  proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                                    realm="string" />  
           <message  algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"  
                                    clientCredentialType="UserName/Certificate"/>  
       </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</basicHttpContextBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`allowCookies`|Wartość logiczna wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań. Wartość domyślna to `false`.<br /><br /> Tej właściwości można użyć w przypadku interakcji z usługami sieci Web ASMX, które używają plików cookie. W ten sposób można się upewnić, że pliki cookie zwrócony z serwera, automatycznie są kopiowane do wszystkich przyszłych żądań dla tej usługi.|  
|`bypassProxyOnLocal`|Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.<br /><br /> Zasobu internetowego jest lokalny, jeśli ma ona adresu lokalnego. Lokalny adres jest taki, który znajduje się na tym samym komputerze, lokalnej sieci LAN lub intranet i jest identyfikowany, składniowo, brak kropki (.) jak identyfikatory URI "http://webserver/"i"http://localhost/".<br /><br /> Ustawienie ten atrybut określa, czy punkty końcowe skonfigurowane z BasicHttpBinding Użyj serwera proxy podczas uzyskiwania dostępu do zasobów lokalnych. Jeśli ten atrybut jest `true`, żądań lokalnych zasobów w Internecie, nie należy używać serwera proxy. Użyj hosta nazw (zamiast localhost), jeśli klienci mają przechodzić przez serwer proxy po rozmowie z usługi na tym samym komputerze, gdy ten atrybut ma ustawioną `true`.<br /><br /> Jeśli ten atrybut jest `false`, wszystkie żądania internetowe są nawiązywane przy użyciu serwera proxy.|  
|`closeTimeout`|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`envelopeVersion`|Określa wersję SOAP używaną dla komunikatów przetwarzanych przez to powiązanie. Jedyne prawidłowe wartości to Soap11.|  
|`hostnameComparisonMode`|Określa tryb porównania nazw hostów HTTP używany do przeprowadzenia analizy identyfikatorów URI. Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje nazwy hosta w dopasowania.|  
|`maxBufferPoolSize`|Wartość całkowita określająca maksymalną ilość pamięci przydzielonej do użycia przez menedżera buforów komunikatów, który odbiera komunikaty z kanału. Wartość domyślna to 524288 (0x80000) bajtów.<br /><br /> Menedżera buforów minimalizację kosztów bufory przy użyciu puli bufora. Bufory są wymagane do przetwarzania komunikatów przez usługę, po znalezieniu poza kanału. Jeśli w puli buforów do przetworzenia obciążenia komunikat nie ma wystarczającej ilości pamięci, menedżera buforów musi przydzielić dodatkową pamięć sterty CLR, co zwiększa obciążenie kolekcji pamięci. Rozbudowana alokacji sterty pamięci CLR jest wskazanie, że rozmiar puli buforów jest za mały, i że można poprawić wydajność z alokacją większych przez odpowiednie zwiększenie limitu określonego przez tego atrybutu.|  
|`maxBufferSize`|Wartość całkowita określająca maksymalny rozmiar w bajtach buforu, który przechowuje komunikaty podczas przetwarzania dla punkt końcowy skonfigurowany dla tego wiązania. Wartość domyślna to 65 536 bajtów.|  
|`maxReceivedMessageSize`|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami komunikatu, który może zostać odebrany w kanale skonfigurowane dla tego wiązania. Nadawca otrzymuje błędu protokołu SOAP, jeśli komunikat jest zbyt duży dla odbiornika. Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65 536 bajtów.|  
|`messageEncoding`|Definiuje koder używany do kodowania komunikatu protokołu SOAP. Prawidłowe wartości są następujące:<br /><br /> -Tekst: Użyj kodera wiadomości tekstowych.<br />-Mtom: Za pomocą kodera wiadomości transmisji organizacji mechanizmu 1.0 (MTOM).<br /><br /> Wartość domyślna to tekst. Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|`messageVersion`|Określa wersję komunikatu używany przez klientów i usług skonfigurowany dla powiązania. Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.|  
|`name`|Ciąg zawierający nazwę konfiguracji powiązania. Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania. Każdego powiązania ma `name` i `namespace` atrybutu niesekwencyjnego razem jednoznacznie zidentyfikować je w metadanych usługi. Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`namespace`|Określa przestrzeń nazw XML powiązania. Wartość domyślna to "http://tempuri.org/Bindings". Każdego powiązania ma `name` i `namespace` atrybutu niesekwencyjnego razem jednoznacznie zidentyfikować je w metadanych usługi.|  
|`openTimeout`|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`proxyAddress`|Identyfikator URI zawierający adres serwera proxy HTTP. Jeśli `useSystemWebProxy` ustawiono `true`, to ustawienie musi być `null`. Wartość domyślna to `null`.|  
|`receiveTimeout`|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|  
|`sendTimeout`|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`textEncoding`|Ustawia kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków. Prawidłowe wartości są następujące:<br /><br /> -BigEndianUnicode: Unicode BigEndian kodowanie.<br />-Unicode: 16-bitowego kodowania.<br />-UTF8: 8-bitowego kodowania o<br /><br /> Wartość domyślna to UTF8. Ten atrybut jest typu <xref:System.Text.Encoding>.|  
|`transferMode`|Prawidłowy <xref:System.ServiceModel.TransferMode> wartość określająca, czy komunikaty są buforowane, czy strumieniowego na żądanie lub odpowiedź.|  
|`useDefaultWebProxy`|Wartość logiczna określająca, czy ma być używane automatycznie skonfigurowany serwer proxy HTTP systemu, jeśli jest dostępna. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element powiązania zapewnia poziom ochrony i mechanizm wymiany w ramach kontekstu `BasicHttpBinding`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.BasicHttpContextBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpContextBindingElement>  
 <xref:System.ServiceModel.Channels.ContextBindingElement>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)  
 [\<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
