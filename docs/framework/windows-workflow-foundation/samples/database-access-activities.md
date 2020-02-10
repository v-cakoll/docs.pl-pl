---
title: Działania dostępu do bazy danych
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: ed3f0ad3f2fd19f622c9cb0faf7d5cd864b81995
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094647"
---
# <a name="database-access-activities"></a>Działania dostępu do bazy danych

Działania dostępu do bazy danych umożliwiają dostęp do bazy danych w ramach przepływu pracy. Te działania umożliwiają dostęp do baz danych w celu pobierania lub modyfikowania informacji oraz korzystania z [ADO.NET](../../data/adonet/index.md) w celu uzyskania dostępu do bazy danych.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do strony (strona pobierania), aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbki. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a>Działania bazy danych

W poniższych sekcjach szczegółowo opisano listę działań uwzględnionych w tym przykładzie.

## <a name="dbupdate"></a>Dbupdate

Wykonuje zapytanie SQL, które generuje modyfikację bazy danych (Wstawianie, aktualizowanie, usuwanie i inne modyfikacje).

Ta klasa wykonuje swoją działania asynchronicznie (pochodzi z <xref:System.Activities.AsyncCodeActivity> i używa jej funkcji asynchronicznych).

Informacje o połączeniu można skonfigurować przez ustawienie niezmiennej nazwy dostawcy (`ProviderName`) i parametrów połączenia (`ConnectionString`) lub po prostu użycie nazwy konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracyjnego aplikacji.

Zapytanie, które ma zostać wykonane, jest skonfigurowane we właściwości `Sql`, a parametry są przesyłane przez kolekcję `Parameters`.

Po wykonaniu `DbUpdate` liczba rekordów, których to dotyczy, jest zwracana we właściwości `AffectedRecords`.

```csharp
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
|ProviderName|Niezmienna nazwa dostawcy ADO.NET. Jeśli ten argument jest ustawiony, należy również ustawić `ConnectionString`.|
|Przekształcon|Parametry połączenia w celu nawiązania połączenia z bazą danych. Jeśli ten argument jest ustawiony, należy również ustawić `ProviderName`.|
|Konfiguracja pliku|Nazwa sekcji pliku konfiguracji, w której są przechowywane informacje o połączeniu. Gdy ten argument jest ustawiony `ProviderName` i `ConnectionString` nie są wymagane.|
|CommandType|Typ <xref:System.Data.Common.DbCommand>, który ma zostać wykonany.|
|Sql|Polecenie SQL, które ma zostać wykonane.|
|Parametry|Kolekcja parametrów zapytania SQL.|
|AffectedRecords|Liczba rekordów, których dotyczy Ostatnia operacja.|

## <a name="dbqueryscalar"></a>DbQueryScalar

Wykonuje zapytanie, które pobiera pojedynczą wartość z bazy danych.

Ta klasa wykonuje swoją działania asynchronicznie (pochodzi z <xref:System.Activities.AsyncCodeActivity%601> i używa jej funkcji asynchronicznych).

Informacje o połączeniu można skonfigurować przez ustawienie niezmiennej nazwy dostawcy (`ProviderName`) i parametrów połączenia (`ConnectionString`) lub po prostu użycie nazwy konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracyjnego aplikacji.

Zapytanie, które ma zostać wykonane, jest skonfigurowane we właściwości `Sql`, a parametry są przesyłane przez kolekcję `Parameters`.

Po wykonaniu `DbQueryScalar` wartość skalarna jest zwracana w argumencie `Result out` (typu `TResult`, który jest zdefiniowany w klasie bazowej <xref:System.Activities.AsyncCodeActivity%601>).

```csharp
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
|ProviderName|Niezmienna nazwa dostawcy ADO.NET. Jeśli ten argument jest ustawiony, należy również ustawić `ConnectionString`.|
|Przekształcon|Parametry połączenia w celu nawiązania połączenia z bazą danych. Jeśli ten argument jest ustawiony, należy również ustawić `ProviderName`.|
|Konfiguracja pliku|Nazwa sekcji pliku konfiguracji, w której są przechowywane informacje o połączeniu. Gdy ten argument jest ustawiony `ProviderName` i `ConnectionString` nie są wymagane.|
|CommandType|Typ <xref:System.Data.Common.DbCommand>, który ma zostać wykonany.|
|Sql|Polecenie SQL, które ma zostać wykonane.|
|Parametry|Kolekcja parametrów zapytania SQL.|
|Wynik|Wartość skalarna, która jest uzyskiwana po wykonaniu zapytania. Ten argument jest typu `TResult`.|

## <a name="dbquery"></a>DBQuery

Wykonuje zapytanie, które pobiera listę obiektów. Po wykonaniu zapytania funkcja mapowania jest wykonywana (może być <xref:System.Func%601><`DbDataReader``TResult`> lub <xref:System.Activities.ActivityFunc%601><`DbDataReader``TResult`). Ta funkcja mapowania pobiera rekord w `DbDataReader` i mapuje go do obiektu, który ma zostać zwrócony.

Informacje o połączeniu można skonfigurować przez ustawienie niezmiennej nazwy dostawcy (`ProviderName`) i parametrów połączenia (`ConnectionString`) lub po prostu użycie nazwy konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracyjnego aplikacji.

Zapytanie, które ma zostać wykonane, jest skonfigurowane we właściwości `Sql`, a parametry są przesyłane przez kolekcję `Parameters`.

Wyniki zapytania SQL są pobierane przy użyciu `DbDataReader`. Działanie iteruje `DbDataReader` i mapuje wiersze w `DbDataReader` do wystąpienia `TResult`. Użytkownik `DbQuery` musi dostarczyć kod mapowania i można to zrobić na dwa sposoby: używając <xref:System.Func%601><`DbDataReader`, `TResult`> lub <xref:System.Activities.ActivityFunc%601><`DbDataReader``TResult`. W pierwszym przypadku mapa jest wykonywana w ramach jednego impulsu wykonywania. W związku z tym jest to szybsze, ale nie można go serializować do XAML. W ostatnim przypadku mapa jest wykonywana w wielu pulsach. W związku z tym może być wolniejszy, ale może być serializowany do XAML i w sposób deklaratywny (wszystkie istniejące działania mogą uczestniczyć w mapowaniu).

```csharp
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
|ProviderName|Niezmienna nazwa dostawcy ADO.NET. Jeśli ten argument jest ustawiony, należy również ustawić `ConnectionString`.|
|Przekształcon|Parametry połączenia w celu nawiązania połączenia z bazą danych. Jeśli ten argument jest ustawiony, należy również ustawić `ProviderName`.|
|Konfiguracja pliku|Nazwa sekcji pliku konfiguracji, w której są przechowywane informacje o połączeniu. Gdy ten argument jest ustawiony `ProviderName` i `ConnectionString` nie są wymagane.|
|CommandType|Typ <xref:System.Data.Common.DbCommand>, który ma zostać wykonany.|
|Sql|Polecenie SQL, które ma zostać wykonane.|
|Parametry|Kolekcja parametrów zapytania SQL.|
|wzor|Funkcja mapowania (<xref:System.Func%601><`DbDataReader`, `TResult`>), która pobiera rekord w `DataReader` uzyskany w wyniku wykonania zapytania i zwraca wystąpienie obiektu typu `TResult`, który zostanie dodany do kolekcji `Result`.<br /><br /> W takim przypadku mapowanie jest wykonywane w ramach pojedynczego impulsu wykonywania, ale nie można go utworzyć deklaratywnie przy użyciu projektanta.|
|MapperFunc|Funkcja mapowania (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>), która pobiera rekord w `DataReader` uzyskany w wyniku wykonania zapytania i zwraca wystąpienie obiektu typu `TResult`, który zostanie dodany do kolekcji `Result`.<br /><br /> W takim przypadku mapowanie jest wykonywane w wielu impulsach wykonania. Tę funkcję można serializować do języka XAML i utworzyć deklaratywnie (wszystkie istniejące działania mogą uczestniczyć w mapowaniu).|
|Wynik|Lista obiektów uzyskanych jako wynik wykonywania zapytania i wykonująca funkcję mapowania dla każdego rekordu w `DataReader`.|

## <a name="dbquerydataset"></a>DbQueryDataSet

Wykonuje zapytanie, które zwraca <xref:System.Data.DataSet>. Ta klasa wykonuje asynchroniczne działanie. Pochodzi on z <xref:System.Activities.AsyncCodeActivity><`TResult`> i używa jego funkcji asynchronicznych.

Informacje o połączeniu można skonfigurować przez ustawienie niezmiennej nazwy dostawcy (`ProviderName`) i parametrów połączenia (`ConnectionString`) lub po prostu użycie nazwy konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracyjnego aplikacji.

Zapytanie, które ma zostać wykonane, jest skonfigurowane we właściwości `Sql`, a parametry są przesyłane przez kolekcję `Parameters`.

Po wykonaniu `DbQueryDataSet` `DataSet` jest zwracany w argumencie `Result out` (typu `TResult`, który jest zdefiniowany w klasie podstawowej <xref:System.Activities.AsyncCodeActivity%601>).

```csharp
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
|ProviderName|Niezmienna nazwa dostawcy ADO.NET. Jeśli ten argument jest ustawiony, należy również ustawić `ConnectionString`.|
|Przekształcon|Parametry połączenia w celu nawiązania połączenia z bazą danych. Jeśli ten argument jest ustawiony, należy również ustawić `ProviderName`.|
|Konfiguracja pliku|Nazwa sekcji pliku konfiguracji, w której są przechowywane informacje o połączeniu. Gdy ten argument jest ustawiony `ProviderName` i `ConnectionString` nie są wymagane.|
|CommandType|Typ <xref:System.Data.Common.DbCommand>, który ma zostać wykonany.|
|Sql|Polecenie SQL, które ma zostać wykonane.|
|Parametry|Kolekcja parametrów zapytania SQL.|
|Wynik|<xref:System.Data.DataSet> uzyskiwany po wykonaniu zapytania.|

## <a name="configuring-connection-information"></a>Konfigurowanie informacji o połączeniu

Wszystkie działania współużytkują te same parametry konfiguracji. Można je skonfigurować na dwa sposoby:

- `ConnectionString + InvariantName`: Ustaw niezmienną nazwę i parametry połączenia dostawcy ADO.NET.

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<DateTime>()
  {
      ProviderName = "System.Data.SqlClient",
      ConnectionString = @"Data Source=.\SQLExpress;
                            Initial Catalog=DbActivitiesSample;
                            Integrated Security=True",
      Sql = "SELECT GetDate()"
  };
  ```

- `ConfigName`: Ustaw nazwę sekcji konfiguracji zawierającej informacje o połączeniu.

  ```xml
  <connectionStrings>
      <add name="DbActivitiesSample"
            providerName="System.Data.SqlClient"
            connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
    </connectionStrings>
  ```

- W działaniu:

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<int>()
  {
      ConfigName = "DbActivitiesSample",
      Sql = "SELECT COUNT(*) FROM Roles"
  };
  ```

## <a name="running-this-sample"></a>Uruchamianie tego przykładu

### <a name="setup-instructions"></a>Instrukcje dotyczące instalacji

Ten przykład używa bazy danych. Skrypt zestawu i ładowania (Setup. cmd) jest dostarczany z przykładem. Należy wykonać ten plik przy użyciu wiersza polecenia.

Skrypt Setup. cmd wywołuje plik skryptu CreateDb. SQL, który zawiera polecenia SQL, które wykonują następujące czynności:

- Tworzy bazę danych o nazwie DbActivitiesSample.

- Tworzy tabelę role.

- Tworzy tabelę Employees.

- Wstawia trzy rekordy do tabeli role.

- Wstawia dwanaście rekordów do tabeli Employees.

##### <a name="to-run-setupcmd"></a>Aby uruchomić program Setup. cmd

1. Otwórz wiersz polecenia.

2. Przejdź do przykładowego folderu DbActivities.

3. Wpisz "Setup. cmd" i naciśnij klawisz ENTER.

    > [!NOTE]
    > Setup. cmd próbuje zainstalować przykład w wystąpieniu programu Local Machine SqlExpress. Jeśli chcesz zainstalować ją w innym wystąpieniu programu SQL Server, edytuj plik Setup. cmd przy użyciu nowej nazwy wystąpienia.

##### <a name="to-uninstall-the-sample-database"></a>Aby odinstalować przykładową bazę danych

1. Uruchom polecenie Oczyść. cmd z przykładowego folderu w wierszu polecenia.

##### <a name="to-run-the-sample"></a>Aby uruchomić przykład

1. Otwórz rozwiązanie w programie Visual Studio 2010

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić przykład bez debugowania, naciśnij klawisze CTRL + F5.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
