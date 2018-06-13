---
title: Pobieranie przykładowe bazy danych (LINQ do DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: f2488b0e1bfc578679a2a2802c332439f374a341
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763056"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>Pobieranie przykładowe bazy danych (LINQ do DataSet)
Przykłady i wskazówki w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dokumentacji Użyj przykładową bazę danych AdventureWorks. Ten produkt bezpłatne można pobrać z witryny pobierania firmy Microsoft. Przykłady i wskazówki w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dokumentacji Użyj programu SQL Server do przechowywania danych. SQL Server Express Edition, który jest dostępny bezpłatnie, mogą służyć do przechowywania danych, zamiast programu SQL Server.  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>Trwa pobieranie i instalowanie bazy danych AdventureWorks  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>Aby pobrać i zainstalować przykładową bazę danych AdventureWorks programu SQL Server  
  
1.  Otwórz program Internet Explorer.  
  
2.  Przejdź do [programu SQL Server 2005 przykłady i przykładowe bazy danych](http://go.microsoft.com/fwlink/?linkid=31046) witryny sieci Web.  
  
3.  Postępuj zgodnie z instrukcjami pobierania przykładowej bazy danych AdventureWorks dla stosowanego typu procesora (na przykład AdventureWorksDB.msi) i Zapisz. Plik MSI na komputerze lokalnym.  
  
4.  Jeśli masz poprzedniej wersji AdventureWorks zainstalowany z pobierania lub podczas instalacji programu SQL Server, należy go usunąć przed uruchomieniem AdventureWorks.msi.  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>Aby usunąć poprzednie pobieranie przykładowej bazy danych AdventureWorks  
  
1.  Usuwanie bazy danych AdventureWorks lub AdventureWorksDW.  
  
2.  Z **Dodaj lub usuń programy**, wybierz pozycję **AdventureWorksDB** lub **AdventureWorksBI** i kliknij przycisk **Usuń**.  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>Aby usunąć przykładową bazę danych AdventureWorks wcześniej zainstalowane przy użyciu Instalatora  
  
1.  Usuwanie bazy danych AdventureWorks lub AdventureWorksDW.  
  
2.  Z **Dodaj lub usuń programy**, wybierz pozycję **Microsoft SQL Server 2005** i kliknij przycisk **zmiany**.  
  
3.  Z **wybór składnika**, wybierz pozycję **składniki stacji roboczej** , a następnie kliknij przycisk **dalej**.  
  
4.  Z **Witamy w Kreatorze instalacji serwera SQL**, kliknij przycisk **dalej**.  
  
5.  Z **sprawdzania konfiguracji systemu**, kliknij przycisk **dalej**.  
  
6.  Z **Zmień lub usuń wystąpienia**, kliknij przycisk **Zmień zainstalowane składniki**.  
  
7.  Z **wybór funkcji**, rozwiń węzeł **dokumentacji, przykłady i przykładowe bazy danych** węzła.  
  
8.  Wybierz **przykładowy kod i aplikacje**. Rozwiń węzeł **przykładowe bazy danych**, wybierz przykładowej bazy danych można usunąć, a następnie wybierz **Cała funkcja będzie niedostępna**. Kliknij przycisk **Dalej**.  
  
9. Kliknij przycisk **zainstalować** i Zakończ pracę Kreatora instalacji.  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>Aby dołączyć przykładowe pliki bazy danych AdventureWorks do wystąpienia programu SQL Server  
  
1.  Po pobraniu pliku Instalatora bazy danych przykładowych plików kliknij dwukrotnie plik **AdventureWorksDB.msi** pliku (lub pobrany plik) do zainstalowania bazy danych. Domyślnie baza danych jest zainstalowana na c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.  
  
2.  Dołącz pliki bazy danych AdventureWorks do wystąpienia programu SQL Server, wykonując następujący skrypt SQLCMD lub SQL Server Management Studio:  
  
    ```  
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Po zainstalowaniu tych plików do innego dysku lub katalogu, należy odpowiednio skorygować ścieżki, przed wykonaniem `sp_attach_db` procedury składowanej.  
  
## <a name="downloading-sql-server-express-edition"></a>Pobieranie programu SQL Server Express Edition.  
 Przykłady i wskazówki w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sekcji, użyj programu SQL Server 2005 do przechowywania danych, ale można zmodyfikować, aby zamiast tego użyj programu SQL Server Express Edition. SQL Server Express Edition jest dostępny bezpłatnie i rozpowszechnić go z aplikacjami. Jeśli używasz programu Visual Studio programu SQL Server Express Edition jest dostępna w wersjach Pro lub nowszy.  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>Aby pobrać i zainstalować program SQL Server Express Edition  
  
1.  Uruchom program Internet Explorer.  
  
2.  Przejdź do [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070) strony pobierania.  
  
3.  Postępuj zgodnie z instrukcjami instalacji w witrynie sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
