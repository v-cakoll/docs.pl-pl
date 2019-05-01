---
title: Pobieranie przykładowych baz danych programu SQL Server, przykłady kodu ADO.NET
description: Pobieranie przykładowych baz danych programu SQL Server, używany w przykładach kodu w dokumentacji programu ADO.NET, a także narzędzia programu SQL Server i zarządzania
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 5580f06f3d28ed6d70f75b619498ac8de7bc3326
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037937"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="75d88-103">Pobieranie przykładowych baz danych, przykłady kodu ADO.NET</span><span class="sxs-lookup"><span data-stu-id="75d88-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="75d88-104">Liczba przykłady i przewodniki w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentacji Korzystanie z przykładowych baz danych z programu SQL Server i programu SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="75d88-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="75d88-105">Możesz pobrać te produkty bezpłatnie od firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="75d88-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="75d88-106">Pobieranie przykładowej bazy danych Northwind dla programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="75d88-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="75d88-107">Pobierz skrypt `instnwnd.sql` z następujących repozytorium GitHub, aby utworzyć i załadować przykładowej bazy danych Northwind dla programu SQL Server:</span><span class="sxs-lookup"><span data-stu-id="75d88-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="75d88-108">Northwind i pubs przykładowych baz danych programu Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="75d88-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="75d88-109">Zanim będzie możliwe użycie bazy danych Northwind, musisz uruchomić pobrany `instnwnd.sql` plik skryptu w celu ponownego utworzenia bazy danych w wystąpieniu programu SQL Server przy użyciu [SQL Server Management Studio](#get_ssms) lub podobnego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="75d88-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="75d88-110">Postępuj zgodnie z instrukcjami w pliku Readme w repozytorium.</span><span class="sxs-lookup"><span data-stu-id="75d88-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="75d88-111">Jeśli szukasz bazy danych Northwind dla programu Microsoft Access, zobacz [Instalowanie przykładowej bazy danych Northwind dla programu Microsoft Access](#northwind_access).</span><span class="sxs-lookup"><span data-stu-id="75d88-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="northwind_access"></a> <span data-ttu-id="75d88-112">Pobieranie przykładowej bazy danych Northwind dla programu Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="75d88-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="75d88-113">Przykładowej bazy danych Northwind dla programu Microsoft Access nie jest dostępna w Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="75d88-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="75d88-114">Aby zainstalować Northwind bezpośrednio z poziomu programu Access, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="75d88-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="75d88-115">Otwórz program Access.</span><span class="sxs-lookup"><span data-stu-id="75d88-115">Open Access.</span></span>

1. <span data-ttu-id="75d88-116">Wprowadź **Northwind** w **wyszukiwanie szablonów Online** , a następnie wybierz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="75d88-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="75d88-117">Na ekranie wyników wybierz **Northwind**.</span><span class="sxs-lookup"><span data-stu-id="75d88-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="75d88-118">Otwiera nowe okno z opisem bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="75d88-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="75d88-119">W nowym oknie w **nazwy pliku** tekst Podaj nazwę pliku dla kopii bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="75d88-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="75d88-120">Wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="75d88-120">Select **Create**.</span></span> <span data-ttu-id="75d88-121">Dostęp pliki do pobrania z bazy danych Northwind i przygotowuje plik.</span><span class="sxs-lookup"><span data-stu-id="75d88-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="75d88-122">Po zakończeniu tego procesu zostanie otwarty ekran powitalny bazy danych.</span><span class="sxs-lookup"><span data-stu-id="75d88-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="75d88-123">Pobierz przykładową bazę danych AdventureWorks programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="75d88-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="75d88-124">Pobierz przykładową bazę danych AdventureWorks programu SQL Server z następujących repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="75d88-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="75d88-125">Przykładowe bazy danych AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="75d88-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="75d88-126">Po pobraniu jedną kopię zapasową bazy danych (\*bak) plików, przywrócenia kopii zapasowej do wystąpienia programu SQL Server przy użyciu programu SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="75d88-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="75d88-127">Zobacz [pobieranie programu SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="75d88-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get_ssms"></a> <span data-ttu-id="75d88-128">Pobieranie programu SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="75d88-128">Get SQL Server Management Studio</span></span>
<span data-ttu-id="75d88-129">Jeśli chcesz wyświetlić lub zmodyfikować bazy danych, który został pobrany, można użyć programu SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="75d88-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="75d88-130">Pobierz program SSMS z następującej strony:</span><span class="sxs-lookup"><span data-stu-id="75d88-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="75d88-131">Pobieranie programu SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="75d88-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="75d88-132">Można również wyświetlać i zarządzać bazami danych w programie Visual Studio zintegrowane środowisko programistyczne (IDE).</span><span class="sxs-lookup"><span data-stu-id="75d88-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="75d88-133">W [programu Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), połączenia z bazą danych z **Eksplorator obiektów SQL Server**, lub Utwórz połączenie danych z bazy danych w **Eksploratora serwera**.</span><span class="sxs-lookup"><span data-stu-id="75d88-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="75d88-134">Otwórz te okienka Eksploratora z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="75d88-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get_sql"></a> <span data-ttu-id="75d88-135">Pobieranie programu SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="75d88-135">Get SQL Server Express</span></span>

<span data-ttu-id="75d88-136">SQL Server Express jest bezpłatny, klasy podstawowej wersji programu SQL Server, które można redystrybuować z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="75d88-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="75d88-137">Pobieranie programu SQL Server Express z następującej strony:</span><span class="sxs-lookup"><span data-stu-id="75d88-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="75d88-138">SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="75d88-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="75d88-139">Jeśli używasz [programu Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB znajduje się w wersji Professional lub nowszy, a także bezpłatna wersja Community programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="75d88-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="75d88-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75d88-140">See also</span></span>

- [<span data-ttu-id="75d88-141">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="75d88-141">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
