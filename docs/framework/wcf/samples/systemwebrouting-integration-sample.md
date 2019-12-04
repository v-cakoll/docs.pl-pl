---
title: Przykład integracji elementu SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 8be76fa97752680700f1c0eb56c1803fc69155d6
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716632"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="15394-102">Przykład integracji elementu SystemWebRouting</span><span class="sxs-lookup"><span data-stu-id="15394-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="15394-103">Ten przykład pokazuje integrację warstwy hostingu z klasami w przestrzeni nazw <xref:System.Web.Routing>.</span><span class="sxs-lookup"><span data-stu-id="15394-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="15394-104">Klasy w przestrzeni nazw <xref:System.Web.Routing> umożliwiają aplikacji korzystanie z adresów URL, które nie są bezpośrednio zgodne z zasobem fizycznym.</span><span class="sxs-lookup"><span data-stu-id="15394-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="15394-105">Użycie routingu sieci Web umożliwia deweloperom tworzenie adresów wirtualnych dla protokołu HTTP, które następnie są mapowane z powrotem do rzeczywistych usług WCF.</span><span class="sxs-lookup"><span data-stu-id="15394-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="15394-106">Jest to przydatne w przypadku, gdy usługa WCF musi być hostowana bez konieczności fizycznego pliku lub zasobu, lub w przypadku uzyskiwania dostępu do usług za pomocą adresów URL, które nie zawierają plików takich jak. html czy. aspx.</span><span class="sxs-lookup"><span data-stu-id="15394-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="15394-107">Ten przykład pokazuje, jak używać klasy <xref:System.Web.Routing.RouteTable> do tworzenia wirtualnych identyfikatorów URI, które mapują na uruchamianie usług zdefiniowanych w Global. asax.</span><span class="sxs-lookup"><span data-stu-id="15394-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> 

> [!NOTE]
> <span data-ttu-id="15394-108">Klasy w przestrzeni nazw <xref:System.Web.Routing> działają tylko dla usług hostowanych za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="15394-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="15394-109">Ten przykład używa programu WCF do tworzenia dwóch źródeł danych RSS: źródła `movies` i źródła `channels`.</span><span class="sxs-lookup"><span data-stu-id="15394-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="15394-110">Adresy URL do aktywowania usług nie zawierają rozszerzenia i są rejestrowane w metodzie `Application_Start` klasy `Global` pochodzącej od klasy <xref:System.Web.HttpApplication>.</span><span class="sxs-lookup"><span data-stu-id="15394-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15394-111">Ten przykład działa tylko w Internet Information Services (IIS) 7,0 i nowszych, ponieważ usługi IIS 6,0 używają innej metody obsługi adresów URL bez rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="15394-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="15394-112">Aby pobrać ten przykład</span><span class="sxs-lookup"><span data-stu-id="15394-112">To download this sample</span></span>
  
<span data-ttu-id="15394-113">Ten przykład może już być zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="15394-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="15394-114">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="15394-114">Check for the following (default) directory before continuing.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 <span data-ttu-id="15394-115">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="15394-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="15394-116">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="15394-116">This sample is located in the following directory.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="15394-117">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="15394-117">To use this sample</span></span>  
  
1. <span data-ttu-id="15394-118">Korzystając z programu Visual Studio, Otwórz plik WebRoutingIntegration. sln.</span><span class="sxs-lookup"><span data-stu-id="15394-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="15394-119">Aby uruchomić rozwiązanie i uruchomić serwer Web Development, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="15394-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="15394-120">Zostanie wyświetlona lista katalogów dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="15394-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="15394-121">Należy zauważyć, że nie ma plików z rozszerzeniem SVC.</span><span class="sxs-lookup"><span data-stu-id="15394-121">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="15394-122">Na pasku adresu Dodaj `movies` do adresu URL, tak aby był odczytywany `http://localhost:[port]/movies` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="15394-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="15394-123">W przeglądarce pojawi się źródło filmów.</span><span class="sxs-lookup"><span data-stu-id="15394-123">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="15394-124">Na pasku adresu Dodaj `channels` do adresu URL, a więc odczytuje `http://localhost:[port]/channels` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="15394-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="15394-125">Kanał informacyjny kanału pojawia się w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="15394-125">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="15394-126">Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="15394-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="15394-127">Jeśli serwer programistyczny nie został zakończony, kliknij prawym przyciskiem myszy ikonę obszaru powiadomień i wybierz polecenie **Zatrzymaj**.</span><span class="sxs-lookup"><span data-stu-id="15394-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="15394-128">Aby użyć tego przykładu, gdy jest hostowany w usługach IIS</span><span class="sxs-lookup"><span data-stu-id="15394-128">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="15394-129">Korzystając z programu Visual Studio, Otwórz plik WebRoutingIntegration. sln.</span><span class="sxs-lookup"><span data-stu-id="15394-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="15394-130">Skompiluj projekt, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="15394-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="15394-131">Utwórz aplikację sieci Web w Menedżerze Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="15394-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="15394-132">W Menedżerze usług IIS kliknij prawym przyciskiem myszy pozycję **Domyślna witryna sieci Web** i wybierz polecenie **Dodaj aplikację**.</span><span class="sxs-lookup"><span data-stu-id="15394-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="15394-133">Dla **aliasu**wpisz w `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="15394-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="15394-134">W polu **Ścieżka fizyczna**wybierz folder usługi wewnątrz projektu.</span><span class="sxs-lookup"><span data-stu-id="15394-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="15394-135">Naciśnij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="15394-135">Press **OK**.</span></span>  
  
4. <span data-ttu-id="15394-136">Uruchom aplikację, klikając prawym przyciskiem myszy aplikację sieci Web i wybierając pozycję **Zarządzaj aplikacją** , a następnie pozycję **Przeglądaj**.</span><span class="sxs-lookup"><span data-stu-id="15394-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="15394-137">Na pasku adresu Dodaj `movies` do adresu URL, a więc odczytuje `http://localhost:[port]/movies` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="15394-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="15394-138">W przeglądarce pojawi się źródło filmów.</span><span class="sxs-lookup"><span data-stu-id="15394-138">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="15394-139">Na pasku adresu Dodaj `channels` do adresu URL, a więc odczytuje `http://localhost:[port]/channels` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="15394-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="15394-140">Kanał informacyjny kanału pojawia się w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="15394-140">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="15394-141">Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="15394-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="15394-142">Ten przykład pokazuje, że warstwa hostingu jest w stanie tworzyć klasy w przestrzeni nazw <xref:System.Web.Routing> na potrzeby routingu żądań usług hostowanych za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="15394-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15394-143">Domyślną wersję puli aplikacji należy zaktualizować do .NET Framework 4, jeśli jest ona ustawiona na wersję 2.</span><span class="sxs-lookup"><span data-stu-id="15394-143">You must update the default application pool version to .NET Framework 4 if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15394-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15394-144">See also</span></span>

- [<span data-ttu-id="15394-145">Przykłady hostingu i trwałości usługi AppFabric</span><span class="sxs-lookup"><span data-stu-id="15394-145">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
