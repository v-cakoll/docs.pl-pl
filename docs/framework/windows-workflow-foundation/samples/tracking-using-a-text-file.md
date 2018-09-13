---
title: Śledzenie za pomocą pliku tekstowego
ms.date: 03/30/2017
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
ms.openlocfilehash: 19b4d544bc1d1c5bc9ebfa51b4ba28eb82c525d0
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44707302"
---
# <a name="tracking-using-a-text-file"></a><span data-ttu-id="dff38-102">Śledzenie za pomocą pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="dff38-102">Tracking Using a Text File</span></span>
<span data-ttu-id="dff38-103">Niniejszy przykład pokazuje, jak rozszerzyć śledzenia w Windows Workflow Foundation (WF) przez tworzenie niestandardowego uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="dff38-103">This sample demonstrates how to extend tracking in Windows Workflow Foundation (WF) by creating a custom tracking participant.</span></span> <span data-ttu-id="dff38-104">Śledzenie uczestników są odbierać rekordów śledzenia ze środowiska wykonawczego, ponieważ są one emitowane klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dff38-104">Tracking participants are .NET Framework classes that receive tracking records from the runtime as they are emitted.</span></span> <span data-ttu-id="dff38-105">Można utworzyć uczestnikiem śledzenia do transportu zdarzenia śledzenia, niezależnie od docelowego jest wymagane dla danego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="dff38-105">You can create a tracking participant to transport the tracking events to whichever destination is required for your scenario.</span></span> <span data-ttu-id="dff38-106">Na przykład uczestnika śledzenia zdarzeń systemu Windows (Event Tracing for Windows) jest dostarczana jako część [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dff38-106">For example, ETW (Event Tracing for Windows) Tracking Participant is provided as part of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="dff38-107">Uczestnik śledzenia w tym przykładzie zapisuje rekordy w formacie XML do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="dff38-107">The tracking participant in this sample writes the records in XML format to a text file.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="dff38-108">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="dff38-108">Sample details</span></span>  
 <span data-ttu-id="dff38-109">W celu zoptymalizowania użyteczność i niezawodność usługi śledzenia uczestnika, celu prawidłowo podłączenia uczestnikiem śledzenia do środowiska uruchomieniowego, należy wykonać kilka dodatkowych kroków.</span><span class="sxs-lookup"><span data-stu-id="dff38-109">To optimize the usefulness and robustness of your tracking participant, some additional steps must be completed to properly wire the tracking participant to the runtime.</span></span> <span data-ttu-id="dff38-110">W poniższej tabeli opisano klasy używane w tym przykładzie do tworzenia śledzenia uczestnika, który jest zgodny z najlepszymi rozwiązaniami.</span><span class="sxs-lookup"><span data-stu-id="dff38-110">The following table describes the classes used in this sample to create a tracking participant that complies with best practices.</span></span>  
  
|<span data-ttu-id="dff38-111">Class</span><span class="sxs-lookup"><span data-stu-id="dff38-111">Class</span></span>|<span data-ttu-id="dff38-112">Opis</span><span class="sxs-lookup"><span data-stu-id="dff38-112">Description</span></span>|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|<span data-ttu-id="dff38-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> służy do definiowania sekcja konfiguracji umożliwia skonfigurowanie uczestnika śledzenia pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="dff38-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> is used to define the configuration section used to configure the text file tracking participant.</span></span> <span data-ttu-id="dff38-114">Dzięki temu użytkownicy mogą określić miejsce docelowe pliku dziennika przy użyciu standardowe pliki konfiguracji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dff38-114">This allows users to specify the destination of the log file using standard .NET Framework configuration files.</span></span>|  
|`TextFileTrackingBehavior`|<span data-ttu-id="dff38-115">Zachowania w programie WCF umożliwiają użytkownikom wstrzyknąć rozszerzenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="dff38-115">Behaviors in WCF allow users to inject extensions into the runtime.</span></span> <span data-ttu-id="dff38-116">To zachowanie dodaje uczestnikiem śledzenia do usługi, po uruchomieniu usługi.</span><span class="sxs-lookup"><span data-stu-id="dff38-116">This behavior adds the tracking participant to the service when the service starts.</span></span>|  
|`TextFileTrackingParticipant`|<span data-ttu-id="dff38-117">Śledzenia uczestnika, który odbiera uczestników śledzenia w czasie wykonywania i zapisuje je w pliku dziennika w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="dff38-117">The tracking participant that receives tracking participants at runtime and stores them to a log file as XML.</span></span>|  
  
## <a name="behavior-extension-elements-configuration"></a><span data-ttu-id="dff38-118">Zachowanie rozszerzenia elementów konfiguracji</span><span class="sxs-lookup"><span data-stu-id="dff38-118">Behavior Extension Elements Configuration</span></span>  
 <span data-ttu-id="dff38-119">Jeszcze jeden krok jest wymagany, aby użyć elementu rozszerzenia zachowanie opisany wcześniej za pomocą plików konfiguracji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dff38-119">One more step is required to make use of the behavior extension element previously described using .NET Framework configuration files.</span></span> <span data-ttu-id="dff38-120">Następująca konfiguracja muszą być umieszczone w plikach konfiguracji, których rozszerzenie ma być używany.</span><span class="sxs-lookup"><span data-stu-id="dff38-120">The following configuration must be placed in configuration files where the extension is to be used.</span></span>  
  
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
>  <span data-ttu-id="dff38-121">Można znaleźć w pliku Web.config w przykładzie użycie kompletny przykład, zachowanie rozszerzeń elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="dff38-121">See the Web.config file in the sample for a complete example usage of behavior extension elements configuration.</span></span>  
  
## <a name="custom-tracking-records"></a><span data-ttu-id="dff38-122">Niestandardowe rekordy śledzenia</span><span class="sxs-lookup"><span data-stu-id="dff38-122">Custom Tracking Records</span></span>  
 <span data-ttu-id="dff38-123">Plik GetStockPrices.cs pokazuje, jak utworzyć niestandardowe rekordy śledzenia z poziomu <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="dff38-123">The GetStockPrices.cs file demonstrates how to create custom tracking records from within a <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="dff38-124">Poszukaj tego rekordu, gdy działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="dff38-124">Look for this record when running the sample.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="dff38-125">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="dff38-125">To use this sample</span></span>  
  
1.  <span data-ttu-id="dff38-126">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania WFStockPriceApplication.sln.</span><span class="sxs-lookup"><span data-stu-id="dff38-126">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="dff38-127">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="dff38-127">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="dff38-128">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="dff38-128">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="dff38-129">Okno przeglądarki otwiera i pokazuje katalog zawierający informacje o aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dff38-129">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="dff38-130">W przeglądarce kliknij przycisk StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="dff38-130">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="dff38-131">Wyświetla przeglądarki **StockPriceService** strony, która zawiera adres wsdl Usługa lokalna.</span><span class="sxs-lookup"><span data-stu-id="dff38-131">The browser displays the **StockPriceService** page, which contains the local service wsdl address.</span></span> <span data-ttu-id="dff38-132">Skopiuj ten adres.</span><span class="sxs-lookup"><span data-stu-id="dff38-132">Copy this address.</span></span>  
  
     <span data-ttu-id="dff38-133">Na przykład adres wsdl Usługa lokalna http://localhost:53797/StockPriceService.xamlx?wsdl.</span><span class="sxs-lookup"><span data-stu-id="dff38-133">An example of the local service wsdl address is http://localhost:53797/StockPriceService.xamlx?wsdl.</span></span>  
  
6.  <span data-ttu-id="dff38-134">Za pomocą [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], przejdź do swojej [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (domyślny folder instalacji to %SystemDrive%\Program Files\Microsoft Visual Studio 10.0).</span><span class="sxs-lookup"><span data-stu-id="dff38-134">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], go to your [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (the default installation folder is %SystemDrive%\Program Files\Microsoft Visual Studio 10.0).</span></span> <span data-ttu-id="dff38-135">Następnie znajdź podfolder Common7\IDE\.</span><span class="sxs-lookup"><span data-stu-id="dff38-135">Then locate the Common7\IDE\ subfolder.</span></span>  
  
7.  <span data-ttu-id="dff38-136">Kliknij dwukrotnie plik WcfTestClient.exe, aby uruchomić klienta testowego WCF.</span><span class="sxs-lookup"><span data-stu-id="dff38-136">Double-click the WcfTestClient.exe file to launch the WCF Test Client.</span></span>  
  
8.  <span data-ttu-id="dff38-137">W kliencie testowym WCF wybierz **Dodaj usługę...**</span><span class="sxs-lookup"><span data-stu-id="dff38-137">In the WCF Test Client, select **Add Service…**</span></span> <span data-ttu-id="dff38-138">z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="dff38-138">from the **File** menu.</span></span>  
  
9. <span data-ttu-id="dff38-139">Wklej adres URL został skopiowany do pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="dff38-139">Paste the URL you just copied into the text box.</span></span>  
  
10. <span data-ttu-id="dff38-140">Kliknij przycisk **OK** aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="dff38-140">Click **OK** to close the dialog.</span></span>  
  
11. <span data-ttu-id="dff38-141">Przetestuj usługę za pomocą klienta testowego WCF.</span><span class="sxs-lookup"><span data-stu-id="dff38-141">Test the service using the WCF Test Client.</span></span>  
  
    1.  <span data-ttu-id="dff38-142">W kliencie testowym WCF, kliknij dwukrotnie **GetStockPrice()** w obszarze **IStockPriceService** węzła.</span><span class="sxs-lookup"><span data-stu-id="dff38-142">In the WCF Test Client, double-click **GetStockPrice()** under the **IStockPriceService** node.</span></span>  
  
         <span data-ttu-id="dff38-143">**GetStockPrice()** metoda pojawia się w okienku po prawej stronie, z jednym parametrem.</span><span class="sxs-lookup"><span data-stu-id="dff38-143">The **GetStockPrice()** method appears in the right pane, with one parameter.</span></span>  
  
    2.  <span data-ttu-id="dff38-144">Wpisz w firmie Contoso jako wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="dff38-144">Type in Contoso as the value for the parameter.</span></span>  
  
    3.  <span data-ttu-id="dff38-145">Kliknij przycisk **wywołania**.</span><span class="sxs-lookup"><span data-stu-id="dff38-145">Click **Invoke**.</span></span>  
  
12. <span data-ttu-id="dff38-146">Zobacz rejestrowanych zdarzeń w pliku dziennika, znajduje się w katalogu % APPDATA%\trackingRecords.log danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dff38-146">See the tracked events in the log file located in your application data directory at %APPDATA%\trackingRecords.log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dff38-147">% APPDATA % jest zmienną środowiskową, który jest rozpoznawany jako %SystemDrive%\Users\\< nazwa_użytkownika\>\AppData\Roaming w [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], lub Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="dff38-147">The %APPDATA% is an environment variable that resolves to %SystemDrive%\Users\\<username\>\AppData\Roaming in [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], or Windows Server 2008.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dff38-148">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="dff38-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="dff38-149">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="dff38-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dff38-150">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="dff38-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dff38-151">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="dff38-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a><span data-ttu-id="dff38-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dff38-152">See Also</span></span>  
 [<span data-ttu-id="dff38-153">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="dff38-153">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
