---
title: "Pobieranie przykładowe bazy danych (LINQ do DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c8c1c2dabb13393764ca8b1fd9c1a717b9e2527e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="downloading-sample-databases-linq-to-dataset"></a><span data-ttu-id="a3de8-102">Pobieranie przykładowe bazy danych (LINQ do DataSet)</span><span class="sxs-lookup"><span data-stu-id="a3de8-102">Downloading Sample Databases (LINQ to DataSet)</span></span>
<span data-ttu-id="a3de8-103">Przykłady i wskazówki w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dokumentacji Użyj przykładową bazę danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a3de8-103">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentation use the AdventureWorks sample database.</span></span> <span data-ttu-id="a3de8-104">Ten produkt bezpłatne można pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a3de8-104">You can download this product free of charge from the Microsoft download site.</span></span> <span data-ttu-id="a3de8-105">Przykłady i wskazówki w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dokumentacji Użyj programu SQL Server do przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="a3de8-105">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentation use SQL Server as the data store.</span></span> <span data-ttu-id="a3de8-106">SQL Server Express Edition, który jest dostępny bezpłatnie, mogą służyć do przechowywania danych, zamiast programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a3de8-106">SQL Server Express Edition, which is available without charge, can also be used as the data store instead of SQL Server.</span></span>  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a><span data-ttu-id="a3de8-107">Trwa pobieranie i instalowanie bazy danych AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="a3de8-107">Downloading and Installing the AdventureWorks Database</span></span>  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="a3de8-108">Aby pobrać i zainstalować przykładową bazę danych AdventureWorks programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="a3de8-108">To download and install the AdventureWorks sample database for SQL Server</span></span>  
  
1.  <span data-ttu-id="a3de8-109">Otwórz program Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a3de8-109">Open Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="a3de8-110">Przejdź do [programu SQL Server 2005 przykłady i przykładowe bazy danych](http://go.microsoft.com/fwlink/?linkid=31046) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a3de8-110">Go to the [SQL Server 2005 Samples and Sample Databases](http://go.microsoft.com/fwlink/?linkid=31046) Web site.</span></span>  
  
3.  <span data-ttu-id="a3de8-111">Postępuj zgodnie z instrukcjami pobierania przykładowej bazy danych AdventureWorks dla stosowanego typu procesora (na przykład AdventureWorksDB.msi) i Zapisz. Plik MSI na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="a3de8-111">Follow the instructions for downloading the AdventureWorks sample database for your processor type (such as AdventureWorksDB.msi), and save the .MSI file to your local computer.</span></span>  
  
4.  <span data-ttu-id="a3de8-112">Jeśli masz poprzedniej wersji AdventureWorks zainstalowany z pobierania lub podczas instalacji programu SQL Server, należy go usunąć przed uruchomieniem AdventureWorks.msi.</span><span class="sxs-lookup"><span data-stu-id="a3de8-112">If you have a previous version of AdventureWorks installed from the download or during the SQL Server setup, you must remove it before running AdventureWorks.msi.</span></span>  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a><span data-ttu-id="a3de8-113">Aby usunąć poprzednie pobieranie przykładowej bazy danych AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="a3de8-113">To remove a previous download of an AdventureWorks sample database</span></span>  
  
1.  <span data-ttu-id="a3de8-114">Usuwanie bazy danych AdventureWorks lub AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="a3de8-114">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2.  <span data-ttu-id="a3de8-115">Z **Dodaj lub usuń programy**, wybierz pozycję **AdventureWorksDB** lub **AdventureWorksBI** i kliknij przycisk **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="a3de8-115">From **Add or Remove Programs**, select **AdventureWorksDB** or **AdventureWorksBI** and click **Remove**.</span></span>  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a><span data-ttu-id="a3de8-116">Aby usunąć przykładową bazę danych AdventureWorks wcześniej zainstalowane przy użyciu Instalatora</span><span class="sxs-lookup"><span data-stu-id="a3de8-116">To remove an AdventureWorks sample database previously installed using Setup</span></span>  
  
1.  <span data-ttu-id="a3de8-117">Usuwanie bazy danych AdventureWorks lub AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="a3de8-117">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2.  <span data-ttu-id="a3de8-118">Z **Dodaj lub usuń programy**, wybierz pozycję **Microsoft SQL Server 2005** i kliknij przycisk **zmiany**.</span><span class="sxs-lookup"><span data-stu-id="a3de8-118">From **Add or Remove Programs**, select **Microsoft SQL Server 2005** and click **Change**.</span></span>  
  
3.  <span data-ttu-id="a3de8-119">Z **wybór składnika**, wybierz pozycję **składniki stacji roboczej** , a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="a3de8-119">From **Component Selection**, select **Workstation Components** and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="a3de8-120">Z **Witamy w Kreatorze instalacji serwera SQL**, kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="a3de8-120">From **Welcome to the SQL Server Installation Wizard**, click **Next**.</span></span>  
  
5.  <span data-ttu-id="a3de8-121">Z **sprawdzania konfiguracji systemu**, kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="a3de8-121">From **System Configuration Check**, click **Next**.</span></span>  
  
6.  <span data-ttu-id="a3de8-122">Z **Zmień lub usuń wystąpienia**, kliknij przycisk **Zmień zainstalowane składniki**.</span><span class="sxs-lookup"><span data-stu-id="a3de8-122">From **Change or Remove Instance**, click **Change Installed Components**.</span></span>  
  
7.  <span data-ttu-id="a3de8-123">Z **wybór funkcji**, rozwiń węzeł **dokumentacji, przykłady i przykładowe bazy danych** węzła.</span><span class="sxs-lookup"><span data-stu-id="a3de8-123">From **Feature Selection**, expand the **Documentation, Samples, and Sample Databases** node.</span></span>  
  
8.  <span data-ttu-id="a3de8-124">Wybierz **przykładowy kod i aplikacje**.</span><span class="sxs-lookup"><span data-stu-id="a3de8-124">Select **Sample Code and Applications**.</span></span> <span data-ttu-id="a3de8-125">Rozwiń węzeł **przykładowe bazy danych**, wybierz przykładowej bazy danych można usunąć, a następnie wybierz **Cała funkcja będzie niedostępna**.</span><span class="sxs-lookup"><span data-stu-id="a3de8-125">Expand **Sample Databases**, select the sample database to be removed, and select **Entire feature will be unavailable**.</span></span> <span data-ttu-id="a3de8-126">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="a3de8-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="a3de8-127">Kliknij przycisk **zainstalować** i Zakończ pracę Kreatora instalacji.</span><span class="sxs-lookup"><span data-stu-id="a3de8-127">Click **Install** and finish the installation wizard.</span></span>  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a><span data-ttu-id="a3de8-128">Aby dołączyć przykładowe pliki bazy danych AdventureWorks do wystąpienia programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="a3de8-128">To attach the AdventureWorks sample database files to an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="a3de8-129">Po pobraniu pliku Instalatora bazy danych przykładowych plików kliknij dwukrotnie plik **AdventureWorksDB.msi** pliku (lub pobrany plik) do zainstalowania bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a3de8-129">After the file sample database installer file has downloaded, double-click the **AdventureWorksDB.msi** file (or the file you downloaded) to install the database.</span></span> <span data-ttu-id="a3de8-130">Domyślnie baza danych jest zainstalowana na c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span><span class="sxs-lookup"><span data-stu-id="a3de8-130">By default, the database is installed at c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span></span>  
  
2.  <span data-ttu-id="a3de8-131">Dołącz pliki bazy danych AdventureWorks do wystąpienia programu SQL Server, wykonując następujący skrypt SQLCMD lub SQL Server Management Studio:</span><span class="sxs-lookup"><span data-stu-id="a3de8-131">Attach the AdventureWorks database files to an instance of SQL Server by executing the following script SQLCMD or SQL Server Management Studio:</span></span>  
  
    ```  
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     <span data-ttu-id="a3de8-132">Po zainstalowaniu tych plików do innego dysku lub katalogu, należy odpowiednio skorygować ścieżki, przed wykonaniem `sp_attach_db` procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="a3de8-132">If you have installed these files to a different drive or directory, you must revise the paths appropriately before you execute the `sp_attach_db` stored procedure.</span></span>  
  
## <a name="downloading-sql-server-express-edition"></a><span data-ttu-id="a3de8-133">Pobieranie programu SQL Server Express Edition.</span><span class="sxs-lookup"><span data-stu-id="a3de8-133">Downloading SQL Server Express Edition</span></span>  
 <span data-ttu-id="a3de8-134">Przykłady i wskazówki w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sekcji, użyj programu SQL Server 2005 do przechowywania danych, ale można zmodyfikować, aby zamiast tego użyj programu SQL Server Express Edition.</span><span class="sxs-lookup"><span data-stu-id="a3de8-134">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] section use SQL Server 2005 as the data store but can be modified to use SQL Server Express Edition, instead.</span></span> <span data-ttu-id="a3de8-135">SQL Server Express Edition jest dostępny bezpłatnie i rozpowszechnić go z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="a3de8-135">SQL Server Express Edition is available without charge, and you can redistribute it with applications.</span></span> <span data-ttu-id="a3de8-136">Jeśli używasz [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], SQL Server Express Edition jest dostępna w wersjach Pro lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="a3de8-136">If you are using [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], SQL Server Express Edition is included in the Pro and higher editions.</span></span>  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a><span data-ttu-id="a3de8-137">Aby pobrać i zainstalować program SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="a3de8-137">To download and install SQL Server Express Edition</span></span>  
  
1.  <span data-ttu-id="a3de8-138">Uruchom program Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a3de8-138">Start Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="a3de8-139">Przejdź do [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070) strony pobierania.</span><span class="sxs-lookup"><span data-stu-id="a3de8-139">Go to the  [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070) download page.</span></span>  
  
3.  <span data-ttu-id="a3de8-140">Postępuj zgodnie z instrukcjami instalacji w witrynie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a3de8-140">Follow the installation instructions on the Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3de8-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3de8-141">See Also</span></span>  
 [<span data-ttu-id="a3de8-142">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="a3de8-142">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
