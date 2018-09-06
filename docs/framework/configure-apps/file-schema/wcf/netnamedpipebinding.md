---
title: '&lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: f3b6771d5a1a07a35bdf3f0ffa92c837aa202e4d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785316"
---
# <a name="ltnetnamedpipebindinggt"></a>&lt;netNamedPipeBinding&gt;
Definiuje powiązanie, które jest bezpieczne i niezawodne, zoptymalizowane pod kątem na maszynie komunikacji pomiędzy procesami. Domyślnie generuje ona stosu środowiska uruchomieniowego komunikacji przy użyciu WS-ReliableMessaging niezawodność i zabezpieczenia transportu dla bezpieczeństwa transferu nazwane potoki dostarczania wiadomości i kodowania komunikatu binarnego.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netNamedPipeBinding>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netNamedPipeBinding>  
   <binding   
      closeTimeout="TimeSpan"  
      hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
      maxBufferPoolSize="Integer"  
      maxBufferSize="Integer"  
      maxConnections="Integer"   
      maxReceivedMessageSize="Integer"  
            name="string"  
      openTimeout="TimeSpan"   
      receiveTimeout="TimeSpan"  
      sendTimeout="TimeSpan"  
      transactionFlow="Boolean"  
      transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"  
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
      <security mode="None/Transport">  
            <transport  protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|hostnameComparisonMode|Określa tryb porównywania nazwy hosta HTTP używany do analizowania identyfikatorów URI. Ten atrybut jest typu `System.ServiceModel.HostnameComparisonMode`, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to `StrongWildcard`, który ignoruje hostname dopasowania.|  
|maxBufferPoolSize|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 524,288 bajtów (512 * 1024). Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów. Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe. Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.|  
|wartość maxBufferSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar w bajtach buforu używany do przechowywania komunikatów w pamięci. Jeśli bufor jest pełna, nadmiar danych pozostaje w podstawowej gniazda, aż buforu, będzie miał miejsce ponownie. Ta wartość nie może być mniejsza niż `maxReceivedMessageSize` atrybutu. Wartość domyślna to 65536. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|MaxConnections|Liczba całkowita określająca maksymalną liczbę połączeń wychodzące i przychodzące usługa tworzenia/akceptuje. Połączenia przychodzące i wychodzące są przeliczane względem oddzielne limit określony przez atrybut.<br /><br /> Połączenia przychodzące poza limitem zostaną umieszczone w kolejce, dopóki miejsce poniżej limitu staje się dostępna.<br /><br /> Połączenia wychodzące poza limitem zostaną umieszczone w kolejce, dopóki miejsce poniżej limitu staje się dostępna.<br /><br /> Wartość domyślna wynosi 10.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, które może zostać odebrany w kanale skonfigurowany tym wiązaniem. Nadawca wiadomości przekroczenie tego limitu zostanie wyświetlony błąd protokołu SOAP. Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|nazwa|Ciąg, który zawiera nazwę konfiguracji powiązania. Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|receiveTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|  
|sendTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|transactionFlow|Wartość logiczna określająca, czy powiązanie obsługuje płynące WS-transakcji. Wartość domyślna to `false`.|  
|Element transactionProtocol|Określa protokół transakcji do użycia z tym powiązaniem. Prawidłowe wartości to:<br /><br /> -OleTransactions<br />WS-AtomicTransactionOctober2004<br /><br /> Wartość domyślna to OleTransactions. Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol>.|  
|Tryb transferu|A <xref:System.ServiceModel.TransferMode> wartość określającą, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|Definiuje ustawienia zabezpieczeń dla wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 `NetNamedPipeBinding` Generuje stosu komunikację w czasie wykonywania, domyślna, która używa zabezpieczenia transportu, nazwanych potoków do dostarczania wiadomości i kodowania komunikatu binarnego. To powiązanie jest właściwe Windows Communication Foundation (WCF) dostarczane przez system wyborem dla komunikacji na maszynie. Obsługuje ona również transakcji.  
  
 W domyślnej konfiguracji `NetNamedPipeBinding` jest podobna do konfiguracji, jaką zapewnia `NetTcpBinding`, ale jest prostsze, ponieważ implementacja WCF jest przeznaczone wyłącznie do użytku na komputerze i w związku z tym są mniej funkcji narażonych. Najbardziej znacząca różnica jest to, że `securityMode` ustawienie tylko oferty `None` i `Transport` opcje. Obsługa zabezpieczeń protokołu SOAP nie jest uwzględniona opcja. Zachowania zabezpieczeń jest można skonfigurować za pomocą opcjonalnego `securityMode` atrybutu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano powiązaniu netNamedPipeBinding zapewnia komunikację między procesami na tym samym komputerze. Nazwane potoki nie działają na komputerach.  
  
 Powiązanie jest określona w plikach konfiguracji klienta i usługi. Typ powiązania jest określona w `binding` atrybutu `<endpoint>` elementu. Jeśli chcesz skonfigurować powiązanie netNamedPipeBinding i zmienić niektóre z jego ustawienia, należy zdefiniować konfigurację powiązania. Punkt końcowy musi odwoływać się Konfiguracja powiązania według nazw z `bindingConfiguration` atrybutu. W tym przykładzie konfiguracja powiązania nosi nazwę Binding1.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->  
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
                  binding="netNamedPipeBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
      <netNamedPipeBinding>  
        <binding   
                 closeTimeout="00:01:00"  
                 openTimeout="00:01:00"   
                 receiveTimeout="00:10:00"   
                 sendTimeout="00:01:00"  
                 transactionFlow="false"   
                 transferMode="Buffered"   
                 transactionProtocol="OleTransactions"  
                 hostNameComparisonMode="StrongWildcard"   
                 maxBufferPoolSize="524288"  
                 maxBufferSize="65536"   
                 maxConnections="10"   
                 maxReceivedMessageSize="65536">  
          <security mode="Transport">  
            <transport protectionLevel="EncryptAndSign" />  
          </security>  
        </binding>  
      </netNamedPipeBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>  
 <xref:System.ServiceModel.NetNamedPipeBinding>  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)
