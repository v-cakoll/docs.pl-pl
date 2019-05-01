---
title: Przykład autonomicznego kanału diagnostycznego
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 2737621a98f6a7e89ef3aee01fd1ad7a2a60f9b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007828"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Przykład autonomicznego kanału diagnostycznego
Ten przykład przedstawia sposób tworzenia RSS/źródła danych Atom w syndykacji dostępne przy użyciu programu Windows Communication Foundation (WCF). Jest to podstawowa programu "Hello World", który zawiera podstawowe informacje o modelu obiektów i sposób konfigurowania usługi Windows Communication Foundation (WCF).  
  
 Usługi WCF modele zespolone kanały informacyjne jako operacje usług, które zwracają to specjalny typ danych, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Wystąpienia elementu <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> może wykonywać serializację kanału informacyjnego w formatach RSS 2.0 i Atom 1.0. Następujący przykładowy kod przedstawia kontraktu używane.  
  
```  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.   
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 `GetProcesses` Operacji jest oznaczony za pomocą <xref:System.ServiceModel.Web.WebGetAttribute> atrybut, który umożliwia kontrolowanie sposobu WCF wywołuje HTTP GET żądania do operacji usługi i określić format wysyłanych wiadomości.  
  
 Podobnie jak żadnej usługi WCF zespolone kanały informacyjne może być samodzielnie hostowane w dowolnej aplikacji zarządzanej. Usługi syndykacji wymagają określonego powiązania ( <xref:System.ServiceModel.WebHttpBinding>) i zachowanie określonego punktu końcowego ( <xref:System.ServiceModel.Description.WebHttpBehavior>) do poprawnego działania. Nowy <xref:System.ServiceModel.Web.WebServiceHost> klasa oferuje wygodny interfejs API do tworzenia tych punktów końcowych bez określonej konfiguracji.  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Alternatywnie, można użyć <xref:System.ServiceModel.Activation.WebServiceHostFactory> z wewnątrz pliku .svc hostowanych przez usługi IIS umożliwiają korzystanie z funkcji równoważna (Ta technika nie jest pokazana w tym przykładowym kodzie).  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 Ponieważ ta usługa odbiera żądania przy użyciu standardowych HTTP GET, można użyć dowolnego źródła danych RSS lub ATOM-aware klienta do uzyskania dostępu do usługi. Na przykład, można wyświetlić dane wyjściowe tej usługi, przechodząc do `http://localhost:8000/diagnostics/feed/?format=atom` lub `http://localhost:8000/diagnostics/feed/?format=rss` w przeglądarce RSS-aware.
  
 Można również użyć [jak WCF syndykacji obiektu modelu mapy Atom i RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) do odczytywania danych syndykowany i przetworzyć te dane przy użyciu kodu imperatywnego.  
  
```  
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",  
new XmlReaderSettings()  
{  
//MaxCharactersInDocument can be used to control the maximum amount of data   
//read from the reader and helps prevent OutOfMemoryException  
MaxCharactersInDocument = 1024 * 64  
} );  
  
SyndicationFeed feed = SyndicationFeed.Load( reader );  
  
foreach (SyndicationItem i in feed.Items)  
{  
        XmlSyndicationContent content = i.Content as XmlSyndicationContent;  
        ProcessData pd = content.ReadContent<ProcessData>();  
  
        Console.WriteLine(i.Title.Text);  
        Console.WriteLine(pd.ToString());  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że adres odpowiednie uprawnienia rejestracji dla protokołu HTTP i HTTPS na komputerze, jak wyjaśniono w konfiguracji zgodnie z instrukcjami w [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Skompiluj rozwiązanie.  
  
3. Uruchom aplikację konsolową.  
  
4. Gdy jest uruchomiona aplikacja konsoli, przejdź do `http://localhost:8000/diagnostics/feed/?format=atom` lub `http://localhost:8000/diagnostics/feed/?format=rss` przy użyciu przeglądarki obsługującej RSS.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a>Zobacz także

- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Syndykacja programu WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
