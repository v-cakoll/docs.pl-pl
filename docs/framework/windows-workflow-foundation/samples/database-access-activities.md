---
title: "Działania dostępu do bazy danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dfc99593e1c705cff5069b5dd864d372f8afda8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="database-access-activities"></a>Działania dostępu do bazy danych
Działania dostępu do bazy danych pozwalają na dostęp do bazy danych w przepływie pracy. Te działania Zezwalaj na dostęp do bazy danych do pobierania lub modyfikowanie informacji i użycia [ADO.NET](http://go.microsoft.com/fwlink/?LinkId=166081) dostęp do bazy danych.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do (stronę pobierania), aby pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`  
  
## <a name="database-activities"></a>Działania bazy danych  
 W poniższych sekcjach opisano na liście działań zawarty w tym przykładzie.  
  
## <a name="dbupdate"></a>DbUpdate  
 Wykonuje zapytanie SQL, które powoduje zmianę w bazie danych (insert, update, delete i innych modyfikacji).  
  
 Ta klasa wykonuje pracę asynchronicznie (dziedziczy <xref:System.Activities.AsyncCodeActivity> i używa jej możliwości asynchroniczne).  
  
 Informacje o połączeniu można skonfigurować przez ustawienie niezmienną nazwę dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub tylko przy użyciu nazwy konfiguracji ciągu połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.  
  
 Kwerenda ma być wykonywana jest skonfigurowana w jego `Sql` właściwości i parametry są przekazywane za pośrednictwem `Parameters` kolekcji.  
  
 Po `DbUpdate` jest wykonywane, liczbę uwzględnionych rekordów jest zwracany w `AffectedRecords` właściwości.  
  
```  
Public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }       
}  
```  
  
|Argument|Opis|  
|-|-|  
|ProviderName|Niezmienna Nazwa dostawcy ADO.NET. Jeśli ten argument jest ustawiona, a następnie `ConnectionString` również musi być ustawiona.|  
|Parametry połączenia|Parametry połączenia do połączenia z bazą danych. Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.|  
|ConfigName|Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu. Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.|  
|Obiekt CommandType|Typ <xref:System.Data.Common.DbCommand> do wykonania.|  
|SQL|Polecenie SQL do wykonania.|  
|Parametry|Kolekcja parametrów zapytania SQL.|  
|AffectedRecords|Liczba rekordów wpływ ostatniej operacji.|  
  
## <a name="dbqueryscalar"></a>DbQueryScalar  
 Wykonuje zapytanie, które pobiera pojedynczą wartość z bazy danych.  
  
 Ta klasa wykonuje pracę asynchronicznie (dziedziczy <xref:System.Activities.AsyncCodeActivity%601> i używa jej możliwości asynchroniczne).  
  
 Informacje o połączeniu można skonfigurować przez ustawienie niezmienną nazwę dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub tylko przy użyciu nazwy konfiguracji ciągu połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.  
  
 Kwerenda ma być wykonywana jest skonfigurowana w jego `Sql` właściwości i parametry są przekazywane za pośrednictwem `Parameters` kolekcji.  
  
 Po `DbQueryScalar` jest wykonywane, skalarnych jest zwracany w `Result``out` argumentu (typu `TResult`, która jest zdefiniowana w klasie podstawowej <xref:System.Activities.AsyncCodeActivity%601>).  
  
```  
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
}  
```  
  
|Argument|Opis|  
|-|-|  
|ProviderName|Niezmienna Nazwa dostawcy ADO.NET. Jeśli ten argument jest ustawiona, a następnie `ConnectionString` również musi być ustawiona.|  
|Parametry połączenia|Parametry połączenia do połączenia z bazą danych. Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.|  
|ConfigName|Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu. Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.|  
|Obiekt CommandType|Typ <xref:System.Data.Common.DbCommand> do wykonania.|  
|SQL|Polecenie SQL do wykonania.|  
|Parametry|Kolekcja parametrów zapytania SQL.|  
|Wynik|Skalarną uzyskany po wykonaniu zapytania. Ten argument jest typu `TResult`.|  
  
## <a name="dbquery"></a>DbQuery  
 Wykonuje zapytanie pobiera listę obiektów. Po wykonaniu zapytania wykonaniu funkcji mapowania (można go <xref:System.Func%601> < `DbDataReader`, `TResult`> lub <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>). Ta funkcja mapowania pobiera rekord w `DbDataReader` oraz opisano, jak obiekt ma zostać zwrócona.  
  
 Informacje o połączeniu można skonfigurować przez ustawienie niezmienną nazwę dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub tylko przy użyciu nazwy konfiguracji ciągu połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.  
  
 Kwerenda ma być wykonywana jest skonfigurowana w jego `Sql` właściwości i parametry są przekazywane za pośrednictwem `Parameters` kolekcji.  
  
 Pobierane są wyniki zapytania SQL, używając `DbDataReader`. Działania wykonuje iterację `DbDataReader` i mapy wierszy w `DbDataReader` na wystąpienie `TResult`. Użytkownik `DbQuery` musi podać kod mapowania i to zrobić na dwa sposoby: za pomocą <xref:System.Func%601> < `DbDataReader`, `TResult`> lub <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>. W pierwszym przypadku mapy odbywa się w jednym pulse wykonywania. W związku z tym szybciej, ale to nie może być serializowany w języku XAML. W ostatnim przypadku mapy odbywa się w wielu impulsów. W związku z tym może przebiegać wolniej, ale można go serializować w języku XAML i deklaratywnie utworzone (wszystkie istniejące działania mogą uczestniczyć w mapowaniu).  
  
```  
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [OverloadGroup("DirectMapping")]  
    [DefaultValue(null)]  
    public Func<DbDataReader, TResult> Mapper { get; set; }  
  
    [OverloadGroup("MultiplePulseMapping")]  
    [DefaultValue(null)]  
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }  
}  
```  
  
|Argument|Opis|  
|-|-|  
|ProviderName|Niezmienna Nazwa dostawcy ADO.NET. Jeśli ten argument jest ustawiona, a następnie `ConnectionString` również musi być ustawiona.|  
|Parametry połączenia|Parametry połączenia do połączenia z bazą danych. Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.|  
|ConfigName|Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu. Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.|  
|Obiekt CommandType|Typ <xref:System.Data.Common.DbCommand> do wykonania.|  
|SQL|Polecenie SQL do wykonania.|  
|Parametry|Kolekcja parametrów zapytania SQL.|  
|mapowania|Mapowanie funkcji (<xref:System.Func%601><`DbDataReader`, `TResult`>) pobierającej rekord `DataReader` uzyskane w rezultacie wykonywania zapytania i zwraca wystąpienie obiektu typu `TResult` mają zostać dodane do `Result` kolekcji.<br /><br /> W takim przypadku mapowania odbywa się w jednym pulse wykonywania, ale nie może być utworzone, deklaratywnego przy użyciu narzędzia Projektant.|  
|MapperFunc|Mapowanie funkcji (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) pobierającej rekord `DataReader` uzyskane w rezultacie wykonywania zapytania i zwraca wystąpienie obiektu typu `TResult` mają zostać dodane do `Result` kolekcji.<br /><br /> W takim przypadku mapowanie odbywa się w wielu impulsów wykonywania. Ta funkcja może być serializacji w języku XAML i deklaratywnie utworzone (wszystkie istniejące działania mogą uczestniczyć w mapowaniu).|  
|Wynik|Lista obiektów uzyskane w rezultacie wykonywania zapytania i wykonywania funkcji mapowania dla każdego rekordu w `DataReader`.|  
  
## <a name="dbquerydataset"></a>DbQueryDataSet  
 Wykonuje zapytanie zwracające <xref:System.Data.DataSet>. Ta klasa wykonuje pracę asynchronicznie. Dziedziczy <xref:System.Activities.AsyncCodeActivity> < `TResult`> i używa jej możliwości asynchroniczne.  
  
 Informacje o połączeniu można skonfigurować przez ustawienie niezmienną nazwę dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub tylko przy użyciu nazwy konfiguracji ciągu połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.  
  
 Kwerenda ma być wykonywana jest skonfigurowana w jego `Sql` właściwości i parametry są przekazywane za pośrednictwem `Parameters` kolekcji.  
  
 Po `DbQueryDataSet` jest wykonywany `DataSet` jest zwracany w `Result``out` argumentu (typu `TResult`, która jest zdefiniowana w klasie podstawowej <xref:System.Activities.AsyncCodeActivity%601>).  
  
```  
public class DbQueryDataSet : AsyncCodeActivity<DataSet>  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
}  
```  
  
|Argument|Opis|  
|-|-|  
|ProviderName|Niezmienna Nazwa dostawcy ADO.NET. Jeśli ten argument jest ustawiona, a następnie `ConnectionString` również musi być ustawiona.|  
|Parametry połączenia|Parametry połączenia do połączenia z bazą danych. Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.|  
|ConfigName|Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu. Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.|  
|Obiekt CommandType|Typ <xref:System.Data.Common.DbCommand> do wykonania.|  
|SQL|Polecenie SQL do wykonania.|  
|Parametry|Kolekcja parametrów zapytania SQL.|  
|Wynik|<xref:System.Data.DataSet>które są uzyskiwane po wykonaniu zapytania.|  
  
## <a name="configuring-connection-information"></a>Konfigurowanie informacji o połączeniu  
 Wszystkie DbActivities mają te same parametry konfiguracji. Można je skonfigurować na dwa sposoby:  
  
-   `ConnectionString + InvariantName`: Ustawienie dostawcy ADO.NET niezmienny ciąg połączenia i nazwę.  
  
    ```  
    Activity dbSelectCount = new DbQueryScalar<DateTime>()  
    {  
        ProviderName = "System.Data.SqlClient",  
        ConnectionString = @"Data Source=.\SQLExpress;  
                             Initial Catalog=DbActivitiesSample;  
                             Integrated Security=True",  
        Sql = "SELECT GetDate()"  
    };  
    ```  
  
-   `ConfigName`: Ustaw nazwę sekcji konfiguracyjnej, który zawiera informacje o połączeniu.  
  
    ```xml  
    <connectionStrings>      
        <add name="DbActivitiesSample"  
             providerName="System.Data.SqlClient"  
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>  
      </connectionStrings>  
    ```  
  
-   W działaniu:  
  
    ```  
    Activity dbSelectCount = new DbQueryScalar<int>()  
    {                  
        ConfigName = "DbActivitiesSample",  
        Sql = "SELECT COUNT(*) FROM Roles"  
    };  
    ```  
  
## <a name="running-this-sample"></a>Uruchomione w tym przykładzie  
  
### <a name="setup-instructions"></a>Instrukcje instalacji  
 W tym przykładzie korzysta z bazy danych. Konfiguracja i obciążenia skryptu (Setup.cmd) jest dostarczany z próbki. Należy wykonać tego pliku przy użyciu wiersza polecenia.  
  
 Skrypt Setup.cmd wywołuje CreateDb.sql pliku skryptu, który zawiera poleceń SQL, które należy wykonać następujące czynności:  
  
-   Tworzy bazę danych o nazwie DbActivitiesSample.  
  
-   Tworzy tabelę ról.  
  
-   Tworzy tabelę pracowników.  
  
-   Wstawia trzy rekordy do tabeli ról.  
  
-   Wstawia dwanaście rekordów do tabeli pracowników.  
  
##### <a name="to-run-setupcmd"></a>Aby uruchomić Setup.cmd  
  
1.  Otwórz wiersz polecenia.  
  
2.  Przejdź do folderu DbActivities próbki.  
  
3.  Wpisz "setup.cmd" i naciśnij klawisz ENTER.  
  
    > [!NOTE]
    >  Setup.cmd próbuje zainstalować przykład wystąpienia SqlExpress komputera lokalnego. Jeśli użytkownik chce go zainstalować w inne wystąpienie programu SQL server, należy edytować Setup.cmd z nową nazwą wystąpienia.  
  
##### <a name="to-uninstall-the-sample-database"></a>Aby odinstalować przykładowej bazy danych  
  
1.  Uruchom Cleanup.cmd z tym samym folderze, w wierszu polecenia.  
  
##### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Otwórz rozwiązanie w[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
2.  Aby skompilować rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić przykładowy bez debugowania, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
