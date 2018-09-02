---
title: Pobieranie przykładowych baz danych (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: 7830095b7c98c0926783324ee7dc2bc1eb345aca
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469846"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>Pobieranie przykładowych baz danych (LINQ to DataSet)
Przykłady i wskazówki w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dokumentacji Użyj przykładowej bazy danych AdventureWorks. Ten produkt bezpłatna można pobrać z witryny pobierania firmy Microsoft. Przykłady i wskazówki w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dokumentacji używania programu SQL Server do przechowywania danych. SQL Server Express Edition, który jest dostępny bez opłat, również może służyć do przechowywania danych, zamiast programu SQL Server.  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>Pobranie i zainstalowanie bazy danych AdventureWorks  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>Aby pobrać i zainstalować przykładową bazę danych AdventureWorks programu SQL Server  
  
1.  Otwórz program Internet Explorer.  
  
2.  Przejdź do [przykładów programu SQL Server 2005 i przykładowych baz danych](https://go.microsoft.com/fwlink/?linkid=31046) witryny sieci Web.  
  
3.  Postępuj zgodnie z instrukcjami pobierania przykładowej bazy danych AdventureWorks dla danego typu procesora (na przykład AdventureWorksDB.msi), a następnie zapisz. Plik MSI na komputerze lokalnym.  
  
4.  Jeśli masz starszą wersję AdventureWorks zainstalowany z pliki do pobrania lub podczas instalacji programu SQL Server, należy go usunąć przed uruchomieniem AdventureWorks.msi.  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>Aby usunąć poprzednie pobieranie przykładową bazę danych AdventureWorks  
  
1.  Usuwanie bazy danych AdventureWorks lub bazy danych AdventureWorksDW.  
  
2.  Z **apletu Dodaj lub usuń programy**, wybierz opcję **AdventureWorksDB** lub **AdventureWorksBI** i kliknij przycisk **Usuń**.  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>Aby usunąć przykładową bazę danych AdventureWorks zainstalowane wcześniej przy użyciu Instalatora  
  
1.  Usuwanie bazy danych AdventureWorks lub bazy danych AdventureWorksDW.  
  
2.  Z **apletu Dodaj lub usuń programy**, wybierz opcję **Microsoft SQL Server 2005** i kliknij przycisk **zmiany**.  
  
3.  Z **wybranych składników**, wybierz opcję **składniki stacji roboczej** a następnie kliknij przycisk **dalej**.  
  
4.  Z **Kreator instalacji programu SQL Server — Zapraszamy**, kliknij przycisk **dalej**.  
  
5.  Z **sprawdzania konfiguracji systemu**, kliknij przycisk **dalej**.  
  
6.  Z **zmiany lub usunięcia wystąpienia**, kliknij przycisk **Zmień zainstalowane składniki**.  
  
7.  Z **wybór funkcji**, rozwiń węzeł **dokumentacji, przykładów i przykładowych baz danych** węzła.  
  
8.  Wybierz **przykładowy kod i aplikacje**. Rozwiń **przykładowych baz danych**, wybierz przykładową bazę danych do usunięcia i wybierz **Cała funkcja będzie niedostępna**. Kliknij przycisk **Dalej**.  
  
9. Kliknij przycisk **zainstalować** i Zakończ działanie Kreatora instalacji.  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>Aby dołączyć plików bazy danych AdventureWorks próbki do wystąpienia programu SQL Server  
  
1.  Po pobraniu pliku Instalatora bazy danych przykładowych plików kliknij dwukrotnie plik **AdventureWorksDB.msi** pliku (lub pobrany plik) w celu zainstalowania bazy danych. Domyślnie baza danych jest zainstalowana na c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.  
  
2.  Dołącz pliki bazy danych AdventureWorks do wystąpienia programu SQL Server, wykonując następujący skrypt SQLCMD lub SQL Server Management Studio:  
  
    ```  
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Jeśli te pliki są zainstalowane na inny dysk lub katalog, należy odpowiednio poprawić ścieżki, przed wykonaniem `sp_attach_db` procedury składowanej.  
  
## <a name="downloading-sql-server-express-edition"></a>Pobieranie programu SQL Server Express Edition  
 Przykłady i wskazówki w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sekcji Użyj programu SQL Server 2005 do przechowywania danych, ale można modyfikować, aby zamiast tego użyj programu SQL Server Express Edition. SQL Server Express Edition jest dostępna bezpłatnie, a następnie rozpowszechnić go z aplikacjami. Jeśli używasz programu Visual Studio, SQL Server Express Edition znajduje się w wersji Pro lub nowszej.  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>Aby pobrać i zainstalować program SQL Server Express Edition  
  
1.  Uruchom program Internet Explorer.  
  
2.  Przejdź do [programu Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) strony pobierania.  
  
3.  W witrynie sieci Web, postępuj zgodnie z instrukcjami instalacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
