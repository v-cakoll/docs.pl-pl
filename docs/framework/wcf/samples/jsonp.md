---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 82fa0bb09ebdf3ca2325872c2b884f4940de17ed
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715723"
---
# <a name="jsonp"></a><span data-ttu-id="c71d0-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="c71d0-102">JSONP</span></span>
<span data-ttu-id="c71d0-103">Ten przykład pokazuje, jak obsługiwać kod JSON z dopełnieniem (JSONP) w usługach WCF REST.</span><span class="sxs-lookup"><span data-stu-id="c71d0-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="c71d0-104">JSONP to Konwencja używana do wywoływania skryptów międzydomenowych przez generowanie tagów skryptów w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="c71d0-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="c71d0-105">Wynik jest zwracany w określonej funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="c71d0-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="c71d0-106">JSONP opiera się na koncepcji, że Tagi takie jak `<script src="http://..." >` mogą ocenić skrypty z dowolnej domeny, a skrypt pobrany przez te Tagi jest oceniany w zakresie, w którym inne funkcje mogą już być zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="c71d0-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c71d0-107">Przedstawia</span><span class="sxs-lookup"><span data-stu-id="c71d0-107">Demonstrates</span></span>
 <span data-ttu-id="c71d0-108">Wykonywanie skryptów międzydomenowych z JSONP.</span><span class="sxs-lookup"><span data-stu-id="c71d0-108">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="c71d0-109">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="c71d0-109">Discussion</span></span>
 <span data-ttu-id="c71d0-110">Przykład zawiera stronę sieci Web, która dynamicznie dodaje blok skryptu po wyrenderowaniu strony w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="c71d0-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="c71d0-111">Ten blok skryptu wywołuje usługę WCF REST z pojedynczą operacją `GetCustomer`.</span><span class="sxs-lookup"><span data-stu-id="c71d0-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="c71d0-112">Usługa WCF REST zwraca nazwę i adres klienta opakowane w nazwie funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="c71d0-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="c71d0-113">Gdy usługa REST WCF reaguje, funkcja wywołania zwrotnego na stronie sieci Web jest wywoływana z danymi klienta, a funkcja wywołania zwrotnego wyświetla dane na stronie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c71d0-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="c71d0-114">Wstrzyknięcie znacznika skryptu i wykonywanie funkcji wywołania zwrotnego jest automatycznie obsługiwane przez kontrolkę ScriptManager ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="c71d0-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="c71d0-115">Wzorzec użycia jest taki sam jak w przypadku wszystkich serwerów proxy ASP.NET AJAX, z dodaniem jednej linii do włączenia JSONP, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="c71d0-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="c71d0-116">Strona sieci Web może wywoływać usługę WCF REST, ponieważ usługa używa <xref:System.ServiceModel.Description.WebScriptEndpoint> z `crossDomainScriptAccessEnabled` ustawionym na `true`.</span><span class="sxs-lookup"><span data-stu-id="c71d0-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="c71d0-117">Obie te konfiguracje są wykonywane w pliku Web. config w ramach elementu \<system. serviceModel >.</span><span class="sxs-lookup"><span data-stu-id="c71d0-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

 <span data-ttu-id="c71d0-118">Element ScriptManager zarządza interakcją z usługą i ukrywa złożoność ręcznej implementacji dostępu JSONP.</span><span class="sxs-lookup"><span data-stu-id="c71d0-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="c71d0-119">Gdy `crossDomainScriptAccessEnabled` jest ustawiona na `true` i format odpowiedzi dla operacji to JSON, Infrastruktura WCF bada identyfikator URI żądania dla parametru ciągu zapytania wywołania zwrotnego i zawija odpowiedź JSON z wartością parametru ciągu zapytania wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="c71d0-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="c71d0-120">W przykładzie Strona sieci Web wywołuje usługę WCF REST z następującym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="c71d0-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="c71d0-121">Ponieważ parametr ciągu zapytania wywołania zwrotnego ma wartość `JsonPCallback`, usługa WCF zwraca odpowiedź JSONP pokazaną w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c71d0-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="c71d0-122">Ta odpowiedź JSONP zawiera dane klienta sformatowane jako JSON, opakowane z nazwą funkcji wywołania zwrotnego żądaną przez stronę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c71d0-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="c71d0-123">Obiekt ScriptManager wykona to wywołanie zwrotne przy użyciu tagu skryptu do wykonania żądania międzydomenowego, a następnie przekaże wynik do procedury obsługi onSuccess, która została przekazana do operacji GetCustomer serwera proxy ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="c71d0-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="c71d0-124">Przykład składa się z dwóch ASP.NET aplikacji sieci Web: jeden zawiera tylko usługę WCF, a drugi zawiera stronę sieci Web. aspx, która wywołuje usługę.</span><span class="sxs-lookup"><span data-stu-id="c71d0-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="c71d0-125">W przypadku uruchamiania rozwiązania program Visual Studio 2012 będzie obsługiwał dwie witryny sieci Web na różnych portach, co tworzy środowisko, w którym usługa i klient znajdują się w różnych domenach.</span><span class="sxs-lookup"><span data-stu-id="c71d0-125">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c71d0-126">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c71d0-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c71d0-127">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="c71d0-127">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="c71d0-128">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c71d0-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c71d0-129">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c71d0-129">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="c71d0-130">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="c71d0-130">To run the sample</span></span>  
  
1. <span data-ttu-id="c71d0-131">Otwórz rozwiązanie dla przykładu JSONP.</span><span class="sxs-lookup"><span data-stu-id="c71d0-131">Open the solution for the JSONP Sample.</span></span>  
  
2. <span data-ttu-id="c71d0-132">Naciśnij klawisz F5, aby uruchomić `http://localhost:26648/JSONPClientPage.aspx` w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="c71d0-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3. <span data-ttu-id="c71d0-133">Zwróć uwagę, że po załadowaniu strony dane wejściowe dla "name" i "Address" są wypełniane przez wartości.</span><span class="sxs-lookup"><span data-stu-id="c71d0-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="c71d0-134">Te wartości zostały przekazane z wywołania usługi WCF po zakończeniu renderowania strony przez przeglądarkę.</span><span class="sxs-lookup"><span data-stu-id="c71d0-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
