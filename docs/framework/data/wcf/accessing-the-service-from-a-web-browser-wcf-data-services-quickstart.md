---
title: "Uzyskiwanie dostępu do usługi z przeglądarki sieci Web (Szybki Start usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71beb254bf258da97207f14afca73cd68c6927ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="d89cd-102">Uzyskiwanie dostępu do usługi z przeglądarki sieci Web (Szybki Start usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="d89cd-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>
<span data-ttu-id="d89cd-103">W tym zadaniu rozpocznie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] z [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] i opcjonalnie Wyłącz źródła odczytu w przeglądarce sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d89cd-103">In this task, you will start the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] from [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="d89cd-104">Możesz zostanie następnie pobrać dokumentu definicji usługi a także uzyskiwać dostęp do danych usługi zasobów poprzez przesłanie żądania HTTP GET za pośrednictwem przeglądarki sieci Web do narażonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="d89cd-104">You will then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d89cd-105">Domyślnie [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] auto przypisuje numeru portu `localhost` identyfikatora URI na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d89cd-105">By default, [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="d89cd-106">To zadanie używa numeru portu `12345` w przykładach identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="d89cd-106">This task uses the port number `12345` in the URI examples.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d89cd-107">jak ustawić określonego numeru portu Twojej [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] projektu zobacz [Tworzenie usługi danych](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="d89cd-107"> how to set a specific port number in your [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] project see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
### <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="d89cd-108">Aby zażądać domyślny dokument usługi przy użyciu programu Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="d89cd-108">To request the default service document by using Internet Explorer</span></span>  
  
1.  <span data-ttu-id="d89cd-109">W programie Internet Explorer z **narzędzia** menu, wybierz opcję **Opcje internetowe**, kliknij przycisk **zawartości** , kliknij pozycję **ustawienia**i wyczyść  **Włącz funkcję przeglądania źródła**.</span><span class="sxs-lookup"><span data-stu-id="d89cd-109">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>  
  
     <span data-ttu-id="d89cd-110">Dzięki temu tego źródła odczytu jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="d89cd-110">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="d89cd-111">Jeśli nie można wyłączyć tę funkcję, przeglądarki sieci Web będzie traktowany zwrócony AtomPub dokumentu zakodowane jako XML źródła danych zamiast nieprzetworzone dane XML.</span><span class="sxs-lookup"><span data-stu-id="d89cd-111">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d89cd-112">Przeglądarka nie może wyświetlić źródła danych jako nieprzetworzone dane XML, nadal należy mogła wyświetlać źródła danych jako kod źródłowy dla strony.</span><span class="sxs-lookup"><span data-stu-id="d89cd-112">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>  
  
2.  <span data-ttu-id="d89cd-113">W [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], naciśnij klawisz F5, aby rozpocząć debugowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d89cd-113">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], press the F5 key to start debugging the application.</span></span>  
  
3.  <span data-ttu-id="d89cd-114">Otwórz przeglądarkę sieci Web na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="d89cd-114">Open a Web browser on the local computer.</span></span> <span data-ttu-id="d89cd-115">Na pasku adresu wpisz następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="d89cd-115">In the address bar, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc  
    ```  
  
     <span data-ttu-id="d89cd-116">To polecenie zwróci usługi dokument domyślny, który znajduje się lista zestawów jednostek, które są udostępniane przez tę usługę danych.</span><span class="sxs-lookup"><span data-stu-id="d89cd-116">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>  
  
### <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="d89cd-117">Aby dostęp do jednostki zestaw zasobów z przeglądarki sieci Web</span><span class="sxs-lookup"><span data-stu-id="d89cd-117">To access entity set resources from a Web browser</span></span>  
  
1.  <span data-ttu-id="d89cd-118">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="d89cd-118">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers  
    ```  
  
     <span data-ttu-id="d89cd-119">To zwraca zestaw wszystkich klientów w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="d89cd-119">This returns a set of all customers in the Northwind sample database.</span></span>  
  
2.  <span data-ttu-id="d89cd-120">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="d89cd-120">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')  
    ```  
  
     <span data-ttu-id="d89cd-121">To polecenie zwróci wystąpienia jednostki dla określonego klienta i `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="d89cd-121">This returns an entity instance for the specific customer, `ALFKI`.</span></span>  
  
3.  <span data-ttu-id="d89cd-122">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="d89cd-122">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders  
    ```  
  
     <span data-ttu-id="d89cd-123">To jest przesyłany relacji między klientami a zamówienia zwraca zestaw wszystkich zleceń dla określonego klienta `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="d89cd-123">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>  
  
4.  <span data-ttu-id="d89cd-124">Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="d89cd-124">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643  
    ```  
  
     <span data-ttu-id="d89cd-125">Filtry to zlecenia, które należą do określonego klienta `ALFKI` tak, aby w dowolnej kolejności jest zwróconych na podstawie wybranych `OrderID` wartość.</span><span class="sxs-lookup"><span data-stu-id="d89cd-125">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d89cd-126">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d89cd-126">Next Steps</span></span>  
 <span data-ttu-id="d89cd-127">Pomyślnie uzyskano dostęp [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] z przeglądarki sieci Web z wystawiania HTTP GET przeglądarką żądania do określonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="d89cd-127">You have successfully accessed the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="d89cd-128">Przeglądarki sieci Web zapewnia prosty sposób na wypróbowanie składni adresowania żądań i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="d89cd-128">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="d89cd-129">Usługi danych produkcyjnych nie jest jednak ogólnie dostępna przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="d89cd-129">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="d89cd-130">Zazwyczaj aplikacje interakcji z usługą danych za pośrednictwem aplikacji kod lub języków skryptów.</span><span class="sxs-lookup"><span data-stu-id="d89cd-130">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="d89cd-131">Następnie utworzysz aplikacji klienckiej, która korzysta z bibliotek klienta można uzyskać dostępu do zasobów usług danych, tak jakby były wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) obiektów:</span><span class="sxs-lookup"><span data-stu-id="d89cd-131">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>  
  
 [<span data-ttu-id="d89cd-132">Tworzenie aplikacji klienckich programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d89cd-132">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a><span data-ttu-id="d89cd-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d89cd-133">See Also</span></span>  
 [<span data-ttu-id="d89cd-134">Uzyskiwanie dostępu do zasobów usługi danych</span><span class="sxs-lookup"><span data-stu-id="d89cd-134">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
