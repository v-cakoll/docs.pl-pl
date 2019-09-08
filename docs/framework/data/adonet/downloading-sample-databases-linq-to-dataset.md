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
# <a name="downloading-sample-databases-linq-to-dataset"></a>Pobieranie przykładowych baz danych (LINQ to DataSet)
Przykłady i instruktaże w dokumentacji LINQ to DataSet korzystają z przykładowej bazy danych AdventureWorks. Ten produkt można pobrać bezpłatnie z witryny pobierania firmy Microsoft. Przykłady i instruktaże w dokumentacji LINQ to DataSet używają SQL Server jako magazynu danych. Wersja SQL Server Express, która jest dostępna bez opłat, może być również używana jako magazyn danych, a nie SQL Server.  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>Pobieranie i Instalowanie bazy danych AdventureWorks  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>Aby pobrać i zainstalować przykładową bazę danych AdventureWorks dla SQL Server  
  
1. Otwórz program Internet Explorer.  
  
2. Przejdź do witryny [SQL Server samples 2005 i przykładowych baz danych](https://go.microsoft.com/fwlink/?linkid=31046) w sieci Web.  
  
3. Postępuj zgodnie z instrukcjami dotyczącymi pobierania przykładowej bazy danych AdventureWorks dla danego typu procesora (na przykład AdventureWorksDB. msi) i Zapisz. Plik MSI na komputer lokalny.  
  
4. Jeśli masz zainstalowaną poprzednią wersję usługi AdventureWorks z pobrania lub w trakcie instalacji SQL Server, musisz ją usunąć przed uruchomieniem pliku AdventureWorks. msi.  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>Aby usunąć poprzednie pobranie przykładowej bazy danych AdventureWorks  
  
1. Porzuć bazę danych AdventureWorks lub AdventureWorksDW.  
  
2. W obszarze **Dodaj lub usuń programy**wybierz pozycję **AdventureWorksDB** lub **AdventureWorksBI** , a następnie kliknij pozycję **Usuń**.  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>Aby usunąć przykładową bazę danych AdventureWorks, która została wcześniej zainstalowana przy użyciu Instalatora  
  
1. Porzuć bazę danych AdventureWorks lub AdventureWorksDW.  
  
2. W obszarze **Dodaj lub usuń programy**wybierz pozycję **Microsoft SQL Server 2005** , a następnie kliknij przycisk **Zmień**.  
  
3. W **obszarze wybór składnika**wybierz pozycję **składniki stacji roboczej** , a następnie kliknij przycisk **dalej**.  
  
4. Na stronie **Witamy w Kreatorze instalacji SQL Server**kliknij przycisk **dalej**.  
  
5. W obszarze **sprawdzenie konfiguracji systemu**kliknij przycisk **dalej**.  
  
6. W obszarze **zmiana lub usuwanie wystąpienia**kliknij pozycję **Zmień zainstalowane składniki**.  
  
7. W **obszarze Wybór funkcji**rozwiń węzeł **Dokumentacja, przykłady i Przykładowa baza danych** .  
  
8. Wybierz **przykładowy kod i aplikacje**. Rozwiń **przykładowe bazy danych**, wybierz przykładową bazę danych do usunięcia, a następnie wybierz opcję **cała funkcja będzie niedostępna**. Kliknij przycisk **Dalej**.  
  
9. Kliknij przycisk **Zainstaluj** i Zakończ pracę Kreatora instalacji.  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>Aby dołączyć pliki przykładowej bazy danych AdventureWorks do wystąpienia SQL Server  
  
1. Po pobraniu pliku instalacyjnego przykładowej bazy danych pliku kliknij dwukrotnie plik **AdventureWorksDB. msi** (lub pobrany plik), aby zainstalować bazę danych. Domyślnie baza danych jest instalowana w katalogu c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.  
  
2. Dołącz pliki bazy danych AdventureWorks do wystąpienia SQL Server, wykonując następujący skrypt SQLCMD lub SQL Server Management Studio:  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Jeśli zainstalowano te pliki na innym dysku lub w katalogu, należy odpowiednio skorygować ścieżki przed wykonaniem `sp_attach_db` procedury składowanej.  
  
## <a name="downloading-sql-server-express-edition"></a>Pobieranie SQL Server Express Edition  
 Przykłady i instruktaże w sekcji LINQ to DataSet używają jako magazynu danych SQL Server 2005, ale można je zmodyfikować tak, aby korzystały z wersji SQL Server Express Edition. Wersja SQL Server Express jest dostępna bez opłat i można ją rozpowszechniać z aplikacjami. Jeśli używasz programu Visual Studio, wersja SQL Server Express jest dołączona do wersji Pro i nowszych.  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>Aby pobrać i zainstalować wersję SQL Server Express  
  
1. Uruchom program Internet Explorer.  
  
2. Przejdź do strony pobierania [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) .  
  
3. Postępuj zgodnie z instrukcjami instalacji w witrynie sieci Web.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](getting-started-linq-to-dataset.md)
