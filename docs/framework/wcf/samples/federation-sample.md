---
title: Federacja — przykład
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 10087c4c18a4bc24dd36d814619fc265f9987c8c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961428"
---
# <a name="federation-sample"></a><span data-ttu-id="083a8-102">Federacja — przykład</span><span class="sxs-lookup"><span data-stu-id="083a8-102">Federation Sample</span></span>
<span data-ttu-id="083a8-103">Ten przykład pokazuje zabezpieczenia federacyjne.</span><span class="sxs-lookup"><span data-stu-id="083a8-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="083a8-104">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="083a8-104">Sample Details</span></span>  
 <span data-ttu-id="083a8-105">Windows Communication Foundation (WCF) zapewnia obsługę wdrażania federacyjnych architektur zabezpieczeń za pomocą programu `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="083a8-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="083a8-106">`wsFederationHttpBinding` Zapewnia bezpieczne, niezawodne i interoperacyjne powiązanie, które polega na użyciu protokołu HTTP jako podstawowego mechanizmu transportowego do komunikacji żądania/odpowiedzi oraz text/xml jako formatu sieci do kodowania.</span><span class="sxs-lookup"><span data-stu-id="083a8-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="083a8-107">Aby uzyskać więcej informacji na temat Federacji w programie WCF, zobacz [Federacja](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="083a8-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="083a8-108">Scenariusz składa się z 4 sztuk:</span><span class="sxs-lookup"><span data-stu-id="083a8-108">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="083a8-109">Usługa księgarni</span><span class="sxs-lookup"><span data-stu-id="083a8-109">BookStore service</span></span>  
  
- <span data-ttu-id="083a8-110">Księgarni STS</span><span class="sxs-lookup"><span data-stu-id="083a8-110">BookStore STS</span></span>  
  
- <span data-ttu-id="083a8-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="083a8-111">HomeRealm STS</span></span>  
  
- <span data-ttu-id="083a8-112">Klient księgarni</span><span class="sxs-lookup"><span data-stu-id="083a8-112">BookStore Client</span></span>  
  
 <span data-ttu-id="083a8-113">Usługa księgarni obsługuje dwie operacje `BrowseBooks` i. `BuyBook`</span><span class="sxs-lookup"><span data-stu-id="083a8-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="083a8-114">Umożliwia anonimowy dostęp do `BrowseBooks` operacji, ale wymaga dostępu uwierzytelnionego, aby `BuyBooks` uzyskać dostęp do operacji.</span><span class="sxs-lookup"><span data-stu-id="083a8-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="083a8-115">Uwierzytelnianie przyjmuje postać tokenu wystawionego przez usługę STS księgarni.</span><span class="sxs-lookup"><span data-stu-id="083a8-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="083a8-116">Plik konfiguracji dla klientów punktów usługi księgarni w usłudze STS księgarni przy użyciu `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="083a8-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="083a8-117">Usługa STS księgarni wymaga, aby klienci uwierzytelniali się przy użyciu tokenu wystawionego przez usługę HomeRealm STS.</span><span class="sxs-lookup"><span data-stu-id="083a8-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="083a8-118">Ponownie plik konfiguracji dla klientów punktów usługi STS księgarni do usługi STS HomeRealm przy użyciu `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="083a8-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="083a8-119">Sekwencja zdarzeń podczas uzyskiwania dostępu `BuyBook` do operacji jest następująca:</span><span class="sxs-lookup"><span data-stu-id="083a8-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="083a8-120">Klient jest uwierzytelniany w usłudze STS HomeRealm przy użyciu poświadczeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="083a8-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="083a8-121">Usługa STS HomeRealm wystawia token, którego można użyć do uwierzytelniania w usłudze księgarni STS.</span><span class="sxs-lookup"><span data-stu-id="083a8-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="083a8-122">Klient jest uwierzytelniany w usłudze STS księgarni przy użyciu tokenu wystawionego przez usługę HomeRealm STS.</span><span class="sxs-lookup"><span data-stu-id="083a8-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="083a8-123">Usługa STS księgarni wystawia token, którego można użyć do uwierzytelnienia w usłudze księgarni.</span><span class="sxs-lookup"><span data-stu-id="083a8-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="083a8-124">Klient jest uwierzytelniany w usłudze księgarni przy użyciu tokenu wystawionego przez usługę księgarni STS.</span><span class="sxs-lookup"><span data-stu-id="083a8-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="083a8-125">Klient uzyskuje dostęp `BuyBook` do operacji.</span><span class="sxs-lookup"><span data-stu-id="083a8-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="083a8-126">Zapoznaj się z poniższymi instrukcjami dotyczącymi sposobu konfigurowania i uruchamiania tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="083a8-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="083a8-127">Aby uruchomić ten przykład, musisz mieć uprawnienia do zapisu w katalogu **wwwroot** .</span><span class="sxs-lookup"><span data-stu-id="083a8-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="083a8-128">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="083a8-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="083a8-129">Otwórz okno polecenia zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="083a8-129">Open the SDK command window.</span></span> <span data-ttu-id="083a8-130">W przykładowej ścieżce uruchom setup. bat.</span><span class="sxs-lookup"><span data-stu-id="083a8-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="083a8-131">Spowoduje to utworzenie katalogów wirtualnych wymaganych dla przykładu i zainstalowanie wymaganych certyfikatów z odpowiednimi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="083a8-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="083a8-132">Plik wsadowy Setup. bat został zaprojektowany tak, aby można go było uruchomić z poziomu wiersza polecenia Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="083a8-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="083a8-133">Wymaga, aby zmienna środowiskowa MSSDK wskazywała katalog, w którym zainstalowano zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="083a8-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="083a8-134">Ta zmienna środowiskowa jest ustawiana automatycznie w wierszu polecenia Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="083a8-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="083a8-135">W [!INCLUDE[wv](../../../../includes/wv-md.md)]systemie należy upewnić się, że zgodność z zarządzaniem usługami IIS 6,0 jest zainstalowana, ponieważ konfiguracja używa skryptów administratora usług IIS.</span><span class="sxs-lookup"><span data-stu-id="083a8-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="083a8-136">Uruchomienie skryptu konfiguracji w [!INCLUDE[wv](../../../../includes/wv-md.md)] programie wymaga uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="083a8-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="083a8-137">Otwórz FederationSample. sln w programie Visual Studio i wybierz opcję **Kompiluj rozwiązanie** z menu **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="083a8-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="083a8-138">Powoduje to utworzenie wspólnych plików projektu, usług księgarni, księgarni STS, HomeRealm STS i wdrożenie ich w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="083a8-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="083a8-139">Powoduje to również kompilację aplikacji klienckiej księgarni i umieszczenie pliku wykonywalnego BookStoreClient. exe w folderze FederationSample\BookStoreClient\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="083a8-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="083a8-140">Double-click BookStoreClient.exe.</span><span class="sxs-lookup"><span data-stu-id="083a8-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="083a8-141">Zostanie wyświetlone okno BookStoreClient.</span><span class="sxs-lookup"><span data-stu-id="083a8-141">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="083a8-142">Książki dostępne w księgarni można przeglądać, klikając pozycję **Przeglądaj książki**.</span><span class="sxs-lookup"><span data-stu-id="083a8-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="083a8-143">Aby zakupić określoną książkę, wybierz ją z listy, a następnie kliknij pozycję **Kup książkę**.</span><span class="sxs-lookup"><span data-stu-id="083a8-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="083a8-144">Aplikacja uruchamia się i uwierzytelnia przy użyciu uwierzytelniania systemu Windows za pomocą usługi tokenu zabezpieczającego HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="083a8-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="083a8-145">Przykład jest skonfigurowany tak, aby zezwalał użytkownikom na kupowanie książek o kosztach $15 lub mniejszych.</span><span class="sxs-lookup"><span data-stu-id="083a8-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="083a8-146">Podjęto próbę zakupu książek, które są droższe niż $15 wyniki w przypadku otrzymania przez klienta komunikatu o odmowie dostępu od usługi książki.</span><span class="sxs-lookup"><span data-stu-id="083a8-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="083a8-147">Przykład nie aktualizuje limitu kredytowego użytkownika po zakupie.</span><span class="sxs-lookup"><span data-stu-id="083a8-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="083a8-148">Można wielokrotnie kupować książki w ramach limitu kredytu użytkownika (ustalonego).</span><span class="sxs-lookup"><span data-stu-id="083a8-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="083a8-149">Aby oczyścić</span><span class="sxs-lookup"><span data-stu-id="083a8-149">To clean up</span></span>  
  
1. <span data-ttu-id="083a8-150">Uruchom Oczyść. bat.</span><span class="sxs-lookup"><span data-stu-id="083a8-150">Run Cleanup.bat.</span></span> <span data-ttu-id="083a8-151">Spowoduje to usunięcie katalogów wirtualnych, które zostały utworzone podczas konfiguracji, a także spowoduje usunięcie certyfikatów zainstalowanych podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="083a8-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="083a8-152">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="083a8-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="083a8-153">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="083a8-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="083a8-154">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="083a8-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="083a8-155">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="083a8-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
