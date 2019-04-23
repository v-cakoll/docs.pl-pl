---
title: Działania dostępu do bazy danych
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: 2463c3a87be7f7e248572d45e018b72661f4f8c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322605"
---
# <a name="database-access-activities"></a><span data-ttu-id="811e0-102">Działania dostępu do bazy danych</span><span class="sxs-lookup"><span data-stu-id="811e0-102">Database Access Activities</span></span>
<span data-ttu-id="811e0-103">Działania dostępu do bazy danych umożliwiają dostęp do bazy danych w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="811e0-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="811e0-104">Te działania, Zezwalaj na dostęp do bazy danych do pobierania lub modyfikowanie informacji i użycia [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) dostęp do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="811e0-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="811e0-105">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="811e0-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="811e0-106">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="811e0-106">Check for the following (default) directory before continuing.</span></span>
>
>  `<InstallDrive>:\WF_WCF_Samples`
>
>  <span data-ttu-id="811e0-107">Jeśli ten katalog nie istnieje, przejdź do (strona pobierania) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="811e0-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="811e0-108">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="811e0-108">This sample is located in the following directory.</span></span>
>
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="811e0-109">Działania bazy danych</span><span class="sxs-lookup"><span data-stu-id="811e0-109">Database Activities</span></span>
 <span data-ttu-id="811e0-110">Na liście działań zawarty w tym przykładzie można znaleźć w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="811e0-110">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="811e0-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="811e0-111">DbUpdate</span></span>
 <span data-ttu-id="811e0-112">Wykonuje zapytanie SQL, które powoduje zmianę w bazie danych (insert, update, delete i inne modyfikacje).</span><span class="sxs-lookup"><span data-stu-id="811e0-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

 <span data-ttu-id="811e0-113">Ta klasa wykonuje swoją pracę asynchronicznie (pochodzi od klasy <xref:System.Activities.AsyncCodeActivity> i używa jej funkcje asynchroniczne).</span><span class="sxs-lookup"><span data-stu-id="811e0-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

 <span data-ttu-id="811e0-114">Informacje dotyczące połączenia, mogą być konfigurowane przez ustawienie Nazwa niezmienna dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub po prostu nazwę konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="811e0-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="811e0-115">Zapytanie do wykonania jest skonfigurowana w jego `Sql` właściwości i parametrów są przekazywane za pośrednictwem `Parameters` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="811e0-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="811e0-116">Po `DbUpdate` jest wykonywane, liczba uwzględnionych rekordów jest zwracany w `AffectedRecords` właściwości.</span><span class="sxs-lookup"><span data-stu-id="811e0-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

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

|<span data-ttu-id="811e0-117">Argument</span><span class="sxs-lookup"><span data-stu-id="811e0-117">Argument</span></span>|<span data-ttu-id="811e0-118">Opis</span><span class="sxs-lookup"><span data-stu-id="811e0-118">Description</span></span>|
|-|-|
|<span data-ttu-id="811e0-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="811e0-119">ProviderName</span></span>|<span data-ttu-id="811e0-120">Niezmienna Nazwa dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="811e0-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="811e0-121">Jeśli ten argument jest ustawiona, a następnie `ConnectionString` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="811e0-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="811e0-122">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="811e0-122">ConnectionString</span></span>|<span data-ttu-id="811e0-123">Parametry połączenia do łączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="811e0-123">Connection string to connect to the database.</span></span> <span data-ttu-id="811e0-124">Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="811e0-124">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="811e0-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="811e0-125">ConfigName</span></span>|<span data-ttu-id="811e0-126">Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="811e0-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="811e0-127">Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="811e0-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="811e0-128">CommandType</span><span class="sxs-lookup"><span data-stu-id="811e0-128">CommandType</span></span>|<span data-ttu-id="811e0-129">Typ <xref:System.Data.Common.DbCommand> do wykonania.</span><span class="sxs-lookup"><span data-stu-id="811e0-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="811e0-130">Sql</span><span class="sxs-lookup"><span data-stu-id="811e0-130">Sql</span></span>|<span data-ttu-id="811e0-131">Polecenie SQL do wykonania.</span><span class="sxs-lookup"><span data-stu-id="811e0-131">The SQL command to be executed.</span></span>|
|<span data-ttu-id="811e0-132">Parametry</span><span class="sxs-lookup"><span data-stu-id="811e0-132">Parameters</span></span>|<span data-ttu-id="811e0-133">Kolekcja parametrów zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="811e0-133">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="811e0-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="811e0-134">AffectedRecords</span></span>|<span data-ttu-id="811e0-135">Liczba rekordów na ostatnią operację.</span><span class="sxs-lookup"><span data-stu-id="811e0-135">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="811e0-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="811e0-136">DbQueryScalar</span></span>
 <span data-ttu-id="811e0-137">Wykonuje kwerendę, która pobiera pojedynczą wartość z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="811e0-137">Executes a query that retrieves a single value from the database.</span></span>

 <span data-ttu-id="811e0-138">Ta klasa wykonuje swoją pracę asynchronicznie (pochodzi od klasy <xref:System.Activities.AsyncCodeActivity%601> i używa jej funkcje asynchroniczne).</span><span class="sxs-lookup"><span data-stu-id="811e0-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

 <span data-ttu-id="811e0-139">Informacje dotyczące połączenia, mogą być konfigurowane przez ustawienie Nazwa niezmienna dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub po prostu nazwę konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="811e0-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="811e0-140">Zapytanie do wykonania jest skonfigurowana w jego `Sql` właściwości i parametrów są przekazywane za pośrednictwem `Parameters` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="811e0-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="811e0-141">Po `DbQueryScalar` jest wykonywane, skalarnej jest zwracany w `Result out` argumentu (typu `TResult`, która jest zdefiniowana w klasie bazowej <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="811e0-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

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

|<span data-ttu-id="811e0-142">Argument</span><span class="sxs-lookup"><span data-stu-id="811e0-142">Argument</span></span>|<span data-ttu-id="811e0-143">Opis</span><span class="sxs-lookup"><span data-stu-id="811e0-143">Description</span></span>|
|-|-|
|<span data-ttu-id="811e0-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="811e0-144">ProviderName</span></span>|<span data-ttu-id="811e0-145">Niezmienna Nazwa dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="811e0-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="811e0-146">Jeśli ten argument jest ustawiona, a następnie `ConnectionString` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="811e0-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="811e0-147">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="811e0-147">ConnectionString</span></span>|<span data-ttu-id="811e0-148">Parametry połączenia do łączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="811e0-148">Connection string to connect to the database.</span></span> <span data-ttu-id="811e0-149">Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="811e0-149">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="811e0-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="811e0-150">ConfigName</span></span>|<span data-ttu-id="811e0-151">Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="811e0-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="811e0-152">Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="811e0-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="811e0-153">CommandType</span><span class="sxs-lookup"><span data-stu-id="811e0-153">CommandType</span></span>|<span data-ttu-id="811e0-154">Typ <xref:System.Data.Common.DbCommand> do wykonania.</span><span class="sxs-lookup"><span data-stu-id="811e0-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="811e0-155">Sql</span><span class="sxs-lookup"><span data-stu-id="811e0-155">Sql</span></span>|<span data-ttu-id="811e0-156">Polecenie SQL do wykonania.</span><span class="sxs-lookup"><span data-stu-id="811e0-156">The SQL command to be executed.</span></span>|
|<span data-ttu-id="811e0-157">Parametry</span><span class="sxs-lookup"><span data-stu-id="811e0-157">Parameters</span></span>|<span data-ttu-id="811e0-158">Kolekcja parametrów zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="811e0-158">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="811e0-159">Wynik</span><span class="sxs-lookup"><span data-stu-id="811e0-159">Result</span></span>|<span data-ttu-id="811e0-160">Scalar, uzyskany po wykonaniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="811e0-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="811e0-161">Ten argument jest typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="811e0-161">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="811e0-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="811e0-162">DbQuery</span></span>
 <span data-ttu-id="811e0-163">Wykonuje kwerendę, która pobiera listę obiektów.</span><span class="sxs-lookup"><span data-stu-id="811e0-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="811e0-164">Po wykonaniu zapytania wykonaniu funkcji mapowania (może być <xref:System.Func%601> < `DbDataReader`, `TResult`> lub <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>).</span><span class="sxs-lookup"><span data-stu-id="811e0-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="811e0-165">Ta funkcja mapowania pobiera rekord w `DbDataReader` i mapowany do obiektu, który ma zostać zwrócona.</span><span class="sxs-lookup"><span data-stu-id="811e0-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

 <span data-ttu-id="811e0-166">Informacje dotyczące połączenia, mogą być konfigurowane przez ustawienie Nazwa niezmienna dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub po prostu nazwę konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="811e0-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="811e0-167">Zapytanie do wykonania jest skonfigurowana w jego `Sql` właściwości i parametrów są przekazywane za pośrednictwem `Parameters` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="811e0-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="811e0-168">Wyniki zapytania SQL są pobierane przy użyciu `DbDataReader`.</span><span class="sxs-lookup"><span data-stu-id="811e0-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="811e0-169">Działanie iteruje `DbDataReader` i mapuje wierszy w `DbDataReader` do wystąpienia `TResult`.</span><span class="sxs-lookup"><span data-stu-id="811e0-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="811e0-170">Użytkownik `DbQuery` musi dostarczyć kod mapowania i to zrobić na dwa sposoby: za pomocą <xref:System.Func%601> < `DbDataReader`, `TResult`> lub <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>.</span><span class="sxs-lookup"><span data-stu-id="811e0-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="811e0-171">W pierwszym przypadku mapie odbywa się w jednym pulse wykonywania.</span><span class="sxs-lookup"><span data-stu-id="811e0-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="811e0-172">Dlatego jest szybszy, ale to nie można serializować do XAML.</span><span class="sxs-lookup"><span data-stu-id="811e0-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="811e0-173">W ostatnim przypadku mapie odbywa się w wielu impulsów.</span><span class="sxs-lookup"><span data-stu-id="811e0-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="811e0-174">W związku z tym, może być niższa, ale można go serializować do XAML i utworzone w sposób deklaratywny (wszelkie istniejące działanie mogą uczestniczyć w mapowaniu).</span><span class="sxs-lookup"><span data-stu-id="811e0-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

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

|<span data-ttu-id="811e0-175">Argument</span><span class="sxs-lookup"><span data-stu-id="811e0-175">Argument</span></span>|<span data-ttu-id="811e0-176">Opis</span><span class="sxs-lookup"><span data-stu-id="811e0-176">Description</span></span>|
|-|-|
|<span data-ttu-id="811e0-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="811e0-177">ProviderName</span></span>|<span data-ttu-id="811e0-178">Niezmienna Nazwa dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="811e0-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="811e0-179">Jeśli ten argument jest ustawiona, a następnie `ConnectionString` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="811e0-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="811e0-180">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="811e0-180">ConnectionString</span></span>|<span data-ttu-id="811e0-181">Parametry połączenia do łączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="811e0-181">Connection string to connect to the database.</span></span> <span data-ttu-id="811e0-182">Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="811e0-182">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="811e0-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="811e0-183">ConfigName</span></span>|<span data-ttu-id="811e0-184">Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="811e0-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="811e0-185">Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="811e0-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="811e0-186">CommandType</span><span class="sxs-lookup"><span data-stu-id="811e0-186">CommandType</span></span>|<span data-ttu-id="811e0-187">Typ <xref:System.Data.Common.DbCommand> do wykonania.</span><span class="sxs-lookup"><span data-stu-id="811e0-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="811e0-188">Sql</span><span class="sxs-lookup"><span data-stu-id="811e0-188">Sql</span></span>|<span data-ttu-id="811e0-189">Polecenie SQL do wykonania.</span><span class="sxs-lookup"><span data-stu-id="811e0-189">The SQL command to be executed.</span></span>|
|<span data-ttu-id="811e0-190">Parametry</span><span class="sxs-lookup"><span data-stu-id="811e0-190">Parameters</span></span>|<span data-ttu-id="811e0-191">Kolekcja parametrów zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="811e0-191">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="811e0-192">mapowania</span><span class="sxs-lookup"><span data-stu-id="811e0-192">Mapper</span></span>|<span data-ttu-id="811e0-193">Mapowanie funkcji (<xref:System.Func%601><`DbDataReader`, `TResult`>) przyjmującej rekord `DataReader` uzyskane w rezultacie wykonywania zapytania, a następnie zwraca wystąpienie obiektu typu `TResult` mają zostać dodane do `Result` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="811e0-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="811e0-194">W tym przypadku mapowanie odbywa się w jednym pulse wykonywania, ale nie utworzono, deklaratywnego za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="811e0-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="811e0-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="811e0-195">MapperFunc</span></span>|<span data-ttu-id="811e0-196">Mapowanie funkcji (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) przyjmującej rekord `DataReader` uzyskane w rezultacie wykonywania zapytania, a następnie zwraca wystąpienie obiektu typu `TResult` mają zostać dodane do `Result` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="811e0-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="811e0-197">W tym przypadku mapowanie odbywa się w wielu impulsów wykonywania.</span><span class="sxs-lookup"><span data-stu-id="811e0-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="811e0-198">Ta funkcja może być serializowany do XAML i utworzone w sposób deklaratywny (wszelkie istniejące działanie mogą uczestniczyć w mapowaniu).</span><span class="sxs-lookup"><span data-stu-id="811e0-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="811e0-199">Wynik</span><span class="sxs-lookup"><span data-stu-id="811e0-199">Result</span></span>|<span data-ttu-id="811e0-200">Lista obiektów uzyskane w rezultacie wykonywania zapytania i wykonywanie funkcji mapowania dla każdego rekordu w `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="811e0-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="811e0-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="811e0-201">DbQueryDataSet</span></span>
 <span data-ttu-id="811e0-202">Wykonuje kwerendę, która zwraca <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="811e0-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="811e0-203">Ta klasa wykonuje swoją pracę asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="811e0-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="811e0-204">Pochodzi od klasy <xref:System.Activities.AsyncCodeActivity> < `TResult`> i używa jej funkcje asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="811e0-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

 <span data-ttu-id="811e0-205">Informacje dotyczące połączenia, mogą być konfigurowane przez ustawienie Nazwa niezmienna dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub po prostu nazwę konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="811e0-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="811e0-206">Zapytanie do wykonania jest skonfigurowana w jego `Sql` właściwości i parametrów są przekazywane za pośrednictwem `Parameters` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="811e0-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="811e0-207">Po `DbQueryDataSet` jest wykonywany `DataSet` jest zwracany w `Result out` argumentu (typu `TResult`, która jest zdefiniowana w klasie bazowej <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="811e0-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

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

|<span data-ttu-id="811e0-208">Argument</span><span class="sxs-lookup"><span data-stu-id="811e0-208">Argument</span></span>|<span data-ttu-id="811e0-209">Opis</span><span class="sxs-lookup"><span data-stu-id="811e0-209">Description</span></span>|
|-|-|
|<span data-ttu-id="811e0-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="811e0-210">ProviderName</span></span>|<span data-ttu-id="811e0-211">Niezmienna Nazwa dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="811e0-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="811e0-212">Jeśli ten argument jest ustawiona, a następnie `ConnectionString` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="811e0-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="811e0-213">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="811e0-213">ConnectionString</span></span>|<span data-ttu-id="811e0-214">Parametry połączenia do łączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="811e0-214">Connection string to connect to the database.</span></span> <span data-ttu-id="811e0-215">Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="811e0-215">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="811e0-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="811e0-216">ConfigName</span></span>|<span data-ttu-id="811e0-217">Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="811e0-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="811e0-218">Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="811e0-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="811e0-219">CommandType</span><span class="sxs-lookup"><span data-stu-id="811e0-219">CommandType</span></span>|<span data-ttu-id="811e0-220">Typ <xref:System.Data.Common.DbCommand> do wykonania.</span><span class="sxs-lookup"><span data-stu-id="811e0-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="811e0-221">Sql</span><span class="sxs-lookup"><span data-stu-id="811e0-221">Sql</span></span>|<span data-ttu-id="811e0-222">Polecenie SQL do wykonania.</span><span class="sxs-lookup"><span data-stu-id="811e0-222">The SQL command to be executed.</span></span>|
|<span data-ttu-id="811e0-223">Parametry</span><span class="sxs-lookup"><span data-stu-id="811e0-223">Parameters</span></span>|<span data-ttu-id="811e0-224">Kolekcja parametrów zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="811e0-224">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="811e0-225">Wynik</span><span class="sxs-lookup"><span data-stu-id="811e0-225">Result</span></span>|<span data-ttu-id="811e0-226"><xref:System.Data.DataSet> które są uzyskiwane po wykonaniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="811e0-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="811e0-227">Konfigurowanie informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="811e0-227">Configuring Connection Information</span></span>
 <span data-ttu-id="811e0-228">Wszystkie DbActivities udostępniać te same parametry konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="811e0-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="811e0-229">Takie grupy można skonfigurować na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="811e0-229">They can be configured in two ways:</span></span>

-   <span data-ttu-id="811e0-230">`ConnectionString + InvariantName`: Ustawienie dostawcy ADO.NET niezmienną nazwę i parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="811e0-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

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

-   <span data-ttu-id="811e0-231">`ConfigName`: Ustaw nazwę sekcji konfiguracji, który zawiera informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="811e0-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

    ```xml
    <connectionStrings>
        <add name="DbActivitiesSample"
             providerName="System.Data.SqlClient"
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
      </connectionStrings>
    ```

-   <span data-ttu-id="811e0-232">W ramach działania:</span><span class="sxs-lookup"><span data-stu-id="811e0-232">In the activity:</span></span>

    ```
    Activity dbSelectCount = new DbQueryScalar<int>()
    {
        ConfigName = "DbActivitiesSample",
        Sql = "SELECT COUNT(*) FROM Roles"
    };
    ```

## <a name="running-this-sample"></a><span data-ttu-id="811e0-233">Uruchomieniem tego przykładu</span><span class="sxs-lookup"><span data-stu-id="811e0-233">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="811e0-234">Instrukcje instalacji</span><span class="sxs-lookup"><span data-stu-id="811e0-234">Setup instructions</span></span>
 <span data-ttu-id="811e0-235">W tym przykładzie korzysta z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="811e0-235">This sample uses a database.</span></span> <span data-ttu-id="811e0-236">Skrypt konfiguracji i obciążenia (plik Setup.cmd) jest dostarczany z próbką.</span><span class="sxs-lookup"><span data-stu-id="811e0-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="811e0-237">Należy wykonać ten plik przy użyciu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="811e0-237">You must execute that file using the command prompt.</span></span>

 <span data-ttu-id="811e0-238">Plik Setup.cmd skrypt wywołuje plik skryptu CreateDb.sql zawiera polecenia SQL, które należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="811e0-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

-   <span data-ttu-id="811e0-239">Tworzy bazę danych o nazwie DbActivitiesSample.</span><span class="sxs-lookup"><span data-stu-id="811e0-239">Creates a database called DbActivitiesSample.</span></span>

-   <span data-ttu-id="811e0-240">Tworzy tabelę ról.</span><span class="sxs-lookup"><span data-stu-id="811e0-240">Creates the Roles table.</span></span>

-   <span data-ttu-id="811e0-241">Tworzy tabelę Pracownicy.</span><span class="sxs-lookup"><span data-stu-id="811e0-241">Creates Employees table.</span></span>

-   <span data-ttu-id="811e0-242">Wstawia trzy rekordy w tabeli ról.</span><span class="sxs-lookup"><span data-stu-id="811e0-242">Inserts three records into the Roles table.</span></span>

-   <span data-ttu-id="811e0-243">Wstawia dwunastu rekordów do tabel pracownikami.</span><span class="sxs-lookup"><span data-stu-id="811e0-243">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="811e0-244">Aby uruchomić plik Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="811e0-244">To run Setup.cmd</span></span>

1. <span data-ttu-id="811e0-245">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="811e0-245">Open a command prompt.</span></span>

2. <span data-ttu-id="811e0-246">Przejdź do folderu przykładu DbActivities.</span><span class="sxs-lookup"><span data-stu-id="811e0-246">Go to the DbActivities sample folder.</span></span>

3. <span data-ttu-id="811e0-247">Wpisz "plik setup.cmd", a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="811e0-247">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="811e0-248">Plik Setup.cmd próbuje zainstalować przykład wystąpienia SqlExpress komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="811e0-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="811e0-249">Jeśli chcesz zainstalować go w inne wystąpienie programu SQL server, należy edytować plik Setup.cmd z nową nazwą wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="811e0-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="811e0-250">Aby odinstalować przykładowej bazy danych</span><span class="sxs-lookup"><span data-stu-id="811e0-250">To uninstall the sample database</span></span>

1. <span data-ttu-id="811e0-251">Uruchom Cleanup.cmd z tym samym folderze, w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="811e0-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="811e0-252">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="811e0-252">To run the sample</span></span>

1. <span data-ttu-id="811e0-253">Otwórz rozwiązanie w programie Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="811e0-253">Open the solution in Visual Studio 2010</span></span>

2. <span data-ttu-id="811e0-254">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="811e0-254">To compile the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="811e0-255">Do uruchomienia przykładu bez debugowania, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="811e0-255">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="811e0-256">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="811e0-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="811e0-257">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="811e0-257">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="811e0-258">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="811e0-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="811e0-259">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="811e0-259">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
