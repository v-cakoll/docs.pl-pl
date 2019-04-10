---
title: Uzyskiwanie dostępu do usługi z przeglądarki sieci Web (WCF Data Services — Szybki Start)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: ebeda2805f3393b298e43aa4dcc601298ce176f6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330327"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="14ca3-102">Uzyskiwanie dostępu do usługi z przeglądarki sieci Web (WCF Data Services — Szybki Start)</span><span class="sxs-lookup"><span data-stu-id="14ca3-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="14ca3-103">To drugie zadanie tego przewodnika Szybki Start usług danych WCF.</span><span class="sxs-lookup"><span data-stu-id="14ca3-103">This is the second task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="14ca3-104">To zadanie służy do start usług danych WCF w programie Visual Studio i opcjonalnie Wyłącz odczytu kanału informacyjnego w przeglądarce sieci Web.</span><span class="sxs-lookup"><span data-stu-id="14ca3-104">In this task, you start the WCF Data Services from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="14ca3-105">Możesz następnie pobierania dokumentu definicji usługi oraz dostęp do zasobów usługi danych przez przesłanie żądania HTTP GET, za pośrednictwem przeglądarki sieci Web do narażonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="14ca3-105">You then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>

> [!NOTE]
> <span data-ttu-id="14ca3-106">Domyślnie program Visual Studio automatycznie przypisuje numer portu `localhost` identyfikatora URI na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="14ca3-106">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="14ca3-107">To zadanie używa numeru portu `12345` w przykładach identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="14ca3-107">This task uses the port number `12345` in the URI examples.</span></span> <span data-ttu-id="14ca3-108">Aby uzyskać więcej informacji na temat sposobu ustawiania określonego numeru portu w projekcie programu Visual Studio zobacz [Tworzenie usługi danych](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="14ca3-108">For more information about how to set a specific port number in your Visual Studio project see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="14ca3-109">Aby zażądać domyślnego dokumentu usługi za pomocą programu Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="14ca3-109">To request the default service document by using Internet Explorer</span></span>

1. <span data-ttu-id="14ca3-110">W programie Internet Explorer z **narzędzia** menu, wybierz opcję **Opcje internetowe**, kliknij przycisk **zawartości** kliknij pozycję **ustawienia**i wyczyść  **Włącz wyświetlanie kanału informacyjnego**.</span><span class="sxs-lookup"><span data-stu-id="14ca3-110">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>

     <span data-ttu-id="14ca3-111">Dzięki temu który kanału informacyjnego odczytu jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="14ca3-111">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="14ca3-112">Jeśli nie można wyłączyć tę funkcję, przeglądarki sieci Web będzie traktowany zwrócone zakodowanego dokumentu AtomPub jako źródła danych zamiast wyświetlanie danych pierwotnych XML pliku XML.</span><span class="sxs-lookup"><span data-stu-id="14ca3-112">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>

    > [!NOTE]
    > <span data-ttu-id="14ca3-113">Jeśli przeglądarka nie może wyświetlić źródła danych jako nieprzetworzone dane XML, nadal należy możliwość wyświetlania źródła danych jako kod źródłowy dla strony.</span><span class="sxs-lookup"><span data-stu-id="14ca3-113">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>

2. <span data-ttu-id="14ca3-114">W programie Visual Studio, naciśnij klawisz **F5** klawisz, aby rozpocząć debugowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="14ca3-114">In Visual Studio, press the **F5** key to start debugging the application.</span></span>

3. <span data-ttu-id="14ca3-115">Otwórz przeglądarkę internetową na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="14ca3-115">Open a Web browser on the local computer.</span></span> <span data-ttu-id="14ca3-116">Na pasku adresu wpisz następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="14ca3-116">In the address bar, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc
    ```

     <span data-ttu-id="14ca3-117">Spowoduje to zwrócenie usługi dokument domyślny, która zawiera listę zestawów encji, udostępnianych przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="14ca3-117">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>

## <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="14ca3-118">Aby dostęp do jednostki zestaw zasobów z przeglądarki sieci Web</span><span class="sxs-lookup"><span data-stu-id="14ca3-118">To access entity set resources from a Web browser</span></span>

1. <span data-ttu-id="14ca3-119">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="14ca3-119">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     <span data-ttu-id="14ca3-120">To zwraca zestaw wszystkich klientów w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="14ca3-120">This returns a set of all customers in the Northwind sample database.</span></span>

2. <span data-ttu-id="14ca3-121">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="14ca3-121">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     <span data-ttu-id="14ca3-122">Spowoduje to zwrócenie wystąpienie jednostki dla określonego klienta `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="14ca3-122">This returns an entity instance for the specific customer, `ALFKI`.</span></span>

3. <span data-ttu-id="14ca3-123">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="14ca3-123">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     <span data-ttu-id="14ca3-124">To jest przesyłany relacji między danymi klientów i zamówień do zwrócenia zbiór wszystkich zamówień dla konkretnego klienta `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="14ca3-124">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>

4. <span data-ttu-id="14ca3-125">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="14ca3-125">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     <span data-ttu-id="14ca3-126">Filtruje zamówienia, które należą do określonego odbiorcy `ALFKI` tak, aby w określonej kolejności są zwracane na podstawie podane `OrderID` wartość.</span><span class="sxs-lookup"><span data-stu-id="14ca3-126">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>

## <a name="next-steps"></a><span data-ttu-id="14ca3-127">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="14ca3-127">Next Steps</span></span>

<span data-ttu-id="14ca3-128">Pomyślnie uzyskano dostęp usługi danych WCF, za pomocą przeglądarki sieci Web, za pomocą przeglądarki wystawiającego żądania HTTP GET do określonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="14ca3-128">You have successfully accessed the WCF Data Services from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="14ca3-129">Przeglądarki sieci Web zapewnia prosty sposób do eksperymentowania przy użyciu składni adresowania żądań i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="14ca3-129">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="14ca3-130">Jednak usługa danych produkcyjnych nie jest ogólnie dostępny przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="14ca3-130">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="14ca3-131">Zazwyczaj aplikacje wchodzą w interakcję z usługą danych przy użyciu aplikacji kod lub języków skryptów.</span><span class="sxs-lookup"><span data-stu-id="14ca3-131">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="14ca3-132">Następnie utworzysz aplikację kliencką, która korzysta z bibliotek klienta na dostęp do zasobów usługi danych, tak, jakby były one wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) obiektów:</span><span class="sxs-lookup"><span data-stu-id="14ca3-132">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="14ca3-133">Tworzenie aplikacji klienckich programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="14ca3-133">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="14ca3-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14ca3-134">See also</span></span>

- [<span data-ttu-id="14ca3-135">Uzyskiwanie dostępu do zasobów usługi danych</span><span class="sxs-lookup"><span data-stu-id="14ca3-135">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
