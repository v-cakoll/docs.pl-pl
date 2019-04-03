---
title: Federacja — przykład
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: e9f0c47a1bafe715a40d150a77543ca71a249920
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816606"
---
# <a name="federation-sample"></a><span data-ttu-id="47a04-102">Federacja — przykład</span><span class="sxs-lookup"><span data-stu-id="47a04-102">Federation Sample</span></span>
<span data-ttu-id="47a04-103">Niniejszy przykład pokazuje zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="47a04-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="47a04-104">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="47a04-104">Sample Details</span></span>  
 <span data-ttu-id="47a04-105">Windows Communication Foundation (WCF) obsługuje wdrażanie architektury zabezpieczeń za pomocą `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="47a04-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="47a04-106">`wsFederationHttpBinding` Zapewnia bezpieczne, niezawodne i interoperacyjne powiązanie, które obejmuje korzystanie z protokołu HTTP jako podstawowy mechanizm transportu dla komunikacji żądanie/nietypizowana odpowiedź i Text/XML do kodowania w formacie o komunikacji sieciowej.</span><span class="sxs-lookup"><span data-stu-id="47a04-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="47a04-107">Aby uzyskać więcej informacji na temat federacji w programie WCF zobacz [Federacji](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="47a04-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="47a04-108">Scenariusz składa się z 4 elementów:</span><span class="sxs-lookup"><span data-stu-id="47a04-108">The scenario is made up of 4 pieces:</span></span>  
  
-   <span data-ttu-id="47a04-109">Usługa księgarni</span><span class="sxs-lookup"><span data-stu-id="47a04-109">BookStore service</span></span>  
  
-   <span data-ttu-id="47a04-110">Księgarni usługi STS</span><span class="sxs-lookup"><span data-stu-id="47a04-110">BookStore STS</span></span>  
  
-   <span data-ttu-id="47a04-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="47a04-111">HomeRealm STS</span></span>  
  
-   <span data-ttu-id="47a04-112">Księgarni klienta</span><span class="sxs-lookup"><span data-stu-id="47a04-112">BookStore Client</span></span>  
  
 <span data-ttu-id="47a04-113">Usługa księgarni obsługuje dwie operacje `BrowseBooks` i `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="47a04-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="47a04-114">Zezwala na dostęp anonimowy do `BrowseBooks` operacja, ale wymaga dostępu uwierzytelnionego do dostępu `BuyBooks` operacji.</span><span class="sxs-lookup"><span data-stu-id="47a04-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="47a04-115">Uwierzytelnianie mają postać token wystawiony przez usługę STS księgarni.</span><span class="sxs-lookup"><span data-stu-id="47a04-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="47a04-116">Wskazuje plik konfiguracyjny usługi księgarni klientów przy użyciu usługi STS księgarni `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="47a04-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="47a04-117">Usługa STS księgarni wymaga, że klienci uwierzytelniania przy użyciu tokenu wystawionego przez usługę STS HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="47a04-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="47a04-118">Ponownie plik konfiguracji dla usługi STS księgarni wskazuje klientów przy użyciu usługi STS HomeRealm `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="47a04-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="47a04-119">Kolejność zdarzeń przy uzyskiwaniu dostępu do `BuyBook` operacja jest w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="47a04-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1.  <span data-ttu-id="47a04-120">Klient uwierzytelnia się do usługi STS HomeRealm przy użyciu poświadczeń Windows.</span><span class="sxs-lookup"><span data-stu-id="47a04-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2.  <span data-ttu-id="47a04-121">HomeRealm usługi STS wystawia token, który może służyć do uwierzytelniania usługi STS księgarni.</span><span class="sxs-lookup"><span data-stu-id="47a04-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3.  <span data-ttu-id="47a04-122">Klient jest uwierzytelniany przy użyciu tokenu wystawionego przez usługę STS HomeRealm usługi STS księgarni.</span><span class="sxs-lookup"><span data-stu-id="47a04-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4.  <span data-ttu-id="47a04-123">Księgarni Usługa STS wystawia token, który może służyć do uwierzytelniania w usłudze księgarni.</span><span class="sxs-lookup"><span data-stu-id="47a04-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5.  <span data-ttu-id="47a04-124">Klient uwierzytelnia się w usłudze księgarni przy użyciu tokenu wystawionego przez usługę STS księgarni.</span><span class="sxs-lookup"><span data-stu-id="47a04-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6.  <span data-ttu-id="47a04-125">Klient uzyskuje dostęp do `BuyBook` operacji.</span><span class="sxs-lookup"><span data-stu-id="47a04-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="47a04-126">Zobacz następujące instrukcje dotyczące sposobu konfigurowania i przeprowadzania tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="47a04-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47a04-127">Musi mieć uprawnienia do zapisu **wwwroot** katalogu, aby uruchomić ten przykład.</span><span class="sxs-lookup"><span data-stu-id="47a04-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="47a04-128">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="47a04-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="47a04-129">Otwórz okno polecenia zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="47a04-129">Open the SDK command window.</span></span> <span data-ttu-id="47a04-130">W ścieżce próbki należy uruchomić Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="47a04-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="47a04-131">Tworzy katalogi wirtualne wymagane dla przykładu i instaluje wymagane certyfikaty z odpowiednimi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="47a04-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="47a04-132">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wierszem polecenia Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="47a04-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="47a04-133">Wymaga to, że zmienna środowiskowa MSSDK odwołują się do katalogu, w którym jest zainstalowany zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="47a04-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="47a04-134">Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="47a04-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="47a04-135">Na [!INCLUDE[wv](../../../../includes/wv-md.md)], należy upewnić się, że zgodność z narzędziami zarządzania usług IIS 6.0 jest zainstalowany, ponieważ konfigurowania używa skrypty administratora usług IIS.</span><span class="sxs-lookup"><span data-stu-id="47a04-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="47a04-136">Uruchamianie skryptu konfiguracji [!INCLUDE[wv](../../../../includes/wv-md.md)] wymaga uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="47a04-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2.  <span data-ttu-id="47a04-137">Otwórz FederationSample.sln w programie Visual Studio i wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="47a04-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="47a04-138">Kompilacje wspólne pliki projektu, księgarni usługi STS księgarni, HomeRealm STS i ich wdrażania w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="47a04-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="47a04-139">To również kompilacji aplikacji klienckiej księgarni i umieszcza BookStoreClient.exe wykonywalny w folderze FederationSample\BookStoreClient\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="47a04-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3.  <span data-ttu-id="47a04-140">Double-click BookStoreClient.exe.</span><span class="sxs-lookup"><span data-stu-id="47a04-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="47a04-141">Zostanie wyświetlone okno BookStoreClient.</span><span class="sxs-lookup"><span data-stu-id="47a04-141">The BookStoreClient window is displayed.</span></span>  
  
4.  <span data-ttu-id="47a04-142">Możesz przeglądać dostępne w księgarni książki, klikając **Przeglądaj książki**.</span><span class="sxs-lookup"><span data-stu-id="47a04-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5.  <span data-ttu-id="47a04-143">Aby dokonać zakupu wybranej książki, wybierz książkę na liście, a następnie kliknij przycisk **kupić książki**.</span><span class="sxs-lookup"><span data-stu-id="47a04-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="47a04-144">Aplikacja uruchamia się i jest uwierzytelniany przy użyciu uwierzytelniania Windows za pomocą usługi tokenu zabezpieczającego HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="47a04-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="47a04-145">Próbka jest skonfigurowane tak, aby umożliwić użytkownikom kupowanie książek, które koszt 15 USD lub mniej.</span><span class="sxs-lookup"><span data-stu-id="47a04-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="47a04-146">Podjęto próbę kupowanie książek, które są droższe niż 15 USD wyniki w kliencie pobieranie komunikat Odmowa dostępu z usługi Store książek.</span><span class="sxs-lookup"><span data-stu-id="47a04-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="47a04-147">Przykład nie aktualizuje limit środków użytkownika po zakupie.</span><span class="sxs-lookup"><span data-stu-id="47a04-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="47a04-148">Można wielokrotnie kupowanie książek w ramach limitu środków (stałe) użytkownika.</span><span class="sxs-lookup"><span data-stu-id="47a04-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="47a04-149">Aby wyczyścić</span><span class="sxs-lookup"><span data-stu-id="47a04-149">To clean up</span></span>  
  
1.  <span data-ttu-id="47a04-150">Uruchom Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="47a04-150">Run Cleanup.bat.</span></span> <span data-ttu-id="47a04-151">Usuwa katalogi wirtualne, które były tworzone podczas konfiguracji i usuwa również zainstalowane podczas instalacji certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="47a04-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="47a04-152">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="47a04-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="47a04-153">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="47a04-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="47a04-154">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="47a04-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="47a04-155">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="47a04-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  
