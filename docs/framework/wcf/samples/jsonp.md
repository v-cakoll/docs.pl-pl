---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 37da57a000376f972cd6da9e04be46ddec1b7144
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989892"
---
# <a name="jsonp"></a><span data-ttu-id="9180c-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="9180c-102">JSONP</span></span>
<span data-ttu-id="9180c-103">Niniejszy przykład pokazuje sposób obsługi formatu JSON przy użyciu dopełnienie (JSONP) w usługach REST programu WCF.</span><span class="sxs-lookup"><span data-stu-id="9180c-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="9180c-104">JSONP jest Konwencji, używane do wywołania między domenami skryptów przez generowanie tagi skryptu w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="9180c-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="9180c-105">Wynik jest zwracany dla funkcji określonego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="9180c-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="9180c-106">JSONP opiera się na koncepcji, takich jak tagi `<script src="http://..." >` ocenić skryptów z dowolnej domeny, a skrypt pobierane przez tych znaczników jest szacowana w zakresie, w którym innych funkcji może być już zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="9180c-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9180c-107">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="9180c-107">Demonstrates</span></span>
 <span data-ttu-id="9180c-108">Między domenami korzystanie ze standardu JSONP skryptów.</span><span class="sxs-lookup"><span data-stu-id="9180c-108">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="9180c-109">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="9180c-109">Discussion</span></span>
 <span data-ttu-id="9180c-110">Przykład obejmuje strony sieci Web, w której są dodawane dynamicznie bloku skryptu po stronie zostało wyrenderowane w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="9180c-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="9180c-111">Ten blok skryptu wywołań usługi REST usługi WCF, która ma jedną operację `GetCustomer`.</span><span class="sxs-lookup"><span data-stu-id="9180c-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="9180c-112">Usługa REST programu WCF zwraca nazwę i adres opakowane w nazwie funkcji wywołania zwrotnego klienta.</span><span class="sxs-lookup"><span data-stu-id="9180c-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="9180c-113">Gdy usługa WCF REST odpowiada, funkcja wywołania zwrotnego na stronie sieci Web jest wywoływana z danymi klienta i funkcji wywołania zwrotnego wyświetla dane na stronie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9180c-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="9180c-114">Iniekcja tag skryptu i wykonanie funkcji wywołania zwrotnego jest realizowane automatycznie przez formantu ScriptManager AJAX programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9180c-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="9180c-115">Wzorzec użycia jest taki sam jak z wszystkich serwerów proxy ASP.NET AJAX, dodając jeden wiersz, aby umożliwić JSONP, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="9180c-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="9180c-116">Strony sieci Web może wywołać usługi REST usługi WCF, ponieważ usługa używa <xref:System.ServiceModel.Description.WebScriptEndpoint> z `crossDomainScriptAccessEnabled` równa `true`.</span><span class="sxs-lookup"><span data-stu-id="9180c-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="9180c-117">Obie te konfiguracje są wykonywane w pliku Web.config w obszarze \<system.serviceModel > element.</span><span class="sxs-lookup"><span data-stu-id="9180c-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

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

 <span data-ttu-id="9180c-118">ScriptManager zarządza interakcję z usługą i natychmiast powoduje ukrycie złożoności ręcznie wykonawczych JSONP dostępu.</span><span class="sxs-lookup"><span data-stu-id="9180c-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="9180c-119">Gdy `crossDomainScriptAccessEnabled` ustawiono `true` i format odpowiedzi dla operacji JSON, infrastruktura WCF sprawdza identyfikator URI żądania dla parametru ciągu zapytania wywołania zwrotnego i otacza odpowiedź JSON z wartością ciągu zapytania wywołania zwrotnego parametr.</span><span class="sxs-lookup"><span data-stu-id="9180c-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="9180c-120">W tym przykładzie strony sieci Web wywołań usługi REST programu WCF za pomocą następujący identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="9180c-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="9180c-121">Ponieważ parametr ciągu zapytania wywołanie zwrotne ma wartość `JsonPCallback`, usługi WCF, zwraca odpowiedź JSONP pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9180c-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="9180c-122">Ta odpowiedź JSONP zawiera dane klienta w formacie JSON, ujęte w nawiasy nazwy funkcji wywołania zwrotnego, który zażądał strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9180c-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="9180c-123">ScriptManager wykonać to wywołanie zwrotne przy użyciu tagu skryptu do wykonania żądania między domenami, a następnie przekazać wynik do obsługi onSuccess, który został przekazany do operacji GetCustomer proxy ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="9180c-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="9180c-124">Przykład składa się z dwóch aplikacji sieci web programu ASP.NET: jedna z nich zawiera tylko usługi WCF, a inny zawiera strona sieci Web .aspx, który wywołuje usługę.</span><span class="sxs-lookup"><span data-stu-id="9180c-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="9180c-125">Podczas uruchamiania rozwiązania, Visual Studio 2012 hostować dwie witryny sieci Web na innym, co powoduje utworzenie środowiska, miejsca zamieszkania usługi i klienta w różnych domenach.</span><span class="sxs-lookup"><span data-stu-id="9180c-125">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="9180c-126">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9180c-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9180c-127">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="9180c-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9180c-128">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="9180c-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9180c-129">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9180c-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="9180c-130">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="9180c-130">To run the sample</span></span>  
  
1. <span data-ttu-id="9180c-131">Otwórz rozwiązanie dla przykładu JSONP.</span><span class="sxs-lookup"><span data-stu-id="9180c-131">Open the solution for the JSONP Sample.</span></span>  
  
2. <span data-ttu-id="9180c-132">Naciśnij klawisz F5, aby uruchomić `http://localhost:26648/JSONPClientPage.aspx` w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="9180c-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3. <span data-ttu-id="9180c-133">Należy zauważyć, że po załadowaniu strony danych wejściowych tekst "Name" i "Address" zostaną wypełnione wartościami.</span><span class="sxs-lookup"><span data-stu-id="9180c-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="9180c-134">Te wartości zostały dostarczone z wywołania do usługi WCF, po zakończeniu przeglądarki, renderowanie strony.</span><span class="sxs-lookup"><span data-stu-id="9180c-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
