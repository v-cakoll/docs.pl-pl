---
title: Przykład autonomicznego kanału diagnostycznego
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 29d8caee48925040db9f1812f015870e3a1272bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144009"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Przykład autonomicznego kanału diagnostycznego
W tym przykładzie pokazano, jak utworzyć kanał RSS/Atom do syndykacji z Windows Communication Foundation (WCF). Jest to podstawowy program "Hello World", który pokazuje podstawy modelu obiektu i jak go skonfigurować w usłudze Windows Communication Foundation (WCF).  
  
 WCF modele syndykacji kanałów jako operacje usługi, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>które zwracają specjalny typ danych, . Wystąpienia <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> mogą serializować kanał informacyjny zarówno w formatach RSS 2.0, jak i Atom 1.0. Poniższy przykładowy kod przedstawia używany kontrakt.  
  
```csharp  
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
  
 Operacja `GetProcesses` jest opisywana za <xref:System.ServiceModel.Web.WebGetAttribute> pomocą atrybutu, który umożliwia kontrolowanie sposobu wywoływania żądań HTTP GET do operacji usługi i określanie formatu wysyłanych wiadomości.  
  
 Podobnie jak każda usługa WCF, źródła danych syndykacji mogą być hostowane samodzielnie w dowolnej aplikacji zarządzanej. Usługi syndykacji wymagają określonego <xref:System.ServiceModel.WebHttpBinding>powiązania () i określonego <xref:System.ServiceModel.Description.WebHttpBehavior>zachowania punktu końcowego () do poprawnego działania. Nowa <xref:System.ServiceModel.Web.WebServiceHost> klasa zapewnia wygodny interfejs API do tworzenia takich punktów końcowych bez określonej konfiguracji.  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Alternatywnie można użyć <xref:System.ServiceModel.Activation.WebServiceHostFactory> z poziomu pliku .svc hostowanego przez iIS, aby zapewnić równoważne funkcje (ta technika nie jest pokazana w tym przykładowym kodzie).  
  
```xml
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 Ponieważ ta usługa odbiera żądania przy użyciu standardowego protokołu HTTP GET, można użyć dowolnego klienta obsługującego protokół RSS lub ATOM, aby uzyskać dostęp do usługi. Na przykład można wyświetlić dane wyjściowe tej `http://localhost:8000/diagnostics/feed/?format=atom` `http://localhost:8000/diagnostics/feed/?format=rss` usługi, przechodząc do lub w przeglądarce obsługującej RSS.
  
 Można również użyć [Jak WCF Syndication Object Model Mapy atom i RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) do odczytu danych zesmażonych i przetwarzania przy użyciu kodu imperatywu.  
  
```csharp
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",
    new XmlReaderSettings()
    {
        //MaxCharactersInDocument can be used to control the maximum amount of data
        //read from the reader and helps prevent OutOfMemoryException
        MaxCharactersInDocument = 1024 * 64
    } );

SyndicationFeed feed = SyndicationFeed.Load(reader);

foreach (SyndicationItem i in feed.Items)
{
    XmlSyndicationContent content = i.Content as XmlSyndicationContent;
    ProcessData pd = content.ReadContent<ProcessData>();

    Console.WriteLine(i.Title.Text);
    Console.WriteLine(pd.ToString());
}
```
  
## <a name="set-up-build-and-run-the-sample"></a>Konfigurowanie, tworzenie i uruchamianie próbki
  
1. Upewnij się, że masz prawo do rejestracji adresów HTTP i HTTPS na komputerze, jak wyjaśniono w instrukcjach konfiguracji w [procedurze jednorazowej konfiguracji dla przykładów programu Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Skompiluj rozwiązanie.

3. Uruchom aplikację konsolową.

4. Gdy aplikacja konsoli jest uruchomiona, przejdź do `http://localhost:8000/diagnostics/feed/?format=atom` przeglądarki obsługującej rss lub `http://localhost:8000/diagnostics/feed/?format=rss` za pomocą niej.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a>Zobacz też

- [Model programowania protokołu HTTP sieci Web w programie WCF](../feature-details/wcf-web-http-programming-model.md)
- [Syndykacja programu WCF](../feature-details/wcf-syndication.md)
