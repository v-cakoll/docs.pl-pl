---
title: Śledzenie SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 24cc484bf11d7cedab949d61c63f805a28a9f849
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038055"
---
# <a name="sql-tracking"></a><span data-ttu-id="6d3c9-102">Śledzenie SQL</span><span class="sxs-lookup"><span data-stu-id="6d3c9-102">SQL Tracking</span></span>
<span data-ttu-id="6d3c9-103">Ten przykład pokazuje, jak napisać niestandardowego uczestnika śledzenia SQL, który zapisuje rekordy śledzenia do bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-103">This sample demonstrates how to write a custom SQL tracking participant, that writes tracking records to a SQL database.</span></span> <span data-ttu-id="6d3c9-104">Windows Workflow Foundation (WF) oferuje śledzenie przepływów pracy, aby uzyskać wgląd w wykonywanie wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="6d3c9-105">Środowisko uruchomieniowe śledzenia emituje rekordy śledzenia przepływu pracy podczas wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="6d3c9-106">Aby uzyskać więcej informacji na temat śledzenia przepływu pracy, zobacz [śledzenie i śledzenie przepływu pracy](../workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="6d3c9-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="6d3c9-107">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="6d3c9-107">To use this sample</span></span>

1. <span data-ttu-id="6d3c9-108">Sprawdź, czy masz SQL Server 2008, SQL Server 2008 Express lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="6d3c9-109">Skrypty spakowane z przykładem zakładają użycie wystąpienia programu SQL Express na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="6d3c9-110">Jeśli istnieje inne wystąpienie, przed uruchomieniem przykładu należy zmodyfikować skrypty powiązane z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="6d3c9-111">Utwórz bazę danych śledzenia SQL Server, uruchamiając Trackingsetup. cmd w katalogu scripts (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span><span class="sxs-lookup"><span data-stu-id="6d3c9-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="6d3c9-112">Spowoduje to utworzenie bazy danych o nazwie TrackingSample.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-112">This creates a database called TrackingSample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6d3c9-113">Skrypt tworzy bazę danych w domyślnym wystąpieniu programu SQL Express.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="6d3c9-114">Jeśli chcesz zainstalować ją w innym wystąpieniu bazy danych, Edytuj skrypt Trackingsetup. cmd.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>  
  
3. <span data-ttu-id="6d3c9-115">Otwórz SqlTrackingSample. sln w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>  
  
4. <span data-ttu-id="6d3c9-116">Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5. <span data-ttu-id="6d3c9-117">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-117">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="6d3c9-118">Zostanie otwarte okno przeglądarki i zostanie wyświetlona lista katalogów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-118">The browser window opens and shows the directory listing for the application.</span></span>  
  
6. <span data-ttu-id="6d3c9-119">W przeglądarce kliknij pozycję StockPriceService. xamlx.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-119">In the browser, click StockPriceService.xamlx.</span></span>  
  
7. <span data-ttu-id="6d3c9-120">W przeglądarce zostanie wyświetlona strona StockPriceService, która zawiera adres WSDL usługi lokalnej.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="6d3c9-121">Kopiuj ten adres.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-121">Copy this address.</span></span>  
  
     <span data-ttu-id="6d3c9-122">Przykładem adresu WSDL usługi lokalnej jest `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>  
  
8. <span data-ttu-id="6d3c9-123">Korzystając z Eksploratora plików, uruchom klienta testowego WCF (WcfTestClient. exe).</span><span class="sxs-lookup"><span data-stu-id="6d3c9-123">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="6d3c9-124">Znajduje się w katalogu Microsoft Visual Studio 10.0 \ Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-124">It is located in the Microsoft Visual Studio 10.0\Common7\IDE directory.</span></span>  
  
9. <span data-ttu-id="6d3c9-125">W kliencie testowym WCF kliknij menu **plik** i wybierz polecenie **Dodaj usługę**.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="6d3c9-126">Wklej adres usługi lokalnej do pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="6d3c9-127">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-127">Click **OK** to close the dialog.</span></span>  
  
10. <span data-ttu-id="6d3c9-128">W kliencie testowym WCF kliknij dwukrotnie pozycję **GetStockPrice**.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="6d3c9-129">Spowoduje to otwarcie `GetStockPrice` operacji, która przyjmuje jeden parametr, wpisz wartość `Contoso` i kliknij przycisk **Wywołaj**.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>  
  
11. <span data-ttu-id="6d3c9-130">Wysyłane rekordy śledzenia są zapisywane w bazie danych SQL.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="6d3c9-131">Aby wyświetlić rekordy śledzenia, Otwórz bazę danych TrackingSample w programie SQL Management Studio i przejdź do tabel.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="6d3c9-132">Aby uzyskać więcej informacji na temat SQL Server Management Studio, zobacz [wprowadzenie SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645).</span><span class="sxs-lookup"><span data-stu-id="6d3c9-132">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645).</span></span> <span data-ttu-id="6d3c9-133">SQL Server 2008 Management Studio Express można pobrać [tutaj](https://go.microsoft.com/fwlink/?LinkId=180520).</span><span class="sxs-lookup"><span data-stu-id="6d3c9-133">SQL Server 2008 Management Studio Express can be downloaded [here](https://go.microsoft.com/fwlink/?LinkId=180520).</span></span> <span data-ttu-id="6d3c9-134">Uruchomienie zapytania SELECT w tabelach wyświetla dane w rekordach śledzenia przechowywanych w odpowiednich tabelach.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-134">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>  
  
#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="6d3c9-135">Aby odinstalować przykład</span><span class="sxs-lookup"><span data-stu-id="6d3c9-135">To uninstall the sample</span></span>  
  
1. <span data-ttu-id="6d3c9-136">Uruchom skrypt theTrackingcleanup. cmd w katalogu przykładowym (\WF\Basic\Tracking\SqlTracking).</span><span class="sxs-lookup"><span data-stu-id="6d3c9-136">Run theTrackingcleanup.cmd script in the sample directory (\WF\Basic\Tracking\SqlTracking).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6d3c9-137">Trackingcleanup. cmd próbuje usunąć bazę danych w lokalnym komputerze SQL Express.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="6d3c9-138">Jeśli używasz innego wystąpienia programu SQL Server, Edytuj Trackingcleanup. cmd.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d3c9-139">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6d3c9-140">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="6d3c9-140">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="6d3c9-141">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6d3c9-142">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6d3c9-142">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a><span data-ttu-id="6d3c9-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d3c9-143">See also</span></span>

- [<span data-ttu-id="6d3c9-144">Przykłady monitorowania oprogramowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="6d3c9-144">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
