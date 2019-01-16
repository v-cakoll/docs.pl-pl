---
title: Pobieranie przykładowych baz danych programu SQL Server, przykłady kodu ADO.NET
description: Pobieranie przykładowych baz danych programu SQL Server, używany w przykładach kodu w dokumentacji programu ADO.NET, a także narzędzia programu SQL Server i zarządzania
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 5580f06f3d28ed6d70f75b619498ac8de7bc3326
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307295"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Pobieranie przykładowych baz danych, przykłady kodu ADO.NET

Liczba przykłady i przewodniki w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentacji Korzystanie z przykładowych baz danych z programu SQL Server i programu SQL Server Express. Możesz pobrać te produkty bezpłatnie od firmy Microsoft.

## <a name="get-the-northwind-sample-database-for-sql-server"></a>Pobieranie przykładowej bazy danych Northwind dla programu SQL Server

Pobierz skrypt `instnwnd.sql` z następujących repozytorium GitHub, aby utworzyć i załadować przykładowej bazy danych Northwind dla programu SQL Server:

[Northwind i pubs przykładowych baz danych programu Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Zanim będzie możliwe użycie bazy danych Northwind, musisz uruchomić pobrany `instnwnd.sql` plik skryptu w celu ponownego utworzenia bazy danych w wystąpieniu programu SQL Server przy użyciu [SQL Server Management Studio](#get_ssms) lub podobnego narzędzia. Postępuj zgodnie z instrukcjami w pliku Readme w repozytorium.

> [!TIP]
> Jeśli szukasz bazy danych Northwind dla programu Microsoft Access, zobacz [Instalowanie przykładowej bazy danych Northwind dla programu Microsoft Access](#northwind_access).

## <a name="northwind_access"></a> Pobieranie przykładowej bazy danych Northwind dla programu Microsoft Access

Przykładowej bazy danych Northwind dla programu Microsoft Access nie jest dostępna w Microsoft Download Center. Aby zainstalować Northwind bezpośrednio z poziomu programu Access, wykonaj następujące czynności:

1. Otwórz program Access.

1. Wprowadź **Northwind** w **wyszukiwanie szablonów Online** , a następnie wybierz **Enter**.

1. Na ekranie wyników wybierz **Northwind**. Otwiera nowe okno z opisem bazy danych Northwind.

1. W nowym oknie w **nazwy pliku** tekst Podaj nazwę pliku dla kopii bazy danych Northwind.

1. Wybierz pozycję **Utwórz**. Dostęp pliki do pobrania z bazy danych Northwind i przygotowuje plik.

1. Po zakończeniu tego procesu zostanie otwarty ekran powitalny bazy danych.

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>Pobierz przykładową bazę danych AdventureWorks programu SQL Server

Pobierz przykładową bazę danych AdventureWorks programu SQL Server z następujących repozytorium GitHub:

[Przykładowe bazy danych AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Po pobraniu jedną kopię zapasową bazy danych (\*bak) plików, przywrócenia kopii zapasowej do wystąpienia programu SQL Server przy użyciu programu SQL Server Management Studio (SSMS). Zobacz [pobieranie programu SQL Server Management Studio](#get_ssms).

## <a name="get_ssms"></a> Pobieranie programu SQL Server Management Studio
Jeśli chcesz wyświetlić lub zmodyfikować bazy danych, który został pobrany, można użyć programu SQL Server Management Studio (SSMS). Pobierz program SSMS z następującej strony:

[Pobieranie programu SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) 

Można również wyświetlać i zarządzać bazami danych w programie Visual Studio zintegrowane środowisko programistyczne (IDE). W [programu Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), połączenia z bazą danych z **Eksplorator obiektów SQL Server**, lub Utwórz połączenie danych z bazy danych w **Eksploratora serwera**. Otwórz te okienka Eksploratora z **widoku** menu.

## <a name="get_sql"></a> Pobieranie programu SQL Server Express

SQL Server Express jest bezpłatny, klasy podstawowej wersji programu SQL Server, które można redystrybuować z aplikacjami. Pobieranie programu SQL Server Express z następującej strony:
  
[SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)

Jeśli używasz [programu Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB znajduje się w wersji Professional lub nowszy, a także bezpłatna wersja Community programu Visual Studio.  

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
