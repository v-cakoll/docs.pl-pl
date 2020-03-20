---
title: Przykład integracji elementu SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 2f12d80085e3ac27dac8ce80b6bb09f69337bfd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143957"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="ff781-102">Przykład integracji elementu SystemWebRouting</span><span class="sxs-lookup"><span data-stu-id="ff781-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="ff781-103">W tym przykładzie pokazano integracji warstwy <xref:System.Web.Routing> hostingu z klasami w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="ff781-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="ff781-104">Klasy w <xref:System.Web.Routing> obszarze nazw umożliwiają aplikacji używanie adresów URL, które nie odpowiadają bezpośrednio zasobowi fizycznemu.</span><span class="sxs-lookup"><span data-stu-id="ff781-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="ff781-105">Za pomocą routingu sieci Web umożliwia deweloperowi tworzenie adresów wirtualnych dla protokołu HTTP, które są następnie mapowane z powrotem do rzeczywistych usług WCF.</span><span class="sxs-lookup"><span data-stu-id="ff781-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="ff781-106">Jest to przydatne, gdy usługa WCF musi być hostowana bez konieczności fizycznego pliku lub zasobu lub gdy usługi muszą być dostępne za pomocą adresów URL, które nie zawierają plików, takich jak .html lub .aspx.</span><span class="sxs-lookup"><span data-stu-id="ff781-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="ff781-107">W tym przykładzie pokazano, <xref:System.Web.Routing.RouteTable> jak korzystać z klasy do tworzenia wirtualnych identyfikatorów URI, które mapują do uruchomionych usług zdefiniowanych w global.asax.</span><span class="sxs-lookup"><span data-stu-id="ff781-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span>

> [!NOTE]
> <span data-ttu-id="ff781-108">Klasy w <xref:System.Web.Routing> obszarze nazw działają tylko dla usług obsługiwanych za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ff781-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="ff781-109">W tym przykładzie użyto WCF do utworzenia dwóch źródeł danych RSS: paszy `movies` i `channels` pliku danych.</span><span class="sxs-lookup"><span data-stu-id="ff781-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="ff781-110">Adresy URL, aby aktywować usługi nie zawierają `Application_Start` rozszerzenia i `Global` są zarejestrowane <xref:System.Web.HttpApplication> w metodzie klasy pochodzące z klasy.</span><span class="sxs-lookup"><span data-stu-id="ff781-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff781-111">Ten przykład działa tylko w internetowych usługach informacyjnych (IIS) 7.0 i nowszych, ponieważ usługi IIS 6.0 używają innej metody obsługi adresów URL bez rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="ff781-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="ff781-112">Aby pobrać ten przykład</span><span class="sxs-lookup"><span data-stu-id="ff781-112">To download this sample</span></span>
  
<span data-ttu-id="ff781-113">Ten przykład może być już zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ff781-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="ff781-114">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="ff781-114">Check for the following (default) directory before continuing.</span></span>  

`<InstallDrive>:\WF_WCF_Samples`  

 <span data-ttu-id="ff781-115">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="ff781-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ff781-116">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ff781-116">This sample is located in the following directory.</span></span>  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="ff781-117">Aby użyć tej próbki</span><span class="sxs-lookup"><span data-stu-id="ff781-117">To use this sample</span></span>  
  
1. <span data-ttu-id="ff781-118">Za pomocą programu Visual Studio otwórz plik WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="ff781-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="ff781-119">Aby uruchomić rozwiązanie i uruchomić serwer programistyczny sieci Web, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="ff781-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="ff781-120">Pojawi się lista katalogów dla próbki.</span><span class="sxs-lookup"><span data-stu-id="ff781-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="ff781-121">Należy zauważyć, że nie ma żadnych plików z rozszerzeniem pliku .svc.</span><span class="sxs-lookup"><span data-stu-id="ff781-121">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="ff781-122">Na pasku adresu `movies` dodaj go do adresu `http://localhost:[port]/movies` URL, aby odczytywać i naciskać klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="ff781-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="ff781-123">Kanał filmów pojawi się w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="ff781-123">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="ff781-124">Na pasku adresu `channels` dodaj do adresu URL, aby był odczytywany `http://localhost:[port]/channels` i nacisnąć klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="ff781-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="ff781-125">Kanał kanałowy pojawi się w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="ff781-125">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="ff781-126">Zamknij przeglądarkę sieci Web, naciskając klawisze ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="ff781-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="ff781-127">Jeśli serwer deweloperów nie został przerwany, kliknij prawym przyciskiem myszy ikonę obszaru powiadomień i wybierz pozycję **Zatrzymaj**.</span><span class="sxs-lookup"><span data-stu-id="ff781-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="ff781-128">Aby użyć tego przykładu hostowanego w użyczonych w u.</span><span class="sxs-lookup"><span data-stu-id="ff781-128">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="ff781-129">Za pomocą programu Visual Studio otwórz plik WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="ff781-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="ff781-130">Tworzenie projektu, naciskając klawisze CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="ff781-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="ff781-131">Tworzenie aplikacji sieci Web w Menedżerze internetowych usług informacyjnych (IIS).</span><span class="sxs-lookup"><span data-stu-id="ff781-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="ff781-132">W Menedżerze usług IIS kliknij prawym przyciskiem myszy **domyślną witrynę sieci Web** i wybierz **polecenie Dodaj aplikację**.</span><span class="sxs-lookup"><span data-stu-id="ff781-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="ff781-133">Dla **aliasu**wpisz `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="ff781-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="ff781-134">W przypadku **ścieżki fizycznej**wybierz folder Usługa wewnątrz projektu.</span><span class="sxs-lookup"><span data-stu-id="ff781-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="ff781-135">Naciśnij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ff781-135">Press **OK**.</span></span>  
  
4. <span data-ttu-id="ff781-136">Uruchom aplikację, klikając prawym przyciskiem myszy aplikację sieci Web i wybierając pozycję **Zarządzaj aplikacją,** a następnie **przeglądaj**.</span><span class="sxs-lookup"><span data-stu-id="ff781-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="ff781-137">Na pasku adresu `movies` dodaj do adresu URL, aby był odczytywany `http://localhost:[port]/movies` i nacisnąć klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="ff781-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="ff781-138">Kanał filmów pojawi się w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="ff781-138">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="ff781-139">Na pasku adresu `channels` dodaj do adresu URL, aby był odczytywany `http://localhost:[port]/channels` i nacisnąć klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="ff781-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="ff781-140">Kanał kanałowy pojawi się w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="ff781-140">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="ff781-141">Zamknij przeglądarkę sieci Web, naciskając klawisze ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="ff781-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="ff781-142">W tym przykładzie pokazano, że warstwa hostingu jest <xref:System.Web.Routing> w stanie komponować z klasami w obszarze nazw do routingu żądań usług hostowanych za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ff781-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff781-143">Należy zaktualizować domyślną wersję puli aplikacji do programu .NET Framework 4, jeśli jest ustawiona na wersję 2.</span><span class="sxs-lookup"><span data-stu-id="ff781-143">You must update the default application pool version to .NET Framework 4 if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff781-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff781-144">See also</span></span>

- <span data-ttu-id="ff781-145">[AppFabric Hosting i trwałość przykłady](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ff781-145">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
