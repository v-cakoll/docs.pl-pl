---
title: "Punkty końcowe protokołów SOAP i HTTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9404d304302360b2be590c814d1f94cb46bd5f84
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="soap-and-http-endpoints"></a><span data-ttu-id="a2e1c-102">Punkty końcowe protokołów SOAP i HTTP</span><span class="sxs-lookup"><span data-stu-id="a2e1c-102">SOAP and HTTP Endpoints</span></span>
<span data-ttu-id="a2e1c-103">W tym przykładzie przedstawiono sposób implementacji usługi opartego na protokole RPC i udostępnić go w formacie protokołu SOAP i formatowanie "Zwykły starego pliku XML" (POX) przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model programowania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-103">This sample demonstrates how to implement an RPC-based service and expose it in the SOAP format and the "Plain Old XML" (POX) format using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Programming model.</span></span> <span data-ttu-id="a2e1c-104">Zobacz [podstawowa usługa HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) przykładowa, aby uzyskać więcej informacji o powiązanie HTTP dla usługi.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-104">See the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample for more details about the HTTP binding for the service.</span></span> <span data-ttu-id="a2e1c-105">Ten przykład dotyczy przede wszystkim szczegółowe informacje, które odnoszą się do udostępnianie tych samych usług za pośrednictwem protokołu SOAP i HTTP przy użyciu różnych powiązań.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-105">This sample focuses on the details that pertain to exposing the same service over SOAP and HTTP using different bindings.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a2e1c-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="a2e1c-106">Demonstrates</span></span>  
 <span data-ttu-id="a2e1c-107">Udostępnianie usługi RPC za pośrednictwem protokołu SOAP i HTTP przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a2e1c-107">Exposing an RPC service over SOAP and HTTP using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="a2e1c-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="a2e1c-108">Discussion</span></span>  
 <span data-ttu-id="a2e1c-109">Ten przykład zawiera dwa składniki: projekt aplikacji sieci Web (usługa), który zawiera [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług i aplikacji konsoli (klient), która wywołuje operacji usługi za pomocą powiązania SOAP i HTTP.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-109">This sample consists of two components: a Web Application project (Service) that contains a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and a console application (Client) that invokes service operations using SOAP and HTTP bindings.</span></span>  
  
 <span data-ttu-id="a2e1c-110">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 2 operacje — udostępnia usługi`GetData` i `PutData` — która echo ciąg, który został przekazany jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-110">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service exposes 2 operations –`GetData` and `PutData` – that echo the string that was passed as input.</span></span> <span data-ttu-id="a2e1c-111">Operacje usług są opatrzoną <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-111">The service operations are annotated with <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="a2e1c-112">Te atrybuty kontrolują projekcji HTTP z tych operacji.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-112">These attributes control the HTTP projection of these operations.</span></span> <span data-ttu-id="a2e1c-113">Ponadto mają adnotacje z <xref:System.ServiceModel.OperationContractAttribute>, co pozwala je, aby być uwidaczniany za pośrednictwem powiązania SOAP.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-113">In addition, they are annotated with <xref:System.ServiceModel.OperationContractAttribute>, which enables them to be exposed over SOAP bindings.</span></span> <span data-ttu-id="a2e1c-114">Usługi `PutData` metoda zgłasza <xref:System.ServiceModel.Web.WebFaultException>, które są wysyłane z powrotem przez serwer HTTP przy użyciu kodu stanu HTTP i są wysyłane z powrotem za pośrednictwem protokołu SOAP jako błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-114">The service’s `PutData` method throws a <xref:System.ServiceModel.Web.WebFaultException>, which gets sent back over HTTP using the HTTP status code and gets sent back over SOAP as a SOAP fault.</span></span>  
  
 <span data-ttu-id="a2e1c-115">Konfiguruje plik Web.config [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi z punktami końcowymi 3:</span><span class="sxs-lookup"><span data-stu-id="a2e1c-115">The Web.config file configures the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with 3 endpoints:</span></span>  
  
-   <span data-ttu-id="a2e1c-116">Punkt końcowy ~/service.svc/mex, który udostępnia metadane usługi dla dostępu klientów opartego na protokole SOAP.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-116">The ~/service.svc/mex endpoint that exposes the service metadata for access by SOAP-based clients.</span></span>  
  
-   <span data-ttu-id="a2e1c-117">Punkt końcowy ~/service.svc/http, który umożliwia klientom dostęp do usługi za pomocą tego powiązania protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-117">The ~/service.svc/http endpoint that enables clients to access the service using the HTTP binding.</span></span>  
  
-   <span data-ttu-id="a2e1c-118">Punkt końcowy ~/service.svc/soap, umożliwiający klientom dostęp do usługi przez powiązanie HTTP za pomocą protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-118">The ~/service.svc/soap endpoint that allows the clients to access the service using the SOAP over HTTP binding.</span></span>  
  
 <span data-ttu-id="a2e1c-119">Punkt końcowy HTTP jest skonfigurowany z <`webHttp`> Standardowy punkt końcowy, który ma `helpEnabled` ustawioną `true`.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-119">The HTTP endpoint is configured with a <`webHttp`> standard endpoint which has `helpEnabled` set to `true`.</span></span> <span data-ttu-id="a2e1c-120">W związku z tym usługa przedstawia strona pomocy XHTML oparte na ~/service.svc/http/help używanego przez klientów oparte na protokole HTTP do uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-120">As a result, the service exposes an XHTML based help page at ~/service.svc/http/help that HTTP-based clients can use to access the service.</span></span>  
  
 <span data-ttu-id="a2e1c-121">Projekt klienta demonstracja uzyskiwania dostępu do usługi przy użyciu serwera proxy protokołu SOAP (wygenerowane za pomocą **Dodaj odwołanie do usługi**) i uzyskiwania dostępu do usługi przy użyciu <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-121">The client project demonstrates accessing the service using a SOAP proxy (generated through **Add Service Reference**) and accessing the service using <xref:System.Net.WebClient>.</span></span>  
  
 <span data-ttu-id="a2e1c-122">Próbka składa się z usługą hostowanych w sieci Web i aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-122">The sample consists of a Web-hosted service and a console application.</span></span> <span data-ttu-id="a2e1c-123">Podczas działania aplikacji konsoli, klient wysyła żądania do usługi i zapisuje istotnych informacji z odpowiedzi w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-123">As the console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="a2e1c-124">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="a2e1c-124">To run the sample</span></span>  
  
1.  <span data-ttu-id="a2e1c-125">Otwórz rozwiązanie SOAP i przykładowe punktów końcowych HTTP.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-125">Open the solution for the SOAP and HTTP Endpoints Sample.</span></span>  
  
2.  <span data-ttu-id="a2e1c-126">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="a2e1c-127">Jeśli go nie jest jeszcze otwarty, naciśnij kombinację klawiszy CTRL + W, S, aby otworzyć **Eksploratora rozwiązań** okna.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-127">If it is not already open, press CTRL+W, S to open the **Solution Explorer** window.</span></span>  
  
4.  <span data-ttu-id="a2e1c-128">Z **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy **usługi** projektu, umieść kursor nad **debugowania** menu kontekstowego, aby **uruchomić nowy Wystąpienie** zostanie wyświetlone menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-128">From the **Solution Explorer** window, right-click the **Service** project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="a2e1c-129">Kliknij przycisk **uruchomić nowe wystąpienie**.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-129">Click **Start New Instance**.</span></span> <span data-ttu-id="a2e1c-130">Spowoduje to uruchomienie ASP.NET development server, który obsługuje usługę.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-130">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5.  <span data-ttu-id="a2e1c-131">Eksplorator rozwiązań systemu Windows, kliknij prawym przyciskiem myszy projekt klienta i umieść kursor nad **debugowania** menu kontekstowego, aby **uruchomić nowe wystąpienie** zostanie wyświetlone menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-131">From the Solution Explorer windows, right-click the Client project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="a2e1c-132">Kliknij przycisk **uruchomić nowe wystąpienie**.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-132">Click **Start New Instance**.</span></span>  
  
6.  <span data-ttu-id="a2e1c-133">Okno konsoli klienta pojawia się i zawiera identyfikator URI uruchomionej usługi i identyfikator URI elementu HTML pomocy strony uruchomionej usługi.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-133">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="a2e1c-134">W dowolnym momencie można wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-134">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7.  <span data-ttu-id="a2e1c-135">Jak działa próbki, klient zapisuje stan bieżącego działania.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-135">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8.  <span data-ttu-id="a2e1c-136">Naciśnij dowolny klawisz, aby zakończyć działanie aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-136">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="a2e1c-137">Naciśnij klawisz SHIFT + F5, aby zatrzymać debugowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-137">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="a2e1c-138">W obszarze powiadomień systemu Windows kliknij prawym przyciskiem myszy ikonę ASP.NET development serwera, a następnie wybierz **zatrzymać** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-138">In the Windows Notification Area, right-click the ASP.NET development server icon and select **Stop** from the context menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a2e1c-139">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a2e1c-140">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a2e1c-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a2e1c-141">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a2e1c-142">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
