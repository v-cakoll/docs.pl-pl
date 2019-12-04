---
title: Integracja buforowania platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 23c10e56dba7daec2d1027de92e8252c8fe69055
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716180"
---
# <a name="aspnet-caching-integration"></a><span data-ttu-id="24190-102">Integracja buforowania platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="24190-102">ASP.NET Caching Integration</span></span>

<span data-ttu-id="24190-103">Ten przykład pokazuje, jak korzystać z pamięci podręcznej ASP.NET Output z modelem programowania HTTP sieci WEB w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="24190-103">This sample demonstrates how to utilize the ASP.NET output cache with the WCF WEB HTTP programming model.</span></span> <span data-ttu-id="24190-104">Ten temat koncentruje się na funkcji integracji wyjściowej pamięci podręcznej ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="24190-104">This topic focuses on the ASP.NET output cache integration feature.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="24190-105">Przedstawia</span><span class="sxs-lookup"><span data-stu-id="24190-105">Demonstrates</span></span>

<span data-ttu-id="24190-106">Integracja z wyjściową pamięcią podręczną ASP.NET</span><span class="sxs-lookup"><span data-stu-id="24190-106">Integration with the ASP.NET Output Cache</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24190-107">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="24190-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="24190-108">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="24190-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="24190-109">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="24190-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="24190-110">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="24190-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a><span data-ttu-id="24190-111">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="24190-111">Discussion</span></span>

<span data-ttu-id="24190-112">W przykładzie użyto <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, aby użyć buforowania danych wyjściowych ASP.NET z usługą Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="24190-112">The sample uses the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> to utilize ASP.NET output caching with the Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="24190-113"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> jest stosowana do operacji usługi i udostępnia nazwę profilu pamięci podręcznej w pliku konfiguracji, który powinien zostać zastosowany do odpowiedzi z danej operacji.</span><span class="sxs-lookup"><span data-stu-id="24190-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is applied to service operations, and provides the name of a cache profile in a configuration file that should be applied to responses from the given operation.</span></span>

<span data-ttu-id="24190-114">W pliku Service.cs przykładowego projektu usługi zarówno operacje `GetCustomer` i `GetCustomers` są oznaczone <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, który zawiera nazwę profilu pamięci podręcznej "CacheFor60Seconds".</span><span class="sxs-lookup"><span data-stu-id="24190-114">In the Service.cs file of the sample Service project, both the `GetCustomer` and `GetCustomers` operations are marked with the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, which provides the cache profile name "CacheFor60Seconds".</span></span> <span data-ttu-id="24190-115">W pliku Web. config projektu usługi jest dostępny profil pamięci podręcznej "CacheFor60Seconds" w obszarze <`caching`> elementu <`system.web`>.</span><span class="sxs-lookup"><span data-stu-id="24190-115">In the Web.config file of the Service project, the cache profile "CacheFor60Seconds" is provided under the <`caching`> element of <`system.web`>.</span></span> <span data-ttu-id="24190-116">Dla tego profilu pamięci podręcznej wartość atrybutu `duration` to "60", więc odpowiedzi skojarzone z tym profilem są buforowane w pamięci podręcznej ASP.NET wyjściowej przez 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="24190-116">For this cache profile, the value of the `duration` attribute is "60", so responses associated with this profile are cached in the ASP.NET output cache for 60 seconds.</span></span> <span data-ttu-id="24190-117">Ponadto dla tego profilu pamięci podręcznej atrybut `varmByParam` ma wartość "format", więc żądania o różnych wartościach dla parametru ciągu zapytania `format` są buforowane osobno.</span><span class="sxs-lookup"><span data-stu-id="24190-117">Also, for this cache profile, the `varmByParam` attribute is set to "format" so requests with different values for the `format` query string parameter have their responses cached separately.</span></span> <span data-ttu-id="24190-118">Na koniec atrybut `varyByHeader` profilu pamięci podręcznej jest ustawiony na wartość "Akceptuj", więc żądania o różnych wartościach nagłówka Accept są buforowane osobno.</span><span class="sxs-lookup"><span data-stu-id="24190-118">Lastly, the cache profile’s `varyByHeader` attribute is set to "Accept", so requests with different Accept header values have their responses cached separately.</span></span>

<span data-ttu-id="24190-119">Program.cs w projekcie klienta pokazuje, jak taki klient może zostać utworzony przy użyciu <xref:System.Net.HttpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="24190-119">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="24190-120">Należy pamiętać, że jest to tylko jeden sposób na dostęp do usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="24190-120">Note that this is just one way to access a WCF service.</span></span> <span data-ttu-id="24190-121">Istnieje również możliwość uzyskiwania dostępu do usługi przy użyciu innych klas .NET Framework, takich jak fabryka kanałów WCF i <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="24190-121">It is also possible to access the service using other .NET Framework classes like the WCF channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="24190-122">Inne przykłady w zestawie SDK (na przykład [podstawowa usługa http](../../../../docs/framework/wcf/samples/basic-http-service.md) ) ilustrują sposób korzystania z tych klas do komunikowania się z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="24190-122">Other samples in the SDK (such as the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample) illustrate how to use these classes to communicate with a WCF service.</span></span>

## <a name="to-run-the-sample"></a><span data-ttu-id="24190-123">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="24190-123">To run the sample</span></span>

<span data-ttu-id="24190-124">Przykład składa się z trzech projektów:</span><span class="sxs-lookup"><span data-stu-id="24190-124">The sample consists of three projects:</span></span>

- <span data-ttu-id="24190-125">**Usługa**: projekt aplikacji sieci Web, który obejmuje usługę HTTP WCF hostowaną w ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="24190-125">**Service**: A Web Application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>

- <span data-ttu-id="24190-126">**Klient**: projekt aplikacji konsolowej, który tworzy wywołania do usługi.</span><span class="sxs-lookup"><span data-stu-id="24190-126">**Client**: A console application project that makes calls to the service.</span></span>

- <span data-ttu-id="24190-127">**Wspólne**: biblioteka udostępniona, która zawiera typ klienta używany przez klienta i usługę.</span><span class="sxs-lookup"><span data-stu-id="24190-127">**Common**: A shared library that contains the Customer type used by the client and service.</span></span>

<span data-ttu-id="24190-128">Gdy aplikacja konsoli klienta zostanie uruchomiona, klient wysyła żądania do usługi i zapisuje odpowiednie informacje z odpowiedzi do okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="24190-128">As the Client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>

#### <a name="to-run-the-sample"></a><span data-ttu-id="24190-129">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="24190-129">To run the sample</span></span>

1. <span data-ttu-id="24190-130">Otwórz rozwiązanie dla przykładu integracji pamięci podręcznej ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="24190-130">Open the solution for the ASP.NET Caching Integration Sample.</span></span>

2. <span data-ttu-id="24190-131">Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="24190-131">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="24190-132">Jeśli okno **Eksplorator rozwiązań** nie jest jeszcze otwarte, naciśnij klawisze Ctrl + W + S.</span><span class="sxs-lookup"><span data-stu-id="24190-132">If the **Solution Explorer** window is not already open, press CTRL+W+S.</span></span>

4. <span data-ttu-id="24190-133">W oknie **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **usługi** i wybierz polecenie **Uruchom nowe wystąpienie**.</span><span class="sxs-lookup"><span data-stu-id="24190-133">From the **Solution Explorer** window, right click the **Service** project and select **Start New Instance**.</span></span> <span data-ttu-id="24190-134">Spowoduje to uruchomienie serwera deweloperskiego ASP.NET, który jest hostem usługi.</span><span class="sxs-lookup"><span data-stu-id="24190-134">This launches the ASP.NET development server, which hosts the service.</span></span>

5. <span data-ttu-id="24190-135">W oknie **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **klienta** i wybierz polecenie **Uruchom nowe wystąpienie**.</span><span class="sxs-lookup"><span data-stu-id="24190-135">From the **Solution Explorer** window, right click the **Client** project and select **Start New Instance**.</span></span>

6. <span data-ttu-id="24190-136">Zostanie wyświetlone okno konsoli klienta z identyfikatorem URI uruchomionej usługi oraz identyfikatorem URI strony pomocy HTML dla działającej usługi.</span><span class="sxs-lookup"><span data-stu-id="24190-136">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="24190-137">W dowolnym momencie możesz wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="24190-137">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>

7. <span data-ttu-id="24190-138">W miarę uruchamiania przykładu klient zapisuje stan bieżącego działania.</span><span class="sxs-lookup"><span data-stu-id="24190-138">As the sample runs, the client writes the status of the current activity.</span></span>

8. <span data-ttu-id="24190-139">Naciśnij dowolny klawisz, aby zakończyć aplikację konsolową klienta.</span><span class="sxs-lookup"><span data-stu-id="24190-139">Press any key to terminate the client console application.</span></span>

9. <span data-ttu-id="24190-140">Naciśnij klawisze SHIFT + F5, aby zatrzymać debugowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="24190-140">Press SHIFT+F5 to stop debugging the service.</span></span>

10. <span data-ttu-id="24190-141">W obszarze powiadomień systemu Windows kliknij prawym przyciskiem myszy ikonę serwera deweloperskiego ASP.NET i wybierz polecenie **Zatrzymaj**.</span><span class="sxs-lookup"><span data-stu-id="24190-141">In the Windows Notification Area, right click the ASP.NET development server icon and select **Stop**.</span></span>
