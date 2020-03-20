---
title: Pobieranie przykładowych baz danych programu SQL Server dla przykładów kodu ADO.NET
description: Pobierz przykładowe bazy danych programu SQL Server używane w przykładach kodu w dokumentacji ADO.NET, a także sql server i narzędzia do zarządzania
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 19d659cbe8f39d27b71dc59c738355f12fce92a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148390"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="01b49-103">Pobieranie przykładowych baz danych dla przykładowych ADO.NET kodów</span><span class="sxs-lookup"><span data-stu-id="01b49-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="01b49-104">Wiele przykładów i instruktaży [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] w dokumentacji użyć przykładowych baz danych programu SQL Server i PROGRAMU SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="01b49-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="01b49-105">Możesz pobrać te produkty bezpłatnie od firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="01b49-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="01b49-106">Pobieranie przykładowej bazy danych Northwind dla programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="01b49-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="01b49-107">Pobierz skrypt `instnwnd.sql` z następującego repozytorium GitHub, aby utworzyć i załadować przykładową bazę danych Northwind dla programu SQL Server:</span><span class="sxs-lookup"><span data-stu-id="01b49-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="01b49-108">Northwind i puby przykładowe bazy danych dla programu Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="01b49-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="01b49-109">Przed użyciem bazy danych Northwind należy uruchomić `instnwnd.sql` pobrany plik skryptu, aby odtworzyć bazę danych w wystąpieniu programu SQL Server przy użyciu [programu SQL Server Management Studio](#get_ssms) lub podobnego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="01b49-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="01b49-110">Postępuj zgodnie z instrukcjami w pliku Readme w repozytorium.</span><span class="sxs-lookup"><span data-stu-id="01b49-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="01b49-111">Jeśli szukasz bazy danych Northwind dla programu Microsoft Access, zobacz [Instalowanie przykładowej bazy danych Northwind dla programu Microsoft Access](#northwind_access).</span><span class="sxs-lookup"><span data-stu-id="01b49-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a><span data-ttu-id="01b49-112">Pobieranie przykładowej bazy danych Northwind dla programu Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="01b49-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="01b49-113">Przykładowa baza danych Northwind dla programu Microsoft Access nie jest dostępna w Centrum pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="01b49-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="01b49-114">Aby zainstalować Northwind bezpośrednio z poziomu programu Access, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="01b49-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="01b49-115">Otwórz dostęp.</span><span class="sxs-lookup"><span data-stu-id="01b49-115">Open Access.</span></span>

1. <span data-ttu-id="01b49-116">Wprowadź **northwind** w polu **Wyszukaj szablony online,** a następnie wybierz pozycję **Wprowadź**.</span><span class="sxs-lookup"><span data-stu-id="01b49-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="01b49-117">Na ekranie wyników wybierz pozycję **Northwind**.</span><span class="sxs-lookup"><span data-stu-id="01b49-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="01b49-118">Otworzy się nowe okno z opisem bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="01b49-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="01b49-119">W nowym oknie w polu tekstowym **Nazwa pliku** podaj nazwę pliku dla kopii bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="01b49-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="01b49-120">Wybierz **pozycję Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="01b49-120">Select **Create**.</span></span> <span data-ttu-id="01b49-121">Program Access pobiera bazę danych Northwind i przygotowuje plik.</span><span class="sxs-lookup"><span data-stu-id="01b49-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="01b49-122">Po zakończeniu tego procesu baza danych zostanie otwarta z ekranem powitalnym.</span><span class="sxs-lookup"><span data-stu-id="01b49-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="01b49-123">Pobierz przykładową bazę danych AdventureWorks dla programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="01b49-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="01b49-124">Pobierz przykładową bazę danych AdventureWorks dla programu SQL Server z następującego repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="01b49-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="01b49-125">Przykładowe bazy danych AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="01b49-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="01b49-126">Po pobraniu jednego z\*plików kopii zapasowej bazy danych (.bak) przywróć kopię zapasową do wystąpienia programu SQL Server przy użyciu programu SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="01b49-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="01b49-127">Zobacz [Get SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="01b49-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a><span data-ttu-id="01b49-128">Pobierz program SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="01b49-128">Get SQL Server Management Studio</span></span>
<span data-ttu-id="01b49-129">Jeśli chcesz wyświetlić lub zmodyfikować pobraną bazę danych, możesz użyć programu SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="01b49-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="01b49-130">Pobierz SSMS z następującej strony:</span><span class="sxs-lookup"><span data-stu-id="01b49-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="01b49-131">Pobieranie programu SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="01b49-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms)

<span data-ttu-id="01b49-132">Można również wyświetlać i zarządzać bazami danych w zintegrowanym środowisku programistycznym Visual Studio (IDE).</span><span class="sxs-lookup"><span data-stu-id="01b49-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="01b49-133">W [programie Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)połącz się z bazą danych z **Eksploratora obiektów programu SQL Server**lub utwórz połączenie danych z bazą danych w **Eksploratorze serwera**.</span><span class="sxs-lookup"><span data-stu-id="01b49-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="01b49-134">Otwórz te okienka eksploratora z menu **Widok.**</span><span class="sxs-lookup"><span data-stu-id="01b49-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get-sql-server-express"></a><a name="get_sql"></a><span data-ttu-id="01b49-135">Pobierz program SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="01b49-135">Get SQL Server Express</span></span>

<span data-ttu-id="01b49-136">SQL Server Express to bezpłatna, podstawowa wersja programu SQL Server, którą można rozpowszechniać z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="01b49-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="01b49-137">Pobierz program SQL Server Express z następującej strony:</span><span class="sxs-lookup"><span data-stu-id="01b49-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="01b49-138">SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="01b49-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="01b49-139">Jeśli używasz [programu Visual Studio,](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)sql Server Express LocalDB znajduje się w bezpłatnej wersji społeczności programu Visual Studio, a także w wersji Professional i wyższych.</span><span class="sxs-lookup"><span data-stu-id="01b49-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="01b49-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01b49-140">See also</span></span>

- [<span data-ttu-id="01b49-141">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="01b49-141">Getting Started</span></span>](getting-started.md)
