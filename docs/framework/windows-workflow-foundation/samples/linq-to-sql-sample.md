---
title: LINQ do SQL próbki
ms.date: 03/30/2017
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
ms.openlocfilehash: 3cfcaf3de1a22b8bb5505083f127a9888b99dbd8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806721"
---
# <a name="linq-to-sql-sample"></a>LINQ do SQL próbki
Ten przykład przedstawia sposób tworzenia działania, aby używać LINQ do jednostek zapytania SQL z tabel w bazach danych programu SQL Server.  
  
> [!IMPORTANT]
>  Przykłady WCF może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  Jeśli ten katalog nie istnieje, kliknij łącze próbki pobierania w górnej części strony. Należy pamiętać, że to łącze pobiera i instaluje wszystkie [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, i [!INCLUDE[infocard](../../../../includes/infocard-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a>Szczegóły działania FindInSqlTable  
 To działanie umożliwia użytkownikom do jednostek zapytania z tabel w bazie danych przy użyciu składnika LINQ to SQL. Użytkownicy działania można też podać predykat LINQ w postaci wyrażenia lambda do filtrowania wyników. Jeśli predykat nie zostanie podany, jest zwracana całą tabelę. W poniższej tabeli przedstawiono wartości właściwości i przywrócenie działania.  
  
|Właściwości lub wartości zwracanej|Opis|  
|------------------------------|-----------------|  
|`Collection` Właściwość|Wymaganą właściwość, która określa kolekcji źródłowej.|  
|`Predicate` Właściwość|Wymaganą właściwość, która określa filtr do kolekcji w postaci wyrażenia lambda.|  
|Wartość zwracana|Filtrowane kolekcji.|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>Przykładem kodu, który używa działania niestandardowe  
 Poniższy przykład kodu wykorzystuje `FindInSqlTable` działania niestandardowego można znaleźć wszystkie wiersze w tabeli programu SQL Server o nazwie `Employee` gdzie `Role` kolumny jest równa `SDE`.  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz wiersz polecenia.  
  
2.  Przejdź do folderu, który zawiera ten przykład.  
  
3.  Uruchom plik polecenia Setup.cmd.  
  
    > [!NOTE]
    >  Skrypt Setup.cmd próbuje zainstalować przykładową bazę danych w komputerze lokalnym programu SQL Server Express. Jeśli użytkownik chce go zainstalować w inne wystąpienie programu SQL server, należy edytować Setup.cmd.  
  
     Skrypt Setup.cmd wykonuje następujące akcje.:  
  
    -   Tworzy bazę danych o nazwie LinqToSqlSample.  
  
    -   Tworzy tabelę ról.  
  
    -   Tworzy tabelę pracowników.  
  
    -   Wstawia 3 rekordy do tabeli ról.  
  
    -   Wstawia 12 rekordów do tabeli pracowników.  
  
4.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania LinqToSQL.sln.  
  
5.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
6.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a>Aby odinstalować LinqToSql przykładowej bazy danych  
  
1.  Otwórz wiersz polecenia.  
  
2.  Przejdź do folderu, który zawiera ten przykład.  
  
3.  Uruchom plik polecenia Cleanup.cmd.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL](http://go.microsoft.com/fwlink/?LinkId=150376)  
 [Wprowadzenie (LINQ to SQL)](http://go.microsoft.com/fwlink/?LinkId=150377)
