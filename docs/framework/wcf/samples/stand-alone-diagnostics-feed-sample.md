---
title: Przykład autonomicznego kanału diagnostycznego
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 4520883b5db19c28544a5576ca600b83e37eede3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787928"
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="43d03-102">Przykład autonomicznego kanału diagnostycznego</span><span class="sxs-lookup"><span data-stu-id="43d03-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="43d03-103">Ten przykład pokazuje, jak utworzyć kanał informacyjny RSS/Atom dla zespalania z Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="43d03-103">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="43d03-104">Jest to podstawowy program "Hello world", który zawiera podstawowe informacje dotyczące modelu obiektów i sposobu konfigurowania go w usłudze Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="43d03-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="43d03-105">Model WCF tworzy źródła danych zespolonych jako operacje usługi, które zwracają specjalny typ dane, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="43d03-105">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="43d03-106">Wystąpienia <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> mogą serializować źródła danych do formatów RSS 2,0 i Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="43d03-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="43d03-107">Następujący przykładowy kod przedstawia użyty kontrakt.</span><span class="sxs-lookup"><span data-stu-id="43d03-107">The following sample code shows the contract used.</span></span>  
  
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
  
 <span data-ttu-id="43d03-108">`GetProcesses` operacji jest adnotacja z atrybutem <xref:System.ServiceModel.Web.WebGetAttribute>, który umożliwia kontrolowanie sposobu, w jaki program WCF wysyła żądania HTTP GET do operacji usługi i określa format wysyłanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="43d03-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="43d03-109">Podobnie jak w przypadku dowolnej usługi WCF, zespolone źródła danych mogą być obsługiwane przez dowolną aplikację zarządzaną.</span><span class="sxs-lookup"><span data-stu-id="43d03-109">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="43d03-110">Usługi zespolone wymagają określonego powiązania (<xref:System.ServiceModel.WebHttpBinding>) i określonego zachowania punktu końcowego (<xref:System.ServiceModel.Description.WebHttpBehavior>) do poprawnego działania.</span><span class="sxs-lookup"><span data-stu-id="43d03-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="43d03-111">Nowa Klasa <xref:System.ServiceModel.Web.WebServiceHost> zapewnia wygodny interfejs API do tworzenia punktów końcowych bez określonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="43d03-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="43d03-112">Alternatywnie można użyć <xref:System.ServiceModel.Activation.WebServiceHostFactory> z poziomu pliku SVC hostowanego przez usługi IIS w celu zapewnienia równoważnej funkcjonalności (Ta technika nie jest przedstawiona w tym przykładowym kodzie).</span><span class="sxs-lookup"><span data-stu-id="43d03-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```xml
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 <span data-ttu-id="43d03-113">Ponieważ ta usługa odbiera żądania przy użyciu standardowego protokołu HTTP GET, do uzyskiwania dostępu do usługi można użyć dowolnego klienta obsługującego technologię RSS lub ATOM.</span><span class="sxs-lookup"><span data-stu-id="43d03-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="43d03-114">Na przykład możesz wyświetlić dane wyjściowe tej usługi, przechodząc do `http://localhost:8000/diagnostics/feed/?format=atom` lub `http://localhost:8000/diagnostics/feed/?format=rss` w przeglądarce obsługującej funkcję RSS.</span><span class="sxs-lookup"><span data-stu-id="43d03-114">For example, you can view the output of this service by navigating to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` in an RSS-aware browser.</span></span>
  
 <span data-ttu-id="43d03-115">Możesz również użyć [modelu obiektów zespolonych WCF, który jest mapowany na Atom i RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) , aby odczytywać dane zespolone i przetwarzać je za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="43d03-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
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
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="43d03-116">Konfigurowanie, kompilowanie i uruchamianie przykładu</span><span class="sxs-lookup"><span data-stu-id="43d03-116">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="43d03-117">Upewnij się, że masz odpowiednie uprawnienia do rejestracji adresów dla protokołów HTTP i HTTPS na komputerze, zgodnie z opisem w temacie Konfigurowanie instrukcji w jednorazowej [procedurze konfiguracyjnej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43d03-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="43d03-118">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="43d03-118">Build the solution.</span></span>

3. <span data-ttu-id="43d03-119">Uruchom aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="43d03-119">Run the console application.</span></span>

4. <span data-ttu-id="43d03-120">Gdy aplikacja konsolowa jest uruchomiona, przejdź do `http://localhost:8000/diagnostics/feed/?format=atom` lub `http://localhost:8000/diagnostics/feed/?format=rss` przy użyciu przeglądarki obsługującej funkcję RSS.</span><span class="sxs-lookup"><span data-stu-id="43d03-120">While the console application is running, navigate to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` using an RSS-aware browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43d03-121">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="43d03-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="43d03-122">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="43d03-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="43d03-123">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="43d03-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43d03-124">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="43d03-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a><span data-ttu-id="43d03-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43d03-125">See also</span></span>

- [<span data-ttu-id="43d03-126">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="43d03-126">WCF Web HTTP Programming Model</span></span>](../feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="43d03-127">Syndykacja programu WCF</span><span class="sxs-lookup"><span data-stu-id="43d03-127">WCF Syndication</span></span>](../feature-details/wcf-syndication.md)
