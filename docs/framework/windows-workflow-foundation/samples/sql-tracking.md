---
title: Śledzenie SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 72bfcaac2903b3e7fa5679422ad4feaa79e93211
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243183"
---
# <a name="sql-tracking"></a><span data-ttu-id="c7bf7-102">Śledzenie SQL</span><span class="sxs-lookup"><span data-stu-id="c7bf7-102">SQL tracking</span></span>

<span data-ttu-id="c7bf7-103">W tym przykładzie pokazano, jak napisać niestandardowego uczestnika śledzenia SQL, który zapisuje rekordy śledzenia do bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-103">This sample demonstrates how to write a custom SQL tracking participant that writes tracking records to a SQL database.</span></span> <span data-ttu-id="c7bf7-104">Windows Workflow Foundation (WF) zapewnia śledzenie przepływu pracy, aby uzyskać wgląd w wykonywanie wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="c7bf7-105">Środowisko uruchomieniowe śledzenia emituje rekordy śledzenia przepływu pracy podczas wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="c7bf7-106">Aby uzyskać więcej informacji na temat śledzenia przepływu pracy, zobacz [Śledzenie przepływu pracy i śledzenie](../workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="c7bf7-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

## <a name="use-the-sample"></a><span data-ttu-id="c7bf7-107">Użyj próbki</span><span class="sxs-lookup"><span data-stu-id="c7bf7-107">Use the sample</span></span>

1. <span data-ttu-id="c7bf7-108">Sprawdź, czy masz zainstalowany program SQL Server 2008, SQL Server 2008 Express lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="c7bf7-109">Skrypty spakowane z przykładem zakładają użycie wystąpienia sql express na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="c7bf7-110">Jeśli masz inne wystąpienie, zmodyfikuj skrypty związane z bazą danych przed uruchomieniem przykładu.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="c7bf7-111">Utwórz bazę danych śledzenia programu SQL Server, uruchamiając plik Trackingsetup.cmd w katalogu skryptów (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span><span class="sxs-lookup"><span data-stu-id="c7bf7-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="c7bf7-112">Spowoduje to utworzenie bazy danych o nazwie TrackingSample.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-112">This creates a database called TrackingSample.</span></span>

   > [!NOTE]
   > <span data-ttu-id="c7bf7-113">Skrypt tworzy bazę danych w domyślnym wystąpieniu programu SQL Express.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="c7bf7-114">Jeśli chcesz zainstalować go w innym wystąpieniu bazy danych, edytuj skrypt Trackingsetup.cmd.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>

3. <span data-ttu-id="c7bf7-115">Otwórz program SqlTrackingSample.sln w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>

4. <span data-ttu-id="c7bf7-116">Naciśnij **klawisze Ctrl**+**Shift**+**B,** aby utworzyć rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-116">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

5. <span data-ttu-id="c7bf7-117">Naciśnij **klawisz F5,** aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-117">Press **F5** to run the application.</span></span>

   <span data-ttu-id="c7bf7-118">Otworzy się okno przeglądarki i zostanie wyświetle listę katalogów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-118">The browser window opens and shows the directory listing for the application.</span></span>

6. <span data-ttu-id="c7bf7-119">W przeglądarce kliknij pozycję StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-119">In the browser, click StockPriceService.xamlx.</span></span>

7. <span data-ttu-id="c7bf7-120">Przeglądarka wyświetla stockpriceservice strony, która zawiera adres WSDL usługi lokalnej.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="c7bf7-121">Skopiuj ten adres.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-121">Copy this address.</span></span>

   <span data-ttu-id="c7bf7-122">Przykładem adresu WSDL usługi `http://localhost:65193/StockPriceService.xamlx?wsdl`lokalnej jest .</span><span class="sxs-lookup"><span data-stu-id="c7bf7-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>

8. <span data-ttu-id="c7bf7-123">Korzystając z Eksploratora plików, uruchom klienta testowego WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="c7bf7-123">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="c7bf7-124">Znajduje się w *katalogu Programu Microsoft Visual Studio 10.0\Common7\IDE*.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-124">It's located in the *Microsoft Visual Studio 10.0\Common7\IDE directory*.</span></span>

9. <span data-ttu-id="c7bf7-125">W kliencie testowym WCF kliknij menu **Plik** i wybierz polecenie **Dodaj usługę**.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="c7bf7-126">Wklej adres usługi lokalnej w skrzynce tekstowej.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="c7bf7-127">Kliknij **przycisk OK,** aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-127">Click **OK** to close the dialog.</span></span>

10. <span data-ttu-id="c7bf7-128">W kliencie testowym WCF kliknij dwukrotnie **getstockprice**.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="c7bf7-129">Spowoduje to `GetStockPrice` otwarcie operacji, która przyjmuje `Contoso` jeden parametr, wpisz wartość i kliknij przycisk **Wywołaj**.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>

11. <span data-ttu-id="c7bf7-130">Emitowane rekordy śledzenia są zapisywane w bazie danych SQL.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="c7bf7-131">Aby wyświetlić rekordy śledzenia, otwórz bazę danych TrackingSample w programie SQL Management Studio i przejdź do tabel.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="c7bf7-132">Uruchomienie kwerendy wybierającej w tabelach wyświetla dane w rekordach śledzenia przechowywanych w odpowiednich tabelach.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-132">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>

   <span data-ttu-id="c7bf7-133">Aby uzyskać więcej informacji na temat programu SQL Server Management Studio, zobacz [Wprowadzenie programu SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span><span class="sxs-lookup"><span data-stu-id="c7bf7-133">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span></span> <span data-ttu-id="c7bf7-134">Pobierz SQL Server Management Studio [tutaj](https://aka.ms/ssmsfullsetup).</span><span class="sxs-lookup"><span data-stu-id="c7bf7-134">Download SQL Server Management Studio [here](https://aka.ms/ssmsfullsetup).</span></span>

## <a name="uninstall-the-sample"></a><span data-ttu-id="c7bf7-135">Odinstalowywanie przykładu</span><span class="sxs-lookup"><span data-stu-id="c7bf7-135">Uninstall the sample</span></span>

1. <span data-ttu-id="c7bf7-136">Uruchom skrypt Trackingingcleanup.cmd w przykładowym katalogu (*\WF\Basic\Tracking\SqlTracking*).</span><span class="sxs-lookup"><span data-stu-id="c7bf7-136">Run theTrackingcleanup.cmd script in the sample directory (*\WF\Basic\Tracking\SqlTracking*).</span></span>

    > [!NOTE]
    > <span data-ttu-id="c7bf7-137">Plik Trackingcleanup.cmd próbuje usunąć bazę danych na komputerze lokalnym SQL Express.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="c7bf7-138">Jeśli używasz innego wystąpienia serwera SQL, edytuj plik Trackingcleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7bf7-139">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c7bf7-140">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c7bf7-141">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7bf7-142">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c7bf7-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a><span data-ttu-id="c7bf7-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7bf7-143">See also</span></span>

- <span data-ttu-id="c7bf7-144">[Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c7bf7-144">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
