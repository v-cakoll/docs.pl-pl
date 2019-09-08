---
title: Pobieranie przykładowych baz danych (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: c67ee699cf594f476a728c7345b47b0c32dea7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795180"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a><span data-ttu-id="5203b-102">Pobieranie przykładowych baz danych (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="5203b-102">Downloading Sample Databases (LINQ to DataSet)</span></span>
<span data-ttu-id="5203b-103">Przykłady i instruktaże w dokumentacji LINQ to DataSet korzystają z przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5203b-103">The samples and walkthroughs in the LINQ to DataSet documentation use the AdventureWorks sample database.</span></span> <span data-ttu-id="5203b-104">Ten produkt można pobrać bezpłatnie z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5203b-104">You can download this product free of charge from the Microsoft download site.</span></span> <span data-ttu-id="5203b-105">Przykłady i instruktaże w dokumentacji LINQ to DataSet używają SQL Server jako magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="5203b-105">The samples and walkthroughs in the LINQ to DataSet documentation use SQL Server as the data store.</span></span> <span data-ttu-id="5203b-106">Wersja SQL Server Express, która jest dostępna bez opłat, może być również używana jako magazyn danych, a nie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5203b-106">SQL Server Express Edition, which is available without charge, can also be used as the data store instead of SQL Server.</span></span>  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a><span data-ttu-id="5203b-107">Pobieranie i Instalowanie bazy danych AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="5203b-107">Downloading and Installing the AdventureWorks Database</span></span>  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="5203b-108">Aby pobrać i zainstalować przykładową bazę danych AdventureWorks dla SQL Server</span><span class="sxs-lookup"><span data-stu-id="5203b-108">To download and install the AdventureWorks sample database for SQL Server</span></span>  
  
1. <span data-ttu-id="5203b-109">Otwórz program Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="5203b-109">Open Internet Explorer.</span></span>  
  
2. <span data-ttu-id="5203b-110">Przejdź do witryny [SQL Server samples 2005 i przykładowych baz danych](https://go.microsoft.com/fwlink/?linkid=31046) w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5203b-110">Go to the [SQL Server 2005 Samples and Sample Databases](https://go.microsoft.com/fwlink/?linkid=31046) Web site.</span></span>  
  
3. <span data-ttu-id="5203b-111">Postępuj zgodnie z instrukcjami dotyczącymi pobierania przykładowej bazy danych AdventureWorks dla danego typu procesora (na przykład AdventureWorksDB. msi) i Zapisz. Plik MSI na komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="5203b-111">Follow the instructions for downloading the AdventureWorks sample database for your processor type (such as AdventureWorksDB.msi), and save the .MSI file to your local computer.</span></span>  
  
4. <span data-ttu-id="5203b-112">Jeśli masz zainstalowaną poprzednią wersję usługi AdventureWorks z pobrania lub w trakcie instalacji SQL Server, musisz ją usunąć przed uruchomieniem pliku AdventureWorks. msi.</span><span class="sxs-lookup"><span data-stu-id="5203b-112">If you have a previous version of AdventureWorks installed from the download or during the SQL Server setup, you must remove it before running AdventureWorks.msi.</span></span>  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a><span data-ttu-id="5203b-113">Aby usunąć poprzednie pobranie przykładowej bazy danych AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="5203b-113">To remove a previous download of an AdventureWorks sample database</span></span>  
  
1. <span data-ttu-id="5203b-114">Porzuć bazę danych AdventureWorks lub AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="5203b-114">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="5203b-115">W obszarze **Dodaj lub usuń programy**wybierz pozycję **AdventureWorksDB** lub **AdventureWorksBI** , a następnie kliknij pozycję **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="5203b-115">From **Add or Remove Programs**, select **AdventureWorksDB** or **AdventureWorksBI** and click **Remove**.</span></span>  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a><span data-ttu-id="5203b-116">Aby usunąć przykładową bazę danych AdventureWorks, która została wcześniej zainstalowana przy użyciu Instalatora</span><span class="sxs-lookup"><span data-stu-id="5203b-116">To remove an AdventureWorks sample database previously installed using Setup</span></span>  
  
1. <span data-ttu-id="5203b-117">Porzuć bazę danych AdventureWorks lub AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="5203b-117">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="5203b-118">W obszarze **Dodaj lub usuń programy**wybierz pozycję **Microsoft SQL Server 2005** , a następnie kliknij przycisk **Zmień**.</span><span class="sxs-lookup"><span data-stu-id="5203b-118">From **Add or Remove Programs**, select **Microsoft SQL Server 2005** and click **Change**.</span></span>  
  
3. <span data-ttu-id="5203b-119">W **obszarze wybór składnika**wybierz pozycję **składniki stacji roboczej** , a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="5203b-119">From **Component Selection**, select **Workstation Components** and then click **Next**.</span></span>  
  
4. <span data-ttu-id="5203b-120">Na stronie **Witamy w Kreatorze instalacji SQL Server**kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="5203b-120">From **Welcome to the SQL Server Installation Wizard**, click **Next**.</span></span>  
  
5. <span data-ttu-id="5203b-121">W obszarze **sprawdzenie konfiguracji systemu**kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="5203b-121">From **System Configuration Check**, click **Next**.</span></span>  
  
6. <span data-ttu-id="5203b-122">W obszarze **zmiana lub usuwanie wystąpienia**kliknij pozycję **Zmień zainstalowane składniki**.</span><span class="sxs-lookup"><span data-stu-id="5203b-122">From **Change or Remove Instance**, click **Change Installed Components**.</span></span>  
  
7. <span data-ttu-id="5203b-123">W **obszarze Wybór funkcji**rozwiń węzeł **Dokumentacja, przykłady i Przykładowa baza danych** .</span><span class="sxs-lookup"><span data-stu-id="5203b-123">From **Feature Selection**, expand the **Documentation, Samples, and Sample Databases** node.</span></span>  
  
8. <span data-ttu-id="5203b-124">Wybierz **przykładowy kod i aplikacje**.</span><span class="sxs-lookup"><span data-stu-id="5203b-124">Select **Sample Code and Applications**.</span></span> <span data-ttu-id="5203b-125">Rozwiń **przykładowe bazy danych**, wybierz przykładową bazę danych do usunięcia, a następnie wybierz opcję **cała funkcja będzie niedostępna**.</span><span class="sxs-lookup"><span data-stu-id="5203b-125">Expand **Sample Databases**, select the sample database to be removed, and select **Entire feature will be unavailable**.</span></span> <span data-ttu-id="5203b-126">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="5203b-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="5203b-127">Kliknij przycisk **Zainstaluj** i Zakończ pracę Kreatora instalacji.</span><span class="sxs-lookup"><span data-stu-id="5203b-127">Click **Install** and finish the installation wizard.</span></span>  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a><span data-ttu-id="5203b-128">Aby dołączyć pliki przykładowej bazy danych AdventureWorks do wystąpienia SQL Server</span><span class="sxs-lookup"><span data-stu-id="5203b-128">To attach the AdventureWorks sample database files to an instance of SQL Server</span></span>  
  
1. <span data-ttu-id="5203b-129">Po pobraniu pliku instalacyjnego przykładowej bazy danych pliku kliknij dwukrotnie plik **AdventureWorksDB. msi** (lub pobrany plik), aby zainstalować bazę danych.</span><span class="sxs-lookup"><span data-stu-id="5203b-129">After the file sample database installer file has downloaded, double-click the **AdventureWorksDB.msi** file (or the file you downloaded) to install the database.</span></span> <span data-ttu-id="5203b-130">Domyślnie baza danych jest instalowana w katalogu c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span><span class="sxs-lookup"><span data-stu-id="5203b-130">By default, the database is installed at c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span></span>  
  
2. <span data-ttu-id="5203b-131">Dołącz pliki bazy danych AdventureWorks do wystąpienia SQL Server, wykonując następujący skrypt SQLCMD lub SQL Server Management Studio:</span><span class="sxs-lookup"><span data-stu-id="5203b-131">Attach the AdventureWorks database files to an instance of SQL Server by executing the following script SQLCMD or SQL Server Management Studio:</span></span>  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     <span data-ttu-id="5203b-132">Jeśli zainstalowano te pliki na innym dysku lub w katalogu, należy odpowiednio skorygować ścieżki przed wykonaniem `sp_attach_db` procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="5203b-132">If you have installed these files to a different drive or directory, you must revise the paths appropriately before you execute the `sp_attach_db` stored procedure.</span></span>  
  
## <a name="downloading-sql-server-express-edition"></a><span data-ttu-id="5203b-133">Pobieranie SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="5203b-133">Downloading SQL Server Express Edition</span></span>  
 <span data-ttu-id="5203b-134">Przykłady i instruktaże w sekcji LINQ to DataSet używają jako magazynu danych SQL Server 2005, ale można je zmodyfikować tak, aby korzystały z wersji SQL Server Express Edition.</span><span class="sxs-lookup"><span data-stu-id="5203b-134">The samples and walkthroughs in the LINQ to DataSet section use SQL Server 2005 as the data store but can be modified to use SQL Server Express Edition, instead.</span></span> <span data-ttu-id="5203b-135">Wersja SQL Server Express jest dostępna bez opłat i można ją rozpowszechniać z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="5203b-135">SQL Server Express Edition is available without charge, and you can redistribute it with applications.</span></span> <span data-ttu-id="5203b-136">Jeśli używasz programu Visual Studio, wersja SQL Server Express jest dołączona do wersji Pro i nowszych.</span><span class="sxs-lookup"><span data-stu-id="5203b-136">If you are using Visual Studio, SQL Server Express Edition is included in the Pro and higher editions.</span></span>  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a><span data-ttu-id="5203b-137">Aby pobrać i zainstalować wersję SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="5203b-137">To download and install SQL Server Express Edition</span></span>  
  
1. <span data-ttu-id="5203b-138">Uruchom program Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="5203b-138">Start Internet Explorer.</span></span>  
  
2. <span data-ttu-id="5203b-139">Przejdź do strony pobierania [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) .</span><span class="sxs-lookup"><span data-stu-id="5203b-139">Go to the  [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) download page.</span></span>  
  
3. <span data-ttu-id="5203b-140">Postępuj zgodnie z instrukcjami instalacji w witrynie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5203b-140">Follow the installation instructions on the Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5203b-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5203b-141">See also</span></span>

- [<span data-ttu-id="5203b-142">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="5203b-142">Getting Started</span></span>](getting-started-linq-to-dataset.md)
