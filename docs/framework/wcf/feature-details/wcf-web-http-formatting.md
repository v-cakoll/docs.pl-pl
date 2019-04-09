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
# <a name="wcf-web-http-formatting"></a>Formatowanie kodu HTTP dla sieci Web WCF
Model programowania protokołu HTTP sieci Web WCF umożliwia dynamiczne określanie najlepszy format dla operacji usługi do zwrócenia w odpowiedzi. Obsługiwane są dwie metody, określając odpowiedni format: automatyczne i jawne.  
  
## <a name="automatic-formatting"></a>Formatowanie automatyczne  
 Po włączeniu automatycznego formatowania wybiera najlepszy format, w której ma zostać zwrócone w odpowiedzi. Określa najlepszy format, sprawdzając poniższe czynności:  
  
1.  Do typów nośników w nagłówku Accept komunikatu żądania.  
  
2.  Typ zawartości komunikatu żądania.  
  
3.  Domyślny format ustawienie w operacji.  
  
4.  Domyślny format w WebHttpBehavior.  
  
 Wiadomość dotycząca żądania zawiera nagłówek Accept infrastruktury usług Windows Communication Foundation (WCF) wyszukuje typ, który ją obsługuje. Jeśli `Accept` nagłówek określa priorytety dla jego typów nośników, są uwzględniane. Jeśli nie formatu odpowiedniego znajduje się w `Accept` nagłówka typu zawartości komunikatu żądania jest używana. Jeśli nie odpowiednie content-type jest określona, jest używany domyślny format ustawienie dla tej operacji. Domyślny format została ustawiona za pomocą `ResponseFormat` parametru <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutów. Jeśli nie domyślny format jest określona w operacji, wartość <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> właściwość jest używana. Automatyczne formatowanie opiera się na <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> właściwości. Jeśli ta właściwość jest równa `true`, infrastruktura WCF Określa format najlepszy do użycia. Automatyczne wybieranie formatu jest domyślnie wyłączona dla zapewnienia zgodności. Można włączyć automatyczne wybieranie formatu programowo lub za pomocą konfiguracji. Poniższy przykład pokazuje, jak włączyć automatyczne wybieranie formatu w kodzie.  
  
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
  
 Automatyczne formatowanie można również włączyć za pomocą konfiguracji. Możesz ustawić <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> bezpośrednio na właściwość <xref:System.ServiceModel.Description.WebHttpBehavior> lub za pomocą <xref:System.ServiceModel.Description.WebHttpEndpoint>. Poniższy przykład pokazuje, jak włączyć automatyczne wybieranie formatu <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
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
  
 Poniższy przykład pokazuje, jak włączyć automatyczne formatowanie zaznaczenie przy użyciu <xref:System.ServiceModel.Description.WebHttpEndpoint>.  
  
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
  
## <a name="explicit-formatting"></a>Jawne, formatowanie  
 Jak wskazuje nazwa, Deweloper w formatowaniu jawne Określa format najlepszy do użycia w kodzie operacji. W przypadku najlepszym formacie XML lub JSON Deweloper ustawia <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> do jednej <xref:System.ServiceModel.Web.WebMessageFormat.Xml> lub <xref:System.ServiceModel.Web.WebMessageFormat.Json>. Jeśli <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> właściwość nie została jawnie ustawiona, a następnie jest używany format domyślny wykonać operację.  
  
 Poniższy przykład sprawdza, czy format parametru ciągu zapytania dla formatu do użycia. Jeśli została określona, ustawia operacji formatowania, przy użyciu <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.  
  
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
  
 Jeśli potrzebujesz do obsługi formatów innych niż JSON lub XML, zdefiniuj operacji ma typ zwracany <xref:System.ServiceModel.Channels.Message>. W kodzie operacji ustala odpowiedni format można użyć, a następnie utwórz <xref:System.ServiceModel.Channels.Message> obiektu przy użyciu jednej z następujących metod:  
  
-   `WebOperationContext.CreateAtom10Response`  
  
-   `WebOperationContext.CreateJsonResponse`  
  
-   `WebOperationContext.CreateStreamResponse`  
  
-   `WebOperationContext.CreateTextResponse`  
  
-   `WebOperationContext.CreateXmlResponse`  
  
 Każda z tych metod przyjmuje zawartości i tworzy komunikat z odpowiednim formacie. `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` Metoda może służyć do uzyskania listy formatów preferowane przez klienta w kolejności malejących preferencji. Poniższy przykład pokazuje, jak używać `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` do określenia formatu do użycia, a następnie używa odpowiednie utworzyć metodę odpowiedzi w celu utworzenia komunikatu odpowiedzi.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Klasy UriTemplate i UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [Model obiektowy programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
