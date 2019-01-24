---
title: Używanie standardu JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 622fbdbf2674aea552cfd57f528d7cc5168cfda8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713489"
---
# <a name="using-jsonp"></a><span data-ttu-id="b5b4b-102">Używanie standardu JSONP</span><span class="sxs-lookup"><span data-stu-id="b5b4b-102">Using JSONP</span></span>

<span data-ttu-id="b5b4b-103">Dopełnienie JSON (JSONP) to mechanizm, który umożliwia obsługę skryptów między witrynami w przeglądarkach sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-103">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="b5b4b-104">JSONP został opracowany na możliwość ładowania skryptów z witryny innej niż bieżący załadować dokument został pobrany z przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-104">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="b5b4b-105">Mechanizm polega na dopełnienie ładunek JSON z nazwą funkcji zdefiniowanych przez użytkownika wywołania zwrotnego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-105">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="b5b4b-106">W powyższym przykładzie ładunek JSON `{"a" = \\"b\\"}`, jest opakowana w wywołaniu funkcji `callback`.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-106">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="b5b4b-107">Funkcja wywołania zwrotnego musi być już zdefiniowane w bieżącej strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-107">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="b5b4b-108">Typ zawartości odpowiedzi JSONP jest `application/javascript`.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-108">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="b5b4b-109">JSONP nie jest automatycznie włączone.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-109">JSONP is not automatically enabled.</span></span> <span data-ttu-id="b5b4b-110">Aby ją włączyć, ustaw `javascriptCallbackEnabled` atrybutu `true` na jednym z standardowych punktów końcowych HTTP (<xref:System.ServiceModel.Description.WebHttpEndpoint> lub <xref:System.ServiceModel.Description.WebScriptEndpoint>), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-110">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="b5b4b-111">Można określić nazwę funkcji wywołania zwrotnego w zmiennej zapytania o nazwie wywołania zwrotnego, jak pokazano w następującym adresem URL.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-111">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="b5b4b-112">Wywołana usługa wysyła odpowiedź, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-112">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="b5b4b-113">Można również określić nazwę funkcji wywołania zwrotnego, stosując <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> do klasy usługi, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-113">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

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

<span data-ttu-id="b5b4b-114">W przypadku usługi przedstawionego wcześniej żądanie wygląda podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-114">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="b5b4b-115">Wywołana usługa odpowiada za pomocą następujących.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-115">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="b5b4b-116">Kody stanu HTTP</span><span class="sxs-lookup"><span data-stu-id="b5b4b-116">HTTP Status Codes</span></span>

<span data-ttu-id="b5b4b-117">JSONP odpowiedzi z kodów stanu HTTP inne niż 200 obejmują drugim parametrem reprezentację liczbową kod stanu HTTP, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-117">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="b5b4b-118">Liczba ocen</span><span class="sxs-lookup"><span data-stu-id="b5b4b-118">Validations</span></span>

<span data-ttu-id="b5b4b-119">Następujące operacje sprawdzania poprawności są wykonywane, gdy format JSONP jest włączony:</span><span class="sxs-lookup"><span data-stu-id="b5b4b-119">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="b5b4b-120">Infrastruktura WCF zgłasza wyjątek, jeśli `javascriptCallback` jest włączona, parametr ciągu zapytania wywołania zwrotnego jest obecne w żądaniu i format odpowiedzi jest ustawiona na format JSON.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-120">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="b5b4b-121">Jeśli żądanie zawiera parametr ciągu zapytania wywołania zwrotnego, ale ta operacja nie jest żądania HTTP GET, parametr wywołania zwrotnego jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-121">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="b5b4b-122">Jeśli nazwa wywołania zwrotnego jest `null` lub pusty ciąg, w odpowiedzi nie jest sformatowany jako JSONP.</span><span class="sxs-lookup"><span data-stu-id="b5b4b-122">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5b4b-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5b4b-123">See also</span></span>

- [<span data-ttu-id="b5b4b-124">Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="b5b4b-124">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
