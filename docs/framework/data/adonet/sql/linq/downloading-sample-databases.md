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
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Pobieranie przykładowych baz danych, przykłady kodu ADO.NET

Liczba przykłady i wskazówki dotyczące w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentacji Korzystanie z przykładowych baz danych i programu SQL Server Express. Możesz pobrać te produkty bezpłatnie od firmy Microsoft.

## <a name="get-the-northwind-sample-database"></a>Pobieranie przykładowej bazy danych Northwind

Pobieranie przykładowej bazy danych Northwind z następującej strony w programie Microsoft Download Center:

[Northwind i Pubs przykładowych baz danych](https://go.microsoft.com/fwlink?linkid=64296)

Po pobraniu pliku, kliknij dwukrotnie plik aby wyodrębnić baz danych i skryptów. Domyślnie pliki są instalowane w folderze `<drive>:\SQL Server 2000 Sample Databases`.

Zanim będzie możliwe użycie bazy danych Northwind, należy ponownie utworzyć bazę danych w wystąpieniu programu SQL Server przy użyciu [SQL Server Management Studio](#get_ssms) lub podobnego narzędzia, aby uruchomić `instnwnd.sql` plik skryptu w folderze instalacyjnym.

## <a name="get-the-adventureworks-sample-database"></a>Pobierz przykładową bazę danych AdventureWorks

Pobierz przykładową bazę danych AdventureWorks z repozytorium GitHub na następujące:

[Przykładowe bazy danych AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Po pobraniu jedną kopię zapasową bazy danych (\*bak) plików, przywrócenia kopii zapasowej do wystąpienia programu SQL Server przy użyciu programu SQL Server Management Studio (SSMS). Zobacz [pobieranie programu SQL Server Management Studio](#get_ssms).

## <a name="get_sql"></a> Pobieranie programu SQL Server Express

SQL Server Express jest bezpłatny, klasy podstawowej wersji programu SQL Server, które można redystrybuować z aplikacjami. Pobieranie programu SQL Server Express z następującej strony:
  
[Edycje Express programu SQL Server](https://www.microsoft.com/sql-server/sql-server-editions-express)

Jeśli używasz [programu Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB są objęte bezpłatna wersja Community, a także wersje Professional i wyższych.  

## <a name="get_ssms"></a> Pobieranie programu SQL Server Management Studio
Jeśli chcesz wyświetlić lub zmodyfikować bazy danych, który został pobrany, można użyć programu SQL Server Management Studio (SSMS). Pobierz program SSMS z następującej strony:

[Pobieranie programu SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) 

Można również wyświetlać i zarządzać bazami danych w programie Visual Studio zintegrowane środowisko programistyczne (IDE). W [programu Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), połączenia z bazą danych z **Eksplorator obiektów SQL Server**, lub Utwórz połączenie danych z bazy danych w **Eksploratora serwera**. Otwórz te okienka Eksploratora z **widoku** menu.
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
