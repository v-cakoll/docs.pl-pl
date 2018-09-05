---
title: Przykład LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
ms.openlocfilehash: 83dc8433459f64860baaca2e8309fbc85e2bb3a2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515371"
---
# <a name="linq-to-sql-sample"></a>Przykład LINQ to SQL
W tym przykładzie pokazano, jak utworzyć działanie używać programu LINQ do jednostek zapytania SQL z tabel bazy danych programu SQL Server.  
  
> [!IMPORTANT]
>  Przykłady WCF może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  Jeśli ten katalog nie istnieje, kliknij link pobierania próbki, w górnej części tej strony. Należy pamiętać, że ten link pobiera i instaluje wszystkie [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, i [!INCLUDE[infocard](../../../../includes/infocard-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a>Szczegóły działań dla FindInSqlTable  
 To działanie umożliwia użytkownikom wykonywanie zapytań dotyczących jednostek z tabel w bazie danych za pomocą LINQ to SQL. Użytkownicy, działania mogą także podać predykat LINQ w postaci wyrażenia lambda do filtrowania wyników. Jeśli nie podano żadnych predykat, zwracany jest całą tabelę. W poniższej tabeli przedstawiono właściwości i zwrócenie wartości dla działania.  
  
|Właściwości lub wartości zwracanej|Opis|  
|------------------------------|-----------------|  
|`Collection` Właściwość|Wymagana właściwość, która określa, kolekcji źródłowej.|  
|`Predicate` Właściwość|Wymagana właściwość, która określa filtr dla kolekcji w postaci wyrażenia lambda.|  
|Wartość zwracana|Kolekcja filtrowane.|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>Przykładowy kod, który używa działania niestandardowe  
 Poniższy przykład kodu wykorzystuje `FindInSqlTable` niestandardowe działanie, aby znaleźć wszystkie wiersze w tabeli programu SQL Server o nazwie `Employee` gdzie `Role` kolumny jest równa `SDE`.  
  
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
  
3.  Uruchom plik Setup.cmd pliku polecenia.  
  
    > [!NOTE]
    >  Plik Setup.cmd skrypt próbuje zainstalować przykładową bazę danych na komputerze lokalnym programu SQL Server Express. Jeśli chcesz zainstalować go w inne wystąpienie programu SQL server, należy edytować plik Setup.cmd.  
  
     Skrypt plik Setup.cmd wykonuje następujące akcje.:  
  
    -   Tworzy bazę danych o nazwie LinqToSqlSample.  
  
    -   Tworzy tabelę ról.  
  
    -   Tworzy tabelę Pracownicy.  
  
    -   Wstawia 3 rekordy w tabeli ról.  
  
    -   Wstawia 12 rekordów do tabel pracownikami.  
  
4.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania LinqToSQL.sln.  
  
5.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
6.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a>Aby odinstalować LinqToSql przykładowej bazy danych  
  
1.  Otwórz wiersz polecenia.  
  
2.  Przejdź do folderu, który zawiera ten przykład.  
  
3.  Uruchom plik polecenia Cleanup.cmd.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL](https://go.microsoft.com/fwlink/?LinkId=150376)  
 [Wprowadzenie (LINQ to SQL)](https://go.microsoft.com/fwlink/?LinkId=150377)
