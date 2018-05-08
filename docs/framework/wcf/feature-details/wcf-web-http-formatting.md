---
title: Formatowanie kodu HTTP sieci Web WCF
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: abbfc74f33ddb676c8ac85eb712757615a2972ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-web-http-formatting"></a>Formatowanie kodu HTTP sieci Web WCF
Model programowania protokołu HTTP sieci Web WCF umożliwia dynamiczne określanie format najlepszy dla operacji usługi zwrócić w odpowiedzi. Obsługiwane są dwie metody, określając odpowiedni format: jawne i automatyczne.  
  
## <a name="automatic-formatting"></a>Automatyczne formatowanie  
 Włączenie automatycznego formatowania wybiera format najlepszy do której należy zwrócić w odpowiedzi. Określa format najlepszy sprawdzając następujące polecenie, w kolejności:  
  
1.  Typy nośnika w nagłówku Accept komunikatu żądania.  
  
2.  Typ zawartości komunikatu żądania.  
  
3.  Domyślny format ustawienie w operacji.  
  
4.  Domyślny format w WebHttpBehavior.  
  
 Wiadomość dotycząca żądania zawiera nagłówek Accept określający infrastrukturę programu Windows Communication Foundation (WCF) wyszukuje typ, który go obsługuje. Jeśli `Accept` nagłówek określa priorytety dotyczące jego typów nośników znajdują się one go uznać. W przypadku znalezienia nie odpowiedni format w `Accept` nagłówka content-type komunikatu żądania jest używana. Jeśli zostanie określony nie odpowiedniego typu zawartości, jest używany domyślny format ustawienie dla tej operacji. Domyślny format ustawiono `ResponseFormat` parametr <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutów. Jeśli nie domyślny format jest określony w operacji wartość <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> właściwość jest używana. Automatyczne formatowanie opiera się na <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> właściwości. Jeśli ta właściwość jest równa `true`, infrastruktura WCF Określa format najlepszy do użycia. Automatyczne wybieranie formatu jest domyślnie wyłączona dla zapewnienia zgodności. Automatyczne wybieranie formatu można włączyć programowo lub przy użyciu konfiguracji. Poniższy przykład przedstawia sposób włączania automatycznego wyboru formatu w kodzie.  
  
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
  
 Automatyczne formatowanie można również włączyć za pomocą konfiguracji. Można ustawić <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> właściwości bezpośrednio na <xref:System.ServiceModel.Description.WebHttpBehavior> lub przy użyciu <xref:System.ServiceModel.Description.WebHttpEndpoint>. Poniższy przykład przedstawia sposób Włącz automatyczne wybieranie formatu <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
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
  
 Poniższy przykład przedstawia sposób Włącz automatyczne formatowanie zaznaczenia przy użyciu <xref:System.ServiceModel.Description.WebHttpEndpoint>.  
  
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
  
## <a name="explicit-formatting"></a>Jawne formatowania  
 Jak wskazuje nazwę, Deweloper w formatowaniu jawne Określa format najlepszy do użycia z kodem operacji. W przypadku najlepszym formacie XML lub JSON dewelopera ustawia <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> albo <xref:System.ServiceModel.Web.WebMessageFormat.Xml> lub <xref:System.ServiceModel.Web.WebMessageFormat.Json>. Jeśli <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> właściwość nie jest jawnie ustawiona, a następnie wykonać operację domyślny format jest używany.  
  
 Poniższy przykład sprawdza, czy format parametru ciągu zapytania dla formatu do użycia. Jeśli zostały określone, ustawia operacji sformatować przy użyciu <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.  
  
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
  
 Jeśli zachodzi potrzeba obsługi formatów innych niż XML lub JSON, definiować operacji ma typ zwracany <xref:System.ServiceModel.Channels.Message>. W ramach kod operacji ustalić odpowiedni format, a następnie utwórz <xref:System.ServiceModel.Channels.Message> przy użyciu jednej z następujących metod:  
  
-   `WebOperationContext.CreateAtom10Response`  
  
-   `WebOperationContext.CreateJsonResponse`  
  
-   `WebOperationContext.CreateStreamResponse`  
  
-   `WebOperationContext.CreateTextResponse`  
  
-   `WebOperationContext.CreateXmlResponse`  
  
 Każda z tych metod ma zawartości i tworzy komunikat z odpowiednim formatem. `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` Metody można użyć w celu uzyskania listy formatów preferowany przez klienta w kolejności malejącej preferencji. Poniższy przykład przedstawia użycie `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` do określenia formatu do użycia, a następnie używa odpowiednie Utwórz metodę odpowiedzi w celu utworzenia komunikatu odpowiedzi.  
  
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
 <xref:System.UriTemplate>  
 <xref:System.UriTemplateMatch>  
 [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Klasy UriTemplate i UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 [Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [Model obiektowy programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
