---
title: Federacja — przykład
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: a9c2b91f7d8bdf24476c76fcd479b7f2fb44c90f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806851"
---
# <a name="federation-sample"></a><span data-ttu-id="bc132-102">Federacja — przykład</span><span class="sxs-lookup"><span data-stu-id="bc132-102">Federation Sample</span></span>
<span data-ttu-id="bc132-103">W tym przykładzie przedstawiono zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bc132-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="bc132-104">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="bc132-104">Sample Details</span></span>  
 <span data-ttu-id="bc132-105">Windows Communication Foundation (WCF) zapewnia obsługę wdrażania architektury zabezpieczeń za pomocą `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="bc132-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="bc132-106">`wsFederationHttpBinding` Udostępnia bezpieczne, niezawodne i interoperacyjne powiązanie, które polega na użyciu protokołu HTTP jako podstawowy mechanizm transportu dla komunikacji żądanie/odpowiedź, a Text/XML jako przewodowy format kodowania.</span><span class="sxs-lookup"><span data-stu-id="bc132-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="bc132-107">Aby uzyskać więcej informacji o federacji w programie WCF, zobacz [federacyjnego](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="bc132-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="bc132-108">Scenariusz składa się z 4 części:</span><span class="sxs-lookup"><span data-stu-id="bc132-108">The scenario is made up of 4 pieces:</span></span>  
  
-   <span data-ttu-id="bc132-109">Usługa księgarni</span><span class="sxs-lookup"><span data-stu-id="bc132-109">BookStore service</span></span>  
  
-   <span data-ttu-id="bc132-110">Księgarni STS</span><span class="sxs-lookup"><span data-stu-id="bc132-110">BookStore STS</span></span>  
  
-   <span data-ttu-id="bc132-111">HomeRealm usługi STS</span><span class="sxs-lookup"><span data-stu-id="bc132-111">HomeRealm STS</span></span>  
  
-   <span data-ttu-id="bc132-112">Księgarni klienta</span><span class="sxs-lookup"><span data-stu-id="bc132-112">BookStore Client</span></span>  
  
 <span data-ttu-id="bc132-113">Usługa księgarni obsługuje dwie operacje `BrowseBooks` i `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="bc132-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="bc132-114">Zezwala na dostęp anonimowy do `BrowseBooks` operacji, ale wymaga dostępu uwierzytelnionego dostępu `BuyBooks` operacji.</span><span class="sxs-lookup"><span data-stu-id="bc132-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="bc132-115">Uwierzytelnianie ma postać token wystawiony przez usługę STS księgarni.</span><span class="sxs-lookup"><span data-stu-id="bc132-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="bc132-116">Wskazuje plik konfiguracji usługi księgarni klientów przy użyciu usługi STS księgarni `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="bc132-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="bc132-117">STS księgarni wymaga, aby klienci uwierzytelniania za pomocą token wystawiony przez usługę STS HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="bc132-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="bc132-118">Ponownie, pliku konfiguracji dla usługi STS księgarni wskazuje klientów przy użyciu usługi STS HomeRealm `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="bc132-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="bc132-119">Kolejność zdarzeń przy uzyskiwaniu dostępu do `BuyBook` operacji wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="bc132-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1.  <span data-ttu-id="bc132-120">Uwierzytelnia klienta do usługi STS HomeRealm przy użyciu poświadczeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bc132-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2.  <span data-ttu-id="bc132-121">HomeRealm STS wystawia token, który może służyć do uwierzytelniania usługi STS księgarni.</span><span class="sxs-lookup"><span data-stu-id="bc132-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3.  <span data-ttu-id="bc132-122">Klient przeprowadza uwierzytelnianie za pomocą tokenu wystawiony przez usługę STS HomeRealm usługi STS księgarni.</span><span class="sxs-lookup"><span data-stu-id="bc132-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4.  <span data-ttu-id="bc132-123">Usługa tokenu Zabezpieczającego księgarni wystawia token, który może służyć do uwierzytelniania w usłudze księgarni.</span><span class="sxs-lookup"><span data-stu-id="bc132-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5.  <span data-ttu-id="bc132-124">Klient przeprowadza uwierzytelnianie w usłudze księgarni przy użyciu token wystawiony przez usługę STS księgarni.</span><span class="sxs-lookup"><span data-stu-id="bc132-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6.  <span data-ttu-id="bc132-125">Klient uzyskuje dostęp do `BuyBook` operacji.</span><span class="sxs-lookup"><span data-stu-id="bc132-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="bc132-126">Zobacz następujące instrukcje dotyczące konfigurowania i uruchamiania tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="bc132-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc132-127">Musi mieć uprawnienia do zapisu **wwwroot** katalogu, aby uruchomić ten przykład.</span><span class="sxs-lookup"><span data-stu-id="bc132-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bc132-128">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="bc132-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bc132-129">Otwórz okno polecenia zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="bc132-129">Open the SDK command window.</span></span> <span data-ttu-id="bc132-130">W ścieżce próbki należy uruchomić pliku Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="bc132-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="bc132-131">Tworzy wymagane przykładowej katalogi wirtualne i instaluje wymagane certyfikaty z odpowiednimi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="bc132-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bc132-132">Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z wiersza polecenia systemu Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="bc132-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="bc132-133">Wymaga ona, że zmienna środowiskowa MSSDK odwołują się do katalogu, w którym jest zainstalowany zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="bc132-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="bc132-134">Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia systemu Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="bc132-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="bc132-135">Na [!INCLUDE[wv](../../../../includes/wv-md.md)], musi zapewnić, że zgodność z narzędziami zarządzania usług IIS 6.0 jest zainstalowany, ponieważ skrypty administratora usług IIS korzysta z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bc132-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="bc132-136">Uruchomienie skryptu konfiguracji [!INCLUDE[wv](../../../../includes/wv-md.md)] wymaga uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="bc132-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2.  <span data-ttu-id="bc132-137">Otwórz FederationSample.sln w programie Visual Studio i wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="bc132-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="bc132-138">Tworzy wspólne pliki projektu, księgarni usługi STS księgarni, HomeRealm STS i wdraża je w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="bc132-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="bc132-139">To również kompilacje księgarni aplikacji klienckiej i umieszcza BookStoreClient.exe wykonywalny w folderze FederationSample\BookStoreClient\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="bc132-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3.  <span data-ttu-id="bc132-140">Kliknij dwukrotnie BookStoreClient.exe.</span><span class="sxs-lookup"><span data-stu-id="bc132-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="bc132-141">Zostanie wyświetlone okno BookStoreClient.</span><span class="sxs-lookup"><span data-stu-id="bc132-141">The BookStoreClient window is displayed.</span></span>  
  
4.  <span data-ttu-id="bc132-142">Możesz przeglądać książki w księgarni dostępne klikając **Przeglądaj książek**.</span><span class="sxs-lookup"><span data-stu-id="bc132-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5.  <span data-ttu-id="bc132-143">Aby kupić wybranej książki, wybierz książkę na liście, a następnie kliknij przycisk **kupić książki**.</span><span class="sxs-lookup"><span data-stu-id="bc132-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="bc132-144">Aplikacja jest uruchamiany i jest uwierzytelniany przy użyciu uwierzytelniania systemu Windows z usługi tokenu zabezpieczającego HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="bc132-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="bc132-145">Próbka jest skonfigurowany, aby umożliwić użytkownikom kupowanie książek, których koszt $15 lub mniej.</span><span class="sxs-lookup"><span data-stu-id="bc132-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="bc132-146">Próba kupowanie książek, które koszty były wyższe niż $15 wyniki w kliencie pobieranie komunikat o odmowie dostępu z książki usługi magazynu.</span><span class="sxs-lookup"><span data-stu-id="bc132-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bc132-147">Próbki nie aktualizuje limit kredytu użytkownika po zakupu.</span><span class="sxs-lookup"><span data-stu-id="bc132-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="bc132-148">Możesz kupić wielokrotnie książek w limicie środki (stałe) użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bc132-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="bc132-149">Aby wyczyścić</span><span class="sxs-lookup"><span data-stu-id="bc132-149">To clean up</span></span>  
  
1.  <span data-ttu-id="bc132-150">Uruchom Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="bc132-150">Run Cleanup.bat.</span></span> <span data-ttu-id="bc132-151">Usuwa katalogi wirtualne, które zostały utworzone podczas zestawu w górę, a spowoduje również usunięcie certyfikaty zainstalowane podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="bc132-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc132-152">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bc132-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bc132-153">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="bc132-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bc132-154">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="bc132-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bc132-155">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="bc132-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  
## <a name="see-also"></a><span data-ttu-id="bc132-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc132-156">See Also</span></span>
