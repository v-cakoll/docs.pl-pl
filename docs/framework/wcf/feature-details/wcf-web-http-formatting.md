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
# <a name="wcf-web-http-formatting"></a>Formatowanie HTTP sieci Web w programie WCF
Model programowania HTTP sieci Web w programie WCF umożliwia dynamiczne określenie najlepszego formatu dla operacji usługi w celu zwrócenia odpowiedzi w programie. Obsługiwane są dwie metody określania odpowiedniego formatu: automatyczne i jawne.  
  
## <a name="automatic-formatting"></a>Automatyczne formatowanie  
 Po włączeniu automatyczne formatowanie wybiera najlepszy format, w którym ma zostać zwrócona odpowiedź. Określa najlepszy format, sprawdzając następujące elementy:  
  
1. Typy nośników w nagłówku akceptowania komunikatu żądania.  
  
2. Typ zawartości komunikatu żądania.  
  
3. Domyślne ustawienie formatu w operacji.  
  
4. Ustawienie domyślnego formatu w WebHttpBehavior.  
  
 Jeśli komunikat żądania zawiera nagłówek Accept, infrastruktura Windows Communication Foundation (WCF) wyszukuje typ, który obsługuje. Jeśli `Accept` nagłówek określa priorytety dla typów nośników, są one honorowane. Jeśli w nagłówku nie zostanie znaleziony odpowiedni format `Accept` , zostanie użyty typ zawartości komunikatu żądania. Jeśli nie określono odpowiedniego typu zawartości, używane jest domyślne ustawienie formatu dla operacji. Domyślny format jest ustawiany z `ResponseFormat` parametrem <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutów. Jeśli w operacji nie określono formatu domyślnego, <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> zostanie użyta wartość właściwości. Automatyczne formatowanie opiera się na <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> właściwości. Jeśli ta właściwość jest ustawiona na `true` , Infrastruktura WCF określa najlepszy format do użycia. Automatyczne wybieranie formatu jest domyślnie wyłączone w celu zapewnienia zgodności z poprzednimi wersjami. Automatyczne wybieranie formatu można włączyć programowo lub za pomocą konfiguracji. Poniższy przykład pokazuje, jak włączyć automatyczne Wybieranie formatu w kodzie.  
  
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
  
 Automatyczne formatowanie można również włączyć przy użyciu konfiguracji. Właściwość można ustawić <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> bezpośrednio na <xref:System.ServiceModel.Description.WebHttpBehavior> lub przy użyciu <xref:System.ServiceModel.Description.WebHttpEndpoint> . Poniższy przykład pokazuje, jak włączyć automatyczne Wybieranie formatu na <xref:System.ServiceModel.Description.WebHttpBehavior> .  
  
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
  
 Poniższy przykład pokazuje, jak włączyć automatyczne Wybieranie formatu przy użyciu <xref:System.ServiceModel.Description.WebHttpEndpoint> .  
  
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
  
## <a name="explicit-formatting"></a>Jawne formatowanie  
 Jak nazywa się, w przypadku jawnego formatowania deweloper określa najlepszy format do użycia w kodzie operacji. Jeśli najlepszym formatem jest XML lub JSON, deweloper ustawia <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> jedną <xref:System.ServiceModel.Web.WebMessageFormat.Xml> lub <xref:System.ServiceModel.Web.WebMessageFormat.Json> . Jeśli <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> Właściwość nie jest jawnie ustawiona, zostanie użyty domyślny format operacji.  
  
 Poniższy przykład sprawdza, czy format ciągu zapytania ma być używany. Jeśli została określona, ustawia format operacji przy użyciu <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> .  
  
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
  
 Jeśli musisz obsługiwać formaty inne niż XML lub JSON, Zdefiniuj dla operacji typ zwracany <xref:System.ServiceModel.Channels.Message> . W kodzie operacji określ odpowiedni format, który ma być używany, a następnie Utwórz <xref:System.ServiceModel.Channels.Message> Obiekt przy użyciu jednej z następujących metod:  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 Każda z tych metod pobiera zawartość i tworzy komunikat z odpowiednim formatem. `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements`Metoda może służyć do uzyskania listy formatów preferowanych przez klienta w kolejności zmniejszania preferencji. Poniższy przykład pokazuje, jak użyć, `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` Aby określić format do użycia, a następnie używa odpowiedniej metody tworzenia odpowiedzi w celu utworzenia komunikatu odpowiedzi.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [Model programowania protokołu HTTP sieci Web w programie WCF](wcf-web-http-programming-model.md)
- [Klasy UriTemplate i UriTemplateTable](uritemplate-and-uritemplatetable.md)
- [Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF](wcf-web-http-programming-model-overview.md)
- [Model obiektowy programowania protokołu HTTP sieci Web w programie WCF](wcf-web-http-programming-object-model.md)
