---
title: "Element formatujący operacji i selektor operacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a10be10687f03b5de45846faa9ca832ead193e19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="operation-formatter-and-operation-selector"></a>Element formatujący operacji i selektor operacji
W przykładzie pokazano, jak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] punkty rozszerzeń może służyć do Zezwalaj komunikat danych w innym formacie z co [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oczekuje. Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] elementy formatujące oczekiwane parametry metody do uwzględnienia w obszarze `soap:body` elementu. Przykład obejmuje implementowania niestandardowych operacji programu formatującego, zamiast tego analizuje dane parametru ciągu zapytania HTTP GET, który wywołuje metody przy użyciu tych danych.  
  
 Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi. Go przedstawiono sposób dodawania, odejmowania wielokrotnie i dzielenia wiadomości, można zmienić użyć żądania HTTP GET dla żądań klienta do serwera i HTTP POST z POX wiadomości odpowiedzi serwera do klienta.  
  
 Aby to zrobić, próbki zapewnia następujące korzyści:  
  
-   `QueryStringFormatter`, które implementuje <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> i <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> dla klienta i serwera, odpowiednio i przetwarza dane w ciągu zapytania.  
  
-   `UriOperationSelector`, które implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na serwerze do wykonywania operacji wysyłki na podstawie nazwy operacji w żądanie GET.  
  
-   `EnableHttpGetRequestsBehavior`punkt końcowy zachowanie (i odpowiedniej konfiguracji), która dodaje selektor operacji niezbędne do środowiska wykonawczego.  
  
-   Pokazuje, jak można wstawić nowej programu formatującego operacji w czasie wykonywania.  
  
-   W tym przykładzie zarówno klient, jak i usługi są aplikacje konsoli (.exe).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="key-concepts"></a>Podstawowe pojęcia  
 `QueryStringFormatter`Programu formatującego operacji jest składnikiem w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] odpowiada do konwertowania wiadomości na tablicę obiektów parametru i tablicę obiektów parametru do wiadomości. Ta próba polega na kliencie przy użyciu <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interfejsu i na serwerze z <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interfejsu. Te interfejsy umożliwiają użytkownikom uzyskiwanie komunikatów żądań i odpowiedzi z `Serialize` i `Deserialize` metody.  
  
 W tym przykładzie `QueryStringFormatter` implementuje obu tych interfejsów i jest zaimplementowana na kliencie i serwerze.  
  
 Żądanie:  
  
-   W przykładzie użyto <xref:System.ComponentModel.TypeConverter> klasy w celu przekonwertowania danych parametru w komunikacie żądania do i z ciągów. Jeśli <xref:System.ComponentModel.TypeConverter> nie jest dostępny dla określonego typu, program formatujący próbki zwraca wyjątek.  
  
-   W `IClientMessageFormatter.SerializeRequest` metoda na kliencie, program formatujący tworzy identyfikator URI odpowiedni adres i dołącza nazwy operacji sufiks. Ta nazwa jest używana do wysłania do odpowiednich operacji na serwerze. Następnie pobiera tablicę obiektów parametru i serializuje dane parametru ciągu zapytania identyfikatora URI przy użyciu nazwy parametrów i wartości przekonwertowane przez <xref:System.ComponentModel.TypeConverter> klasy. <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> i <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> właściwości są następnie ustaw ten identyfikator URI. <xref:System.ServiceModel.Channels.MessageProperties>jest dostępny za pośrednictwem <xref:System.ServiceModel.Channels.Message.Properties%2A> właściwości.  
  
-   W `IDispatchMessageFormatter.DeserializeRequest` metoda na serwerze, program formatujący pobiera `Via` URI we właściwościach komunikatu żądania przychodzące. Analizuje pary nazwa wartość w ciągu zapytania identyfikatora URI do nazwy i wartości parametrów, a używa nazwy parametrów i wartości do wypełnienia Tablica parametrów przekazana do metody. Należy pamiętać, że już przeprowadzono operacji wysyłania, więc sufiks nazwy operacji jest ignorowana w przypadku tej metody.  
  
 Odpowiedź:  
  
-   W tym przykładzie HTTP GET jest używany tylko dla żądania. Program formatujący deleguje wysyłanie odpowiedzi na oryginalny element formatujący, który będzie używany do generowania wiadomości XML. Jest jednym z celów tego przykładu pokazanie implementowania delegujące formatującego.  
  
### <a name="uripathsuffixoperationselector-class"></a>Klasa UriPathSuffixOperationSelector  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> Interfejs umożliwia użytkownikom wdrożenia własnej logiki dla operacji, które powinny wysłać danego komunikatu.  
  
 W tym przykładzie `UriPathSuffixOperationSelector` musi zostać wdrożone na serwerze, aby wybrać odpowiednie działania, ponieważ nazwa operacji znajduje się identyfikator URI GET protokołu HTTP zamiast nagłówka action w komunikacie. Aby umożliwić działanie tylko bez uwzględniania wielkości liter nazwy skonfigurowano próbki.  
  
 `SelectOperation` Metoda pobiera komunikat przychodzący i wyszukuje `Via` identyfikatora URI w jego właściwościach komunikatu. Go wyodrębnia sufiks nazwy operacji z identyfikatora URI, odwołuje się do wewnętrznej tabeli można uzyskać nazwy operacji, które wiadomości powinna być wysyłane do i zwraca nazwę tej operacji.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>Klasa EnableHttpGetRequestsBehavior  
 `UriPathSuffixOperationSelector` Składnika można skonfigurować programowo lub za pośrednictwem zachowanie punktu końcowego. Implementuje próbki `EnableHttpGetRequestsBehavior` zachowanie, które jest określone w pliku konfiguracyjnym aplikacji usługi.  
  
 Na serwerze:  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Ustawiono <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementacji.  
  
 Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa filtra dokładnie dopasowanego adresu. Identyfikator URI w komunikacie przychodzącym zawiera sufiks nazwy operacji następuje zawierający dane parametru ciągu zapytania, dzięki zachowania punktu końcowego również zmiany filtr adresów jako prefiksu pasuje do filtru. Używa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> w tym celu.  
  
### <a name="installing-operation-formatters"></a>Instalowanie formatujących operacji  
 Operacja zachowania, określające elementy formatujące są unikatowe. Domyślnie dla każdej operacji tworzenia programu formatującego niezbędnych operacji zawsze zaimplementowano jednego takiego zachowania. Jednak te zachowania wyglądać kolejna operacja zachowanie; nie są identyfikowane przez inny atrybut. Aby zainstalować zachowanie zastąpienia, implementacja musi wyglądać dla określonego programu formatującego zachowania, które są instalowane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modułu ładującego typu domyślnie i zastąp go lub dodać zachowanie zgodne do uruchomienia po zachowanie domyślne.  
  
 Te zachowania elementy formatujące operacji można skonfigurować programowo przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> lub określając zachowanie operacji, która jest wykonywana po domyślny. Jednak go nie można łatwo można skonfigurować przy zachowanie punktu końcowego (i w związku z tym w konfiguracji) ponieważ modelu zachowanie nie zezwala na zachowanie zastąpić innych zachowań lub modyfikację drzewa opis.  
  
 Na komputerze klienckim:  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Wdrożenia musi być implementowana tak, aby można przekonwertować żądania na żądania HTTP GET i delegować do oryginalnego program formatujący dla odpowiedzi. Jest to realizowane przez wywołanie `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` metody pomocnika.  
  
 Należy to zrobić przed wywołaniem `CreateChannel`.  
  
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
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Interfejs musi zostać wdrożone, dzięki czemu może odczytywać żądania HTTP GET i delegować do oryginalnego elementu formatującego do zapisywania odpowiedzi. Polega to na takie same wywoływania `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` metody pomocnika jako klient (zobacz poprzedni przykład kodu).  
  
-   Należy to zrobić przed <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> jest wywoływana. W tym przykładzie zostanie przedstawiony sposób program formatujący jest modyfikowany ręcznie przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Innym sposobem uzyskania samo jest wyprowadzenia klasy z <xref:System.ServiceModel.ServiceHost> dzięki temu wywołań `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` przed otwarciem (Zobacz hosting dokumentacja i przykłady przykłady).  
  
### <a name="user-experience"></a>Środowisko użytkownika  
 Na serwerze:  
  
-   Serwer `ICalculator` implementacji nie trzeba zmieniać.  
  
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
  
-   App.config dla usługi również określić niestandardowe `EnableHttpGetRequestsBehavior` przez dodanie go do sekcji rozszerzenia zachowania i przy jego użyciu.  
  
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
  
-   Dodaj elementy formatujące operacji przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
 Na komputerze klienckim:  
  
-   Implementacja klienta nie trzeba zmieniać.  
  
-   App.config dla klienta, należy użyć niestandardowego powiązania POX, która ustawia `messageVersion` atrybutu `textMessageEncoding` elementu `None`. Różnica jednego z usługi jest klienta należy włączyć, ręcznego adresowania, tak aby wychodzących na adres może być modyfikowany.  
  
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
  
-   App.config dla klienta należy określić niestandardowy tego samego `EnableHttpGetRequestsBehavior` jako serwer.  
  
-   Dodaj elementy formatujące operacji przed wywołaniem <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Wszystkie cztery operacje (Dodawanie, odjąć mnożenia i dzielenia) musi się zakończyć powodzeniem.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też
