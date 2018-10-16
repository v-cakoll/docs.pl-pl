---
title: Pobieranie przykładowych baz danych, przykłady kodu ADO.NET
description: Pobierz przykładowe bazy danych używany w przykładach kodu w dokumentacji programu ADO.NET, a także narzędzia programu SQL Server i zarządzania
ms.date: 10/12/2018
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 75ae1895d683b669f51b33130fc2f47010e39814
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347524"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="55606-103">Pobieranie przykładowych baz danych, przykłady kodu ADO.NET</span><span class="sxs-lookup"><span data-stu-id="55606-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="55606-104">Liczba przykłady i wskazówki dotyczące w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentacji Korzystanie z przykładowych baz danych i programu SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="55606-104">A number of samples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample databases and SQL Server Express.</span></span> <span data-ttu-id="55606-105">Możesz pobrać te produkty bezpłatnie od firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="55606-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-adventureworks-sample-database"></a><span data-ttu-id="55606-106">Pobierz przykładową bazę danych AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="55606-106">Get the AdventureWorks sample database</span></span>

<span data-ttu-id="55606-107">Pobierz przykładową bazę danych AdventureWorks z repozytorium GitHub na następujące:</span><span class="sxs-lookup"><span data-stu-id="55606-107">Download the AdventureWorks sample database from the following GitHub repository:</span></span>

[<span data-ttu-id="55606-108">Przykładowe bazy danych AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="55606-108">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="55606-109">Po pobraniu jedną kopię zapasową bazy danych (\*bak) plików, przywrócenia kopii zapasowej do wystąpienia programu SQL Server przy użyciu programu SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="55606-109">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="55606-110">Zobacz [pobieranie programu SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="55606-110">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-the-northwind-sample-database"></a><span data-ttu-id="55606-111">Pobieranie przykładowej bazy danych Northwind</span><span class="sxs-lookup"><span data-stu-id="55606-111">Get the Northwind sample database</span></span>

<span data-ttu-id="55606-112">Pobieranie przykładowej bazy danych Northwind z następującej strony w programie Microsoft Download Center:</span><span class="sxs-lookup"><span data-stu-id="55606-112">Download the Northwind sample database from the following page in the Microsoft Download Center:</span></span>

[<span data-ttu-id="55606-113">Northwind i Pubs przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="55606-113">Northwind and Pubs Sample Databases</span></span>](https://go.microsoft.com/fwlink?linkid=64296)

<span data-ttu-id="55606-114">Po pobraniu pliku, kliknij dwukrotnie plik aby wyodrębnić baz danych i skryptów.</span><span class="sxs-lookup"><span data-stu-id="55606-114">After the file has downloaded, double-click the file to extract the databases and scripts.</span></span> <span data-ttu-id="55606-115">Domyślnie pliki są instalowane w folderze `<drive>:\SQL Server 2000 Sample Databases`.</span><span class="sxs-lookup"><span data-stu-id="55606-115">By default, the files are installed in the folder `<drive>:\SQL Server 2000 Sample Databases`.</span></span>

<span data-ttu-id="55606-116">Zanim będzie możliwe użycie bazy danych Northwind, należy wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="55606-116">Before you can use the Northwind database, you have to do one of the following things:</span></span>

- <span data-ttu-id="55606-117">Ponowne utworzenie bazy danych w wystąpieniu programu SQL Server, uruchamiając `instnwnd.sql` plik skryptu w folderze instalacyjnym.</span><span class="sxs-lookup"><span data-stu-id="55606-117">Recreate the database on an instance of SQL Server by running the `instnwnd.sql` script file in the installation folder.</span></span>

- <span data-ttu-id="55606-118">Dołącz `northwnd.mdf` pliku z odpowiadającymi mu dostawcami `*.ldf` pliku dziennika do wystąpienia programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="55606-118">Attach the `northwnd.mdf` file with its corresponding `*.ldf` log file to an instance of SQL Server.</span></span>

## <a name="get_sql"></a> <span data-ttu-id="55606-119">Pobieranie programu SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="55606-119">Get SQL Server Express</span></span>

<span data-ttu-id="55606-120">SQL Server Express jest bezpłatny, klasy podstawowej wersji programu SQL Server, które można redystrybuować z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="55606-120">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="55606-121">Pobieranie programu SQL Server Express z następującej strony:</span><span class="sxs-lookup"><span data-stu-id="55606-121">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="55606-122">Edycje Express programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="55606-122">SQL Server Express Editions</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="55606-123">Jeśli używasz [programu Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB znajduje się w wersji Community, a także wersje Professional i wyższych.</span><span class="sxs-lookup"><span data-stu-id="55606-123">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the Community edition as well as the Professional and higher editions.</span></span>  

## <a name="get_ssms"></a> <span data-ttu-id="55606-124">Pobieranie programu SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="55606-124">Get SQL Server Management Studio</span></span>
<span data-ttu-id="55606-125">Jeśli chcesz wyświetlić lub zmodyfikować bazy danych, który został pobrany, można użyć programu SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="55606-125">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="55606-126">Pobierz program SSMS z następującej strony:</span><span class="sxs-lookup"><span data-stu-id="55606-126">Download SSMS from the following page:</span></span>

[<span data-ttu-id="55606-127">Pobieranie programu SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="55606-127">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="55606-128">Można również wyświetlać i zarządzać bazami danych w programie Visual Studio zintegrowane środowisko programistyczne (IDE).</span><span class="sxs-lookup"><span data-stu-id="55606-128">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="55606-129">W [programu Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), połączenia z bazą danych z **Eksplorator obiektów SQL Server**, lub Utwórz połączenie danych z bazy danych w **Eksploratora serwera**.</span><span class="sxs-lookup"><span data-stu-id="55606-129">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="55606-130">Otwórz te okienka Eksploratora z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="55606-130">Open these explorer panes from the **View** menu.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="55606-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55606-131">See also</span></span>

- [<span data-ttu-id="55606-132">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="55606-132">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
