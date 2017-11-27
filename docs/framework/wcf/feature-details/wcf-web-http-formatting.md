---
title: Formatowanie kodu HTTP sieci Web WCF
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3a41c6c7304234535993d83329c4faa464218e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="1e078-102">Formatowanie kodu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="1e078-102">WCF Web HTTP formatting</span></span>
<span data-ttu-id="1e078-103">Model programowania protokołu HTTP sieci Web WCF umożliwia dynamiczne określanie format najlepszy dla operacji usługi zwrócić w odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1e078-103">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="1e078-104">Obsługiwane są dwie metody, określając odpowiedni format: jawne i automatyczne.</span><span class="sxs-lookup"><span data-stu-id="1e078-104">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="1e078-105">Automatyczne formatowanie</span><span class="sxs-lookup"><span data-stu-id="1e078-105">Automatic formatting</span></span>  
 <span data-ttu-id="1e078-106">Włączenie automatycznego formatowania wybiera format najlepszy do której należy zwrócić w odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1e078-106">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="1e078-107">Określa format najlepszy sprawdzając następujące polecenie, w kolejności:</span><span class="sxs-lookup"><span data-stu-id="1e078-107">It determines the best format by checking the following, in order:</span></span>  
  
1.  <span data-ttu-id="1e078-108">Typy nośnika w nagłówku Accept komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="1e078-108">The media types in the request message’s Accept header.</span></span>  
  
2.  <span data-ttu-id="1e078-109">Typ zawartości komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="1e078-109">The content-type of the request message.</span></span>  
  
3.  <span data-ttu-id="1e078-110">Domyślny format ustawienie w operacji.</span><span class="sxs-lookup"><span data-stu-id="1e078-110">The default format setting in the operation.</span></span>  
  
4.  <span data-ttu-id="1e078-111">Domyślny format w WebHttpBehavior.</span><span class="sxs-lookup"><span data-stu-id="1e078-111">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="1e078-112">Jeśli wiadomość dotycząca żądania zawiera nagłówek Accept [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] infrastruktury wyszukuje typ, który go obsługuje.</span><span class="sxs-lookup"><span data-stu-id="1e078-112">If the request message contains an Accept header the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="1e078-113">Jeśli `Accept` nagłówek określa priorytety dotyczące jego typów nośników znajdują się one go uznać.</span><span class="sxs-lookup"><span data-stu-id="1e078-113">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="1e078-114">W przypadku znalezienia nie odpowiedni format w `Accept` nagłówka content-type komunikatu żądania jest używana.</span><span class="sxs-lookup"><span data-stu-id="1e078-114">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="1e078-115">Jeśli zostanie określony nie odpowiedniego typu zawartości, jest używany domyślny format ustawienie dla tej operacji.</span><span class="sxs-lookup"><span data-stu-id="1e078-115">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="1e078-116">Domyślny format ustawiono `ResponseFormat` parametr <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="1e078-116">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="1e078-117">Jeśli nie domyślny format jest określony w operacji wartość <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> właściwość jest używana.</span><span class="sxs-lookup"><span data-stu-id="1e078-117">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="1e078-118">Automatyczne formatowanie opiera się na <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1e078-118">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="1e078-119">Jeśli ta właściwość jest skonfigurowana `true`, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury Określa format najlepszy do użycia.</span><span class="sxs-lookup"><span data-stu-id="1e078-119">When this property is set to `true`, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure determines the best format to use.</span></span> <span data-ttu-id="1e078-120">Automatyczne wybieranie formatu jest domyślnie wyłączona dla zapewnienia zgodności.</span><span class="sxs-lookup"><span data-stu-id="1e078-120">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="1e078-121">Automatyczne wybieranie formatu można włączyć programowo lub przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1e078-121">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="1e078-122">Poniższy przykład przedstawia sposób włączania automatycznego wyboru formatu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1e078-122">The following example shows how to enable automatic format selection in code.</span></span>  
  
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
  
 <span data-ttu-id="1e078-123">Automatyczne formatowanie można również włączyć za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1e078-123">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="1e078-124">Można ustawić <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> właściwości bezpośrednio na <xref:System.ServiceModel.Description.WebHttpBehavior> lub przy użyciu <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="1e078-124">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="1e078-125">Poniższy przykład przedstawia sposób Włącz automatyczne wybieranie formatu <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="1e078-125">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
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
  
 <span data-ttu-id="1e078-126">Poniższy przykład przedstawia sposób Włącz automatyczne formatowanie zaznaczenia przy użyciu <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="1e078-126">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
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
  
## <a name="explicit-formatting"></a><span data-ttu-id="1e078-127">Jawne formatowania</span><span class="sxs-lookup"><span data-stu-id="1e078-127">Explicit formatting</span></span>  
 <span data-ttu-id="1e078-128">Jak wskazuje nazwę, Deweloper w formatowaniu jawne Określa format najlepszy do użycia z kodem operacji.</span><span class="sxs-lookup"><span data-stu-id="1e078-128">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="1e078-129">W przypadku najlepszym formacie XML lub JSON dewelopera ustawia <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> albo <xref:System.ServiceModel.Web.WebMessageFormat.Xml> lub <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="1e078-129">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="1e078-130">Jeśli <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> właściwość nie jest jawnie ustawiona, a następnie wykonać operację domyślny format jest używany.</span><span class="sxs-lookup"><span data-stu-id="1e078-130">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="1e078-131">Poniższy przykład sprawdza, czy format parametru ciągu zapytania dla formatu do użycia.</span><span class="sxs-lookup"><span data-stu-id="1e078-131">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="1e078-132">Jeśli zostały określone, ustawia operacji sformatować przy użyciu <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span><span class="sxs-lookup"><span data-stu-id="1e078-132">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
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
                 throw new WebFaultException<string>(string.Format("Unsupported format '{0}'", formatQueryStringValue), HttpStatusCode.BadRequest);  
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 <span data-ttu-id="1e078-133">Jeśli zachodzi potrzeba obsługi formatów innych niż XML lub JSON, definiować operacji ma typ zwracany <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="1e078-133">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="1e078-134">W ramach kod operacji ustalić odpowiedni format, a następnie utwórz <xref:System.ServiceModel.Channels.Message> przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="1e078-134">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
-   `WebOperationContext.CreateAtom10Response`  
  
-   `WebOperationContext.CreateJsonResponse`  
  
-   `WebOperationContext.CreateStreamResponse`  
  
-   `WebOperationContext.CreateTextResponse`  
  
-   `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="1e078-135">Każda z tych metod ma zawartości i tworzy komunikat z odpowiednim formatem.</span><span class="sxs-lookup"><span data-stu-id="1e078-135">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="1e078-136">`WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` Metody można użyć w celu uzyskania listy formatów preferowany przez klienta w kolejności malejącej preferencji.</span><span class="sxs-lookup"><span data-stu-id="1e078-136">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="1e078-137">Poniższy przykład przedstawia użycie `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` do określenia formatu do użycia, a następnie używa odpowiednie Utwórz metodę odpowiedzi w celu utworzenia komunikatu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1e078-137">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1e078-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e078-138">See also</span></span>  
 <xref:System.UriTemplate>  
 <xref:System.UriTemplateMatch>  
 [<span data-ttu-id="1e078-139">Model programowania protokołu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="1e078-139">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="1e078-140">Obiekt UriTemplate i UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="1e078-140">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 [<span data-ttu-id="1e078-141">Omówienie modelu programowania protokołu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="1e078-141">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [<span data-ttu-id="1e078-142">Model obiektowy programowania protokołu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="1e078-142">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
