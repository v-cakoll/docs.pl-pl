---
title: Element formatujący operacji i selektor operacji
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: a814de7433f2d06491245dc1d6e6e637b514118a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44065934"
---
# <a name="operation-formatter-and-operation-selector"></a>Element formatujący operacji i selektor operacji
Niniejszy przykład pokazuje, jak punkty rozszerzeń usługi Windows Communication Foundation (WCF) można umożliwić danych komunikatu w innym formacie z WCF oczekuje. Domyślnie elementy formatujące WCF oczekiwane parametry metody, które mają zostać uwzględnione w ramach `soap:body` elementu. Przykład pokazuje, jak implementować niestandardowe działania programu formatującego, zamiast tego analizuje dane parametru ciągu zapytania HTTP GET, która wywołuje metody przy użyciu tych danych.  
  
 Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi. Jego pokazuje jak dodawanie, odejmowanie, mnożenie, dzielenie wiadomości, można ją zmienić na użyć żądania HTTP GET dla żądań klienta do serwera i HTTP POST z POX komunikatów dla odpowiedzi z serwera do klienta.  
  
 Aby to zrobić, przykład zapewnia następujące korzyści:  
  
-   `QueryStringFormatter`, która implementuje <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> i <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> dla klienta i serwera, odpowiednio i przetwarza dane w ciągu zapytania.  
  
-   `UriOperationSelector`, która implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na serwerze w celu wykonania wysyłki operacji na podstawie nazwy operacji żądania GET.  
  
-   `EnableHttpGetRequestsBehavior` punkt końcowy zachowanie i odpowiedniej konfiguracji, która dodaje do środowiska uruchomieniowego selektor niezbędnych operacji.  
  
-   Pokazuje, jak można wstawić nowy element formatujący operacji w czasie wykonywania.  
  
-   W tym przykładzie zarówno klient, jak i usługi są aplikacje konsoli (.exe).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
## <a name="key-concepts"></a>Kluczowe pojęcia  
 `QueryStringFormatter` Element formatujący operacji jest składnikiem programu WCF, odpowiedzialną za konwersji wiadomość do tablicy obiektów parametru i tablicę obiektów parametr do wiadomości. Odbywa się na komputerze klienckim, za pomocą <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interfejsu i na serwerze z <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interfejsu. Te interfejsy umożliwiają użytkownikom pobieranie komunikatów żądań i odpowiedzi z `Serialize` i `Deserialize` metody.  
  
 W tym przykładzie `QueryStringFormatter` implementuje obu tych interfejsów i jest zaimplementowana na kliencie i serwerze.  
  
 Żądanie:  
  
-   W przykładzie użyto <xref:System.ComponentModel.TypeConverter> klasy w celu przekonwertowania danych parametru w komunikacie żądania do i z ciągów. Jeśli <xref:System.ComponentModel.TypeConverter> nie jest dostępna dla określonego typu, zgłasza program formatujący przykładowy wyjątek, który.  
  
-   W `IClientMessageFormatter.SerializeRequest` metody na kliencie, program formatujący tworzy identyfikator URI przy użyciu odpowiedniego adresu i dołącza nazwy operacji jako sufiks. Ta nazwa jest używana do wysłania do odpowiednich operacji na serwerze. Następnie pobiera tablicę obiektów parametru i serializuje dane parametru ciągu zapytania identyfikatora URI za pomocą nazwy i wartości przekonwertowane przez <xref:System.ComponentModel.TypeConverter> klasy. <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> i <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> właściwości są następnie ustawione do tego identyfikatora URI. <xref:System.ServiceModel.Channels.MessageProperties> jest dostępny za pośrednictwem <xref:System.ServiceModel.Channels.Message.Properties%2A> właściwości.  
  
-   W `IDispatchMessageFormatter.DeserializeRequest` pobiera element formatujący metody na serwerze, `Via` URI we właściwościach komunikatu żądania przychodzące. On analizuje pary nazwa wartość w ciągu zapytania identyfikatora URI do nazwy parametrów i wartości i użyje nazwy parametrów i wartości, aby wypełnić Tablica parametrów przekazana do metody. Należy pamiętać, że operacja wysyłania już wystąpił, więc sufiks nazwy operacji jest ignorowany w przypadku tej metody.  
  
 Odpowiedź:  
  
-   W tym przykładzie HTTP GET jest używana tylko dla żądania. Element formatujący deleguje, wysyła odpowiedź do oryginalnego elementu formatującego, który będzie używany do generowania wiadomości XML. Jednym z celów tego przykładu jest pokazanie implementacji delegowania formatującego.  
  
### <a name="uripathsuffixoperationselector-class"></a>Klasa UriPathSuffixOperationSelector  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> Interfejs umożliwia użytkownikom do zaimplementowania własnej logiki dla operacji, który można wysłać określonej wiadomości.  
  
 W tym przykładzie `UriPathSuffixOperationSelector` musi zostać wdrożone na serwerze, aby wybrać odpowiednią operację, ponieważ nazwa operacji jest uwzględniony w identyfikator URI Pobierz protokołu HTTP, a nie nagłówek akcji w wiadomości. Aby zezwolić na działanie tylko bez uwzględniania wielkości liter nazwy skonfigurowano próbki.  
  
 `SelectOperation` Metoda przyjmuje wiadomości przychodzącej i wyszukuje `Via` identyfikatora URI w jego właściwościach wiadomości. Jego wyodrębnia sufiks nazwy operacji z identyfikatora URI odwołuje się do wewnętrznej tabeli można uzyskać nazwy operacji, który komunikat powinien być wysyłane do i zwraca nazwę tej operacji.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>Klasa EnableHttpGetRequestsBehavior  
 `UriPathSuffixOperationSelector` Składnika można skonfigurować pod kątem programowo lub za pomocą zachowanie punktu końcowego. Implementuje próbki `EnableHttpGetRequestsBehavior` zachowanie, które określono w pliku konfiguracji aplikacji usługi.  
  
 Na serwerze:  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Ustawiono <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementacji.  
  
 Domyślnie program WCF używa filtra dokładnie dopasowanego adresu. Identyfikator URI na przychodząca wiadomość zawiera sufiks nazwy operacji następuje ciąg zapytania, który zawiera dane parametru, więc zachowanie punktu końcowego zmienia także filtr adresów jako prefiks, który pasuje do filtru. Używa ona WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> do tego celu.  
  
### <a name="installing-operation-formatters"></a>Instalowanie elementów formatujących operacji  
 Zachowania operacji, które określają elementy formatujące są unikatowe. Jednego takiego zachowania zawsze jest implementowany przez domyślne dla każdej operacji utworzyć element formatujący niezbędnych operacji. Jednak te zachowania wyglądać kolejna operacja zachowań. nie są identyfikowane przez inne atrybuty. Aby zainstalować zachowanie zastępczy, implementacja musi poszukaj go zastąpić określonego programu formatującego zachowań, które są instalowane przez moduł ładujący typu WCF domyślnie i za pomocą lub dodać zachowanie zgodne do uruchomienia po zachowanie domyślne.  
  
 Zachowania elementy formatujące tych operacji można skonfigurować pod kątem programowo przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> lub określając zachowanie operacji, który jest wykonywany po domyślny. Jednak go nie można łatwo można skonfigurować przez zachowanie punktu końcowego (i w związku z tym przez konfigurację), ponieważ model zachowanie nie zezwala na to zachowanie zastąpić innych zachowań lub inny sposób modyfikować drzewa opis.  
  
 Na komputerze klienckim:  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Implementacji należy zaimplementować tak, aby ją przekonwertować żądania na żądania HTTP GET i delegować do oryginalnego program formatujący dla odpowiedzi. Jest to realizowane przez wywołanie `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` metody pomocnika.  
  
 To musi odbywać się przed wywołaniem `CreateChannel`.  
  
```  
void ReplaceFormatterBehavior(OperationDescription operationDescription, EndpointAddress address)  
{  
    // Remove the DataContract behavior if it is present.  
    IOperationBehavior formatterBehavior = operationDescription.Behaviors.Remove<DataContractSerializerOperationBehavior>();  
    if (formatterBehavior == null)  
    {  
        // Remove the XmlSerializer behavior if it is present.  
        formatterBehavior = operationDescription.Behaviors.Remove<XmlSerializerOperationBehavior>();  
        ...  
    }  
  
    // Remember what the innerFormatterBehavior was.  
    DelegatingFormatterBehavior delegatingFormatterBehavior = new DelegatingFormatterBehavior(address);  
    delegatingFormatterBehavior.InnerFormatterBehavior = formatterBehavior;  
   operationDescription.Behaviors.Add(delegatingFormatterBehavior);  
}  
```  
  
 Na serwerze:  
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Można zaimplementować interfejsu, czemu może odczytywać żądania HTTP GET i delegować do oryginalnego elementu formatującego do pisania odpowiedzi. Odbywa się przez wywołanie metody takie same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` metody pomocnika jako klient (zobacz poprzedni przykład kodu).  
  
-   To musi odbywać się przed <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> jest wywoływana. W tym przykładzie pokazano, jak program formatujący jest modyfikowany ręcznie przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Innym sposobem, aby osiągnąć ten sam efekt jest wyprowadzić klasę z <xref:System.ServiceModel.ServiceHost> sprawia to, że wywołania `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` przed otwarciem (zobacz hostingu, dokumentację i przykłady dotyczące przykładów).  
  
### <a name="user-experience"></a>Środowisko użytkownika  
 Na serwerze:  
  
-   Serwer `ICalculator` wdrożenia nie trzeba zmieniać.  
  
-   App.config dla usługi, należy użyć niestandardowego powiązania POX, która ustawia `messageVersion` atrybutu `textMessageEncoding` elementu `None`.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
-   App.config dla usługi również podać niestandardową `EnableHttpGetRequestsBehavior` , dodając go do sekcji rozszerzenia zachowania i korzystania z niego.  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="enableHttpGetRequestsBehavior">  
          <enableHttpGetRequests />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
    <extensions>  
      <behaviorExtensions>  
        <!-- Enabling HTTP GET requests: Behavior Extension -->  
        <add   
          name="enableHttpGetRequests"           type="Microsoft.ServiceModel.Samples.EnableHttpGetRequestsBehaviorElement, QueryStringFormatter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
    ```  
  
-   Dodaj elementy formatujące operacji, przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
 Na komputerze klienckim:  
  
-   Implementacja klienta nie trzeba zmieniać.  
  
-   App.config dla klienta, należy użyć niestandardowego powiązania POX, która ustawia `messageVersion` atrybutu `textMessageEncoding` elementu `None`. Jedną różnicaą z usługi jest to klienta należy włączyć, ręcznego adresowania, tak aby wychodzących na adres może być modyfikowany.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport manualAddressing="True" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
-   App.config dla klienta należy określić ten sam niestandardowy `EnableHttpGetRequestsBehavior` co serwer.  
  
-   Dodaj elementy formatujące operacji, przed wywołaniem <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.  
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Wszystkie cztery operacje (dodawania, odejmowania, mnożenia i dzielenia) musi zakończyć się sukcesem.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też
