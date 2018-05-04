---
title: '&lt;netHttpsBinding&gt;'
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: fb279321cccc325700ac18697d484da20c685c9d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltnethttpsbindinggt"></a>&lt;netHttpsBinding&gt;
Reprezentuje powiązanie, które usługi Windows Communication Foundation (WCF) można użyć do konfiguracji i ekspozycji punktów końcowych, które mogą się komunikować za pośrednictwem protokołu HTTPS. W przypadku użycia z kontrakt dupleksowy, gniazda sieci Web, który będzie używany, w przeciwnym razie będzie używany protokół HTTPS.  
  
 Element główny  
Następny Element  
  
## <a name="syntax"></a>Składnia  

```xml
<netHttpsBinding>  
  <binding allowCookies="Boolean"  
           bypassProxyOnLocal="Boolean"  
           closeTimeout="TimeSpan"   
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
           maxBufferPoolSize="Integer"  
           maxBufferSize="Integer"  
           maxReceivedMessageSize="Integer"  
           messageEncoding="Binary/Text/Mtom"  
           name="string"   
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
                 realm="string" />  
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" 
               clientCredentialType="UserName/Certificate"/>  
    </security>  
    <readerQuotas maxArrayLength="Integer" 
                  maxBytesPerRead="Integer" 
                  maxDepth="Integer" 
                  maxNameTableCharCount="Integer" 
                  maxStringContentLength="Integer" />  
  </binding>  
</netHttpsBinding>  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`allowCookies`|Wartość logiczna wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań. Wartość domyślna to `false`.<br /><br /> Tej właściwości można użyć w przypadku interakcji z usługami sieci Web ASMX, które używają plików cookie. W ten sposób można się upewnić, że pliki cookie zwrócony z serwera, automatycznie są kopiowane do wszystkich przyszłych żądań dla tej usługi.|  
|`bypassProxyOnLocal`|Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.<br /><br /> Zasobu internetowego jest lokalny, jeśli ma ona adresu lokalnego. Lokalny adres jest taki, który znajduje się na tym samym komputerze, lokalnej sieci LAN lub intranet i jest identyfikowany, składniowo, brak kropki (.) jak identyfikatory URI "http://webserver/"i"http://localhost/".<br /><br /> Ustawienie ten atrybut określa, czy punkty końcowe skonfigurowane z BasicHttpBinding Użyj serwera proxy podczas uzyskiwania dostępu do zasobów lokalnych. Jeśli ten atrybut jest `true`, żądań lokalnych zasobów w Internecie, nie należy używać serwera proxy. Użyj hosta nazw (zamiast localhost), jeśli klienci mają przechodzić przez serwer proxy po rozmowie z usługi na tym samym komputerze, gdy ten atrybut ma ustawioną `true`.<br /><br /> Jeśli ten atrybut jest `false`, wszystkie żądania internetowe są nawiązywane przy użyciu serwera proxy.|  
|`closeTimeout`|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`hostnameComparisonMode`|Określa tryb porównania nazw hostów HTTP używany do przeprowadzenia analizy identyfikatorów URI. Ten atrybut jest typu `HostnameComparisonMode`, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to `StrongWildcard`, który ignoruje nazwy hosta w dopasowania.|  
|`maxBufferPoolSize`|Wartość całkowita określająca maksymalną ilość pamięci przydzielonej do użycia przez menedżera buforów komunikatów, który odbiera komunikaty z kanału. Wartość domyślna to 524288 (0x80000) bajtów.<br /><br /> Menedżera buforów minimalizację kosztów bufory przy użyciu puli bufora. Bufory są wymagane do przetwarzania komunikatów przez usługę, po znalezieniu poza kanału. Jeśli w puli buforów do przetworzenia obciążenia komunikat nie ma wystarczającej ilości pamięci, menedżera buforów musi przydzielić dodatkową pamięć sterty CLR, co zwiększa obciążenie kolekcji pamięci. Rozbudowana alokacji sterty pamięci CLR jest wskazanie, że rozmiar puli buforów jest za mały, i że można poprawić wydajność z alokacją większych przez odpowiednie zwiększenie limitu określonego przez tego atrybutu.|  
|`maxBufferSize`|Wartość całkowita określająca maksymalny rozmiar w bajtach buforu, który przechowuje komunikaty podczas przetwarzania dla punkt końcowy skonfigurowany dla tego wiązania. Wartość domyślna to 65 536 bajtów.|  
|`maxReceivedMessageSize`|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami komunikatu, który może zostać odebrany w kanale skonfigurowane dla tego wiązania. Nadawca otrzymuje błędu protokołu SOAP, jeśli komunikat jest zbyt duży dla odbiornika. Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65 536 bajtów.|  
|`messageEncoding`|Definiuje koder używany do kodowania komunikatu protokołu SOAP. Prawidłowe wartości są następujące:<br /><br /> -Tekst: Użyj kodera wiadomości tekstowych.<br />-Mtom: Za pomocą kodera wiadomości transmisji organizacji mechanizmu 1.0 (MTOM).<br /><br /> Wartość domyślna to tekst. Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Ciąg zawierający nazwę konfiguracji powiązania. Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania. Każdego powiązania ma `name` i `namespace` atrybutu niesekwencyjnego razem jednoznacznie zidentyfikować je w metadanych usługi. Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`namespace`|Określa przestrzeń nazw XML powiązania. Wartość domyślna to "http://tempuri.org/Bindings". Każdego powiązania ma `name` i `namespace` atrybutu niesekwencyjnego razem jednoznacznie zidentyfikować je w metadanych usługi.|  
|`openTimeout`|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`proxyAddress`|Identyfikator URI zawierający adres serwera proxy HTTP. Jeśli `useSystemWebProxy` ustawiono `true`, to ustawienie musi być `null`. Wartość domyślna to `null`.|  
|`receiveTimeout`|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|  
|`sendTimeout`|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`textEncoding`|Ustawia kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków. Prawidłowe wartości są następujące:<br /><br /> -BigEndianUnicode: Unicode BigEndian kodowanie.<br />-Unicode: 16-bitowego kodowania.<br />-UTF8: 8-bitowego kodowania o<br /><br /> Wartość domyślna to UTF8. Ten atrybut jest typu <xref:System.Text.Encoding>.|  
|`transferMode`|Prawidłowy <xref:System.ServiceModel.TransferMode> wartość określająca, czy komunikaty są buforowane, czy strumieniowego na żądanie lub odpowiedź.|  
|`useDefaultWebProxy`|Wartość logiczna określająca, czy ma być używane automatycznie skonfigurowany serwer proxy HTTP systemu, jeśli jest dostępna. Wartość domyślna to `true`.|  
|||  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>. |  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 NetHttpsBinding używa protokołu HTTPS jako transportu do wysyłania wiadomości. W przypadku użycia z kontrakt dupleksowy, będą używane gniazda sieci Web.  W przypadku korzystania z kontraktem "żądanie-odpowiedź", który NetHttpsBinding będą zachowywać się jak BasicHttpsBinding z kodera binarnego.  
  
 Zabezpieczenia jest domyślnie wyłączona, ale można dodać ustawienie atrybutu tryb [ \<zabezpieczeń >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) element podrzędny, wartość inną niż `None`. Używa tekst kodowania i UTF-8 komunikatu "Text" kodowaniu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie <xref:System.ServiceModel.NetHttpBinding> zapewnia współdziałanie komunikacji i maksymalnie HTTPS z pierwszej - i second - generation usług sieci Web. Powiązanie jest określona w plikach konfiguracji dla klienta i usługi. Typ powiązania jest określona za pomocą `binding` atrybutu `<endpoint>` elementu. Jeśli chcesz skonfigurować podstawowe powiązanie i zmieniania jego ustawień należy zdefiniować konfiguracji powiązania. Punkt końcowy musi odwoływać się Konfiguracja powiązania o nazwie przy użyciu `bindingConfiguration` atrybutu `<endpoint>` element, jak pokazano w poniższym kodzie konfiguracji dla usługi.  
  
```xml  
<system.serviceModel>   
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="netHttpsBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
    <netHttpsBinding>  
      <binding name="Binding1"   
               hostNameComparisonMode="StrongWildcard" 
               receiveTimeout="00:10:00" 
               sendTimeout="00:10:00" 
               openTimeout="00:10:00" 
               closeTimeout="00:10:00" 
               maxReceivedMessageSize="65536" 
               maxBufferSize="65536" 
               maxBufferPoolSize="524288" 
               transferMode="Buffered" 
               messageEncoding="Binary" 
               textEncoding="utf-8" 
               bypassProxyOnLocal="false" 
               useDefaultWebProxy="true">  
        <security mode="None" />  
      </binding>  
    </netHttpsBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a>Przykład  
 Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Funkcje z poprzednim przykładzie można osiągnąć przez usunięcie bindingConfiguration z adres punktu końcowego i frm nazwę powiązania.  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpsBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpsBinding>  
        <binding   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Binary"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </netHttpsBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
