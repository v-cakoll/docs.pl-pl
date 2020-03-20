---
title: Formatowanie HTTP w sieci Web WCF
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: b6c9728fe40e26977366b73337e72b1514a12a19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184198"
---
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="4e9ea-102">Formatowanie HTTP w sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="4e9ea-102">WCF Web HTTP formatting</span></span>
<span data-ttu-id="4e9ea-103">Model programowania HTTP w sieci Web WCF umożliwia dynamiczne określenie najlepszego formatu operacji usługi w celu zwrócenia odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-103">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="4e9ea-104">Obsługiwane są dwie metody określania odpowiedniego formatu: automatyczne i jawne.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-104">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="4e9ea-105">Automatyczne formatowanie</span><span class="sxs-lookup"><span data-stu-id="4e9ea-105">Automatic formatting</span></span>  
 <span data-ttu-id="4e9ea-106">Po włączeniu automatyczne formatowanie wybiera najlepszy format, w którym ma być zwracana odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-106">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="4e9ea-107">Określa najlepszy format, sprawdzając następujące, w kolejności:</span><span class="sxs-lookup"><span data-stu-id="4e9ea-107">It determines the best format by checking the following, in order:</span></span>  
  
1. <span data-ttu-id="4e9ea-108">Typy nośników w nagłówku Akceptuj komunikat żądania.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-108">The media types in the request message’s Accept header.</span></span>  
  
2. <span data-ttu-id="4e9ea-109">Typ zawartości komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-109">The content-type of the request message.</span></span>  
  
3. <span data-ttu-id="4e9ea-110">Domyślne ustawienie formatu w operacji.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-110">The default format setting in the operation.</span></span>  
  
4. <span data-ttu-id="4e9ea-111">Domyślne ustawienie formatu w programie WebHttpBehavior.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-111">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="4e9ea-112">Jeśli komunikat żądania zawiera nagłówek Akceptuj, infrastruktura Programu Windows Communication Foundation (WCF) wyszukuje typ, który obsługuje.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-112">If the request message contains an Accept header the Windows Communication Foundation (WCF) infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="4e9ea-113">Jeśli `Accept` nagłówek określa priorytety dla swoich typów nośników, są one honorowane.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-113">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="4e9ea-114">Jeśli w nagłówku `Accept` nie zostanie znaleziony odpowiedni format, używany jest typ zawartości komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-114">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="4e9ea-115">Jeśli nie określono odpowiedniego typu zawartości, używane jest domyślne ustawienie formatu operacji.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-115">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="4e9ea-116">Domyślny format jest `ResponseFormat` ustawiany <xref:System.ServiceModel.Web.WebGetAttribute> z <xref:System.ServiceModel.Web.WebInvokeAttribute> parametrem i atrybutami.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-116">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="4e9ea-117">Jeśli w operacji nie określono formatu domyślnego, używana jest wartość <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-117">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="4e9ea-118">Automatyczne formatowanie zależy <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> od właściwości.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-118">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="4e9ea-119">Gdy ta właściwość `true`jest ustawiona na , WCF infrastruktury określa najlepszy format do użycia.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-119">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="4e9ea-120">Automatyczne zaznaczanie formatu jest domyślnie wyłączone ze zgodnych z przeszywem.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-120">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="4e9ea-121">Automatyczny wybór formatu można włączyć programowo lub za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-121">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="4e9ea-122">W poniższym przykładzie pokazano, jak włączyć automatyczne zaznaczanie formatu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-122">The following example shows how to enable automatic format selection in code.</span></span>  
  
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
  
 <span data-ttu-id="4e9ea-123">Automatyczne formatowanie można również włączyć za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-123">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="4e9ea-124">Właściwość <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> można ustawić bezpośrednio <xref:System.ServiceModel.Description.WebHttpBehavior> na stronie <xref:System.ServiceModel.Description.WebHttpEndpoint>lub za pomocą pliku .</span><span class="sxs-lookup"><span data-stu-id="4e9ea-124">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="4e9ea-125">W poniższym przykładzie pokazano, jak <xref:System.ServiceModel.Description.WebHttpBehavior>włączyć automatyczne zaznaczanie formatu w pliku .</span><span class="sxs-lookup"><span data-stu-id="4e9ea-125">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
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
  
 <span data-ttu-id="4e9ea-126">W poniższym przykładzie pokazano, <xref:System.ServiceModel.Description.WebHttpEndpoint>jak włączyć automatyczne zaznaczanie formatu za pomocą programu .</span><span class="sxs-lookup"><span data-stu-id="4e9ea-126">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
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
  
## <a name="explicit-formatting"></a><span data-ttu-id="4e9ea-127">Jawne formatowanie</span><span class="sxs-lookup"><span data-stu-id="4e9ea-127">Explicit formatting</span></span>  
 <span data-ttu-id="4e9ea-128">Jak sama nazwa wskazuje, w jawnym formatowaniu deweloper określa najlepszy format do użycia w kodzie operacji.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-128">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="4e9ea-129">Jeśli najlepszym formatem jest XML lub <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> JSON, deweloper ustawia na jeden <xref:System.ServiceModel.Web.WebMessageFormat.Xml> lub <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-129">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="4e9ea-130">Jeśli <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> właściwość nie jest jawnie ustawiona, używany jest domyślny format operacji.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-130">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="4e9ea-131">Poniższy przykład sprawdza parametr ciągu kwerendy formatu dla formatu do użycia.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-131">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="4e9ea-132">Jeśli został określony, ustawia format operacji za <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>pomocą .</span><span class="sxs-lookup"><span data-stu-id="4e9ea-132">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
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
  
 <span data-ttu-id="4e9ea-133">Jeśli chcesz obsługiwać formaty inne niż XML lub JSON, zdefiniuj operację, aby mieć typ zwracany <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-133">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="4e9ea-134">W kodzie operacji określ odpowiedni format do <xref:System.ServiceModel.Channels.Message> użycia, a następnie utwórz obiekt przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="4e9ea-134">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="4e9ea-135">Każda z tych metod pobiera zawartość i tworzy komunikat o odpowiednim formacie.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-135">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="4e9ea-136">Metoda `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` ta może służyć do uzyskania listy formatów preferowanych przez klienta w kolejności malejącej preferencji.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-136">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="4e9ea-137">W poniższym przykładzie `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` pokazano, jak użyć do określenia formatu do użycia, a następnie używa odpowiedniej metody tworzenia odpowiedzi do utworzenia komunikatu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="4e9ea-137">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4e9ea-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e9ea-138">See also</span></span>

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [<span data-ttu-id="4e9ea-139">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="4e9ea-139">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="4e9ea-140">Klasy UriTemplate i UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="4e9ea-140">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="4e9ea-141">Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="4e9ea-141">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="4e9ea-142">Model obiektowy programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="4e9ea-142">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
