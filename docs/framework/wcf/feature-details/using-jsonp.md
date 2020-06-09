---
title: Używanie standardu JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 82290319b5d8b58708f0b2ebf40522ee76127b84
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594962"
---
# <a name="using-jsonp"></a><span data-ttu-id="cf8f8-102">Używanie standardu JSONP</span><span class="sxs-lookup"><span data-stu-id="cf8f8-102">Using JSONP</span></span>

<span data-ttu-id="cf8f8-103">Uzupełnienie JSON (JSONP) to mechanizm, który umożliwia obsługę skryptów między lokacjami w przeglądarkach sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-103">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="cf8f8-104">Funkcja JSONP została zaprojektowana z założenia, że przeglądarki sieci Web mają ładować skrypty z innej lokacji niż ta, z której został pobrany bieżący załadowany dokument.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-104">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="cf8f8-105">Mechanizm ten działa przez uzupełnienie ładunku JSON przez zdefiniowaną przez użytkownika nazwę funkcji wywołania zwrotnego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-105">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="cf8f8-106">W poprzednim przykładzie ładunek JSON `{"a" = \\"b\\"}` jest opakowany w wywołaniu funkcji `callback` .</span><span class="sxs-lookup"><span data-stu-id="cf8f8-106">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="cf8f8-107">Funkcja wywołania zwrotnego musi już być zdefiniowana na bieżącej stronie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-107">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="cf8f8-108">Typ zawartości odpowiedzi JSONP to `application/javascript` .</span><span class="sxs-lookup"><span data-stu-id="cf8f8-108">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="cf8f8-109">JSONP nie jest automatycznie włączona.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-109">JSONP is not automatically enabled.</span></span> <span data-ttu-id="cf8f8-110">Aby je włączyć, należy ustawić `javascriptCallbackEnabled` atrybut na `true` jeden z standardowych punktów końcowych protokołu HTTP ( <xref:System.ServiceModel.Description.WebHttpEndpoint> lub <xref:System.ServiceModel.Description.WebScriptEndpoint> ), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-110">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="cf8f8-111">Nazwę funkcji wywołania zwrotnego można określić w zmiennej zapytania o nazwie callback, jak pokazano w poniższym adresie URL.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-111">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="cf8f8-112">Po wywołaniu usługa wysyła odpowiedź podobną do następującej.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-112">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="cf8f8-113">Możesz również określić nazwę funkcji wywołania zwrotnego, stosując <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> do klasy usługi, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-113">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

```csharp
[ServiceContract]
[JavascriptCallbackBehavior(ParameterName = "$callback")]
public class Service1
{
    [OperationContract]
    [WebGet(ResponseFormat=WebMessageFormat.Json)]
    public string GetData()
    {
    }
}
```

<span data-ttu-id="cf8f8-114">W przypadku usługi pokazanej wcześniej żądanie wygląda następująco.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-114">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="cf8f8-115">Po wywołaniu usługa reaguje na następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-115">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="cf8f8-116">Kody stanu HTTP</span><span class="sxs-lookup"><span data-stu-id="cf8f8-116">HTTP Status Codes</span></span>

<span data-ttu-id="cf8f8-117">Odpowiedzi JSONP z kodami stanu HTTP innych niż 200 zawierają drugi parametr z reprezentacją liczbową kodu stanu HTTP, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-117">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="cf8f8-118">Weryfikacje</span><span class="sxs-lookup"><span data-stu-id="cf8f8-118">Validations</span></span>

<span data-ttu-id="cf8f8-119">Następujące walidacji są wykonywane po włączeniu JSONP:</span><span class="sxs-lookup"><span data-stu-id="cf8f8-119">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="cf8f8-120">Infrastruktura WCF zgłasza wyjątek `javascriptCallback` , jeśli jest włączona, w żądaniu jest obecny parametr ciągu zapytania wywołania zwrotnego, a format odpowiedzi jest ustawiony na wartość JSON.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-120">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="cf8f8-121">Jeśli żądanie zawiera parametr ciągu zapytania wywołania zwrotnego, ale operacja nie jest operacją HTTP GET, parametr wywołania zwrotnego jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-121">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="cf8f8-122">Jeśli nazwa wywołania zwrotnego to `null` lub pusty ciąg, odpowiedź nie jest sformatowana jako JSONP.</span><span class="sxs-lookup"><span data-stu-id="cf8f8-122">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf8f8-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf8f8-123">See also</span></span>

- [<span data-ttu-id="cf8f8-124">Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="cf8f8-124">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
