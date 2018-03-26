---
title: '&lt;netNamedPipeBinding&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd11c1381de3d2c965e884ee2d43b8a0c08063bb
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="ltnetnamedpipebindinggt"></a>&lt;netNamedPipeBinding&gt;
Definiuje powiązanie, które jest bezpieczne, niezawodne, zoptymalizowane pod kątem na komputerze komunikacji pomiędzy procesami. Domyślnie generuje środowiska uruchomieniowego stosu komunikacji z WS-ReliableMessaging niezawodności, zabezpieczeń transportu dla bezpieczeństwa transfer nazwanych potoków do dostarczanie komunikatów, a Kodowanie komunikatu binarnego.  
  
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
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|hostnameComparisonMode|Określa tryb porównania nazw hostów HTTP używany do przeprowadzenia analizy identyfikatorów URI. Ten atrybut jest typu `System.ServiceModel.HostnameComparisonMode`, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to `StrongWildcard`, który ignoruje nazwy hosta w dopasowania.|  
|maxBufferPoolSize|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 524,288 bajtów (512 * 1024). Bufory za pomocą wielu części programu Windows Communication Foundation (WCF). Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne i odzyskiwanie pamięci dla buforów również jest kosztowna. Używając puli buforów można podjąć buforu z puli, ten jest używany i zwracać do puli, gdy wszystko będzie gotowe. W związku z tym jest unikać obciążenie związane z tworzeniem i niszczenie buforów.|  
|wartość maxBufferSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar w bajtach buforu używany do przechowywania wiadomości w pamięci. Jeśli bufor jest pełna, nadmiarowych danych pozostaje w podstawowej gniazda do momentu buforu ma miejsce ponownie. Ta wartość nie może być mniejsza niż `maxReceivedMessageSize` atrybutu. Wartość domyślna to 65536. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|maxConnections|Liczba całkowita określająca maksymalną liczbę połączeń wychodzące i przychodzące usługi Utwórz/akceptuje. Połączenia przychodzące i wychodzące są uwzględniane w oddzielnych określonym przez atrybut.<br /><br /> Połączenia przychodzące poza limitem są umieszczane w kolejce, dopóki nie będzie dostępne miejsce poniżej limitu.<br /><br /> Połączenia wychodzące poza limitem są umieszczane w kolejce, dopóki nie będzie dostępne miejsce poniżej limitu.<br /><br /> Wartość domyślna to 10.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, odebranych z kanału skonfigurowane dla tego wiązania. Nadawcy wiadomości przekracza ten limit, zostanie wyświetlony błąd protokołu SOAP. Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|nazwa|Ciąg zawierający nazwę konfiguracji powiązania. Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|receiveTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|  
|sendTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|transactionFlow|Wartość logiczna określająca, czy wiązanie obsługuje przechodzenia WS-transakcji. Wartość domyślna to `false`.|  
|Element TransactionProtocol|Określa protokół transakcji do użycia z tym powiązaniem. Prawidłowe wartości to<br /><br /> -OleTransactions<br />WS-AtomicTransactionOctober2004<br /><br /> Wartość domyślna to OleTransactions. Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol>.|  
|Tryb transferu|A <xref:System.ServiceModel.TransferMode> wartość określająca, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 `NetNamedPipeBinding` Generuje stosu komunikacji środowiska wykonawczego domyślnie korzysta z zabezpieczeń transportu, nazwanych potoków do dostarczanie komunikatów, a Kodowanie komunikatu binarnego. To powiązanie jest właściwy Windows Communication Foundation (WCF) dostarczane przez system wybór komunikacji na komputerze. Obsługuje ona również transakcji.  
  
 Konfigurację domyślną dla `NetNamedPipeBinding` jest podobna do konfiguracji udostępniane przez `NetTcpBinding`, ale jest łatwiejsze, ponieważ implementacja WCF jest przeznaczone tylko do użytku na komputerze i w związku z tym są mniej funkcji uwidocznione. Najbardziej znacząca różnica jest to, że `securityMode` ustawienie tylko oferty `None` i `Transport` opcje. Obsługi zabezpieczeń protokołu SOAP nie jest dołączony. Zachowania zabezpieczeń jest można skonfigurować za pomocą opcjonalnego `securityMode` atrybutu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano powiązanie netNamedPipeBinding, który zapewnia komunikację między procesami na tym samym komputerze. Nazwane potoki nie działają na komputerach.  
  
 Powiązanie jest określona w plikach konfiguracji dla klienta i usługi. Typ powiązania jest określona w `binding` atrybutu `<endpoint>` elementu. Jeśli chcesz skonfigurować powiązanie netNamedPipeBinding i zmieniania jego ustawień, należy zdefiniować konfiguracji powiązania. Punkt końcowy musi odwoływać się Konfiguracja powiązania o nazwie z `bindingConfiguration` atrybutu. W tym przykładzie nosi nazwę konfiguracji powiązania Binding1.  
  
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
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)
