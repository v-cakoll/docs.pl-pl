---
title: Tworzenie usług AJAX WCF bez platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: b5f0f730f90227dcccc7e5ebf533d80a28f6e6eb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599298"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="a04b3-102">Tworzenie usług AJAX WCF bez platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a04b3-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="a04b3-103">Usługi Windows Communication Foundation (WCF) AJAX są dostępne z dowolnej strony sieci Web z obsługą języka JavaScript, bez konieczności ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="a04b3-103">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="a04b3-104">W tym temacie opisano sposób tworzenia takiej usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="a04b3-104">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="a04b3-105">Aby uzyskać instrukcje dotyczące korzystania z programu WCF z ASP.NET AJAX, zobacz [Tworzenie usług WCF dla ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="a04b3-105">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="a04b3-106">Istnieją trzy części do tworzenia usługi WCF AJAX:</span><span class="sxs-lookup"><span data-stu-id="a04b3-106">There are three parts to a creating a WCF AJAX service:</span></span>  
  
- <span data-ttu-id="a04b3-107">Tworzenie punktu końcowego AJAX, do którego można uzyskać dostęp za pomocą przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="a04b3-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
- <span data-ttu-id="a04b3-108">Tworzenie kontraktu usługi zgodnej ze standardem AJAX.</span><span class="sxs-lookup"><span data-stu-id="a04b3-108">Creating an AJAX-compatible service contract.</span></span>  
  
- <span data-ttu-id="a04b3-109">Uzyskiwanie dostępu do usług WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="a04b3-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="a04b3-110">Tworzenie punktu końcowego AJAX</span><span class="sxs-lookup"><span data-stu-id="a04b3-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="a04b3-111">Najbardziej podstawowym sposobem na włączenie obsługi technologii AJAX w usłudze WCF jest użycie <xref:System.ServiceModel.Activation.WebServiceHostFactory> pliku w formacie SVC skojarzonym z usługą, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a04b3-111">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="a04b3-112">Alternatywnie można również użyć konfiguracji, aby dodać punkt końcowy AJAX.</span><span class="sxs-lookup"><span data-stu-id="a04b3-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="a04b3-113">Użyj <xref:System.ServiceModel.WebHttpBinding> w punkcie końcowym usługi i skonfiguruj ten punkt końcowy przy użyciu <xref:System.ServiceModel.Description.WebHttpBehavior> tak jak pokazano w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="a04b3-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="a04b3-114">Aby zapoznać się z przykładem roboczym, zobacz [Usługa AJAX z danymi JSON i XML](../samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a04b3-114">For a working example, see the [AJAX Service with JSON and XML](../samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="a04b3-115">Tworzenie kontraktu usługi zgodnej ze standardem AJAX</span><span class="sxs-lookup"><span data-stu-id="a04b3-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="a04b3-116">Domyślnie kontrakty usługi udostępniane za pośrednictwem punktu końcowego AJAX zwracają dane w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="a04b3-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="a04b3-117">Ponadto domyślnie operacje usługi są dostępne za pośrednictwem żądań HTTP POST do adresów URL, które zawierają adres punktu końcowego, a następnie nazwę operacji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a04b3-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="a04b3-118">Ta operacja jest dostępna za pomocą polecenia POST protokołu HTTP w celu `http://serviceaddress/endpointaddress/GetCities` zwrócenia wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="a04b3-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="a04b3-119">Aby dostosować te podstawowe aspekty, można użyć pełnego modelu programowania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a04b3-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="a04b3-120">Na przykład można użyć <xref:System.ServiceModel.Web.WebGetAttribute> atrybutów lub, <xref:System.ServiceModel.Web.WebInvokeAttribute> Aby kontrolować czasownik http, do którego operacja reaguje, lub użyć `UriTemplate` właściwości tych atrybutów, aby określić niestandardowe identyfikatory URI.</span><span class="sxs-lookup"><span data-stu-id="a04b3-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="a04b3-121">Aby uzyskać więcej informacji, zobacz temat [model programowania HTTP sieci Web](wcf-web-http-programming-model.md) w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="a04b3-121">For more information, see the [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="a04b3-122">Format danych JSON jest często używany w usługach AJAX.</span><span class="sxs-lookup"><span data-stu-id="a04b3-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="a04b3-123">Aby utworzyć operację zwracającą kod JSON zamiast XML, ustaw <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> Właściwość (lub <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> ) na <xref:System.ServiceModel.Web.WebMessageFormat.Json> .</span><span class="sxs-lookup"><span data-stu-id="a04b3-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="a04b3-124">W temacie [autonomiczna Serializacja kodu JSON](stand-alone-json-serialization.md) pokazano, jak wbudowane typy .NET i typy kontraktów danych są mapowane na format JSON.</span><span class="sxs-lookup"><span data-stu-id="a04b3-124">The [Stand-Alone JSON Serialization](stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="a04b3-125">Zwykle żądania JSON i odpowiedzi składają się tylko z jednego elementu.</span><span class="sxs-lookup"><span data-stu-id="a04b3-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="a04b3-126">Dla poprzedniej `GetCities` operacji żądanie jest podobne do następującej.</span><span class="sxs-lookup"><span data-stu-id="a04b3-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```json
"na"  
```  
  
 <span data-ttu-id="a04b3-127">Odpowiedź na to żądanie jest podobna do następującej.</span><span class="sxs-lookup"><span data-stu-id="a04b3-127">The response to that request resembles the following statement.</span></span>  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="a04b3-128">Jeśli operacja przyjmuje dodatkowy parametr, styl żądania musi być opakowany, aby otoczyć oba parametry pojedynczym obiektem JSON.</span><span class="sxs-lookup"><span data-stu-id="a04b3-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="a04b3-129">Przykład tego komunikatu JSON w stylu znajduje się w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a04b3-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="a04b3-130">Następujący kontrakt akceptuje tę wiadomość.</span><span class="sxs-lookup"><span data-stu-id="a04b3-130">The following contract accepts this message.</span></span>  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="a04b3-131">Uzyskiwanie dostępu do usług AJAX</span><span class="sxs-lookup"><span data-stu-id="a04b3-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="a04b3-132">Punkty końcowe AJAX programu WCF zawsze akceptują zarówno żądania JSON, jak i XML.</span><span class="sxs-lookup"><span data-stu-id="a04b3-132">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="a04b3-133">Żądania POST protokołu HTTP z typem zawartości "Application/JSON" są traktowane jako dane JSON oraz z typem zawartości, który wskazuje na XML (na przykład "text/xml"), są traktowane jako XML.</span><span class="sxs-lookup"><span data-stu-id="a04b3-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="a04b3-134">Żądania HTTP GET zawierają wszystkie parametry żądania w samym adresie URL.</span><span class="sxs-lookup"><span data-stu-id="a04b3-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="a04b3-135">Użytkownik może zdecydować, jak utworzyć żądanie HTTP do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a04b3-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="a04b3-136">Ponadto użytkownik ma pełną kontrolę nad konstruowaniem kodu JSON, który stanowi treść żądania.</span><span class="sxs-lookup"><span data-stu-id="a04b3-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="a04b3-137">Aby zapoznać się z przykładem tworzenia żądania w języku JavaScript, zobacz [usługę AJAX z danymi JSON i XML](../samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a04b3-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../samples/ajax-service-with-json-and-xml-sample.md).</span></span>
