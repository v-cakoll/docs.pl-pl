---
title: Uzyskiwanie dostępu do usługi z przeglądarki sieci Web (Usługi danych programu WCF Szybki Start)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: eb7f1c97722b45a93c310fb8bcbdb42beece2553
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780545"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="41ae3-102">Uzyskiwanie dostępu do usługi z przeglądarki sieci Web (Usługi danych programu WCF Szybki Start)</span><span class="sxs-lookup"><span data-stu-id="41ae3-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="41ae3-103">Jest to drugie zadanie przewodnika Szybki Start dotyczącego Usługi danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="41ae3-103">This is the second task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="41ae3-104">W tym zadaniu można uruchomić Usługi danych programu WCF z programu Visual Studio i opcjonalnie wyłączyć odczytywanie kanału informacyjnego w przeglądarce internetowej.</span><span class="sxs-lookup"><span data-stu-id="41ae3-104">In this task, you start the WCF Data Services from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="41ae3-105">Następnie można pobrać dokument definicji usługi oraz uzyskać dostęp do zasobów usługi danych przez przesłanie żądań HTTP GET za pośrednictwem przeglądarki sieci Web do narażonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="41ae3-105">You then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>

> [!NOTE]
> <span data-ttu-id="41ae3-106">Domyślnie program Visual Studio przypisuje numer portu do `localhost` identyfikatora URI na komputerze.</span><span class="sxs-lookup"><span data-stu-id="41ae3-106">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="41ae3-107">To zadanie używa numeru `12345` portu w przykładach identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="41ae3-107">This task uses the port number `12345` in the URI examples.</span></span> <span data-ttu-id="41ae3-108">Aby uzyskać więcej informacji na temat sposobu ustawiania określonego numeru portu w projekcie programu Visual Studio, zobacz [Tworzenie usługi danych](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="41ae3-108">For more information about how to set a specific port number in your Visual Studio project see [Creating the Data Service](creating-the-data-service.md).</span></span>

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="41ae3-109">Aby zażądać domyślnego dokumentu usługi przy użyciu programu Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="41ae3-109">To request the default service document by using Internet Explorer</span></span>

1. <span data-ttu-id="41ae3-110">W programie Internet Explorer z menu **Narzędzia** wybierz pozycję **Opcje internetowe**, kliknij kartę **zawartość** , kliknij pozycję **Ustawienia**, a następnie wyczyść pole wyboru **Włącz wyświetlanie źródła**.</span><span class="sxs-lookup"><span data-stu-id="41ae3-110">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>

     <span data-ttu-id="41ae3-111">Gwarantuje to, że odczytywanie źródła danych jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="41ae3-111">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="41ae3-112">Jeśli ta funkcja nie zostanie wyłączona, przeglądarka sieci Web będzie traktować zwracany dokument zakodowany AtomPub jako źródło danych XML zamiast wyświetlać pierwotne dane XML.</span><span class="sxs-lookup"><span data-stu-id="41ae3-112">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>

    > [!NOTE]
    > <span data-ttu-id="41ae3-113">Jeśli przeglądarka nie może wyświetlić kanału informacyjnego jako pierwotne dane XML, nadal będzie można wyświetlić źródło danych jako kod źródłowy strony.</span><span class="sxs-lookup"><span data-stu-id="41ae3-113">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>

2. <span data-ttu-id="41ae3-114">W programie Visual Studio naciśnij klawisz **F5** , aby rozpocząć debugowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41ae3-114">In Visual Studio, press the **F5** key to start debugging the application.</span></span>

3. <span data-ttu-id="41ae3-115">Otwórz przeglądarkę sieci Web na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="41ae3-115">Open a Web browser on the local computer.</span></span> <span data-ttu-id="41ae3-116">Na pasku adresu wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="41ae3-116">In the address bar, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc
    ```

     <span data-ttu-id="41ae3-117">Spowoduje to zwrócenie domyślnego dokumentu usługi zawierającego listę zestawów jednostek, które są udostępniane przez tę usługę danych.</span><span class="sxs-lookup"><span data-stu-id="41ae3-117">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>

## <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="41ae3-118">Aby uzyskać dostęp do zasobów zestawu jednostek z przeglądarki sieci Web</span><span class="sxs-lookup"><span data-stu-id="41ae3-118">To access entity set resources from a Web browser</span></span>

1. <span data-ttu-id="41ae3-119">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="41ae3-119">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     <span data-ttu-id="41ae3-120">Spowoduje to zwrócenie zestawu wszystkich klientów z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="41ae3-120">This returns a set of all customers in the Northwind sample database.</span></span>

2. <span data-ttu-id="41ae3-121">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="41ae3-121">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     <span data-ttu-id="41ae3-122">Spowoduje to zwrócenie wystąpienia jednostki dla określonego klienta `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="41ae3-122">This returns an entity instance for the specific customer, `ALFKI`.</span></span>

3. <span data-ttu-id="41ae3-123">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="41ae3-123">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     <span data-ttu-id="41ae3-124">Powoduje to przechodzenie między klientami i zamówieniami w celu zwrócenia zestawu wszystkich zamówień dla określonego klienta `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="41ae3-124">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>

4. <span data-ttu-id="41ae3-125">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="41ae3-125">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     <span data-ttu-id="41ae3-126">To filtruje zamówienia należące do określonego klienta `ALFKI` , aby tylko określona kolejność była zwracana na podstawie podanej `OrderID` wartości.</span><span class="sxs-lookup"><span data-stu-id="41ae3-126">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>

## <a name="next-steps"></a><span data-ttu-id="41ae3-127">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="41ae3-127">Next Steps</span></span>

<span data-ttu-id="41ae3-128">Pomyślnie uzyskano dostęp do Usługi danych programu WCF z przeglądarki sieci Web przy użyciu przeglądarki wysyłającej żądania HTTP GET do określonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="41ae3-128">You have successfully accessed the WCF Data Services from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="41ae3-129">Przeglądarka sieci Web zapewnia łatwy sposób eksperymentowania z składnią adresów żądań i wyświetlania wyników.</span><span class="sxs-lookup"><span data-stu-id="41ae3-129">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="41ae3-130">Jednak usługa danych produkcyjnych nie jest ogólnie używana przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="41ae3-130">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="41ae3-131">Zazwyczaj aplikacje współpracują z usługą danych za pomocą kodu aplikacji lub języków skryptów.</span><span class="sxs-lookup"><span data-stu-id="41ae3-131">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="41ae3-132">Następnie utworzysz aplikację kliencką, która używa bibliotek klienckich do uzyskiwania dostępu do zasobów usługi danych, tak jakby były obiektami środowiska uruchomieniowego języka wspólnego (CLR):</span><span class="sxs-lookup"><span data-stu-id="41ae3-132">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="41ae3-133">Tworzenie aplikacji klienckich programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="41ae3-133">Creating the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="41ae3-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41ae3-134">See also</span></span>

- [<span data-ttu-id="41ae3-135">Uzyskiwanie dostępu do zasobów usługi danych</span><span class="sxs-lookup"><span data-stu-id="41ae3-135">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
