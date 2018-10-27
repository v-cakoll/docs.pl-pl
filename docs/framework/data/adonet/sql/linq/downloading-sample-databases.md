---
title: Pobieranie przykładowych baz danych, przykłady kodu ADO.NET
description: Pobierz przykładowe bazy danych używany w przykładach kodu w dokumentacji programu ADO.NET, a także narzędzia programu SQL Server i zarządzania
ms.date: 10/18/2018
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 9779300288135cb9332a028d547ce55a07e89471
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188394"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="cacd5-103">Pobieranie przykładowych baz danych, przykłady kodu ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cacd5-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="cacd5-104">Liczba przykłady i wskazówki dotyczące w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentacji Korzystanie z przykładowych baz danych i programu SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="cacd5-104">A number of samples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample databases and SQL Server Express.</span></span> <span data-ttu-id="cacd5-105">Możesz pobrać te produkty bezpłatnie od firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cacd5-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database"></a><span data-ttu-id="cacd5-106">Pobieranie przykładowej bazy danych Northwind</span><span class="sxs-lookup"><span data-stu-id="cacd5-106">Get the Northwind sample database</span></span>

<span data-ttu-id="cacd5-107">Pobieranie przykładowej bazy danych Northwind z następującej strony w programie Microsoft Download Center:</span><span class="sxs-lookup"><span data-stu-id="cacd5-107">Download the Northwind sample database from the following page in the Microsoft Download Center:</span></span>

[<span data-ttu-id="cacd5-108">Northwind i Pubs przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="cacd5-108">Northwind and Pubs Sample Databases</span></span>](https://go.microsoft.com/fwlink?linkid=64296)

<span data-ttu-id="cacd5-109">Po pobraniu pliku, kliknij dwukrotnie plik aby wyodrębnić baz danych i skryptów.</span><span class="sxs-lookup"><span data-stu-id="cacd5-109">After the file has downloaded, double-click the file to extract the databases and scripts.</span></span> <span data-ttu-id="cacd5-110">Domyślnie pliki są instalowane w folderze `<drive>:\SQL Server 2000 Sample Databases`.</span><span class="sxs-lookup"><span data-stu-id="cacd5-110">By default, the files are installed in the folder `<drive>:\SQL Server 2000 Sample Databases`.</span></span>

<span data-ttu-id="cacd5-111">Zanim będzie możliwe użycie bazy danych Northwind, należy ponownie utworzyć bazę danych w wystąpieniu programu SQL Server przy użyciu [SQL Server Management Studio](#get_ssms) lub podobnego narzędzia, aby uruchomić `instnwnd.sql` plik skryptu w folderze instalacyjnym.</span><span class="sxs-lookup"><span data-stu-id="cacd5-111">Before you can use the Northwind database, you have to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool to run the `instnwnd.sql` script file in the installation folder.</span></span>

## <a name="get-the-adventureworks-sample-database"></a><span data-ttu-id="cacd5-112">Pobierz przykładową bazę danych AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="cacd5-112">Get the AdventureWorks sample database</span></span>

<span data-ttu-id="cacd5-113">Pobierz przykładową bazę danych AdventureWorks z repozytorium GitHub na następujące:</span><span class="sxs-lookup"><span data-stu-id="cacd5-113">Download the AdventureWorks sample database from the following GitHub repository:</span></span>

[<span data-ttu-id="cacd5-114">Przykładowe bazy danych AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="cacd5-114">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="cacd5-115">Po pobraniu jedną kopię zapasową bazy danych (\*bak) plików, przywrócenia kopii zapasowej do wystąpienia programu SQL Server przy użyciu programu SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="cacd5-115">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="cacd5-116">Zobacz [pobieranie programu SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="cacd5-116">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get_sql"></a> <span data-ttu-id="cacd5-117">Pobieranie programu SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="cacd5-117">Get SQL Server Express</span></span>

<span data-ttu-id="cacd5-118">SQL Server Express jest bezpłatny, klasy podstawowej wersji programu SQL Server, które można redystrybuować z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="cacd5-118">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="cacd5-119">Pobieranie programu SQL Server Express z następującej strony:</span><span class="sxs-lookup"><span data-stu-id="cacd5-119">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="cacd5-120">Edycje Express programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="cacd5-120">SQL Server Express Editions</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="cacd5-121">Jeśli używasz [programu Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB są objęte bezpłatna wersja Community, a także wersje Professional i wyższych.</span><span class="sxs-lookup"><span data-stu-id="cacd5-121">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the free Community edition as well as the Professional and higher editions.</span></span>  

## <a name="get_ssms"></a> <span data-ttu-id="cacd5-122">Pobieranie programu SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cacd5-122">Get SQL Server Management Studio</span></span>
<span data-ttu-id="cacd5-123">Jeśli chcesz wyświetlić lub zmodyfikować bazy danych, który został pobrany, można użyć programu SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="cacd5-123">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="cacd5-124">Pobierz program SSMS z następującej strony:</span><span class="sxs-lookup"><span data-stu-id="cacd5-124">Download SSMS from the following page:</span></span>

[<span data-ttu-id="cacd5-125">Pobieranie programu SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="cacd5-125">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="cacd5-126">Można również wyświetlać i zarządzać bazami danych w programie Visual Studio zintegrowane środowisko programistyczne (IDE).</span><span class="sxs-lookup"><span data-stu-id="cacd5-126">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="cacd5-127">W [programu Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), połączenia z bazą danych z **Eksplorator obiektów SQL Server**, lub Utwórz połączenie danych z bazy danych w **Eksploratora serwera**.</span><span class="sxs-lookup"><span data-stu-id="cacd5-127">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="cacd5-128">Otwórz te okienka Eksploratora z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="cacd5-128">Open these explorer panes from the **View** menu.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cacd5-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cacd5-129">See also</span></span>

- [<span data-ttu-id="cacd5-130">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="cacd5-130">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
