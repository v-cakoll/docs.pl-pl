---
title: Formatowanie kodu HTTP dla sieci Web WCF
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: 37f0506822ca03aed3755ad42f9bf7ecdc962da7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094453"
---
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="63515-102">Formatowanie kodu HTTP dla sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="63515-102">WCF Web HTTP formatting</span></span>
<span data-ttu-id="63515-103">Model programowania protokołu HTTP sieci Web WCF umożliwia dynamiczne określanie najlepszy format dla operacji usługi do zwrócenia w odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="63515-103">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="63515-104">Obsługiwane są dwie metody, określając odpowiedni format: automatyczne i jawne.</span><span class="sxs-lookup"><span data-stu-id="63515-104">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="63515-105">Formatowanie automatyczne</span><span class="sxs-lookup"><span data-stu-id="63515-105">Automatic formatting</span></span>  
 <span data-ttu-id="63515-106">Po włączeniu automatycznego formatowania wybiera najlepszy format, w której ma zostać zwrócone w odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="63515-106">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="63515-107">Określa najlepszy format, sprawdzając poniższe czynności:</span><span class="sxs-lookup"><span data-stu-id="63515-107">It determines the best format by checking the following, in order:</span></span>  
  
1.  <span data-ttu-id="63515-108">Do typów nośników w nagłówku Accept komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="63515-108">The media types in the request message’s Accept header.</span></span>  
  
2.  <span data-ttu-id="63515-109">Typ zawartości komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="63515-109">The content-type of the request message.</span></span>  
  
3.  <span data-ttu-id="63515-110">Domyślny format ustawienie w operacji.</span><span class="sxs-lookup"><span data-stu-id="63515-110">The default format setting in the operation.</span></span>  
  
4.  <span data-ttu-id="63515-111">Domyślny format w WebHttpBehavior.</span><span class="sxs-lookup"><span data-stu-id="63515-111">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="63515-112">Wiadomość dotycząca żądania zawiera nagłówek Accept infrastruktury usług Windows Communication Foundation (WCF) wyszukuje typ, który ją obsługuje.</span><span class="sxs-lookup"><span data-stu-id="63515-112">If the request message contains an Accept header the Windows Communication Foundation (WCF) infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="63515-113">Jeśli `Accept` nagłówek określa priorytety dla jego typów nośników, są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="63515-113">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="63515-114">Jeśli nie formatu odpowiedniego znajduje się w `Accept` nagłówka typu zawartości komunikatu żądania jest używana.</span><span class="sxs-lookup"><span data-stu-id="63515-114">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="63515-115">Jeśli nie odpowiednie content-type jest określona, jest używany domyślny format ustawienie dla tej operacji.</span><span class="sxs-lookup"><span data-stu-id="63515-115">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="63515-116">Domyślny format została ustawiona za pomocą `ResponseFormat` parametru <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="63515-116">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="63515-117">Jeśli nie domyślny format jest określona w operacji, wartość <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> właściwość jest używana.</span><span class="sxs-lookup"><span data-stu-id="63515-117">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="63515-118">Automatyczne formatowanie opiera się na <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="63515-118">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="63515-119">Jeśli ta właściwość jest równa `true`, infrastruktura WCF Określa format najlepszy do użycia.</span><span class="sxs-lookup"><span data-stu-id="63515-119">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="63515-120">Automatyczne wybieranie formatu jest domyślnie wyłączona dla zapewnienia zgodności.</span><span class="sxs-lookup"><span data-stu-id="63515-120">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="63515-121">Można włączyć automatyczne wybieranie formatu programowo lub za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63515-121">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="63515-122">Poniższy przykład pokazuje, jak włączyć automatyczne wybieranie formatu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="63515-122">The following example shows how to enable automatic format selection in code.</span></span>  
  
```csharp
// This code assumes the service name is MyService and the service contract is IMyContract     
Uri baseAddress = new Uri("http://localhost:8000");  
  
WebServiceHost host = new WebServiceHost(typeof(MyService), baseAddress)  
try  
{  
   ServiceEndpoint sep = host.AddServiceEndpoint(typeof(IMyContract), new WebHttpBinding(), "");  
   // Check it see if the WebHttpBehavior already exists  
   WebHttpBehavior whb = sep.Behaviors.Find<WebHttpBehavior>();  
  
   if (whb != null)  
   {  
      whb.AutomaticFormatSelectionEnabled = true;  
   }  
   else  
   {  
      WebHttpBehavior webBehavior = new WebHttpBehavior();  
      webBehavior.AutomaticFormatSelectionEnabled = true;  
      sep.Behaviors.Add(webBehavior);  
   }  
         // Open host to start listening for messages  
   host.Open();        
  
  // ...  
}  
  catch(CommunicationException ex)  
  {  
     Console.WriteLine("An exception occurred: " + ex.Message());  
  }  
```  
  
 <span data-ttu-id="63515-123">Automatyczne formatowanie można również włączyć za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63515-123">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="63515-124">Możesz ustawić <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> bezpośrednio na właściwość <xref:System.ServiceModel.Description.WebHttpBehavior> lub za pomocą <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="63515-124">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="63515-125">Poniższy przykład pokazuje, jak włączyć automatyczne wybieranie formatu <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="63515-125">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <endpointBehaviors>  
      <behavior>  
        <webHttp automaticFormatSelectionEnabled="true" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
      <standardEndpoint name="" helpEnabled="true" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="63515-126">Poniższy przykład pokazuje, jak włączyć automatyczne formatowanie zaznaczenie przy użyciu <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="63515-126">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
      <webHttpEndpoint>  
        <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
        <standardEndpoint name="" helpEnabled="true" automaticFormatSelectionEnabled="true"  />  
      </webHttpEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```  
  
## <a name="explicit-formatting"></a><span data-ttu-id="63515-127">Jawne, formatowanie</span><span class="sxs-lookup"><span data-stu-id="63515-127">Explicit formatting</span></span>  
 <span data-ttu-id="63515-128">Jak wskazuje nazwa, Deweloper w formatowaniu jawne Określa format najlepszy do użycia w kodzie operacji.</span><span class="sxs-lookup"><span data-stu-id="63515-128">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="63515-129">W przypadku najlepszym formacie XML lub JSON Deweloper ustawia <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> do jednej <xref:System.ServiceModel.Web.WebMessageFormat.Xml> lub <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="63515-129">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="63515-130">Jeśli <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> właściwość nie została jawnie ustawiona, a następnie jest używany format domyślny wykonać operację.</span><span class="sxs-lookup"><span data-stu-id="63515-130">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="63515-131">Poniższy przykład sprawdza, czy format parametru ciągu zapytania dla formatu do użycia.</span><span class="sxs-lookup"><span data-stu-id="63515-131">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="63515-132">Jeśli została określona, ustawia operacji formatowania, przy użyciu <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span><span class="sxs-lookup"><span data-stu-id="63515-132">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
```csharp
public class Service : IService  
{  
    [WebGet]  
     public string EchoWithGet(string s)  
    {  
        // if a format query string parameter has been specified, set the response format to that. If no such
        // query string parameter exists the Accept header will be used
        string formatQueryStringValue = WebOperationContext.Current.IncomingRequest.UriTemplateMatch.QueryParameters["format"];  
        if (!string.IsNullOrEmpty(formatQueryStringValue))  
        {  
            if (formatQueryStringValue.Equals("xml", System.StringComparison.OrdinalIgnoreCase))  
            {
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Xml;
            }
            else if (formatQueryStringValue.Equals("json", System.StringComparison.OrdinalIgnoreCase))  
            {  
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Json;  
            }  
            else  
            {  
                throw new WebFaultException<string>($"Unsupported format '{formatQueryStringValue}'",   HttpStatusCode.BadRequest);
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 <span data-ttu-id="63515-133">Jeśli potrzebujesz do obsługi formatów innych niż JSON lub XML, zdefiniuj operacji ma typ zwracany <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="63515-133">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="63515-134">W kodzie operacji ustala odpowiedni format można użyć, a następnie utwórz <xref:System.ServiceModel.Channels.Message> obiektu przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="63515-134">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
-   `WebOperationContext.CreateAtom10Response`  
  
-   `WebOperationContext.CreateJsonResponse`  
  
-   `WebOperationContext.CreateStreamResponse`  
  
-   `WebOperationContext.CreateTextResponse`  
  
-   `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="63515-135">Każda z tych metod przyjmuje zawartości i tworzy komunikat z odpowiednim formacie.</span><span class="sxs-lookup"><span data-stu-id="63515-135">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="63515-136">`WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` Metoda może służyć do uzyskania listy formatów preferowane przez klienta w kolejności malejących preferencji.</span><span class="sxs-lookup"><span data-stu-id="63515-136">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="63515-137">Poniższy przykład pokazuje, jak używać `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` do określenia formatu do użycia, a następnie używa odpowiednie utworzyć metodę odpowiedzi w celu utworzenia komunikatu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="63515-137">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
```csharp
public class Service : IService  
{  
    public Message EchoListWithGet(string list)  
    {  
        List<string> returnList = new List<string>(list.Split(new char[] { ',' }, StringSplitOptions.RemoveEmptyEntries));  
        IList<ContentType> acceptHeaderElements = WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements();  
        for (int x = 0; x < acceptHeaderElements.Count; x++)  
        {  
            string normalizedMediaType = acceptHeaderElements[x].MediaType.ToLowerInvariant();  
            switch (normalizedMediaType)  
            {  
                case "image/jpeg": return CreateJpegResponse(returnList);  
                case "application/xhtml+xml": return CreateXhtmlResponse(returnList);  
                case "application/atom+xml": return CreateAtom10Response(returnList);  
                case "application/xml": return CreateXmlResponse(returnList);  
                case "application/json": return CreateJsonResponse(returnList);  
          }  
    }  
  
    // Default response format is XML  
    return CreateXmlResponse(returnList);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="63515-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63515-138">See also</span></span>

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [<span data-ttu-id="63515-139">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="63515-139">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="63515-140">Klasy UriTemplate i UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="63515-140">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="63515-141">Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="63515-141">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="63515-142">Model obiektowy programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="63515-142">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
