---
title: Element formatujący operacji i selektor operacji
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 5853a791a92535c970f8010dd08d42e10292ffa8
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039031"
---
# <a name="operation-formatter-and-operation-selector"></a>Element formatujący operacji i selektor operacji
Ten przykład pokazuje, w jaki sposób punkty rozszerzalności Windows Communication Foundation (WCF) mogą być używane do zezwalania na dane komunikatów w innym formacie niż oczekiwany przez WCF. Domyślnie `soap:body` elementy formatujące WCF oczekują parametrów metody, które mają być zawarte w elemencie. W przykładzie przedstawiono sposób implementacji niestandardowego programu formatującego operacji, który analizuje dane parametrów z ciągu zapytania HTTP GET, a następnie wywołuje metody przy użyciu tych danych.  
  
 Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontrakt usługi. Pokazano, jak można zmienić komunikaty dodawania, odejmowania, mnożenia i dzielenia, aby używać protokołu HTTP GET dla żądań klient-serwer i HTTP POST z komunikatami POX dla odpowiedzi między serwerami i klientami.  
  
 W tym celu przykład zawiera następujące elementy:  
  
- `QueryStringFormatter`, który implementuje <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> odpowiednio <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> i dla klienta i serwera, i przetwarza dane w ciągu zapytania.  
  
- `UriOperationSelector`, który implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na serwerze wykonywanie operacji wysyłania na podstawie nazwy operacji w żądaniu get.  
  
- `EnableHttpGetRequestsBehavior`zachowanie punktu końcowego (i odpowiednia konfiguracja), które dodaje do środowiska uruchomieniowego niezbędny selektor operacji.  
  
- Pokazuje, w jaki sposób wstawić nowy program formatujący operacji do środowiska uruchomieniowego.  
  
- W tym przykładzie zarówno klient, jak i usługa są aplikacjami konsolowymi (. exe).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="key-concepts"></a>Kluczowe pojęcia  
 `QueryStringFormatter`— Program formatujący operacji jest składnikiem programu WCF, który jest odpowiedzialny za konwertowanie komunikatu na tablicę obiektów parametrów i tablicę obiektów parametrów w wiadomości. Jest to wykonywane na kliencie przy użyciu <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interfejsu i na serwerze <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> z interfejsem. Te interfejsy umożliwiają użytkownikom uzyskiwanie żądań i komunikatów odpowiedzi z `Serialize` metod i. `Deserialize`  
  
 W tym przykładzie `QueryStringFormatter` implementuje obydwa te interfejsy i jest zaimplementowany na kliencie i serwerze.  
  
 Żądając  
  
- Przykład używa <xref:System.ComponentModel.TypeConverter> klasy do konwersji danych parametrów w komunikacie żądania do i z ciągów znaków. Jeśli element <xref:System.ComponentModel.TypeConverter> nie jest dostępny dla określonego typu, przykładowy program formatujący zgłosi wyjątek.  
  
- `IClientMessageFormatter.SerializeRequest` W metodzie klienta program formatujący tworzy identyfikator URI z odpowiednim adresem i dołącza nazwę operacji jako sufiks. Ta nazwa jest używana do wysyłania do odpowiedniej operacji na serwerze. Następnie pobiera tablicę obiektów parametrów i serializować dane parametrów do ciągu zapytania identyfikatora URI przy użyciu nazw parametrów i wartości przekonwertowanych przez <xref:System.ComponentModel.TypeConverter> klasę. A następnie <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> właściwości i są ustawiane na ten identyfikator URI. <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> <xref:System.ServiceModel.Channels.MessageProperties>jest dostępny za pomocą <xref:System.ServiceModel.Channels.Message.Properties%2A> właściwości.  
  
- W metodzie na serwerze program formatujący `Via` Pobiera identyfikator URI we właściwościach komunikatu o żądaniu przychodzącym. `IDispatchMessageFormatter.DeserializeRequest` Analizuje pary nazwa-wartość w ciągu zapytania identyfikatora URI do nazw i wartości parametrów, a następnie używa nazw i wartości parametrów do wypełnienia tablicy parametrów przekazaną do metody. Należy zauważyć, że wysyłka operacji już się zakończyła, więc sufiks nazwy operacji jest ignorowany w tej metodzie.  
  
 Reakcji  
  
- W tym przykładzie HTTP GET jest używany tylko dla żądania. Program formatujący deleguje wysyłanie odpowiedzi do oryginalnego programu formatującego, który mógłby zostać użyty do wygenerowania wiadomości XML. Jednym z celów tego przykładu jest przedstawienie sposobu, w jaki można zaimplementować ten program formatujący delegowanie.  
  
### <a name="uripathsuffixoperationselector-class"></a>Klasa UriPathSuffixOperationSelector  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> Interfejs umożliwia użytkownikom implementację własnej logiki, dla której należy wysłać konkretną wiadomość.  
  
 W tym przykładzie należy `UriPathSuffixOperationSelector` wdrożyć na serwerze, aby wybrać odpowiednią operację, ponieważ nazwa operacji jest uwzględniona w identyfikatorze URI http Get, a nie w nagłówku akcji w komunikacie. Przykład jest skonfigurowany tak, aby zezwalał tylko na nazwy operacji bez uwzględniania wielkości liter.  
  
 Metoda przyjmuje komunikat przychodzący i wyszukuje `Via` identyfikator URI we właściwościach komunikatu. `SelectOperation` Wyodrębnia sufiks nazwy operacji z identyfikatora URI, wyszukuje wewnętrzną tabelę, aby uzyskać nazwę operacji, do której wiadomość powinna zostać wysłana, i zwraca tę nazwę operacji.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>Klasa EnableHttpGetRequestsBehavior  
 `UriPathSuffixOperationSelector` Składnik można skonfigurować programowo lub za pomocą zachowania punktu końcowego. Przykład implementuje `EnableHttpGetRequestsBehavior` zachowanie, które jest określone w pliku konfiguracyjnym aplikacji usługi.  
  
 Na serwerze programu:  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Ustawiono<xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementację.  
  
 Domyślnie WCF używa filtru adresów dokładnie dopasowane. Identyfikator URI komunikatu przychodzącego zawiera sufiks nazwy operacji, po którym następuje ciąg zapytania, który zawiera dane parametrów, więc zachowanie punktu końcowego zmienia również filtr adresów na filtr dopasowania prefiksu. W tym celu używa<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> programu WCF.  
  
### <a name="installing-operation-formatters"></a>Instalowanie programów formatujących operacje  
 Zachowania operacji określające elementy formatujące są unikatowe. Takie zachowanie jest zawsze zaimplementowane domyślnie dla każdej operacji w celu utworzenia wymaganego programu formatującego operacji. Jednak te zachowania wyglądają jak tylko inne zachowanie operacji; nie są one identyfikowane przez żaden inny atrybut. Aby można było zainstalować zachowanie zamiany, implementacja musi szukać określonych zachowań programu formatującego, które są instalowane domyślnie przez program ładujący typ WCF, i zastąpić je lub dodać zgodne zachowanie, które zostanie uruchomione po domyślnym zachowaniu.  
  
 Te zachowania programu formatującego operacji można skonfigurować programowo przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> lub przez określenie zachowania operacji, które jest wykonywane po wartości domyślnej. Nie można go jednak łatwo konfigurować przy użyciu zachowania punktu końcowego (w związku z czym konfiguracja), ponieważ model zachowania nie zezwala na zachowanie innych zachowań lub modyfikowanie drzewa opisów.  
  
 Na kliencie:  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Implementacja musi być zaimplementowana, aby można było skonwertować żądania na żądania HTTP GET i delegować do oryginalnego programu formatującego dla odpowiedzi. W tym celu należy wywołać `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` metodę pomocnika.  
  
 Należy to zrobić przed wywołaniem `CreateChannel`metody.  
  
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
  
 Na serwerze programu:  
  
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Interfejs musi być zaimplementowany, aby mógł odczytywać żądania HTTP GET i delegować do oryginalnego programu formatującego w celu zapisywania odpowiedzi. Jest to realizowane przez wywołanie tej samej `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` metody pomocnika co klient (zobacz poprzedni przykład kodu).  
  
- Należy to zrobić przed <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> wywołaniem metody. W tym przykładzie pokazano, jak program formatujący został ręcznie zmodyfikowany przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Innym sposobem osiągnięcia tego samego celu jest wyprowadzenie klasy z <xref:System.ServiceModel.ServiceHost> tego, że `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` wywołania przed otwarciem (patrz dokumentacja hostingu i przykłady).  
  
### <a name="user-experience"></a>Środowisko użytkownika  
 Na serwerze programu:  
  
- Implementacja serwera `ICalculator` nie musi się zmieniać.  
  
- Plik App. config usługi musi używać niestandardowego powiązania POX, które ustawia `messageVersion` atrybut `textMessageEncoding` elementu na `None`.  
  
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
  
- Plik App. config usługi musi również określać niestandardowe `EnableHttpGetRequestsBehavior` przez dodanie go do sekcji rozszerzenia zachowań i używanie go.  
  
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
  
- Dodaj elementy formatujące operacji przed <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>wywołaniem metody.  
  
 Na kliencie:  
  
- Implementacja klienta nie musi być zmieniana.  
  
- Plik App. config klienta musi używać niestandardowego powiązania POX, które ustawia `messageVersion` atrybut `textMessageEncoding` elementu na `None`. Jedną z różnic polega na tym, że klient musi włączyć ręczne adresowanie, aby można było zmodyfikować adres wychodzący.  
  
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
  
- Plik App. config klienta musi określać ten sam niestandardowy `EnableHttpGetRequestsBehavior` serwer.  
  
- Dodaj elementy formatujące operacji przed <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>wywołaniem metody.  
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Wszystkie cztery operacje (Dodawanie, odejmowanie, mnożenie i dzielenie) muszą się zakończyć pomyślnie.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
