---
title: Federacja — przykład
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 9ec462f88c0e3a039b7f288554be3e28f13ece08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144672"
---
# <a name="federation-sample"></a><span data-ttu-id="2a410-102">Federacja — przykład</span><span class="sxs-lookup"><span data-stu-id="2a410-102">Federation Sample</span></span>
<span data-ttu-id="2a410-103">Ten przykład pokazuje zabezpieczenia federacyjne.</span><span class="sxs-lookup"><span data-stu-id="2a410-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="2a410-104">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="2a410-104">Sample Details</span></span>  
 <span data-ttu-id="2a410-105">Windows Communication Foundation (WCF) zapewnia obsługę wdrażania architektur zabezpieczeń `wsFederationHttpBinding`federacyjnego za pośrednictwem .</span><span class="sxs-lookup"><span data-stu-id="2a410-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="2a410-106">Zapewnia `wsFederationHttpBinding` bezpieczne, niezawodne i interoperacyjne powiązanie, które obejmuje użycie protokołu HTTP jako podstawowy mechanizm transportu dla komunikacji żądania/odpowiedzi i Text/XML jako formatu przewodowego do kodowania.</span><span class="sxs-lookup"><span data-stu-id="2a410-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="2a410-107">Aby uzyskać więcej informacji na temat federacji w WCF, zobacz [Federacja](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="2a410-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="2a410-108">Scenariusz składa się z 4 sztuk:</span><span class="sxs-lookup"><span data-stu-id="2a410-108">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="2a410-109">Usługa Księgarnia</span><span class="sxs-lookup"><span data-stu-id="2a410-109">BookStore service</span></span>  
  
- <span data-ttu-id="2a410-110">Księgarnia STS</span><span class="sxs-lookup"><span data-stu-id="2a410-110">BookStore STS</span></span>  
  
- <span data-ttu-id="2a410-111">Strona głównaRealm STS</span><span class="sxs-lookup"><span data-stu-id="2a410-111">HomeRealm STS</span></span>  
  
- <span data-ttu-id="2a410-112">Klient księgarni</span><span class="sxs-lookup"><span data-stu-id="2a410-112">BookStore Client</span></span>  
  
 <span data-ttu-id="2a410-113">Usługa Księgarnia obsługuje dwie `BrowseBooks` `BuyBook`operacje i .</span><span class="sxs-lookup"><span data-stu-id="2a410-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="2a410-114">Umożliwia anonimowy `BrowseBooks` dostęp do operacji, ale wymaga `BuyBooks` uwierzytelnionego dostępu do operacji.</span><span class="sxs-lookup"><span data-stu-id="2a410-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="2a410-115">Uwierzytelnianie ma formę tokenu wystawionego przez sts księgarni.</span><span class="sxs-lookup"><span data-stu-id="2a410-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="2a410-116">Plik konfiguracyjny usługi Księgarni wskazuje klientom usługę `wsFederationHttpBinding`BOOKStore STS przy użyciu pliku .</span><span class="sxs-lookup"><span data-stu-id="2a410-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="2a410-117">BookStore STS następnie wymaga, aby klienci uwierzytelnić przy użyciu tokenu wystawionego przez HomeRealm STS.</span><span class="sxs-lookup"><span data-stu-id="2a410-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="2a410-118">Ponownie, plik konfiguracyjny dla BookStore STS wskazuje klientom `wsFederationHttpBinding`HomeRealm STS za pomocą .</span><span class="sxs-lookup"><span data-stu-id="2a410-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="2a410-119">Kolejność zdarzeń podczas uzyskiwania `BuyBook` dostępu do operacji jest następująca:</span><span class="sxs-lookup"><span data-stu-id="2a410-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="2a410-120">Klient uwierzytelnia się w homerealm STS przy użyciu poświadczeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2a410-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="2a410-121">HomeRealm STS wystawia token, który może służyć do uwierzytelniania w sts księgarni.</span><span class="sxs-lookup"><span data-stu-id="2a410-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="2a410-122">Klient uwierzytelnia się w sts księgarni przy użyciu tokenu wydanego przez HomeRealm STS.</span><span class="sxs-lookup"><span data-stu-id="2a410-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="2a410-123">BookStore STS wystawia token, który może służyć do uwierzytelniania w usłudze Księgarni.</span><span class="sxs-lookup"><span data-stu-id="2a410-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="2a410-124">Klient uwierzytelnia się w usłudze Księgarni przy użyciu tokenu wystawionego przez sts księgarni.</span><span class="sxs-lookup"><span data-stu-id="2a410-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="2a410-125">Klient uzyskuje dostęp `BuyBook` do operacji.</span><span class="sxs-lookup"><span data-stu-id="2a410-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="2a410-126">Zobacz poniższe instrukcje dotyczące konfigurowania i uruchamiania tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="2a410-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a410-127">Aby uruchomić ten przykład, musisz mieć uprawnienia do zapisu w katalogu **wwwroot.**</span><span class="sxs-lookup"><span data-stu-id="2a410-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2a410-128">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="2a410-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2a410-129">Otwórz okno polecenia SDK.</span><span class="sxs-lookup"><span data-stu-id="2a410-129">Open the SDK command window.</span></span> <span data-ttu-id="2a410-130">W przykładowej ścieżce uruchom plik Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="2a410-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="2a410-131">Spowoduje to utworzenie katalogów wirtualnych wymaganych dla próbki i zainstalowanie wymaganych certyfikatów z odpowiednimi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="2a410-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2a410-132">Plik wsadowy setup.bat jest przeznaczony do uruchamiania z wiersza polecenia SDK systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2a410-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="2a410-133">Wymaga to, aby zmienna środowiskowa MSSDK wskazywała katalog, w którym jest zainstalowany pakiet SDK.</span><span class="sxs-lookup"><span data-stu-id="2a410-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="2a410-134">Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia zestawu Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="2a410-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="2a410-135">W systemie Windows Vista należy upewnić się, że zgodność zarządzania usługami IIS 6.0 jest zainstalowana, ponieważ konfiguracja używa skryptów administratora usług IIS.</span><span class="sxs-lookup"><span data-stu-id="2a410-135">On Windows Vista, you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="2a410-136">Uruchamianie skryptu konfiguracji w systemie Windows Vista wymaga uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="2a410-136">Running the set-up script on Windows Vista requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="2a410-137">Otwórz FederationSample.sln w programie Visual Studio i wybierz **pozycję Zbudować rozwiązanie** z menu **Kompilacja.**</span><span class="sxs-lookup"><span data-stu-id="2a410-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="2a410-138">Spowoduje to zbudowanie typowych plików projektu, usługi Księgarnia, StS księgarni, HomeRealm STS i wdraża je w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="2a410-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="2a410-139">Spowoduje to również kompilację aplikacji klienta księgarni i umieszcza plik wykonywalny BookStoreClient.exe w folderze FederationSample\BookStoreClient\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="2a410-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="2a410-140">Kliknij dwukrotnie pozycję BookStoreClient.exe.</span><span class="sxs-lookup"><span data-stu-id="2a410-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="2a410-141">Zostanie wyświetlone okno BookStoreClient.</span><span class="sxs-lookup"><span data-stu-id="2a410-141">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="2a410-142">Książki dostępne w księgarni można przeglądać, klikając pozycję **Przeglądaj książki**.</span><span class="sxs-lookup"><span data-stu-id="2a410-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="2a410-143">Aby kupić konkretną książkę, wybierz książkę na liście i kliknij pozycję **Kup książkę**.</span><span class="sxs-lookup"><span data-stu-id="2a410-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="2a410-144">Aplikacja uruchamia się i uwierzytelnia przy użyciu uwierzytelniania systemu Windows za pomocą usługi tokenu zabezpieczającego HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="2a410-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="2a410-145">Próbka jest skonfigurowana tak, aby umożliwić użytkownikom zakup książek, które kosztują 15 USD lub mniej.</span><span class="sxs-lookup"><span data-stu-id="2a410-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="2a410-146">Próba zakupu książek, które kosztują więcej niż 15 USD powoduje, że klient otrzymuje komunikat Odmowa dostępu z usługi Księgarnia.</span><span class="sxs-lookup"><span data-stu-id="2a410-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2a410-147">Przykład nie aktualizuje limitu kredytowego użytkownika po zakupie.</span><span class="sxs-lookup"><span data-stu-id="2a410-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="2a410-148">Książki można wielokrotnie kupować w ramach (stałego) limitu kredytowego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2a410-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="2a410-149">Aby oczyścić</span><span class="sxs-lookup"><span data-stu-id="2a410-149">To clean up</span></span>  
  
1. <span data-ttu-id="2a410-150">Uruchom Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="2a410-150">Run Cleanup.bat.</span></span> <span data-ttu-id="2a410-151">Spowoduje to usunięcie katalogów wirtualnych utworzonych podczas konfigurowania, a także usunięcie certyfikatów zainstalowanych podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="2a410-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2a410-152">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2a410-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2a410-153">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="2a410-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2a410-154">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="2a410-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2a410-155">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2a410-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
