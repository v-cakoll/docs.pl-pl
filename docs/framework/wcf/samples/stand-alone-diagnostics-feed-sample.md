---
title: "Przykład autonomicznego kanału diagnostycznego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c95a2e1e1790633df77e7c4ecd6603e68321e478
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Przykład autonomicznego kanału diagnostycznego
Ten przykład przedstawia sposób tworzenia źródła danych dla zespolonego z RSS/Atom [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Jest podstawowy program "Hello World", który zawiera podstawowe informacje o modelu obiektów oraz jak je skonfigurować na [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]modele zespolonego źródła danych jako operacji usługi, które zwracają specjalnego typu danych, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Wystąpienia <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> może serializować źródło danych do formatów RSS 2.0 i Atom 1.0. Następujący przykładowy kod przedstawia kontraktu używane.  
  
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
  
 `GetProcesses` Operacji jest oznaczony za pomocą <xref:System.ServiceModel.Web.WebGetAttribute> atrybut, który umożliwia kontrolowanie sposobu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wywołuje żądania HTTP GET do usługi operations i określić format wysyłanych wiadomości.  
  
 Takie jak dowolne [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, zespolonego źródła danych mogą być samodzielnie hostowana w dowolnej aplikacji zarządzanych. Syndykacja usługi wymagają określonego powiązania ( <xref:System.ServiceModel.WebHttpBinding>) i zachowanie określonego punktu końcowego ( <xref:System.ServiceModel.Description.WebHttpBehavior>) do poprawnego działania. Nowe <xref:System.ServiceModel.Web.WebServiceHost> klasy oferuje wygodny interfejs API do tworzenia tych punktów końcowych bez określonej konfiguracji.  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Alternatywnie można użyć <xref:System.ServiceModel.Activation.WebServiceHostFactory> od w pliku svc hostowanych przez usługi IIS, aby zapewnić równoważne funkcje (Ta metoda nie jest prezentowana w tym przykładowym kodzie).  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 Ponieważ ta usługa odbiera żądania przy użyciu standardowych HTTP GET, można użyć dowolnego źródła danych RSS lub obsługujący ATOM klienta do uzyskania dostępu do usługi. Na przykład możesz wyświetlić dane wyjściowe tej usługi przechodząc do kanał-http://localhost: 8000/diagnostyczny /? format = atom lub kanał-http://localhost: 8000/diagnostyczny /? format = rss obsługujących funkcję RSS przeglądarki, takich jak program Internet Explorer 7.  
  
 Można również użyć [jak WCF zespolonego obiektu modelu mapy Atom i RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) do odczytywania danych zespolonej i przetwarzanie za pomocą kodu nadrzędnych.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, czy masz uprawnienie rejestracji właściwym adresem protokołu HTTP i HTTPS na komputerze, zgodnie z objaśnieniem w konfiguracji instrukcje w [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Skompiluj rozwiązanie.  
  
3.  Uruchom aplikację konsolową.  
  
4.  Po uruchomieniu aplikacji konsoli przejdź do http://localhost: 8000/Diagnostyka/kanału informacyjnego /? format = atom lub kanał-http://localhost: 8000/diagnostyczny /? format = rss za pomocą przeglądarki obsługującej funkcję RSS.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a>Zobacz też  
 [Model programowania protokołu HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Syndykacja programu WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
