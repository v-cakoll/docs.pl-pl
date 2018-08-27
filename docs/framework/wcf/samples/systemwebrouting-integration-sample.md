---
title: Przykład integracji elementu SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 944eb8f2bd907308e60525f8917fcad826caa472
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932069"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="34acf-102">Przykład integracji elementu SystemWebRouting</span><span class="sxs-lookup"><span data-stu-id="34acf-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="34acf-103">W tym przykładzie przedstawiono warstwy obsługi integracji z klas w <xref:System.Web.Routing> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="34acf-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="34acf-104">Klasy w <xref:System.Web.Routing> przestrzeni nazw Zezwalaj aplikacji na używanie adresów URL, które nie odpowiadają bezpośrednio zasób fizyczny.</span><span class="sxs-lookup"><span data-stu-id="34acf-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="34acf-105">Przy użyciu routingu w sieci Web umożliwia deweloperom tworzenie wirtualnych adresów dla protokołu HTTP, które następnie są mapowane z powrotem na rzeczywiste usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="34acf-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="34acf-106">Jest to przydatne, gdy usługa WCF muszą być obsługiwane bez konieczności fizyczny plik lub zasób lub usług muszą być dostępne z adresami URL, które nie zawierają plików, takich jak HTML lub .aspx.</span><span class="sxs-lookup"><span data-stu-id="34acf-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="34acf-107">W tym przykładzie pokazano, jak wykorzystywać <xref:System.Web.Routing.RouteTable> klasy w celu utworzenia identyfikatorów URI wirtualnych mapowane na uruchamianie usługi zdefiniowane w pliku global.asax.</span><span class="sxs-lookup"><span data-stu-id="34acf-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> 

> [!NOTE]
>  <span data-ttu-id="34acf-108">Klasy w <xref:System.Web.Routing> przestrzeni nazw jest prawidłowe tylko dla usług hostowanych za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="34acf-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="34acf-109">W tym przykładzie użyto usługi WCF, aby utworzyć dwa źródła danych RSS: `movies` kanału informacyjnego i `channels` źródła danych.</span><span class="sxs-lookup"><span data-stu-id="34acf-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="34acf-110">Adresy URL, aby aktywować usługi nie zawiera rozszerzenia i są zarejestrowane w usłudze `Application_Start` metody `Global` klasą pochodną <xref:System.Web.HttpApplication> klasy.</span><span class="sxs-lookup"><span data-stu-id="34acf-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34acf-111">Ten przykład działa tylko w Internet informacji Services (IIS) 7.0 i nowsze, jako usług IIS 6.0 używa innej metody do obsługi adresów URL bez rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="34acf-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="34acf-112">Aby pobrać w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="34acf-112">To download this sample</span></span>
  
<span data-ttu-id="34acf-113">W tym przykładzie może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="34acf-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="34acf-114">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="34acf-114">Check for the following (default) directory before continuing.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 <span data-ttu-id="34acf-115">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="34acf-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="34acf-116">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="34acf-116">This sample is located in the following directory.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="34acf-117">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="34acf-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="34acf-118">Za pomocą programu Visual Studio, otwórz plik WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="34acf-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="34acf-119">Aby uruchomić rozwiązanie i uruchomić serwera wdrożeniowego sieci Web, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="34acf-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="34acf-120">Pojawi się listę katalogów we próbki.</span><span class="sxs-lookup"><span data-stu-id="34acf-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="34acf-121">Należy pamiętać, że nie istnieją żadne pliki z rozszerzeniem nazwy pliku .svc.</span><span class="sxs-lookup"><span data-stu-id="34acf-121">Note that there are no files with an .svc file extension.</span></span>  
  
3.  <span data-ttu-id="34acf-122">Na pasku adresu Dodaj `movies` do adresu URL, tak że odczytuje `http://localhost:[port]/movies` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="34acf-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="34acf-123">Kanał informacyjny filmy zostanie wyświetlona w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="34acf-123">The movies feed appears in the browser.</span></span>  
  
4.  <span data-ttu-id="34acf-124">Na pasku adresu Dodaj `channels` do adresu URL, więc to odczyty `http://localhost:[port]/channels` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="34acf-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="34acf-125">Źródło strumieniowe kanały zostanie wyświetlona w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="34acf-125">The channels feed appears in the browser.</span></span>  
  
5.  <span data-ttu-id="34acf-126">Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="34acf-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="34acf-127">Jeśli nie zakończył serwera wdrożeniowego programu, kliknij prawym przyciskiem myszy ikonę w obszarze powiadomień, a następnie wybierz **zatrzymać**.</span><span class="sxs-lookup"><span data-stu-id="34acf-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="34acf-128">Aby użyć tego przykładu, w przypadku hostowania w usługach IIS</span><span class="sxs-lookup"><span data-stu-id="34acf-128">To use this sample when hosted in IIS</span></span>  
  
1.  <span data-ttu-id="34acf-129">Za pomocą programu Visual Studio, otwórz plik WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="34acf-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="34acf-130">Skompiluj projekt, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="34acf-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="34acf-131">Utwórz aplikację sieci Web w Menedżerze usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="34acf-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="34acf-132">Kliknij prawym przyciskiem myszy w Menedżerze usług IIS **domyślna witryna sieci Web** i wybierz **Dodawanie aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="34acf-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2.  <span data-ttu-id="34acf-133">Aby uzyskać **alias**, wpisz `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="34acf-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3.  <span data-ttu-id="34acf-134">Aby uzyskać **ścieżkę fizyczną**, wybierz folder usługi w projekcie.</span><span class="sxs-lookup"><span data-stu-id="34acf-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4.  <span data-ttu-id="34acf-135">Naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="34acf-135">Press **OK**.</span></span>  
  
4.  <span data-ttu-id="34acf-136">Uruchom aplikację, klikając prawym przyciskiem myszy aplikację sieci Web i wybierając polecenie **Zarządzanie aplikacją** i następnie **Przeglądaj**.</span><span class="sxs-lookup"><span data-stu-id="34acf-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5.  <span data-ttu-id="34acf-137">Na pasku adresu Dodaj `movies` do adresu URL, więc to odczyty `http://localhost:[port]/movies` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="34acf-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="34acf-138">Kanał informacyjny filmy zostanie wyświetlona w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="34acf-138">The movies feed appears in the browser.</span></span>  
  
6.  <span data-ttu-id="34acf-139">Na pasku adresu Dodaj `channels` do adresu URL, więc to odczyty `http://localhost:[port]/channels` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="34acf-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="34acf-140">Źródło strumieniowe kanały zostanie wyświetlona w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="34acf-140">The channels feed appears in the browser.</span></span>  
  
7.  <span data-ttu-id="34acf-141">Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="34acf-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="34acf-142">Niniejszy przykład pokazuje, w warstwie hostingu jest w stanie tworzenie z klasami <xref:System.Web.Routing> przestrzeni nazw w przypadku routingu żądań usług obsługiwanych za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="34acf-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34acf-143">Należy zaktualizować wersję puli aplikacji domyślnej, aby [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] Jeśli jest ustawiony do wersji 2.</span><span class="sxs-lookup"><span data-stu-id="34acf-143">You must update the default application pool version to [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34acf-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34acf-144">See Also</span></span>  
 [<span data-ttu-id="34acf-145">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="34acf-145">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
