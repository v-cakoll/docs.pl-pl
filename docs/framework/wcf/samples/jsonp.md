---
title: JSONP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 02332e04f729abd125f43acdbe0883851004537e
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="jsonp"></a><span data-ttu-id="5227f-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="5227f-102">JSONP</span></span>
<span data-ttu-id="5227f-103">W tym przykładzie przedstawiono sposób obsługi formatu JSON z dopełnienie (JSONP) w usługach WCF REST.</span><span class="sxs-lookup"><span data-stu-id="5227f-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="5227f-104">Format JSONP jest Konwencji, używany do innej domeny skrypty wywołania przez generowanie tagi skryptu w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="5227f-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="5227f-105">Wynik zostanie zwrócony w funkcji określonej wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="5227f-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="5227f-106">JSONP opiera się na założeniu, że tagi, takie jak \<skryptu src = "http:/ /..." > można ocenić skryptów z dowolnej domeny i pobierane przez tagi skryptu jest obliczane w zakresie, w którym mogą już zdefiniowany innych funkcji.</span><span class="sxs-lookup"><span data-stu-id="5227f-106">JSONP is based on the idea that tags such as \<script src="http://..." > can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5227f-107">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="5227f-107">Demonstrates</span></span>  
 <span data-ttu-id="5227f-108">Między domenami skryptów JSONP.</span><span class="sxs-lookup"><span data-stu-id="5227f-108">Cross-domain scripting with JSONP.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5227f-109">Omówienie</span><span class="sxs-lookup"><span data-stu-id="5227f-109">Discussion</span></span>  
 <span data-ttu-id="5227f-110">Przykład obejmuje strony sieci Web, które są dodawane dynamicznie bloku skryptu po wyrenderowaniu strony w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="5227f-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="5227f-111">Ten blok skryptu wywołuje usługa REST usługi WCF, która zawiera jedną operację `GetCustomer`.</span><span class="sxs-lookup"><span data-stu-id="5227f-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="5227f-112">Usługa WCF REST zwraca nazwę i adres otoczona nazwę funkcji wywołania zwrotnego klienta.</span><span class="sxs-lookup"><span data-stu-id="5227f-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="5227f-113">Gdy usługa WCF REST odpowiada, funkcja wywołania zwrotnego na stronie sieci Web została wywołana z danych klienta i funkcja wywołania zwrotnego wyświetla dane na stronie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5227f-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="5227f-114">Iniekcji tagu i wykonywania funkcji wywołania zwrotnego jest realizowane automatycznie przez formant ASP.NET AJAX ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="5227f-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="5227f-115">Wzorca użycia jest taka sama jak z wszystkich serwerów proxy ASP.NET AJAX, z uwzględnieniem jeden wiersz, aby włączyć JSONP, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="5227f-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>  
  
```csharp  
var proxy = new JsonpAjaxService.CustomerService();  
proxy.set_enableJsonp(true);  
proxy.GetCustomer(onSuccess, onFail, null);  
```  
  
 <span data-ttu-id="5227f-116">Strony sieci Web można wywołać usługi REST usługi WCF, ponieważ usługa używa <xref:System.ServiceModel.Description.WebScriptEndpoint> z `crossDomainScriptAccessEnabled` ustawioną `true`.</span><span class="sxs-lookup"><span data-stu-id="5227f-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="5227f-117">Obie te konfiguracje są wykonywane w pliku Web.config w obszarze \<system.serviceModel > elementu.</span><span class="sxs-lookup"><span data-stu-id="5227f-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>  
  
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
  
 <span data-ttu-id="5227f-118">ScriptManager zarządza interakcji z usługą i ukrywa optymalizacji złożoności ręcznie wdrażania dostępu JSONP.</span><span class="sxs-lookup"><span data-stu-id="5227f-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="5227f-119">Gdy `crossDomainScriptAccessEnabled` ma ustawioną wartość `true` i odpowiedzi format dla formatu JSON, jest operacja [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury sprawdza identyfikator URI żądania dla wywołania zwrotnego parametr ciągu zapytania i opakowuje JSON odpowiedzi o wartości zapytania wywołania zwrotnego Parametr typu String.</span><span class="sxs-lookup"><span data-stu-id="5227f-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="5227f-120">W przykładzie strony sieci Web wywołuje usługę WCF REST z następujący identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="5227f-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 <span data-ttu-id="5227f-121">Ponieważ parametru ciągu zapytania wywołanie zwrotne ma wartość `JsonPCallback`, usługi WCF zwraca odpowiedź JSONP pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5227f-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 <span data-ttu-id="5227f-122">Tej odpowiedzi JSONP zawiera dane klienta w formacie JSON, opakowana z nazwą funkcji wywołania zwrotnego, która żądanej strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5227f-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="5227f-123">ScriptManager wykonanie tego wywołania zwrotnego przy użyciu tagu skryptu do wykonania żądania między domenami, a następnie przekazać wynik do obsługi onSuccess, który został przekazany do operacji GetCustomer proxy ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="5227f-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>  
  
 <span data-ttu-id="5227f-124">Próbka składa się z dwóch aplikacji sieci web platformy ASP.NET: jeden zawiera po prostu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, a inny zawiera sieci Web .aspx, który wywołuje usługę.</span><span class="sxs-lookup"><span data-stu-id="5227f-124">The sample consists of two ASP.NET web applications: one contains just a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="5227f-125">Podczas uruchamiania rozwiązania, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] będzie obsługiwać dwie witryny sieci Web na inne porty, które tworzy środowisko, w którym usługa i klient na żywo w różnych domenach.</span><span class="sxs-lookup"><span data-stu-id="5227f-125">When running the solution, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5227f-126">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5227f-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5227f-127">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5227f-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5227f-128">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="5227f-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5227f-129">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5227f-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="5227f-130">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="5227f-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="5227f-131">Otwórz rozwiązanie przykładowej JSONP.</span><span class="sxs-lookup"><span data-stu-id="5227f-131">Open the solution for the JSONP Sample.</span></span>  
  
2.  <span data-ttu-id="5227f-132">Naciśnij klawisz F5, aby uruchomić HYPERLINK "http://localhost:26648/JSONPClientPage.aspx" http://localhost:26648/JSONPClientPage.aspx w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="5227f-132">Press F5 to launch  HYPERLINK "http://localhost:26648/JSONPClientPage.aspx" http://localhost:26648/JSONPClientPage.aspx in the browser.</span></span>  
  
3.  <span data-ttu-id="5227f-133">Należy zauważyć, że po załadowaniu strony wejść tekst "Name" i "Address" są wypełniane przy wartości.</span><span class="sxs-lookup"><span data-stu-id="5227f-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="5227f-134">Wartości te zostały podane po wywołaniu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi po zakończeniu przeglądarki renderowania strony.</span><span class="sxs-lookup"><span data-stu-id="5227f-134">These values were supplied from a call to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service after the browser finished rendering the page.</span></span>
