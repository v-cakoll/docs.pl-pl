---
title: Formatowanie HTTP sieci Web w programie WCF
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: 011ff4f2e667268fac1aa2d82c0a2c4ffefc8dde
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585561"
---
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="2bc84-102">Formatowanie HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="2bc84-102">WCF Web HTTP formatting</span></span>
<span data-ttu-id="2bc84-103">Model programowania HTTP sieci Web w programie WCF umożliwia dynamiczne określenie najlepszego formatu dla operacji usługi w celu zwrócenia odpowiedzi w programie.</span><span class="sxs-lookup"><span data-stu-id="2bc84-103">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="2bc84-104">Obsługiwane są dwie metody określania odpowiedniego formatu: automatyczne i jawne.</span><span class="sxs-lookup"><span data-stu-id="2bc84-104">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="2bc84-105">Automatyczne formatowanie</span><span class="sxs-lookup"><span data-stu-id="2bc84-105">Automatic formatting</span></span>  
 <span data-ttu-id="2bc84-106">Po włączeniu automatyczne formatowanie wybiera najlepszy format, w którym ma zostać zwrócona odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="2bc84-106">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="2bc84-107">Określa najlepszy format, sprawdzając następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="2bc84-107">It determines the best format by checking the following, in order:</span></span>  
  
1. <span data-ttu-id="2bc84-108">Typy nośników w nagłówku akceptowania komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="2bc84-108">The media types in the request message’s Accept header.</span></span>  
  
2. <span data-ttu-id="2bc84-109">Typ zawartości komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="2bc84-109">The content-type of the request message.</span></span>  
  
3. <span data-ttu-id="2bc84-110">Domyślne ustawienie formatu w operacji.</span><span class="sxs-lookup"><span data-stu-id="2bc84-110">The default format setting in the operation.</span></span>  
  
4. <span data-ttu-id="2bc84-111">Ustawienie domyślnego formatu w WebHttpBehavior.</span><span class="sxs-lookup"><span data-stu-id="2bc84-111">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="2bc84-112">Jeśli komunikat żądania zawiera nagłówek Accept, infrastruktura Windows Communication Foundation (WCF) wyszukuje typ, który obsługuje.</span><span class="sxs-lookup"><span data-stu-id="2bc84-112">If the request message contains an Accept header the Windows Communication Foundation (WCF) infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="2bc84-113">Jeśli `Accept` nagłówek określa priorytety dla typów nośników, są one honorowane.</span><span class="sxs-lookup"><span data-stu-id="2bc84-113">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="2bc84-114">Jeśli w nagłówku nie zostanie znaleziony odpowiedni format `Accept` , zostanie użyty typ zawartości komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="2bc84-114">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="2bc84-115">Jeśli nie określono odpowiedniego typu zawartości, używane jest domyślne ustawienie formatu dla operacji.</span><span class="sxs-lookup"><span data-stu-id="2bc84-115">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="2bc84-116">Domyślny format jest ustawiany z `ResponseFormat` parametrem <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="2bc84-116">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="2bc84-117">Jeśli w operacji nie określono formatu domyślnego, <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> zostanie użyta wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="2bc84-117">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="2bc84-118">Automatyczne formatowanie opiera się na <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2bc84-118">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="2bc84-119">Jeśli ta właściwość jest ustawiona na `true` , Infrastruktura WCF określa najlepszy format do użycia.</span><span class="sxs-lookup"><span data-stu-id="2bc84-119">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="2bc84-120">Automatyczne wybieranie formatu jest domyślnie wyłączone w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="2bc84-120">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="2bc84-121">Automatyczne wybieranie formatu można włączyć programowo lub za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2bc84-121">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="2bc84-122">Poniższy przykład pokazuje, jak włączyć automatyczne Wybieranie formatu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2bc84-122">The following example shows how to enable automatic format selection in code.</span></span>  
  
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
  
 <span data-ttu-id="2bc84-123">Automatyczne formatowanie można również włączyć przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2bc84-123">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="2bc84-124">Właściwość można ustawić <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> bezpośrednio na <xref:System.ServiceModel.Description.WebHttpBehavior> lub przy użyciu <xref:System.ServiceModel.Description.WebHttpEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="2bc84-124">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="2bc84-125">Poniższy przykład pokazuje, jak włączyć automatyczne Wybieranie formatu na <xref:System.ServiceModel.Description.WebHttpBehavior> .</span><span class="sxs-lookup"><span data-stu-id="2bc84-125">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
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
  
 <span data-ttu-id="2bc84-126">Poniższy przykład pokazuje, jak włączyć automatyczne Wybieranie formatu przy użyciu <xref:System.ServiceModel.Description.WebHttpEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="2bc84-126">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
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
  
## <a name="explicit-formatting"></a><span data-ttu-id="2bc84-127">Jawne formatowanie</span><span class="sxs-lookup"><span data-stu-id="2bc84-127">Explicit formatting</span></span>  
 <span data-ttu-id="2bc84-128">Jak nazywa się, w przypadku jawnego formatowania deweloper określa najlepszy format do użycia w kodzie operacji.</span><span class="sxs-lookup"><span data-stu-id="2bc84-128">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="2bc84-129">Jeśli najlepszym formatem jest XML lub JSON, deweloper ustawia <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> jedną <xref:System.ServiceModel.Web.WebMessageFormat.Xml> lub <xref:System.ServiceModel.Web.WebMessageFormat.Json> .</span><span class="sxs-lookup"><span data-stu-id="2bc84-129">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="2bc84-130">Jeśli <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> Właściwość nie jest jawnie ustawiona, zostanie użyty domyślny format operacji.</span><span class="sxs-lookup"><span data-stu-id="2bc84-130">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="2bc84-131">Poniższy przykład sprawdza, czy format ciągu zapytania ma być używany.</span><span class="sxs-lookup"><span data-stu-id="2bc84-131">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="2bc84-132">Jeśli została określona, ustawia format operacji przy użyciu <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> .</span><span class="sxs-lookup"><span data-stu-id="2bc84-132">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
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
  
 <span data-ttu-id="2bc84-133">Jeśli musisz obsługiwać formaty inne niż XML lub JSON, Zdefiniuj dla operacji typ zwracany <xref:System.ServiceModel.Channels.Message> .</span><span class="sxs-lookup"><span data-stu-id="2bc84-133">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="2bc84-134">W kodzie operacji określ odpowiedni format, który ma być używany, a następnie Utwórz <xref:System.ServiceModel.Channels.Message> Obiekt przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="2bc84-134">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="2bc84-135">Każda z tych metod pobiera zawartość i tworzy komunikat z odpowiednim formatem.</span><span class="sxs-lookup"><span data-stu-id="2bc84-135">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="2bc84-136">`WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements`Metoda może służyć do uzyskania listy formatów preferowanych przez klienta w kolejności zmniejszania preferencji.</span><span class="sxs-lookup"><span data-stu-id="2bc84-136">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="2bc84-137">Poniższy przykład pokazuje, jak użyć, `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` Aby określić format do użycia, a następnie używa odpowiedniej metody tworzenia odpowiedzi w celu utworzenia komunikatu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2bc84-137">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2bc84-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bc84-138">See also</span></span>

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [<span data-ttu-id="2bc84-139">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="2bc84-139">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="2bc84-140">Klasy UriTemplate i UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="2bc84-140">UriTemplate and UriTemplateTable</span></span>](uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="2bc84-141">Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="2bc84-141">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="2bc84-142">Model obiektowy programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="2bc84-142">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
