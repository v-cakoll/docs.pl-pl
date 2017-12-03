---
title: "Śledzenie za pomocą pliku tekstowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abb29dc584bbede14adcb396df8cd37a894b6f2f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="tracking-using-a-text-file"></a><span data-ttu-id="d0afc-102">Śledzenie za pomocą pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="d0afc-102">Tracking Using a Text File</span></span>
<span data-ttu-id="d0afc-103">W tym przykładzie pokazano, jak rozszerzyć śledzenia [!INCLUDE[wf](../../../../includes/wf-md.md)] tworząc niestandardowe śledzenia uczestnika.</span><span class="sxs-lookup"><span data-stu-id="d0afc-103">This sample demonstrates how to extend tracking in [!INCLUDE[wf](../../../../includes/wf-md.md)] by creating a custom tracking participant.</span></span> <span data-ttu-id="d0afc-104">Klasy .NET Framework, które odbierają rekordy śledzenia z środowiska uruchomieniowego, ponieważ są one emitowane się uczestników śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d0afc-104">Tracking participants are .NET Framework classes that receive tracking records from the runtime as they are emitted.</span></span> <span data-ttu-id="d0afc-105">Można utworzyć uczestnika śledzenia do transportu zdarzenia śledzenia do niezależnie od docelowego jest wymagane dla danego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="d0afc-105">You can create a tracking participant to transport the tracking events to whichever destination is required for your scenario.</span></span> <span data-ttu-id="d0afc-106">Na przykład uczestnika śledzenia funkcji ETW (zdarzenia śledzenia dla systemu Windows) jest dostarczana jako część [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d0afc-106">For example, ETW (Event Tracing for Windows) Tracking Participant is provided as part of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="d0afc-107">Uczestnik śledzenia w tym przykładzie zapisuje rekordy w formacie XML w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="d0afc-107">The tracking participant in this sample writes the records in XML format to a text file.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="d0afc-108">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="d0afc-108">Sample details</span></span>  
 <span data-ttu-id="d0afc-109">Aby zoptymalizować użyteczność i niezawodność sieci uczestnika śledzenia, dodatkowe kroki musi zostać wypełniony prawidłowo okablować uczestnika śledzenia do środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="d0afc-109">To optimize the usefulness and robustness of your tracking participant, some additional steps must be completed to properly wire the tracking participant to the runtime.</span></span> <span data-ttu-id="d0afc-110">W poniższej tabeli opisano klasy używane w tym przykładzie do tworzenia uczestnika śledzenia, który jest zgodny z najlepszymi rozwiązaniami.</span><span class="sxs-lookup"><span data-stu-id="d0afc-110">The following table describes the classes used in this sample to create a tracking participant that complies with best practices.</span></span>  
  
|<span data-ttu-id="d0afc-111">Class</span><span class="sxs-lookup"><span data-stu-id="d0afc-111">Class</span></span>|<span data-ttu-id="d0afc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d0afc-112">Description</span></span>|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|<span data-ttu-id="d0afc-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> służy do definiowania sekcji konfiguracji używane do konfigurowania tego uczestnika tekstu pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d0afc-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> is used to define the configuration section used to configure the text file tracking participant.</span></span> <span data-ttu-id="d0afc-114">Dzięki temu użytkownicy mogą określić miejsce docelowe pliku dziennika przy użyciu standardowe pliki konfiguracji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0afc-114">This allows users to specify the destination of the log file using standard .NET Framework configuration files.</span></span>|  
|`TextFileTrackingBehavior`|<span data-ttu-id="d0afc-115">Zachowania w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Zezwalaj użytkownikom na iniekcję rozszerzenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d0afc-115">Behaviors in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allow users to inject extensions into the runtime.</span></span> <span data-ttu-id="d0afc-116">To zachowanie dodaje uczestnika śledzenia do usługi, po uruchomieniu usługi.</span><span class="sxs-lookup"><span data-stu-id="d0afc-116">This behavior adds the tracking participant to the service when the service starts.</span></span>|  
|`TextFileTrackingParticipant`|<span data-ttu-id="d0afc-117">Uczestnik śledzenia, który odbiera uczestników śledzenia w czasie wykonywania i zapisuje je w pliku dziennika w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="d0afc-117">The tracking participant that receives tracking participants at runtime and stores them to a log file as XML.</span></span>|  
  
## <a name="behavior-extension-elements-configuration"></a><span data-ttu-id="d0afc-118">Zachowanie rozszerzenia elementów konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d0afc-118">Behavior Extension Elements Configuration</span></span>  
 <span data-ttu-id="d0afc-119">Jeden krok jest wymagany, aby użyć elementu rozszerzenia zachowanie opisany wcześniej za pomocą plików konfiguracji platformy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0afc-119">One more step is required to make use of the behavior extension element previously described using .NET Framework configuration files.</span></span> <span data-ttu-id="d0afc-120">Następująca konfiguracja muszą znajdować się w plikach konfiguracji, w którym ma być używany rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d0afc-120">The following configuration must be placed in configuration files where the extension is to be used.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
      <behaviorExtensions>  
        <add name="textFileTracking" type="Microsoft.Samples.TextFileTracking.TextFileTrackingExtensionElement, WFStockPriceApplication, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
…  
  </system.serviceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="d0afc-121">Znajduje się w pliku Web.config w próbce użytkowania pełny przykład zachowanie rozszerzenia elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d0afc-121">See the Web.config file in the sample for a complete example usage of behavior extension elements configuration.</span></span>  
  
## <a name="custom-tracking-records"></a><span data-ttu-id="d0afc-122">Śledzenie niestandardowych rekordów</span><span class="sxs-lookup"><span data-stu-id="d0afc-122">Custom Tracking Records</span></span>  
 <span data-ttu-id="d0afc-123">Plik GetStockPrices.cs demonstruje sposób tworzenia niestandardowych śledzenie rekordów z poziomu <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="d0afc-123">The GetStockPrices.cs file demonstrates how to create custom tracking records from within a <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="d0afc-124">Wyszukaj ten rekord podczas uruchamiania próbki.</span><span class="sxs-lookup"><span data-stu-id="d0afc-124">Look for this record when running the sample.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d0afc-125">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="d0afc-125">To use this sample</span></span>  
  
1.  <span data-ttu-id="d0afc-126">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania WFStockPriceApplication.sln.</span><span class="sxs-lookup"><span data-stu-id="d0afc-126">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="d0afc-127">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="d0afc-127">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="d0afc-128">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="d0afc-128">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="d0afc-129">Oknie przeglądarki zostanie otwarty i zawiera katalog zawierający informacje o aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0afc-129">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="d0afc-130">W przeglądarce kliknij przycisk StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="d0afc-130">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="d0afc-131">Wyświetla przeglądarki **StockPriceService** strony, która zawiera adres wsdl Usługa lokalna.</span><span class="sxs-lookup"><span data-stu-id="d0afc-131">The browser displays the **StockPriceService** page, which contains the local service wsdl address.</span></span> <span data-ttu-id="d0afc-132">Skopiuj ten adres.</span><span class="sxs-lookup"><span data-stu-id="d0afc-132">Copy this address.</span></span>  
  
     <span data-ttu-id="d0afc-133">Przykładem adresu wsdl Usługa lokalna jest http://localhost:53797/StockPriceService.xamlx?wsdl.</span><span class="sxs-lookup"><span data-stu-id="d0afc-133">An example of the local service wsdl address is http://localhost:53797/StockPriceService.xamlx?wsdl.</span></span>  
  
6.  <span data-ttu-id="d0afc-134">Przy użyciu [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], przejdź do Twojej [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (%SystemDrive%\Program Files\Microsoft Visual Studio 10.0 domyślny folder instalacji to).</span><span class="sxs-lookup"><span data-stu-id="d0afc-134">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], go to your [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (the default installation folder is %SystemDrive%\Program Files\Microsoft Visual Studio 10.0).</span></span> <span data-ttu-id="d0afc-135">Następnie odszukaj podfolder Common7\IDE\.</span><span class="sxs-lookup"><span data-stu-id="d0afc-135">Then locate the Common7\IDE\ subfolder.</span></span>  
  
7.  <span data-ttu-id="d0afc-136">Kliknij dwukrotnie plik WcfTestClient.exe, aby uruchomić klienta testowego WCF.</span><span class="sxs-lookup"><span data-stu-id="d0afc-136">Double-click the WcfTestClient.exe file to launch the WCF Test Client.</span></span>  
  
8.  <span data-ttu-id="d0afc-137">W kliencie testowym WCF, wybierz **Dodawanie usługi...**</span><span class="sxs-lookup"><span data-stu-id="d0afc-137">In the WCF Test Client, select **Add Service…**</span></span> <span data-ttu-id="d0afc-138">z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="d0afc-138">from the **File** menu.</span></span>  
  
9. <span data-ttu-id="d0afc-139">Wklej skopiowany w polu tekstowym adres URL.</span><span class="sxs-lookup"><span data-stu-id="d0afc-139">Paste the URL you just copied into the text box.</span></span>  
  
10. <span data-ttu-id="d0afc-140">Kliknij przycisk **OK** aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d0afc-140">Click **OK** to close the dialog.</span></span>  
  
11. <span data-ttu-id="d0afc-141">Przetestuj usługę za pomocą klienta testowego WCF.</span><span class="sxs-lookup"><span data-stu-id="d0afc-141">Test the service using the WCF Test Client.</span></span>  
  
    1.  <span data-ttu-id="d0afc-142">W kliencie testowym WCF, kliknij dwukrotnie **GetStockPrice()** w obszarze **IStockPriceService** węzła.</span><span class="sxs-lookup"><span data-stu-id="d0afc-142">In the WCF Test Client, double-click **GetStockPrice()** under the **IStockPriceService** node.</span></span>  
  
         <span data-ttu-id="d0afc-143">**GetStockPrice()** metoda pojawia się w okienku po prawej stronie, z jednym parametrem.</span><span class="sxs-lookup"><span data-stu-id="d0afc-143">The **GetStockPrice()** method appears in the right pane, with one parameter.</span></span>  
  
    2.  <span data-ttu-id="d0afc-144">Jako wartość parametru, wpisz w firmie Contoso.</span><span class="sxs-lookup"><span data-stu-id="d0afc-144">Type in Contoso as the value for the parameter.</span></span>  
  
    3.  <span data-ttu-id="d0afc-145">Kliknij przycisk **wywołania**.</span><span class="sxs-lookup"><span data-stu-id="d0afc-145">Click **Invoke**.</span></span>  
  
12. <span data-ttu-id="d0afc-146">Zobacz śledzonych zdarzeń w pliku dziennika znajduje się w katalogu % APPDATA%\trackingRecords.log danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0afc-146">See the tracked events in the log file located in your application data directory at %APPDATA%\trackingRecords.log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d0afc-147">% APPDATA % jest zmienną środowiskową, który jest rozpoznawany jako %SystemDrive%\Users\\< nazwa_użytkownika\>\AppData\Roaming w [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], lub Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="d0afc-147">The %APPDATA% is an environment variable that resolves to %SystemDrive%\Users\\<username\>\AppData\Roaming in [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], or Windows Server 2008.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d0afc-148">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d0afc-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d0afc-149">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="d0afc-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d0afc-150">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="d0afc-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d0afc-151">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d0afc-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a><span data-ttu-id="d0afc-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0afc-152">See Also</span></span>  
 [<span data-ttu-id="d0afc-153">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="d0afc-153">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
