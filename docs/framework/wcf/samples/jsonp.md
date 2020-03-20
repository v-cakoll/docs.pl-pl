---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 6b5b42285539c2334bccaa04e1ba179d2cf0046c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183570"
---
# <a name="jsonp"></a><span data-ttu-id="75971-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="75971-102">JSONP</span></span>
<span data-ttu-id="75971-103">W tym przykładzie pokazano, jak obsługiwać JSON z padding (JSONP) w usługach WCF REST.</span><span class="sxs-lookup"><span data-stu-id="75971-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="75971-104">JSONP jest konwencją używaną do wywoływania skryptów między domenami przez generowanie tagów skryptów w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="75971-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="75971-105">Wynik jest zwracany w określonej funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="75971-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="75971-106">JSONP opiera się na założeniu, `<script src="http://..." >` że tagi, takie jak można ocenić skrypty z dowolnej domeny i skrypt pobrany przez te tagi jest oceniane w zakresie, w którym inne funkcje mogą być już zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="75971-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="75971-107">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="75971-107">Demonstrates</span></span>
 <span data-ttu-id="75971-108">Skrypty między domenami z JSONP.</span><span class="sxs-lookup"><span data-stu-id="75971-108">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="75971-109">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="75971-109">Discussion</span></span>
 <span data-ttu-id="75971-110">Przykład zawiera stronę sieci Web, która dynamicznie dodaje blok skryptu po renderowaniu strony w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="75971-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="75971-111">Ten blok skryptu wywołuje usługę WCF REST, która ma jedną operację, `GetCustomer`.</span><span class="sxs-lookup"><span data-stu-id="75971-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="75971-112">Usługa WCF REST zwraca nazwę i adres klienta opakowane w nazwę funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="75971-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="75971-113">Gdy usługa WCF REST odpowiada, funkcja wywołania zwrotnego na stronie sieci Web jest wywoływana z danymi klienta, a funkcja wywołania zwrotnego wyświetla dane na stronie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="75971-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="75971-114">Iniekcja tagu skryptu i wykonanie funkcji wywołania zwrotnego jest automatycznie obsługiwane przez ASP.NET kontrolki AJAX ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="75971-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="75971-115">Wzorzec użycia jest taki sam jak w wszystkich ASP.NET serwerów proxy AJAX, z dodatkiem jednego wiersza, aby włączyć JSONP, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="75971-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="75971-116">Strona sieci Web może wywołać usługę WCF <xref:System.ServiceModel.Description.WebScriptEndpoint> REST, ponieważ usługa używa z `crossDomainScriptAccessEnabled` zestawem do `true`.</span><span class="sxs-lookup"><span data-stu-id="75971-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="75971-117">Obie te konfiguracje są wykonywane w pliku Web.config w ramach \<elementu system.serviceModel>.</span><span class="sxs-lookup"><span data-stu-id="75971-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

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

 <span data-ttu-id="75971-118">ScriptManager zarządza interakcji z usługą i ukrywa złożoność ręcznego implementowania dostępu JSONP.</span><span class="sxs-lookup"><span data-stu-id="75971-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="75971-119">Po `crossDomainScriptAccessEnabled` ustawieniu `true` i format odpowiedzi dla operacji jest JSON, infrastruktura WCF sprawdza identyfikator URI żądania dla parametru ciągu zapytania wywołania zwrotnego i zawija odpowiedź JSON z wartością parametru ciągu zapytania wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="75971-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="75971-120">W przykładzie strona sieci Web wywołuje usługę WCF REST z następującym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="75971-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="75971-121">Ponieważ parametr ciągu zapytania wywołania `JsonPCallback`zwrotnego ma wartość , usługa WCF zwraca odpowiedź JSONP pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="75971-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="75971-122">Ta odpowiedź JSONP zawiera dane klienta sformatowane jako JSON, opakowane o nazwę funkcji wywołania zwrotnego, że strona sieci Web żądana.</span><span class="sxs-lookup"><span data-stu-id="75971-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="75971-123">ScriptManager wykona to wywołanie zwrotne przy użyciu tagu skryptu do wykonania żądania między domenami, a następnie przekazać wynik do onSuccess obsługi, który został przekazany do GetCustomer operacji ASP.NET ajax proxy.</span><span class="sxs-lookup"><span data-stu-id="75971-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="75971-124">Przykład składa się z dwóch ASP.NET aplikacji sieci web: jeden zawiera tylko usługę WCF, a drugi zawiera stronę sieci Web .aspx, która wywołuje usługę.</span><span class="sxs-lookup"><span data-stu-id="75971-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="75971-125">Po uruchomieniu rozwiązania visual studio 2012 będzie hostować dwie witryny sieci Web na różnych portach, co tworzy środowisko, w którym usługa i klient działają w różnych domenach.</span><span class="sxs-lookup"><span data-stu-id="75971-125">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="75971-126">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="75971-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="75971-127">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="75971-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="75971-128">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="75971-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="75971-129">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="75971-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="75971-130">Aby uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="75971-130">To run the sample</span></span>  
  
1. <span data-ttu-id="75971-131">Otwórz rozwiązanie dla próbki JSONP.</span><span class="sxs-lookup"><span data-stu-id="75971-131">Open the solution for the JSONP Sample.</span></span>  
  
2. <span data-ttu-id="75971-132">Naciśnij klawisz F5, aby uruchomić go `http://localhost:26648/JSONPClientPage.aspx` w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="75971-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3. <span data-ttu-id="75971-133">Należy zauważyć, że po załadowaniu strony, wprowadzania tekstu dla "Nazwa" i "Adres" są wypełniane przez wartości.</span><span class="sxs-lookup"><span data-stu-id="75971-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="75971-134">Te wartości zostały dostarczone z wywołania do usługi WCF po zakończeniu renderowania strony przez przeglądarkę.</span><span class="sxs-lookup"><span data-stu-id="75971-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
