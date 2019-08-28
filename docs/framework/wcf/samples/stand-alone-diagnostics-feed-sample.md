---
title: Przykład autonomicznego kanału diagnostycznego
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 6b83bda154a76fe10487da00359e0ceace8ce8cb
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044678"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Przykład autonomicznego kanału diagnostycznego
Ten przykład pokazuje, jak utworzyć kanał informacyjny RSS/Atom dla zespalania z Windows Communication Foundation (WCF). Jest to podstawowy program "Hello world", który zawiera podstawowe informacje dotyczące modelu obiektów i sposobu konfigurowania go w usłudze Windows Communication Foundation (WCF).  
  
 Program WCF modeluje źródła danych zespolonych jako operacje usługi, które zwracają <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>specjalne dane typu. Wystąpienia programu <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> mogą serializować źródło danych do formatów RSS 2,0 i Atom 1,0. Następujący przykładowy kod przedstawia użyty kontrakt.  
  
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
  
 Operacja ma adnotację <xref:System.ServiceModel.Web.WebGetAttribute> z atrybutem, który umożliwia kontrolowanie sposobu, w jaki program WCF wysyła żądania HTTP GET do operacji usługi i określa format wysyłanych komunikatów. `GetProcesses`  
  
 Podobnie jak w przypadku dowolnej usługi WCF, zespolone źródła danych mogą być obsługiwane przez dowolną aplikację zarządzaną. Usługi zespolone wymagają określonego powiązania ( <xref:System.ServiceModel.WebHttpBinding>) i określonego zachowania punktu końcowego <xref:System.ServiceModel.Description.WebHttpBehavior>() w celu poprawnego działania. Nowa <xref:System.ServiceModel.Web.WebServiceHost> Klasa zapewnia wygodny interfejs API do tworzenia punktów końcowych bez określonej konfiguracji.  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Alternatywnie można użyć <xref:System.ServiceModel.Activation.WebServiceHostFactory> programu z poziomu pliku SVC hostowanego przez usługi IIS w celu zapewnienia równoważnej funkcjonalności (Ta technika nie jest przedstawiona w tym przykładowym kodzie).  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 Ponieważ ta usługa odbiera żądania przy użyciu standardowego protokołu HTTP GET, do uzyskiwania dostępu do usługi można użyć dowolnego klienta obsługującego technologię RSS lub ATOM. Na przykład dane wyjściowe tej usługi można wyświetlić, przechodząc do `http://localhost:8000/diagnostics/feed/?format=atom` lub `http://localhost:8000/diagnostics/feed/?format=rss` w przeglądarce obsługującej funkcję RSS.
  
 Możesz również użyć [modelu obiektów zespolonych WCF, który jest mapowany na Atom i RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) , aby odczytywać dane zespolone i przetwarzać je za pomocą kodu.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że masz odpowiednie uprawnienia do rejestracji adresów dla protokołów HTTP i HTTPS na komputerze, zgodnie z opisem w temacie Konfigurowanie instrukcji w jednorazowej [procedurze konfiguracyjnej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Skompiluj rozwiązanie.  
  
3. Uruchom aplikację konsolową.  
  
4. Gdy aplikacja konsolowa jest uruchomiona, przejdź do `http://localhost:8000/diagnostics/feed/?format=atom` lub `http://localhost:8000/diagnostics/feed/?format=rss` korzystając z przeglądarki obsługującej funkcję RSS.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a>Zobacz także

- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Syndykacja programu WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
