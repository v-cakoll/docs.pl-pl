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
# <a name="wcf-web-http-formatting"></a>Formatowanie HTTP w sieci Web WCF
Model programowania HTTP w sieci Web WCF umożliwia dynamiczne określenie najlepszego formatu operacji usługi w celu zwrócenia odpowiedzi. Obsługiwane są dwie metody określania odpowiedniego formatu: automatyczne i jawne.  
  
## <a name="automatic-formatting"></a>Automatyczne formatowanie  
 Po włączeniu automatyczne formatowanie wybiera najlepszy format, w którym ma być zwracana odpowiedź. Określa najlepszy format, sprawdzając następujące, w kolejności:  
  
1. Typy nośników w nagłówku Akceptuj komunikat żądania.  
  
2. Typ zawartości komunikatu żądania.  
  
3. Domyślne ustawienie formatu w operacji.  
  
4. Domyślne ustawienie formatu w programie WebHttpBehavior.  
  
 Jeśli komunikat żądania zawiera nagłówek Akceptuj, infrastruktura Programu Windows Communication Foundation (WCF) wyszukuje typ, który obsługuje. Jeśli `Accept` nagłówek określa priorytety dla swoich typów nośników, są one honorowane. Jeśli w nagłówku `Accept` nie zostanie znaleziony odpowiedni format, używany jest typ zawartości komunikatu żądania. Jeśli nie określono odpowiedniego typu zawartości, używane jest domyślne ustawienie formatu operacji. Domyślny format jest `ResponseFormat` ustawiany <xref:System.ServiceModel.Web.WebGetAttribute> z <xref:System.ServiceModel.Web.WebInvokeAttribute> parametrem i atrybutami. Jeśli w operacji nie określono formatu domyślnego, używana jest wartość <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> właściwości. Automatyczne formatowanie zależy <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> od właściwości. Gdy ta właściwość `true`jest ustawiona na , WCF infrastruktury określa najlepszy format do użycia. Automatyczne zaznaczanie formatu jest domyślnie wyłączone ze zgodnych z przeszywem. Automatyczny wybór formatu można włączyć programowo lub za pomocą konfiguracji. W poniższym przykładzie pokazano, jak włączyć automatyczne zaznaczanie formatu w kodzie.  
  
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
  
 Automatyczne formatowanie można również włączyć za pomocą konfiguracji. Właściwość <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> można ustawić bezpośrednio <xref:System.ServiceModel.Description.WebHttpBehavior> na stronie <xref:System.ServiceModel.Description.WebHttpEndpoint>lub za pomocą pliku . W poniższym przykładzie pokazano, jak <xref:System.ServiceModel.Description.WebHttpBehavior>włączyć automatyczne zaznaczanie formatu w pliku .  
  
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
  
 W poniższym przykładzie pokazano, <xref:System.ServiceModel.Description.WebHttpEndpoint>jak włączyć automatyczne zaznaczanie formatu za pomocą programu .  
  
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
 Jak sama nazwa wskazuje, w jawnym formatowaniu deweloper określa najlepszy format do użycia w kodzie operacji. Jeśli najlepszym formatem jest XML lub <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> JSON, deweloper ustawia na jeden <xref:System.ServiceModel.Web.WebMessageFormat.Xml> lub <xref:System.ServiceModel.Web.WebMessageFormat.Json>. Jeśli <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> właściwość nie jest jawnie ustawiona, używany jest domyślny format operacji.  
  
 Poniższy przykład sprawdza parametr ciągu kwerendy formatu dla formatu do użycia. Jeśli został określony, ustawia format operacji za <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>pomocą .  
  
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
  
 Jeśli chcesz obsługiwać formaty inne niż XML lub JSON, zdefiniuj operację, aby mieć typ zwracany <xref:System.ServiceModel.Channels.Message>. W kodzie operacji określ odpowiedni format do <xref:System.ServiceModel.Channels.Message> użycia, a następnie utwórz obiekt przy użyciu jednej z następujących metod:  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 Każda z tych metod pobiera zawartość i tworzy komunikat o odpowiednim formacie. Metoda `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` ta może służyć do uzyskania listy formatów preferowanych przez klienta w kolejności malejącej preferencji. W poniższym przykładzie `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` pokazano, jak użyć do określenia formatu do użycia, a następnie używa odpowiedniej metody tworzenia odpowiedzi do utworzenia komunikatu odpowiedzi.  
  
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
- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Klasy UriTemplate i UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [Model obiektowy programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
