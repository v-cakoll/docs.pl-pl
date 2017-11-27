---
title: "Przykład integracji elementu SystemWebRouting"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e5050834ff01ebb6a25e746d88f7d328ded505cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="a7a4e-102">Przykład integracji elementu SystemWebRouting</span><span class="sxs-lookup"><span data-stu-id="a7a4e-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="a7a4e-103">W tym przykładzie pokazano integracji hostingu warstwy z klas w <xref:System.Web.Routing> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="a7a4e-104">Klasy w <xref:System.Web.Routing> przestrzeni nazw Zezwalaj aplikacji na używanie adresów URL, które nie odpowiadają bezpośrednio zasób fizyczny.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="a7a4e-105">Przy użyciu routingu w sieci Web umożliwia deweloperom tworzenie wirtualnych adresów dla protokołu HTTP, które następnie są mapowane do rzeczywistego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="a7a4e-106">Jest to przydatne, gdy usługa WCF musi być obsługiwana bez konieczności fizycznej plik lub zasób, lub gdy usług muszą być dostępne z adresami URL, które nie zawierają plików, takich jak HTML lub aspx.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="a7a4e-107">W tym przykładzie pokazano, jak korzystać z <xref:System.Web.Routing.RouteTable> klasy w celu utworzenia wirtualnego identyfikatorów URI mapowane na uruchamianie usług zdefiniowane w pliku global.asax.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> <span data-ttu-id="a7a4e-108">Na przykład istnieją dwa źródła danych RSS utworzone przy użyciu programu WCF: `movies` źródła danych i `channels` źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-108">For this example, there are two RSS feeds created using WCF: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="a7a4e-109">Adresy URL do aktywowania usługi nie zawiera rozszerzenia i są rejestrowane w `Application_Start` metody `Global` klasą pochodną <xref:System.Web.HttpApplication.Application_Start> klasy.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-109">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication.Application_Start> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7a4e-110">Klasy w <xref:System.Web.Routing> przestrzeni nazw jest prawidłowe tylko dla usługi hostowanej za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-110">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7a4e-111">W tym przykładzie działa tylko [!INCLUDE[iisver](../../../../includes/iisver-md.md)], jako [!INCLUDE[iis60](../../../../includes/iis60-md.md)] używa innej metody do obsługi adresów URL bez rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-111">This sample only works in [!INCLUDE[iisver](../../../../includes/iisver-md.md)], as [!INCLUDE[iis60](../../../../includes/iis60-md.md)] uses a different method for supporting extension-less URLs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a7a4e-112">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a7a4e-113">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a7a4e-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a7a4e-114">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a7a4e-115">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a7a4e-116">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="a7a4e-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="a7a4e-117">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-117">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="a7a4e-118">Aby uruchomić rozwiązanie i uruchomić serwera wdrożeniowego sieci Web, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-118">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="a7a4e-119">Zostanie wyświetlone listę przykładowej katalogów.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-119">A directory listing for the sample appears.</span></span> <span data-ttu-id="a7a4e-120">Należy pamiętać, że nie ma żadnych plików z rozszerzeniem nazwy pliku svc.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-120">Note that there are no files with an .svc file extension.</span></span>  
  
3.  <span data-ttu-id="a7a4e-121">Na pasku adresu dodać `movies` do adresu URL, więc to odczyty http://localhost: [portu] / filmy i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-121">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="a7a4e-122">Źródła strumieniowego filmów zostanie wyświetlona w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-122">The movies feed appears in the browser.</span></span>  
  
4.  <span data-ttu-id="a7a4e-123">Na pasku adresu dodać `channels` do adresu URL, więc to odczyty http://localhost: [portu] / kanałów i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-123">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="a7a4e-124">Źródło strumieniowe kanały zostanie wyświetlona w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-124">The channels feed appears in the browser.</span></span>  
  
5.  <span data-ttu-id="a7a4e-125">Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-125">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="a7a4e-126">Jeśli nie zakończył serwera wdrożeniowego programu, kliknij prawym przyciskiem myszy ikonę w obszarze powiadomień i wybierz **zatrzymać**.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-126">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="a7a4e-127">Aby użyć tego przykładu, podczas udostępniania w usługach IIS</span><span class="sxs-lookup"><span data-stu-id="a7a4e-127">To use this sample when hosted in IIS</span></span>  
  
1.  <span data-ttu-id="a7a4e-128">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-128">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="a7a4e-129">Skompiluj projekt, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-129">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a7a4e-130">Utwórz aplikację sieci Web w programie Internet Information Services (IIS) Manager.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-130">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="a7a4e-131">W Menedżerze usług IIS kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** i wybierz **Dodawanie aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-131">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2.  <span data-ttu-id="a7a4e-132">Aby uzyskać **alias**, wpisz w `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-132">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3.  <span data-ttu-id="a7a4e-133">Aby uzyskać **ścieżka fizyczna**, wybierz folder usługi wewnątrz projektu.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-133">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4.  <span data-ttu-id="a7a4e-134">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-134">Press **OK**.</span></span>  
  
4.  <span data-ttu-id="a7a4e-135">Uruchom aplikację, klikając prawym przyciskiem myszy aplikację sieci Web i wybierając polecenie **aplikacji Zarządzanie** , a następnie **Przeglądaj**.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-135">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5.  <span data-ttu-id="a7a4e-136">Na pasku adresu dodać `movies` do adresu URL, więc to odczyty http://localhost: [portu] / filmy i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-136">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="a7a4e-137">Źródła strumieniowego filmów zostanie wyświetlona w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-137">The movies feed appears in the browser.</span></span>  
  
6.  <span data-ttu-id="a7a4e-138">Na pasku adresu dodać `channels` do adresu URL, więc to odczyty http://localhost: [portu] / kanałów i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-138">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="a7a4e-139">Źródło strumieniowe kanały zostanie wyświetlona w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-139">The channels feed appears in the browser.</span></span>  
  
7.  <span data-ttu-id="a7a4e-140">Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-140">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="a7a4e-141">W przykładzie pokazano warstwy obsługi jest w stanie składających się z klas w <xref:System.Web.Routing> przestrzeń nazw dla routingu żądań usług hostowanych za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-141">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7a4e-142">Zaktualizuj domyślnej wersji puli aplikacji do [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] Jeśli ustawiono w wersji 2.</span><span class="sxs-lookup"><span data-stu-id="a7a4e-142">Please update the default application pool version to [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a4e-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7a4e-143">See Also</span></span>  
 [<span data-ttu-id="a7a4e-144">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="a7a4e-144">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
