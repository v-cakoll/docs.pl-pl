---
title: Integracja buforowania platformy ASP.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d56c435088be383821d17250e230cae848d2bab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="aspnet-caching-integration"></a><span data-ttu-id="82592-102">Integracja buforowania platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="82592-102">ASP.NET Caching Integration</span></span>
<span data-ttu-id="82592-103">W tym przykładzie pokazano, jak korzystać z pamięci podręcznej danych wyjściowych programu ASP.NET z modelem programowania protokołu HTTP sieci WEB WCF.</span><span class="sxs-lookup"><span data-stu-id="82592-103">This sample demonstrates how to utilize the ASP.NET output cache with the WCF WEB HTTP programming model.</span></span> <span data-ttu-id="82592-104">Zobacz [podstawowej usługi zasobów](../../../../docs/framework/wcf/samples/basic-resource-service.md) próbkowania dla siebie wersji tego scenariusza, który opisano szczegółowo implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="82592-104">Please see the [Basic Resource Service](../../../../docs/framework/wcf/samples/basic-resource-service.md) sample for a self-hosted version of this scenario that discusses the service implementation in depth.</span></span> <span data-ttu-id="82592-105">Ten temat koncentruje się na funkcji Integracja z pamięci podręcznej danych wyjściowych programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="82592-105">This topic focuses on the ASP.NET output cache integration feature.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="82592-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="82592-106">Demonstrates</span></span>  
 <span data-ttu-id="82592-107">Integracja z pamięci podręcznej danych wyjściowych programu ASP.NET</span><span class="sxs-lookup"><span data-stu-id="82592-107">Integration with the ASP.NET Output Cache</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="82592-108">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="82592-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="82592-109">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="82592-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="82592-110">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="82592-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="82592-111">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="82592-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a><span data-ttu-id="82592-112">Omówienie</span><span class="sxs-lookup"><span data-stu-id="82592-112">Discussion</span></span>  
 <span data-ttu-id="82592-113">W przykładzie użyto <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> mogą korzystać z ASP.NET dane wyjściowe z buforowania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="82592-113">The sample uses the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> to utilize ASP.NET output caching with the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="82592-114"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Jest stosowany do operacji usługi, a także nazwę profilu pamięci podręcznej w pliku konfiguracji, który ma zostać zastosowany do odpowiedzi od danej operacji.</span><span class="sxs-lookup"><span data-stu-id="82592-114">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is applied to service operations, and provides the name of a cache profile in a configuration file that should be applied to responses from the given operation.</span></span>  
  
 <span data-ttu-id="82592-115">W pliku Service.cs przykładowy projekt usługi zarówno `GetCustomer` i `GetCustomers` operacji są oznaczone ikoną z <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, która zawiera nazwę profilu pamięci podręcznej "CacheFor60Seconds".</span><span class="sxs-lookup"><span data-stu-id="82592-115">In the Service.cs file of the sample Service project, both the `GetCustomer` and `GetCustomers` operations are marked with the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, which provides the cache profile name "CacheFor60Seconds".</span></span> <span data-ttu-id="82592-116">W pliku Web.config projektu usługi, profil pamięci podręcznej "CacheFor60Seconds" znajduje się w obszarze <`caching`> elementu <`system.web`>.</span><span class="sxs-lookup"><span data-stu-id="82592-116">In the Web.config file of the Service project, the cache profile "CacheFor60Seconds" is provided under the <`caching`> element of <`system.web`>.</span></span> <span data-ttu-id="82592-117">Dla tego profilu pamięci podręcznej, wartość `duration` atrybutu jest "60", dlatego skojarzone z tym profilem odpowiedzi są buforowane w pamięci podręcznej danych wyjściowych programu ASP.NET przez 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="82592-117">For this cache profile, the value of the `duration` attribute is "60", so responses associated with this profile are cached in the ASP.NET output cache for 60 seconds.</span></span> <span data-ttu-id="82592-118">Ponadto dla tego profilu pamięci podręcznej `varmByParam` atrybut jest ustawiony na "format" wniosek o różnych wartościach dla `format` zapytania parametr ciągu ma odpowiedzi w pamięci podręcznej oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="82592-118">Also, for this cache profile, the `varmByParam` attribute is set to "format" so requests with different values for the `format` query string parameter have their responses cached separately.</span></span> <span data-ttu-id="82592-119">Ponadto pamięć podręczna profilu `varyByHeader` atrybut jest ustawiony na "Akceptuj", więc żądania za pomocą innej wartości nagłówka Accept oddzielnie buforowane odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="82592-119">Lastly, the cache profile’s `varyByHeader` attribute is set to "Accept", so requests with different Accept header values have their responses cached separately.</span></span>  
  
 <span data-ttu-id="82592-120">Program.CS w projekcie klienta pokazano, jak takiego klienta mogą być tworzone za pomocą <xref:System.Net.HttpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="82592-120">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="82592-121">Należy pamiętać, że jest tylko jeden sposób uzyskiwania dostępu do usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="82592-121">Note that this is just one way to access a WCF service.</span></span> <span data-ttu-id="82592-122">Istnieje również możliwość uzyskania dostępu do usługi przy użyciu innych klas .NET Framework, takich jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fabryki kanałów i <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="82592-122">It is also possible to access the service using other .NET Framework classes like the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="82592-123">Inne przykłady w zestawie SDK (takich jak [podstawowa usługa HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) próbki i [automatycznego wyboru formatu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) przykładowe) ilustrują sposób używania tych klas do komunikowania się z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="82592-123">Other samples in the SDK (such as the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample and the [Automatic Format Selection](../../../../docs/framework/wcf/samples/automatic-format-selection.md) sample) illustrate how to use these classes to communicate with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
## <a name="to-run-the-sample"></a><span data-ttu-id="82592-124">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="82592-124">To run the sample</span></span>  
 <span data-ttu-id="82592-125">Przykład obejmuje trzy projekty:</span><span class="sxs-lookup"><span data-stu-id="82592-125">The sample consists of three projects:</span></span>  
  
-   <span data-ttu-id="82592-126">**Usługa**: projekt aplikacji sieci Web A, która obejmuje usługi HTTP usług WCF hostowanych w programie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="82592-126">**Service**: A Web Application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>  
  
-   <span data-ttu-id="82592-127">**Klient**: projekt aplikacji konsoli wykonywania wywołań do usługi.</span><span class="sxs-lookup"><span data-stu-id="82592-127">**Client**: A console application project that makes calls to the service.</span></span>  
  
-   <span data-ttu-id="82592-128">**Typowe**: biblioteki udostępnionej, którą zawiera typ klienta używany przez klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="82592-128">**Common**: A shared library that contains the Customer type used by the client and service.</span></span>  
  
 <span data-ttu-id="82592-129">Podczas działania aplikacji konsoli klienta, klient wysyła żądania do usługi i zapisuje istotnych informacji z odpowiedzi w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="82592-129">As the Client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="82592-130">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="82592-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="82592-131">Otwórz rozwiązanie przykładowej integracja buforowania platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="82592-131">Open the solution for the ASP.NET Caching Integration Sample.</span></span>  
  
2.  <span data-ttu-id="82592-132">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="82592-132">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="82592-133">Jeśli **Eksploratora rozwiązań** okno nie jest jeszcze otwarty, naciśnij kombinację klawiszy CTRL + P + S.</span><span class="sxs-lookup"><span data-stu-id="82592-133">If the **Solution Explorer** window is not already open, press CTRL+W+S.</span></span>  
  
4.  <span data-ttu-id="82592-134">Z **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy **usługi** projekt i wybierz **uruchomić nowe wystąpienie**.</span><span class="sxs-lookup"><span data-stu-id="82592-134">From the **Solution Explorer** window, right click the **Service** project and select **Start New Instance**.</span></span> <span data-ttu-id="82592-135">Spowoduje to uruchomienie ASP.NET development server, który obsługuje usługę.</span><span class="sxs-lookup"><span data-stu-id="82592-135">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5.  <span data-ttu-id="82592-136">Z **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy **klienta** projekt i wybierz **uruchomić nowe wystąpienie**.</span><span class="sxs-lookup"><span data-stu-id="82592-136">From the **Solution Explorer** window, right click the **Client** project and select **Start New Instance**.</span></span>  
  
6.  <span data-ttu-id="82592-137">Okno konsoli klienta pojawia się i zawiera identyfikator URI uruchomionej usługi i identyfikator URI elementu HTML pomocy strony uruchomionej usługi.</span><span class="sxs-lookup"><span data-stu-id="82592-137">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="82592-138">W dowolnym momencie można wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="82592-138">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7.  <span data-ttu-id="82592-139">Jak działa próbki, klient zapisuje stan bieżącego działania.</span><span class="sxs-lookup"><span data-stu-id="82592-139">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8.  <span data-ttu-id="82592-140">Naciśnij dowolny klawisz, aby zakończyć działanie aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="82592-140">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="82592-141">Naciśnij klawisz SHIFT + F5, aby zatrzymać debugowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="82592-141">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="82592-142">W obszarze powiadomień systemu Windows kliknij prawym przyciskiem myszy ikonę ASP.NET development serwera i wybierz **zatrzymać**.</span><span class="sxs-lookup"><span data-stu-id="82592-142">In the Windows Notification Area, right click the ASP.NET development server icon and select **Stop**.</span></span>
