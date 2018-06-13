---
title: Tworzenie usług AJAX WCF bez platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 77a850408c3d952dbd4f682ea704d3248ae17c3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490360"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="70ca5-102">Tworzenie usług AJAX WCF bez platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="70ca5-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="70ca5-103">Usług AJAX Windows Communication Foundation (WCF) są dostępne z dowolnej strony włączenia obsługi języka JavaScript sieci Web bez konieczności ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="70ca5-103">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="70ca5-104">W tym temacie opisano sposób tworzenia usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="70ca5-104">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="70ca5-105">Aby uzyskać instrukcje dotyczące przy użyciu programu WCF z ASP.NET AJAX, zobacz [tworzenie usług WCF dla środowiska ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="70ca5-105">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="70ca5-106">Istnieją trzy części Tworzenie usług WCF AJAX:</span><span class="sxs-lookup"><span data-stu-id="70ca5-106">There are three parts to a creating a WCF AJAX service:</span></span>  
  
-   <span data-ttu-id="70ca5-107">Tworzenie punktu końcowego AJAX, które są dostępne w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="70ca5-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
-   <span data-ttu-id="70ca5-108">Tworzenie AJAX zgodnego kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="70ca5-108">Creating an AJAX-compatible service contract.</span></span>  
  
-   <span data-ttu-id="70ca5-109">Dostęp do usług WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="70ca5-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="70ca5-110">Tworzenie punktu końcowego AJAX</span><span class="sxs-lookup"><span data-stu-id="70ca5-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="70ca5-111">Najprostszym sposobem włączenie obsługi technologii AJAX w usługi WCF jest użycie <xref:System.ServiceModel.Activation.WebServiceHostFactory> w pliku svc skojarzonego z usługą, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="70ca5-111">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="70ca5-112">Alternatywnie umożliwia także konfiguracji można dodać punktu końcowego AJAX.</span><span class="sxs-lookup"><span data-stu-id="70ca5-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="70ca5-113">Użyj <xref:System.ServiceModel.WebHttpBinding> na punkt końcowy usługi i konfigurowania tego punktu końcowego z <xref:System.ServiceModel.Description.WebHttpBehavior> pokazane na poniższy fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="70ca5-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="70ca5-114">Na przykład pracy, zobacz [usługa AJAX z formatami JSON i XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="70ca5-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="70ca5-115">Tworzenie kontraktu usługi zgodnego AJAX</span><span class="sxs-lookup"><span data-stu-id="70ca5-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="70ca5-116">Domyślnie kontraktów usług uwidaczniany za pośrednictwem danych zwrotnych punktu końcowego AJAX w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="70ca5-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="70ca5-117">Domyślnie operacje usług są także dostępne za pośrednictwem żądania HTTP POST do adresów URL, które obejmują adres punktu końcowego, a następnie według nazwy operacji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="70ca5-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="70ca5-118">Ta operacja jest dostępna przy użyciu protokołu HTTP POST do `http://serviceaddress/endpointaddress/GetCities` i zwraca komunikat XML.</span><span class="sxs-lookup"><span data-stu-id="70ca5-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="70ca5-119">Pełny Model programowania sieci Web umożliwia dostosowanie tych podstawowych właściwości.</span><span class="sxs-lookup"><span data-stu-id="70ca5-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="70ca5-120">Na przykład można użyć <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybuty do kontrolowania zlecenie HTTP, na które odpowiada operacji lub użyj `UriTemplate` właściwości tych odpowiednich atrybutów, aby określić identyfikatory URI niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="70ca5-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="70ca5-121">Aby uzyskać więcej informacji, zobacz [modelu programowania protokołu HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="70ca5-121">For more information, see the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="70ca5-122">Format danych JSON jest często używane w usługach interfejsu AJAX.</span><span class="sxs-lookup"><span data-stu-id="70ca5-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="70ca5-123">Aby utworzyć operację zwracającą JSON zamiast XML, ustaw <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (lub <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) dla właściwości <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="70ca5-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="70ca5-124">[Serializacji JSON autonomicznego](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) temacie przedstawiono sposób wbudowanych .NET danych i typów kontraktu typy mapy do formatu JSON.</span><span class="sxs-lookup"><span data-stu-id="70ca5-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="70ca5-125">Zwykle JSON żądań i odpowiedzi składa się z tylko jednego elementu.</span><span class="sxs-lookup"><span data-stu-id="70ca5-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="70ca5-126">Dla poprzedniego `GetCities` działania, żądania przypomina następującą instrukcję.</span><span class="sxs-lookup"><span data-stu-id="70ca5-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```  
"na"  
```  
  
 <span data-ttu-id="70ca5-127">Poniższa instrukcja jest podobny do odpowiedzi na to żądanie.</span><span class="sxs-lookup"><span data-stu-id="70ca5-127">The response to that request resembles the following statement.</span></span>  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="70ca5-128">Jeśli operacja przyjmuje dodatkowych parametrów, styl żądanie może opakowana opakowywać obydwu tych parametrów w pojedynczy obiekt JSON.</span><span class="sxs-lookup"><span data-stu-id="70ca5-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="70ca5-129">Przykładem tego stylu komunikatu JSON jest w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="70ca5-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="70ca5-130">Następujące kontraktu akceptuje tego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="70ca5-130">The following contract accepts this message.</span></span>  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="70ca5-131">Uzyskiwanie dostępu do usług AJAX</span><span class="sxs-lookup"><span data-stu-id="70ca5-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="70ca5-132">Punktów końcowych WCF AJAX zawsze akceptowania żądań JSON i XML.</span><span class="sxs-lookup"><span data-stu-id="70ca5-132">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="70ca5-133">Żądania HTTP POST z typem zawartości "application/json" są traktowane jako JSON, a te z typem zawartości XML (na przykład "text/xml") wskazujące, są traktowane jako XML.</span><span class="sxs-lookup"><span data-stu-id="70ca5-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="70ca5-134">Żądania HTTP GET zawiera wszystkie parametry żądania w adresie URL, do samej siebie.</span><span class="sxs-lookup"><span data-stu-id="70ca5-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="70ca5-135">Jest użytkownika decyzji o tym, jak utworzyć żądanie HTTP do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="70ca5-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="70ca5-136">Ponadto użytkownik ma pełną kontrolę nad konstruowania JSON, który wchodzi w skład treści żądania.</span><span class="sxs-lookup"><span data-stu-id="70ca5-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="70ca5-137">Przykład tworzenia żądania z kodu JavaScript, zobacz [usługa AJAX z formatami JSON i XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="70ca5-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
