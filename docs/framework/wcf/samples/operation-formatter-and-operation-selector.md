---
title: Element formatujący operacji i selektor operacji
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 9d1bc0afa54f89e064eab3f3e45da60c8d10de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144282"
---
# <a name="operation-formatter-and-operation-selector"></a>Element formatujący operacji i selektor operacji
W tym przykładzie pokazano, jak Windows Communication Foundation (WCF) punkty rozszerzalności może służyć do zezwalania na dane wiadomości w innym formacie, niż oczekuje WCF. Domyślnie formaterów WCF oczekiwać parametry metody `soap:body` mają być zawarte w elemencie. W przykładzie pokazano, jak zaimplementować niestandardowy formater operacji, który analizuje dane parametrów z ciągu zapytania HTTP GET zamiast i wywołuje metody przy użyciu tych danych.  
  
 Próbka jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` który implementuje umowy serwisowej. Pokazuje, jak można zmienić komunikaty Dodaj, Odejmować, Mnożenie i Podziel, aby używać protokołu HTTP GET dla żądań klient-serwer i HTTP POST z komunikatami POX dla odpowiedzi między serwerami.  
  
 W tym celu próbka zawiera następujące elementy:  
  
- `QueryStringFormatter`, który <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementuje i <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> dla klienta i serwera, odpowiednio, i przetwarza dane w ciągu zapytania.  
  
- `UriOperationSelector`, który <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementuje na serwerze do wykonywania operacji wysyłki na podstawie nazwy operacji w żądaniu GET.  
  
- `EnableHttpGetRequestsBehavior`zachowanie punktu końcowego (i odpowiednia konfiguracja), który dodaje selektor operacji niezbędne do środowiska wykonawczego.  
  
- Pokazuje, jak wstawić nowy program formatowania operacji do środowiska wykonawczego.  
  
- W tym przykładzie zarówno klient, jak i usługa są aplikacjami konsoli (.exe).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="key-concepts"></a>Kluczowe pojęcia  
 `QueryStringFormatter`- Formater operacji jest składnikiem w WCF, który jest odpowiedzialny za konwersję wiadomości do tablicy obiektów parametrów i tablicy obiektów parametrów w wiadomości. Odbywa się to na <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> kliencie za pomocą <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interfejsu i na serwerze z interfejsem. Interfejsy te umożliwiają użytkownikom uzyskanie komunikatów `Serialize` żądania `Deserialize` i odpowiedzi z i metod.  
  
 W tym `QueryStringFormatter` przykładzie implementuje oba te interfejsy i jest zaimplementowany na kliencie i serwerze.  
  
 Żądanie:  
  
- Przykład używa <xref:System.ComponentModel.TypeConverter> klasy do konwersji danych parametrów w wiadomości żądania do i z ciągów. Jeśli <xref:System.ComponentModel.TypeConverter> a nie jest dostępna dla określonego typu, przykładowy formater zgłasza wyjątek.  
  
- W `IClientMessageFormatter.SerializeRequest` metodzie na kliencie formater tworzy identyfikator URI z odpowiednim Adresem i dołącza nazwę operacji jako sufiks. Ta nazwa jest używana do wysyłania do odpowiedniej operacji na serwerze. Następnie pobiera tablicę obiektów parametrów i serializuje dane parametrów do ciągu kwerendy URI <xref:System.ComponentModel.TypeConverter> przy użyciu nazw parametrów i wartości przekonwertowanych przez klasę. Właściwości <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> i są następnie ustawione na ten identyfikator URI. <xref:System.ServiceModel.Channels.MessageProperties>dostęp do <xref:System.ServiceModel.Channels.Message.Properties%2A> obiektu.  
  
- W `IDispatchMessageFormatter.DeserializeRequest` metodzie na serwerze program formatujący pobiera identyfikator `Via` URI we właściwościach komunikatu żądania przychodzącego. Analizuje pary nazwa-wartość w ciągu kwerendy URI na nazwy i wartości parametrów i używa nazw parametrów i wartości do wypełniania tablicy parametrów przekazanych do metody. Należy zauważyć, że wysyłka operacji już wystąpiła, więc sufiks nazwy operacji jest ignorowany w tej metodzie.  
  
 Odpowiedź:  
  
- W tym przykładzie HTTP GET jest używany tylko dla żądania. Formater deleguje wysyłanie odpowiedzi do oryginalnego formatera, który zostałby użyty do wygenerowania wiadomości XML. Jednym z celów tego przykładu jest pokazanie, jak można zaimplementować takiego formatera delegującego.  
  
### <a name="uripathsuffixoperationselector-class"></a>UriPathSuffixOperationSelector Klasa  
 Interfejs <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> umożliwia użytkownikom zaimplementowanie własnej logiki, dla której należy wysłać określoną wiadomość.  
  
 W tym `UriPathSuffixOperationSelector` przykładzie muszą być zaimplementowane na serwerze, aby wybrać odpowiednią operację, ponieważ nazwa operacji znajduje się w identyfikatorze URI HTTP GET, a nie nagłówek akcji w komunikacie. Próbka jest skonfigurowana tak, aby zezwalać tylko na nazwy operacji bez uwzględniania wielkości liter.  
  
 Metoda `SelectOperation` przyjmuje przychodzące wiadomości i `Via` wyszukuje identyfikator URI we właściwościach wiadomości. Wyodrębnia sufiks nazwy operacji z identyfikatora URI, wyszukuje tabelę wewnętrzną, aby uzyskać nazwę operacji, do których powinien być wywoływany komunikat, i zwraca tę nazwę operacji.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>Włącz klasę HttpGetRequestsBehavior  
 Składnik `UriPathSuffixOperationSelector` można skonfigurować programowo lub za pomocą zachowania punktu końcowego. Przykład implementuje `EnableHttpGetRequestsBehavior` zachowanie, które jest określone w pliku konfiguracji aplikacji usługi.  
  
 Na serwerze:  
  
 Jest <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> ustawiona <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na implementację.  
  
 Domyślnie WCF używa filtru adresów dopasowania ścisłego. Identyfikator URI w wiadomości przychodzącej zawiera sufiks nazwy operacji, po którym następuje ciąg zapytania zawierający dane parametrów, więc zachowanie punktu końcowego zmienia również filtr adresów jako filtr dopasowania prefiksu. Używa WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> do tego celu.  
  
### <a name="installing-operation-formatters"></a>Instalowanie programów formatujących operacji  
 Zachowania operacji, które określają formaterów są unikatowe. Jedno takie zachowanie jest zawsze implementowane domyślnie dla każdej operacji, aby utworzyć formater operacji niezbędne. Jednak te zachowania wyglądają jak tylko inne zachowanie operacji; nie można ich zidentyfikować za pomocą żadnego innego atrybutu. Aby zainstalować zachowanie zastępcze, implementacja musi wyszukać określone zachowania formatera, które są domyślnie instalowane przez program ładujący typu WCF i zastąpić go lub dodać zgodne zachowanie do uruchomienia po domyślnym zachowaniu.  
  
 Te zachowania programowe formaterów operacji można skonfigurować <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> programowo przed wywołaniem lub określając zachowanie operacji wykonywane po domyślnym. Jednak nie można łatwo skonfigurować przez zachowanie punktu końcowego (i w związku z tym przez konfigurację), ponieważ model zachowania nie zezwala na zachowanie, aby zastąpić inne zachowania lub w inny sposób zmodyfikować drzewo opisu.  
  
 Na kliencie:  
  
 Implementacja <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> musi zostać zaimplementowana, aby mogła konwertować żądania na żądania HTTP GET i delegować do oryginalnego formatera odpowiedzi. Odbywa się to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` przez wywołanie metody pomocnika.  
  
 Należy to zrobić `CreateChannel`przed wywołaniem .  
  
```csharp  
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
  
- Interfejs <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> musi być zaimplementowany tak, aby mógł odczytywać żądania HTTP GET i delegować do oryginalnego formatera do pisania odpowiedzi. Odbywa się to przez `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` wywołanie tej samej metody pomocnika jako klienta (zobacz poprzedni przykład kodu).  
  
- Należy to zrobić, zanim <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> zostanie wywołana. W tym przykładzie pokazujemy, jak formater jest <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>ręcznie modyfikowany przed wywołaniem . Innym sposobem osiągnięcia tego samego jest wyprowadzenie klasy <xref:System.ServiceModel.ServiceHost> `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` z tego sprawia, że wywołania przed otwarciem (zobacz dokumentację hostingu i przykłady przykładów).  
  
### <a name="user-experience"></a>Środowisko użytkownika  
 Na serwerze:  
  
- Implementacja `ICalculator` serwera nie musi się zmieniać.  
  
- App.config dla usługi musi używać niestandardowego powiązania `messageVersion` POX, `textMessageEncoding` które `None`ustawia atrybut elementu do .  
  
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
  
- App.config dla usługi również należy `EnableHttpGetRequestsBehavior` określić niestandardowe, dodając go do rozszerzenia zachowania sekcji i używając go.  
  
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
  
- Dodaj programy formaterów <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>operacji przed wywołaniem .  
  
 Na kliencie:  
  
- Implementacja klienta nie musi się zmieniać.  
  
- App.config dla klienta musi używać niestandardowego powiązania `messageVersion` POX, `textMessageEncoding` które `None`ustawia atrybut elementu na . Jedną z różnic w stosunku do usługi jest to, że klient musi włączyć adres ręczny, tak aby adres wychodzący do może być modyfikowany.  
  
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
  
- App.config dla klienta musi określić `EnableHttpGetRequestsBehavior` ten sam niestandardowy jako serwer.  
  
- Dodaj programy formaterów <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>operacji przed wywołaniem .  
  
 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Wszystkie cztery operacje (Dodaj, Odejmij, Mnożenie i Podziel) muszą zakończyć się pomyślnie.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
