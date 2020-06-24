---
title: Uzyskiwanie dostępu do usługi z przeglądarki sieci Web (Usługi danych programu WCF Szybki Start)
description: Dowiedz się, jak rozpocząć Usługi danych programu WCF w programie Visual Studio i wyłączyć odczytywanie źródła w przeglądarce. Pobierz zasoby definicji usługi i uzyskaj dostęp do zasobów usługi danych.
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: 713436c31bc3f622c4f44a83e33fff3fcbba1c1c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247781"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="a0d1a-104">Uzyskiwanie dostępu do usługi z przeglądarki sieci Web (Usługi danych programu WCF Szybki Start)</span><span class="sxs-lookup"><span data-stu-id="a0d1a-104">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="a0d1a-105">Jest to drugie zadanie przewodnika Szybki Start dotyczącego Usługi danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-105">This is the second task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="a0d1a-106">W tym zadaniu można uruchomić Usługi danych programu WCF z programu Visual Studio i opcjonalnie wyłączyć odczytywanie kanału informacyjnego w przeglądarce internetowej.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-106">In this task, you start the WCF Data Services from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="a0d1a-107">Następnie można pobrać dokument definicji usługi oraz uzyskać dostęp do zasobów usługi danych przez przesłanie żądań HTTP GET za pośrednictwem przeglądarki sieci Web do narażonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-107">You then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>

> [!NOTE]
> <span data-ttu-id="a0d1a-108">Domyślnie program Visual Studio przypisuje numer portu do `localhost` identyfikatora URI na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-108">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="a0d1a-109">To zadanie używa numeru portu `12345` w przykładach identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-109">This task uses the port number `12345` in the URI examples.</span></span> <span data-ttu-id="a0d1a-110">Aby uzyskać więcej informacji na temat sposobu ustawiania określonego numeru portu w projekcie programu Visual Studio, zobacz [Tworzenie usługi danych](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="a0d1a-110">For more information about how to set a specific port number in your Visual Studio project see [Creating the Data Service](creating-the-data-service.md).</span></span>

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="a0d1a-111">Aby zażądać domyślnego dokumentu usługi przy użyciu programu Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="a0d1a-111">To request the default service document by using Internet Explorer</span></span>

1. <span data-ttu-id="a0d1a-112">W programie Internet Explorer z menu **Narzędzia** wybierz pozycję **Opcje internetowe**, kliknij kartę **zawartość** , kliknij pozycję **Ustawienia**, a następnie wyczyść pole wyboru **Włącz wyświetlanie źródła**.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-112">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>

     <span data-ttu-id="a0d1a-113">Gwarantuje to, że odczytywanie źródła danych jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-113">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="a0d1a-114">Jeśli ta funkcja nie zostanie wyłączona, przeglądarka sieci Web będzie traktować zwracany dokument zakodowany AtomPub jako źródło danych XML zamiast wyświetlać pierwotne dane XML.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-114">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a0d1a-115">Jeśli przeglądarka nie może wyświetlić kanału informacyjnego jako pierwotne dane XML, nadal będzie można wyświetlić źródło danych jako kod źródłowy strony.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-115">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>

2. <span data-ttu-id="a0d1a-116">W programie Visual Studio naciśnij klawisz **F5** , aby rozpocząć debugowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-116">In Visual Studio, press the **F5** key to start debugging the application.</span></span>

3. <span data-ttu-id="a0d1a-117">Otwórz przeglądarkę sieci Web na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-117">Open a Web browser on the local computer.</span></span> <span data-ttu-id="a0d1a-118">Na pasku adresu wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="a0d1a-118">In the address bar, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc
    ```

     <span data-ttu-id="a0d1a-119">Spowoduje to zwrócenie domyślnego dokumentu usługi zawierającego listę zestawów jednostek, które są udostępniane przez tę usługę danych.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-119">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>

## <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="a0d1a-120">Aby uzyskać dostęp do zasobów zestawu jednostek z przeglądarki sieci Web</span><span class="sxs-lookup"><span data-stu-id="a0d1a-120">To access entity set resources from a Web browser</span></span>

1. <span data-ttu-id="a0d1a-121">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="a0d1a-121">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers
    ```

     <span data-ttu-id="a0d1a-122">Spowoduje to zwrócenie zestawu wszystkich klientów z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-122">This returns a set of all customers in the Northwind sample database.</span></span>

2. <span data-ttu-id="a0d1a-123">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="a0d1a-123">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     <span data-ttu-id="a0d1a-124">Spowoduje to zwrócenie wystąpienia jednostki dla określonego klienta `ALFKI` .</span><span class="sxs-lookup"><span data-stu-id="a0d1a-124">This returns an entity instance for the specific customer, `ALFKI`.</span></span>

3. <span data-ttu-id="a0d1a-125">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="a0d1a-125">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     <span data-ttu-id="a0d1a-126">Powoduje to przechodzenie między klientami i zamówieniami w celu zwrócenia zestawu wszystkich zamówień dla określonego klienta `ALFKI` .</span><span class="sxs-lookup"><span data-stu-id="a0d1a-126">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>

4. <span data-ttu-id="a0d1a-127">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="a0d1a-127">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     <span data-ttu-id="a0d1a-128">To filtruje zamówienia należące do określonego klienta, `ALFKI` aby tylko określona kolejność była zwracana na podstawie podanej `OrderID` wartości.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-128">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a0d1a-129">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a0d1a-129">Next Steps</span></span>

<span data-ttu-id="a0d1a-130">Pomyślnie uzyskano dostęp do Usługi danych programu WCF z przeglądarki sieci Web przy użyciu przeglądarki wysyłającej żądania HTTP GET do określonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-130">You have successfully accessed the WCF Data Services from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="a0d1a-131">Przeglądarka sieci Web zapewnia łatwy sposób eksperymentowania z składnią adresów żądań i wyświetlania wyników.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-131">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="a0d1a-132">Jednak usługa danych produkcyjnych nie jest ogólnie używana przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-132">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="a0d1a-133">Zazwyczaj aplikacje współpracują z usługą danych za pomocą kodu aplikacji lub języków skryptów.</span><span class="sxs-lookup"><span data-stu-id="a0d1a-133">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="a0d1a-134">Następnie utworzysz aplikację kliencką, która używa bibliotek klienckich do uzyskiwania dostępu do zasobów usługi danych, tak jakby były obiektami środowiska uruchomieniowego języka wspólnego (CLR):</span><span class="sxs-lookup"><span data-stu-id="a0d1a-134">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a0d1a-135">Tworzenie aplikacji klienckich programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a0d1a-135">Creating the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="a0d1a-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0d1a-136">See also</span></span>

- [<span data-ttu-id="a0d1a-137">Uzyskiwanie dostępu do zasobów usługi danych</span><span class="sxs-lookup"><span data-stu-id="a0d1a-137">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
