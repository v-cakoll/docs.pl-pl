---
title: Śledzenie SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: f3c48b40e2d3d7dec2b9008b3de738f9b2983610
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785921"
---
# <a name="sql-tracking"></a><span data-ttu-id="c3a2d-102">Śledzenie SQL</span><span class="sxs-lookup"><span data-stu-id="c3a2d-102">SQL Tracking</span></span>
<span data-ttu-id="c3a2d-103">W tym przykładzie pokazano, jak napisać uczestnikiem niestandardowe śledzenia SQL, który zapisuje rekordy śledzenia bazą danych SQL.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-103">This sample demonstrates how to write a custom SQL tracking participant, that writes tracking records to a SQL database.</span></span> <span data-ttu-id="c3a2d-104">Windows Workflow Foundation (WF) zapewnia wgląd w wykonywania wystąpienia przepływu pracy śledzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="c3a2d-105">Środowisko uruchomieniowe śledzenia emituje przepływu pracy śledzenia rekordów podczas wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="c3a2d-106">Aby uzyskać więcej informacji na temat śledzenia przepływu pracy, zobacz [przepływu pracy i śledzenie](../workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="c3a2d-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="c3a2d-107">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="c3a2d-107">To use this sample</span></span>

1. <span data-ttu-id="c3a2d-108">Sprawdź, zainstalowany jest program SQL Server 2008, SQL Server 2008 Express lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="c3a2d-109">Skrypty w pakiecie z przykładem założono korzystanie z wystąpienia programu SQL Express na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="c3a2d-110">Jeśli masz inne wystąpienie, zmodyfikuj skrypty związane z bazy danych przed uruchomieniem przykładu.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="c3a2d-111">Utwórz bazę danych śledzenia programu SQL Server, uruchamiając Trackingsetup.cmd w katalogu skryptów (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span><span class="sxs-lookup"><span data-stu-id="c3a2d-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="c3a2d-112">Spowoduje to utworzenie bazy danych o nazwie TrackingSample.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-112">This creates a database called TrackingSample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c3a2d-113">Skrypt tworzy bazę danych w domyślnym wystąpieniu programu SQL Express.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="c3a2d-114">Jeśli chcesz zainstalować je na inne wystąpienie bazy danych, zmodyfikuj skrypt Trackingsetup.cmd.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>  
  
3. <span data-ttu-id="c3a2d-115">Otwórz SqlTrackingSample.sln w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>  
  
4. <span data-ttu-id="c3a2d-116">Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5. <span data-ttu-id="c3a2d-117">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-117">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="c3a2d-118">Okno przeglądarki otwiera i pokazuje katalog zawierający informacje o aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-118">The browser window opens and shows the directory listing for the application.</span></span>  
  
6. <span data-ttu-id="c3a2d-119">W przeglądarce kliknij przycisk StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-119">In the browser, click StockPriceService.xamlx.</span></span>  
  
7. <span data-ttu-id="c3a2d-120">W przeglądarce pojawi się stronie StockPriceService zawiera usługę lokalnego adresu WSDL.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="c3a2d-121">Skopiuj ten adres.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-121">Copy this address.</span></span>  
  
     <span data-ttu-id="c3a2d-122">Na przykład adres WSDL Usługa lokalna `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>  
  
8. <span data-ttu-id="c3a2d-123">Za pomocą [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], uruchom klienta testowego WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="c3a2d-123">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="c3a2d-124">Znajduje się on w katalogu programu Microsoft Visual Studio 10.0\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-124">It is located in the Microsoft Visual Studio 10.0\Common7\IDE directory.</span></span>  
  
9. <span data-ttu-id="c3a2d-125">W kliencie testowym WCF kliknij **pliku** menu, a następnie wybierz **Dodaj usługę**.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="c3a2d-126">Wklej adres lokalnej usługi w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="c3a2d-127">Kliknij przycisk **OK** aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-127">Click **OK** to close the dialog.</span></span>  
  
10. <span data-ttu-id="c3a2d-128">W kliencie testowym WCF, kliknij dwukrotnie **GetStockPrice**.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="c3a2d-129">Spowoduje to otwarcie `GetStockPrice` operacji, która przyjmuje jeden parametr, typ wartości `Contoso` i kliknij przycisk **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>  
  
11. <span data-ttu-id="c3a2d-130">Rekordów emitowany śledzenia są zapisywane w bazie danych SQL.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="c3a2d-131">Aby wyświetlić rekordy śledzenia, należy otworzyć TrackingSample bazy danych w programie SQL Management Studio i przejdź do tabel.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="c3a2d-132">Aby uzyskać więcej informacji na temat programu SQL Server Management Studio, zobacz [wprowadzenie do programu SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645).</span><span class="sxs-lookup"><span data-stu-id="c3a2d-132">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645).</span></span> <span data-ttu-id="c3a2d-133">SQL Server 2008 Management Studio Express można pobrać [tutaj](https://go.microsoft.com/fwlink/?LinkId=180520).</span><span class="sxs-lookup"><span data-stu-id="c3a2d-133">SQL Server 2008 Management Studio Express can be downloaded [here](https://go.microsoft.com/fwlink/?LinkId=180520).</span></span> <span data-ttu-id="c3a2d-134">Uruchamianie zapytania select w tabelach wyświetla dane przechowywane w tabelach odpowiednich rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-134">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>  
  
#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="c3a2d-135">Aby odinstalować próbki</span><span class="sxs-lookup"><span data-stu-id="c3a2d-135">To uninstall the sample</span></span>  
  
1. <span data-ttu-id="c3a2d-136">Uruchom skrypt theTrackingcleanup.cmd w katalogu próbki (\WF\Basic\Tracking\SqlTracking).</span><span class="sxs-lookup"><span data-stu-id="c3a2d-136">Run theTrackingcleanup.cmd script in the sample directory (\WF\Basic\Tracking\SqlTracking).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3a2d-137">Trackingcleanup.cmd próbuje usunąć bazę danych programu SQL Express komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="c3a2d-138">Jeśli używasz innego wystąpienia programu SQL server, należy edytować Trackingcleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="c3a2d-139">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c3a2d-140">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c3a2d-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c3a2d-141">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3a2d-142">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c3a2d-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a><span data-ttu-id="c3a2d-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3a2d-143">See also</span></span>

- [<span data-ttu-id="c3a2d-144">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="c3a2d-144">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
