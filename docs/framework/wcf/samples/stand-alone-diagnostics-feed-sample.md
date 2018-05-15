---
title: Przykład autonomicznego kanału diagnostycznego
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 730cf011208ea1b57929fff4a1953fd3a935335c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="55be3-102">Przykład autonomicznego kanału diagnostycznego</span><span class="sxs-lookup"><span data-stu-id="55be3-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="55be3-103">Ten przykład przedstawia sposób tworzenia RSS/źródło danych Atom dla zespolonego z usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="55be3-103">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="55be3-104">Jest podstawowe program "Hello World", który zawiera podstawowe informacje o modelu obiektów oraz sposobu konfigurowania usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="55be3-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="55be3-105">Usługi WCF modeli zespolonego źródła danych operacji usługi, które zwracają specjalnego typu danych, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="55be3-105">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="55be3-106">Wystąpienia <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> może serializować źródło danych do formatów RSS 2.0 i Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="55be3-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="55be3-107">Następujący przykładowy kod przedstawia kontraktu używane.</span><span class="sxs-lookup"><span data-stu-id="55be3-107">The following sample code shows the contract used.</span></span>  
  
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
  
 <span data-ttu-id="55be3-108">`GetProcesses` Operacji jest oznaczony za pomocą <xref:System.ServiceModel.Web.WebGetAttribute> atrybut, który umożliwia kontrolowanie sposobu WCF wywołuje HTTP GET żądania do usługi operations i określić format wysyłanych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="55be3-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="55be3-109">Podobnie jak żadnej usługi WCF zespolonego źródła danych mogą być samodzielnie hostowana w dowolnej aplikacji zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="55be3-109">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="55be3-110">Syndykacja usługi wymagają określonego powiązania ( <xref:System.ServiceModel.WebHttpBinding>) i zachowanie określonego punktu końcowego ( <xref:System.ServiceModel.Description.WebHttpBehavior>) do poprawnego działania.</span><span class="sxs-lookup"><span data-stu-id="55be3-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="55be3-111">Nowe <xref:System.ServiceModel.Web.WebServiceHost> klasy oferuje wygodny interfejs API do tworzenia tych punktów końcowych bez określonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="55be3-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="55be3-112">Alternatywnie można użyć <xref:System.ServiceModel.Activation.WebServiceHostFactory> od w pliku svc hostowanych przez usługi IIS, aby zapewnić równoważne funkcje (Ta metoda nie jest prezentowana w tym przykładowym kodzie).</span><span class="sxs-lookup"><span data-stu-id="55be3-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 <span data-ttu-id="55be3-113">Ponieważ ta usługa odbiera żądania przy użyciu standardowych HTTP GET, można użyć dowolnego źródła danych RSS lub obsługujący ATOM klienta do uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="55be3-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="55be3-114">Na przykład można wyświetlić dane wyjściowe tej usługi, przechodząc do http://localhost:8000/diagnostics/feed/?format=atom lub http://localhost:8000/diagnostics/feed/?format=rss obsługujących funkcję RSS przeglądarki, takich jak program Internet Explorer 7.</span><span class="sxs-lookup"><span data-stu-id="55be3-114">For example, you can view the output of this service by navigating to http://localhost:8000/diagnostics/feed/?format=atom or http://localhost:8000/diagnostics/feed/?format=rss in an RSS-aware browser such as Internet Explorer 7.</span></span>  
  
 <span data-ttu-id="55be3-115">Można również użyć [jak WCF zespolonego obiektu modelu mapy Atom i RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) do odczytywania danych zespolonej i przetwarzanie za pomocą kodu nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="55be3-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="55be3-116">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="55be3-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="55be3-117">Upewnij się, czy masz uprawnienie rejestracji właściwym adresem protokołu HTTP i HTTPS na komputerze, zgodnie z objaśnieniem w konfiguracji instrukcje w [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="55be3-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="55be3-118">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="55be3-118">Build the solution.</span></span>  
  
3.  <span data-ttu-id="55be3-119">Uruchom aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="55be3-119">Run the console application.</span></span>  
  
4.  <span data-ttu-id="55be3-120">Po uruchomieniu aplikacji konsoli przejdź do http://localhost:8000/diagnostics/feed/?format=atom lub http://localhost:8000/diagnostics/feed/?format=rss za pomocą przeglądarki obsługującej funkcję RSS.</span><span class="sxs-lookup"><span data-stu-id="55be3-120">While the console application is running, navigate to http://localhost:8000/diagnostics/feed/?format=atom or http://localhost:8000/diagnostics/feed/?format=rss using an RSS-aware browser.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="55be3-121">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="55be3-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="55be3-122">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="55be3-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="55be3-123">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="55be3-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="55be3-124">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="55be3-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a><span data-ttu-id="55be3-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55be3-125">See Also</span></span>  
 [<span data-ttu-id="55be3-126">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="55be3-126">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="55be3-127">Syndykacja programu WCF</span><span class="sxs-lookup"><span data-stu-id="55be3-127">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
