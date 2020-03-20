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
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Pobieranie przykładowych baz danych dla przykładowych ADO.NET kodów

Wiele przykładów i instruktaży [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] w dokumentacji użyć przykładowych baz danych programu SQL Server i PROGRAMU SQL Server Express. Możesz pobrać te produkty bezpłatnie od firmy Microsoft.

## <a name="get-the-northwind-sample-database-for-sql-server"></a>Pobieranie przykładowej bazy danych Northwind dla programu SQL Server

Pobierz skrypt `instnwnd.sql` z następującego repozytorium GitHub, aby utworzyć i załadować przykładową bazę danych Northwind dla programu SQL Server:

[Northwind i puby przykładowe bazy danych dla programu Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Przed użyciem bazy danych Northwind należy uruchomić `instnwnd.sql` pobrany plik skryptu, aby odtworzyć bazę danych w wystąpieniu programu SQL Server przy użyciu [programu SQL Server Management Studio](#get_ssms) lub podobnego narzędzia. Postępuj zgodnie z instrukcjami w pliku Readme w repozytorium.

> [!TIP]
> Jeśli szukasz bazy danych Northwind dla programu Microsoft Access, zobacz [Instalowanie przykładowej bazy danych Northwind dla programu Microsoft Access](#northwind_access).

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a>Pobieranie przykładowej bazy danych Northwind dla programu Microsoft Access

Przykładowa baza danych Northwind dla programu Microsoft Access nie jest dostępna w Centrum pobierania firmy Microsoft. Aby zainstalować Northwind bezpośrednio z poziomu programu Access, wykonaj następujące czynności:

1. Otwórz dostęp.

1. Wprowadź **northwind** w polu **Wyszukaj szablony online,** a następnie wybierz pozycję **Wprowadź**.

1. Na ekranie wyników wybierz pozycję **Northwind**. Otworzy się nowe okno z opisem bazy danych Northwind.

1. W nowym oknie w polu tekstowym **Nazwa pliku** podaj nazwę pliku dla kopii bazy danych Northwind.

1. Wybierz **pozycję Utwórz**. Program Access pobiera bazę danych Northwind i przygotowuje plik.

1. Po zakończeniu tego procesu baza danych zostanie otwarta z ekranem powitalnym.

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>Pobierz przykładową bazę danych AdventureWorks dla programu SQL Server

Pobierz przykładową bazę danych AdventureWorks dla programu SQL Server z następującego repozytorium GitHub:

[Przykładowe bazy danych AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Po pobraniu jednego z\*plików kopii zapasowej bazy danych (.bak) przywróć kopię zapasową do wystąpienia programu SQL Server przy użyciu programu SQL Server Management Studio (SSMS). Zobacz [Get SQL Server Management Studio](#get_ssms).

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a>Pobierz program SQL Server Management Studio
Jeśli chcesz wyświetlić lub zmodyfikować pobraną bazę danych, możesz użyć programu SQL Server Management Studio (SSMS). Pobierz SSMS z następującej strony:

[Pobieranie programu SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms)

Można również wyświetlać i zarządzać bazami danych w zintegrowanym środowisku programistycznym Visual Studio (IDE). W [programie Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)połącz się z bazą danych z **Eksploratora obiektów programu SQL Server**lub utwórz połączenie danych z bazą danych w **Eksploratorze serwera**. Otwórz te okienka eksploratora z menu **Widok.**

## <a name="get-sql-server-express"></a><a name="get_sql"></a>Pobierz program SQL Server Express

SQL Server Express to bezpłatna, podstawowa wersja programu SQL Server, którą można rozpowszechniać z aplikacjami. Pobierz program SQL Server Express z następującej strony:
  
[SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)

Jeśli używasz [programu Visual Studio,](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)sql Server Express LocalDB znajduje się w bezpłatnej wersji społeczności programu Visual Studio, a także w wersji Professional i wyższych.  

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie](getting-started.md)
