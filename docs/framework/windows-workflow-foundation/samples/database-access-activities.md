---
title: Działania dostępu do bazy danych
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: efcdd25ee3e6b86d87d551623b166eab4fa76845
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850405"
---
# <a name="database-access-activities"></a>Działania dostępu do bazy danych
Działania dostępu do bazy danych umożliwiają dostęp do bazy danych w przepływie pracy. Te działania, Zezwalaj na dostęp do bazy danych do pobierania lub modyfikowanie informacji i użycia [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) dostęp do bazy danych.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).
>
>  `<InstallDrive>:\WF_WCF_Samples`
>
>  Jeśli ten katalog nie istnieje, przejdź do (strona pobierania) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.
>
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a>Działania bazy danych
 Na liście działań zawarty w tym przykładzie można znaleźć w poniższych sekcjach.

## <a name="dbupdate"></a>DbUpdate
 Wykonuje zapytanie SQL, które powoduje zmianę w bazie danych (insert, update, delete i inne modyfikacje).

 Ta klasa wykonuje swoją pracę asynchronicznie (pochodzi od klasy <xref:System.Activities.AsyncCodeActivity> i używa jej funkcje asynchroniczne).

 Informacje dotyczące połączenia, mogą być konfigurowane przez ustawienie Nazwa niezmienna dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub po prostu nazwę konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.

 Zapytanie do wykonania jest skonfigurowana w jego `Sql` właściwości i parametrów są przekazywane za pośrednictwem `Parameters` kolekcji.

 Po `DbUpdate` jest wykonywane, liczba uwzględnionych rekordów jest zwracany w `AffectedRecords` właściwości.

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
|Parametry połączenia|Parametry połączenia do łączenia z bazą danych. Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.|
|ConfigName|Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu. Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.|
|CommandType|Typ <xref:System.Data.Common.DbCommand> do wykonania.|
|SQL|Polecenie SQL do wykonania.|
|Parametry|Kolekcja parametrów zapytania SQL.|
|AffectedRecords|Liczba rekordów na ostatnią operację.|

## <a name="dbqueryscalar"></a>DbQueryScalar
 Wykonuje kwerendę, która pobiera pojedynczą wartość z bazy danych.

 Ta klasa wykonuje swoją pracę asynchronicznie (pochodzi od klasy <xref:System.Activities.AsyncCodeActivity%601> i używa jej funkcje asynchroniczne).

 Informacje dotyczące połączenia, mogą być konfigurowane przez ustawienie Nazwa niezmienna dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub po prostu nazwę konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.

 Zapytanie do wykonania jest skonfigurowana w jego `Sql` właściwości i parametrów są przekazywane za pośrednictwem `Parameters` kolekcji.

 Po `DbQueryScalar` jest wykonywane, skalarnej jest zwracany w `Result``out` argumentu (typu `TResult`, która jest zdefiniowana w klasie bazowej <xref:System.Activities.AsyncCodeActivity%601>).

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
|Parametry połączenia|Parametry połączenia do łączenia z bazą danych. Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.|
|ConfigName|Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu. Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.|
|CommandType|Typ <xref:System.Data.Common.DbCommand> do wykonania.|
|SQL|Polecenie SQL do wykonania.|
|Parametry|Kolekcja parametrów zapytania SQL.|
|Wynik|Scalar, uzyskany po wykonaniu zapytania. Ten argument jest typu `TResult`.|

## <a name="dbquery"></a>DbQuery
 Wykonuje kwerendę, która pobiera listę obiektów. Po wykonaniu zapytania wykonaniu funkcji mapowania (może być <xref:System.Func%601> < `DbDataReader`, `TResult`> lub <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>). Ta funkcja mapowania pobiera rekord w `DbDataReader` i mapowany do obiektu, który ma zostać zwrócona.

 Informacje dotyczące połączenia, mogą być konfigurowane przez ustawienie Nazwa niezmienna dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub po prostu nazwę konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.

 Zapytanie do wykonania jest skonfigurowana w jego `Sql` właściwości i parametrów są przekazywane za pośrednictwem `Parameters` kolekcji.

 Wyniki zapytania SQL są pobierane przy użyciu `DbDataReader`. Działanie iteruje `DbDataReader` i mapuje wierszy w `DbDataReader` do wystąpienia `TResult`. Użytkownik `DbQuery` musi dostarczyć kod mapowania i to zrobić na dwa sposoby: za pomocą <xref:System.Func%601> < `DbDataReader`, `TResult`> lub <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>. W pierwszym przypadku mapie odbywa się w jednym pulse wykonywania. Dlatego jest szybszy, ale to nie można serializować do XAML. W ostatnim przypadku mapie odbywa się w wielu impulsów. W związku z tym, może być niższa, ale można go serializować do XAML i utworzone w sposób deklaratywny (wszelkie istniejące działanie mogą uczestniczyć w mapowaniu).

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
|Parametry połączenia|Parametry połączenia do łączenia z bazą danych. Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.|
|ConfigName|Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu. Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.|
|CommandType|Typ <xref:System.Data.Common.DbCommand> do wykonania.|
|SQL|Polecenie SQL do wykonania.|
|Parametry|Kolekcja parametrów zapytania SQL.|
|mapowania|Mapowanie funkcji (<xref:System.Func%601><`DbDataReader`, `TResult`>) przyjmującej rekord `DataReader` uzyskane w rezultacie wykonywania zapytania, a następnie zwraca wystąpienie obiektu typu `TResult` mają zostać dodane do `Result` kolekcji.<br /><br /> W tym przypadku mapowanie odbywa się w jednym pulse wykonywania, ale nie utworzono, deklaratywnego za pomocą projektanta.|
|MapperFunc|Mapowanie funkcji (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) przyjmującej rekord `DataReader` uzyskane w rezultacie wykonywania zapytania, a następnie zwraca wystąpienie obiektu typu `TResult` mają zostać dodane do `Result` kolekcji.<br /><br /> W tym przypadku mapowanie odbywa się w wielu impulsów wykonywania. Ta funkcja może być serializowany do XAML i utworzone w sposób deklaratywny (wszelkie istniejące działanie mogą uczestniczyć w mapowaniu).|
|Wynik|Lista obiektów uzyskane w rezultacie wykonywania zapytania i wykonywanie funkcji mapowania dla każdego rekordu w `DataReader`.|

## <a name="dbquerydataset"></a>DbQueryDataSet
 Wykonuje kwerendę, która zwraca <xref:System.Data.DataSet>. Ta klasa wykonuje swoją pracę asynchronicznie. Pochodzi od klasy <xref:System.Activities.AsyncCodeActivity> < `TResult`> i używa jej funkcje asynchroniczne.

 Informacje dotyczące połączenia, mogą być konfigurowane przez ustawienie Nazwa niezmienna dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub po prostu nazwę konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.

 Zapytanie do wykonania jest skonfigurowana w jego `Sql` właściwości i parametrów są przekazywane za pośrednictwem `Parameters` kolekcji.

 Po `DbQueryDataSet` jest wykonywany `DataSet` jest zwracany w `Result``out` argumentu (typu `TResult`, która jest zdefiniowana w klasie bazowej <xref:System.Activities.AsyncCodeActivity%601>).

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
|Parametry połączenia|Parametry połączenia do łączenia z bazą danych. Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.|
|ConfigName|Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu. Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.|
|CommandType|Typ <xref:System.Data.Common.DbCommand> do wykonania.|
|SQL|Polecenie SQL do wykonania.|
|Parametry|Kolekcja parametrów zapytania SQL.|
|Wynik|<xref:System.Data.DataSet> które są uzyskiwane po wykonaniu zapytania.|

## <a name="configuring-connection-information"></a>Konfigurowanie informacji o połączeniu
 Wszystkie DbActivities udostępniać te same parametry konfiguracji. Takie grupy można skonfigurować na dwa sposoby:

-   `ConnectionString + InvariantName`: Ustaw dostawcy ADO.NET niezmienną nazwę i parametry połączenia.

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

-   `ConfigName`: Ustaw nazwę sekcji konfiguracji, który zawiera informacje o połączeniu.

    ```xml
    <connectionStrings>
        <add name="DbActivitiesSample"
             providerName="System.Data.SqlClient"
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
      </connectionStrings>
    ```

-   W ramach działania:

    ```
    Activity dbSelectCount = new DbQueryScalar<int>()
    {
        ConfigName = "DbActivitiesSample",
        Sql = "SELECT COUNT(*) FROM Roles"
    };
    ```

## <a name="running-this-sample"></a>Uruchomieniem tego przykładu

### <a name="setup-instructions"></a>Instrukcje instalacji
 W tym przykładzie korzysta z bazy danych. Skrypt konfiguracji i obciążenia (plik Setup.cmd) jest dostarczany z próbką. Należy wykonać ten plik przy użyciu wiersza polecenia.

 Plik Setup.cmd skrypt wywołuje plik skryptu CreateDb.sql zawiera polecenia SQL, które należy wykonać następujące czynności:

-   Tworzy bazę danych o nazwie DbActivitiesSample.

-   Tworzy tabelę ról.

-   Tworzy tabelę Pracownicy.

-   Wstawia trzy rekordy w tabeli ról.

-   Wstawia dwunastu rekordów do tabel pracownikami.

##### <a name="to-run-setupcmd"></a>Aby uruchomić plik Setup.cmd

1.  Otwórz wiersz polecenia.

2.  Przejdź do folderu przykładu DbActivities.

3.  Wpisz "plik setup.cmd", a następnie naciśnij klawisz ENTER.

    > [!NOTE]
    >  Plik Setup.cmd próbuje zainstalować przykład wystąpienia SqlExpress komputera lokalnego. Jeśli chcesz zainstalować go w inne wystąpienie programu SQL server, należy edytować plik Setup.cmd z nową nazwą wystąpienia.

##### <a name="to-uninstall-the-sample-database"></a>Aby odinstalować przykładowej bazy danych

1.  Uruchom Cleanup.cmd z tym samym folderze, w wierszu polecenia.

##### <a name="to-run-the-sample"></a>Aby uruchomić przykład

1.  Otwórz rozwiązanie w programie Visual Studio 2010

2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3.  Do uruchomienia przykładu bez debugowania, naciśnij kombinację klawiszy CTRL + F5.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
