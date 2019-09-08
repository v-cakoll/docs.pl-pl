---
title: Pobierz przykładowe SQL Server bazy danych dla przykładów kodu ADO.NET
description: Pobierz przykładowe SQL Server bazy danych używane w przykładach kodu w dokumentacji programu ADO.NET, a także narzędzia do SQL Server i zarządzania
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 60566041ff4f99e96c9aee052dbcc17b5e5da9e5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794027"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Pobierz przykładowe bazy danych dla przykładów kodu ADO.NET

Kilka przykładów i instruktaży w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentacji używają przykładowych baz danych SQL Server i SQL Server Express. Te produkty można pobrać bezpłatnie od firmy Microsoft.

## <a name="get-the-northwind-sample-database-for-sql-server"></a>Pobierz przykładową bazę danych Northwind dla SQL Server

Pobierz skrypt `instnwnd.sql` z następującego repozytorium GitHub, aby utworzyć i załadować przykładową bazę danych Northwind dla SQL Server:

[Przykładowe bazy danych Northwind i pubs dla Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Aby można było korzystać z bazy danych Northwind, należy uruchomić pobrany `instnwnd.sql` plik skryptu w celu odtworzenia bazy danych w wystąpieniu SQL Server przy użyciu [SQL Server Management Studio](#get_ssms) lub podobnego narzędzia. Postępuj zgodnie z instrukcjami w pliku Readme w repozytorium.

> [!TIP]
> Jeśli szukasz bazy danych Northwind dla programu Microsoft Access, zobacz [Instalowanie przykładowej bazy danych Northwind dla programu Microsoft Access](#northwind_access).

## <a name="northwind_access"></a>Pobieranie przykładowej bazy danych Northwind dla programu Microsoft Access

Przykładowa baza danych Northwind dla programu Microsoft Access nie jest dostępna w centrum pobierania Microsoft. Aby zainstalować Northwind bezpośrednio z poziomu programu Access, wykonaj następujące czynności:

1. Otwórz program Access.

1. Wprowadź ciąg **Northwind** w polu **Wyszukaj szablony online** , a następnie wybierz klawisz **Enter**.

1. Na ekranie Wyniki wybierz pozycję **Northwind**. Zostanie otwarte nowe okno z opisem bazy danych Northwind.

1. W nowym oknie, w polu tekstowym **Nazwa pliku** Podaj nazwę pliku dla kopii bazy danych Northwind.

1. Wybierz pozycję **Utwórz**. Program Access pobiera bazę danych Northwind i przygotowuje plik.

1. Po zakończeniu tego procesu zostanie otwarta baza danych z ekranem powitalnym.

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>Pobierz przykładową bazę danych AdventureWorks dla SQL Server

Pobierz przykładową bazę danych AdventureWorks dla SQL Server z następującego repozytorium GitHub:

[Przykładowe bazy danych AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Po pobraniu jednego z plików kopii zapasowej\*bazy danych (. bak) Przywróć kopię zapasową do wystąpienia SQL Server przy użyciu SQL Server Management Studio (SSMS). Zobacz [pobieranie SQL Server Management Studio](#get_ssms).

## <a name="get_ssms"></a>Pobierz SQL Server Management Studio
Jeśli chcesz wyświetlić lub zmodyfikować bazę danych, która została pobrana, możesz użyć SQL Server Management Studio (SSMS). Pobierz narzędzie SSMS z następującej strony:

[Pobierz SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) 

Możesz również wyświetlać bazy danych i zarządzać nimi w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio. W programie [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)Połącz się z bazą danych z programu **Eksplorator obiektów SQL Server**lub Utwórz połączenie danych z bazą danych w programie **Eksplorator serwera**. Otwórz te okienka Eksploratora z menu **Widok** .

## <a name="get_sql"></a>Pobierz SQL Server Express

SQL Server Express to bezpłatna wersja SQL Server, którą można rozpowszechniać za pomocą aplikacji. Pobierz SQL Server Express z następującej strony:
  
[SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)

Jeśli używasz [programu Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB jest zawarty w bezpłatnej wersji Community programu Visual Studio, a także w wersjach Professional i wyższych.  

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](getting-started.md)
