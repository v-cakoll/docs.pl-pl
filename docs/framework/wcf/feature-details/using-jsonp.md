---
title: "Używanie standardu JSONP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1eedacf6e98d8c6cb71b1cb62b41ce3ef7fcb47
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="using-jsonp"></a><span data-ttu-id="04db3-102">Używanie standardu JSONP</span><span class="sxs-lookup"><span data-stu-id="04db3-102">Using JSONP</span></span>

<span data-ttu-id="04db3-103">Dopełnienie JSON (JSONP) jest mechanizm, który umożliwia obsługę skryptów między witrynami w przeglądarkach sieci Web.</span><span class="sxs-lookup"><span data-stu-id="04db3-103">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="04db3-104">Format JSONP jest zaprojektowana dla możliwość ładowanie skryptów z poziomu witryny innej niż załadować dokument został pobrany z przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="04db3-104">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="04db3-105">Mechanizm działa przez ładunek JSON z nazwą funkcji zdefiniowanej przez użytkownika wywołania zwrotnego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="04db3-105">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="04db3-106">W powyższym przykładzie ładunek JSON `{"a" = \\"b\\"}`, jest ujęte w wywołaniu funkcji `callback`.</span><span class="sxs-lookup"><span data-stu-id="04db3-106">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="04db3-107">Funkcja wywołania zwrotnego musi być już zdefiniowana w bieżącej strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="04db3-107">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="04db3-108">Typ zawartości odpowiedzi JSONP jest `application/javascript`.</span><span class="sxs-lookup"><span data-stu-id="04db3-108">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="04db3-109">JSONP nie jest automatycznie włączone.</span><span class="sxs-lookup"><span data-stu-id="04db3-109">JSONP is not automatically enabled.</span></span> <span data-ttu-id="04db3-110">Aby go włączyć, ustaw `javascriptCallbackEnabled` atrybutu `true` na jednym standardowych punktów końcowych HTTP (<xref:System.ServiceModel.Description.WebHttpEndpoint> lub <xref:System.ServiceModel.Description.WebScriptEndpoint>), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="04db3-110">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="04db3-111">Nazwa funkcji wywołania zwrotnego można określić w zmienną zapytania o nazwie wywołania zwrotnego, jak pokazano w następującym adresem URL.</span><span class="sxs-lookup"><span data-stu-id="04db3-111">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="04db3-112">Gdy została wywołana, usługa wysyła odpowiedź podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="04db3-112">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="04db3-113">Można również określić nazwę funkcji wywołania zwrotnego, stosując <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> do klasy usługi, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="04db3-113">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

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

<span data-ttu-id="04db3-114">W usłudze przedstawione wcześniej żądanie wygląda następująco.</span><span class="sxs-lookup"><span data-stu-id="04db3-114">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="04db3-115">Gdy została wywołana, usługa odpowiada z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="04db3-115">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="04db3-116">Kody stanu HTTP</span><span class="sxs-lookup"><span data-stu-id="04db3-116">HTTP Status Codes</span></span>

<span data-ttu-id="04db3-117">Odpowiedzi JSONP z kodów stanu HTTP innych niż 200 obejmują drugi parametr z reprezentację liczbową kod stanu HTTP, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="04db3-117">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="04db3-118">Sprawdzanie poprawności</span><span class="sxs-lookup"><span data-stu-id="04db3-118">Validations</span></span>

<span data-ttu-id="04db3-119">Gdy format JSONP jest włączony, wykonywane są następujących sprawdzań poprawności:</span><span class="sxs-lookup"><span data-stu-id="04db3-119">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="04db3-120">Infrastruktura WCF zgłasza wyjątek, jeśli `javascriptCallback` jest włączona, parametr ciągu zapytania wywołania zwrotnego jest obecne w żądaniu i format odpowiedzi jest ustawiona na format JSON.</span><span class="sxs-lookup"><span data-stu-id="04db3-120">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="04db3-121">Jeśli żądanie zawiera parametr ciągu zapytania wywołania zwrotnego, ale ta operacja nie jest HTTP GET, parametr wywołania zwrotnego jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="04db3-121">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="04db3-122">Jeśli nazwa wywołania zwrotnego jest `null` lub pusty ciąg odpowiedzi nie jest sformatowany jako JSONP.</span><span class="sxs-lookup"><span data-stu-id="04db3-122">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="04db3-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04db3-123">See also</span></span>

[<span data-ttu-id="04db3-124">Omówienie modelu programowania protokołu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="04db3-124">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
