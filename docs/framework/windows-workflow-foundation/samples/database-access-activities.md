---
title: Działania dostępu do bazy danych
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: eec368803eeacb2bab729bcd6d57cc7fc6107256
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710861"
---
# <a name="database-access-activities"></a><span data-ttu-id="635b3-102">Działania dostępu do bazy danych</span><span class="sxs-lookup"><span data-stu-id="635b3-102">Database Access Activities</span></span>

<span data-ttu-id="635b3-103">Działania dostępu do bazy danych umożliwiają dostęp do bazy danych w ramach przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="635b3-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="635b3-104">Te działania umożliwiają dostęp do baz danych w celu pobierania lub modyfikowania informacji oraz korzystania z [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) w celu uzyskania dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="635b3-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="635b3-105">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="635b3-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="635b3-106">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="635b3-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="635b3-107">Jeśli ten katalog nie istnieje, przejdź do strony (strona pobierania), aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbki.</span><span class="sxs-lookup"><span data-stu-id="635b3-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="635b3-108">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="635b3-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="635b3-109">Działania bazy danych</span><span class="sxs-lookup"><span data-stu-id="635b3-109">Database Activities</span></span>

<span data-ttu-id="635b3-110">W poniższych sekcjach szczegółowo opisano listę działań uwzględnionych w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="635b3-110">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="635b3-111">Dbupdate</span><span class="sxs-lookup"><span data-stu-id="635b3-111">DbUpdate</span></span>

<span data-ttu-id="635b3-112">Wykonuje zapytanie SQL, które generuje modyfikację bazy danych (Wstawianie, aktualizowanie, usuwanie i inne modyfikacje).</span><span class="sxs-lookup"><span data-stu-id="635b3-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

<span data-ttu-id="635b3-113">Ta klasa wykonuje swoją działania asynchronicznie (pochodzi z <xref:System.Activities.AsyncCodeActivity> i używa jej funkcji asynchronicznych).</span><span class="sxs-lookup"><span data-stu-id="635b3-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="635b3-114">Informacje o połączeniu można skonfigurować przez ustawienie niezmiennej nazwy dostawcy (`ProviderName`) i parametrów połączenia (`ConnectionString`) lub po prostu użycie nazwy konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="635b3-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="635b3-115">Zapytanie, które ma zostać wykonane, jest skonfigurowane we właściwości `Sql`, a parametry są przesyłane przez kolekcję `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="635b3-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="635b3-116">Po wykonaniu `DbUpdate` liczba rekordów, których to dotyczy, jest zwracana we właściwości `AffectedRecords`.</span><span class="sxs-lookup"><span data-stu-id="635b3-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

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

|<span data-ttu-id="635b3-117">Argument</span><span class="sxs-lookup"><span data-stu-id="635b3-117">Argument</span></span>|<span data-ttu-id="635b3-118">Opis</span><span class="sxs-lookup"><span data-stu-id="635b3-118">Description</span></span>|
|-|-|
|<span data-ttu-id="635b3-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="635b3-119">ProviderName</span></span>|<span data-ttu-id="635b3-120">Niezmienna nazwa dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="635b3-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="635b3-121">Jeśli ten argument jest ustawiony, należy również ustawić `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="635b3-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="635b3-122">Przekształcon</span><span class="sxs-lookup"><span data-stu-id="635b3-122">ConnectionString</span></span>|<span data-ttu-id="635b3-123">Parametry połączenia w celu nawiązania połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="635b3-123">Connection string to connect to the database.</span></span> <span data-ttu-id="635b3-124">Jeśli ten argument jest ustawiony, należy również ustawić `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="635b3-124">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="635b3-125">Konfiguracja pliku</span><span class="sxs-lookup"><span data-stu-id="635b3-125">ConfigName</span></span>|<span data-ttu-id="635b3-126">Nazwa sekcji pliku konfiguracji, w której są przechowywane informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="635b3-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="635b3-127">Gdy ten argument jest ustawiony `ProviderName` i `ConnectionString` nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="635b3-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="635b3-128">CommandType</span><span class="sxs-lookup"><span data-stu-id="635b3-128">CommandType</span></span>|<span data-ttu-id="635b3-129">Typ <xref:System.Data.Common.DbCommand>, który ma zostać wykonany.</span><span class="sxs-lookup"><span data-stu-id="635b3-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="635b3-130">Server</span><span class="sxs-lookup"><span data-stu-id="635b3-130">Sql</span></span>|<span data-ttu-id="635b3-131">Polecenie SQL, które ma zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="635b3-131">The SQL command to be executed.</span></span>|
|<span data-ttu-id="635b3-132">Parametry</span><span class="sxs-lookup"><span data-stu-id="635b3-132">Parameters</span></span>|<span data-ttu-id="635b3-133">Kolekcja parametrów zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="635b3-133">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="635b3-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="635b3-134">AffectedRecords</span></span>|<span data-ttu-id="635b3-135">Liczba rekordów, których dotyczy Ostatnia operacja.</span><span class="sxs-lookup"><span data-stu-id="635b3-135">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="635b3-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="635b3-136">DbQueryScalar</span></span>

<span data-ttu-id="635b3-137">Wykonuje zapytanie, które pobiera pojedynczą wartość z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="635b3-137">Executes a query that retrieves a single value from the database.</span></span>

<span data-ttu-id="635b3-138">Ta klasa wykonuje swoją działania asynchronicznie (pochodzi z <xref:System.Activities.AsyncCodeActivity%601> i używa jej funkcji asynchronicznych).</span><span class="sxs-lookup"><span data-stu-id="635b3-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="635b3-139">Informacje o połączeniu można skonfigurować przez ustawienie niezmiennej nazwy dostawcy (`ProviderName`) i parametrów połączenia (`ConnectionString`) lub po prostu użycie nazwy konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="635b3-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="635b3-140">Zapytanie, które ma zostać wykonane, jest skonfigurowane we właściwości `Sql`, a parametry są przesyłane przez kolekcję `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="635b3-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="635b3-141">Po wykonaniu `DbQueryScalar` wartość skalarna jest zwracana w argumencie `Result out` (typu `TResult`, który jest zdefiniowany w klasie bazowej <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="635b3-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

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

|<span data-ttu-id="635b3-142">Argument</span><span class="sxs-lookup"><span data-stu-id="635b3-142">Argument</span></span>|<span data-ttu-id="635b3-143">Opis</span><span class="sxs-lookup"><span data-stu-id="635b3-143">Description</span></span>|
|-|-|
|<span data-ttu-id="635b3-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="635b3-144">ProviderName</span></span>|<span data-ttu-id="635b3-145">Niezmienna nazwa dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="635b3-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="635b3-146">Jeśli ten argument jest ustawiony, należy również ustawić `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="635b3-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="635b3-147">Przekształcon</span><span class="sxs-lookup"><span data-stu-id="635b3-147">ConnectionString</span></span>|<span data-ttu-id="635b3-148">Parametry połączenia w celu nawiązania połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="635b3-148">Connection string to connect to the database.</span></span> <span data-ttu-id="635b3-149">Jeśli ten argument jest ustawiony, należy również ustawić `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="635b3-149">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="635b3-150">Konfiguracja pliku</span><span class="sxs-lookup"><span data-stu-id="635b3-150">ConfigName</span></span>|<span data-ttu-id="635b3-151">Nazwa sekcji pliku konfiguracji, w której są przechowywane informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="635b3-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="635b3-152">Gdy ten argument jest ustawiony `ProviderName` i `ConnectionString` nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="635b3-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="635b3-153">CommandType</span><span class="sxs-lookup"><span data-stu-id="635b3-153">CommandType</span></span>|<span data-ttu-id="635b3-154">Typ <xref:System.Data.Common.DbCommand>, który ma zostać wykonany.</span><span class="sxs-lookup"><span data-stu-id="635b3-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="635b3-155">Server</span><span class="sxs-lookup"><span data-stu-id="635b3-155">Sql</span></span>|<span data-ttu-id="635b3-156">Polecenie SQL, które ma zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="635b3-156">The SQL command to be executed.</span></span>|
|<span data-ttu-id="635b3-157">Parametry</span><span class="sxs-lookup"><span data-stu-id="635b3-157">Parameters</span></span>|<span data-ttu-id="635b3-158">Kolekcja parametrów zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="635b3-158">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="635b3-159">Wynik</span><span class="sxs-lookup"><span data-stu-id="635b3-159">Result</span></span>|<span data-ttu-id="635b3-160">Wartość skalarna, która jest uzyskiwana po wykonaniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="635b3-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="635b3-161">Ten argument jest typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="635b3-161">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="635b3-162">DBQuery</span><span class="sxs-lookup"><span data-stu-id="635b3-162">DbQuery</span></span>

<span data-ttu-id="635b3-163">Wykonuje zapytanie, które pobiera listę obiektów.</span><span class="sxs-lookup"><span data-stu-id="635b3-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="635b3-164">Po wykonaniu zapytania funkcja mapowania jest wykonywana (może być <xref:System.Func%601><`DbDataReader``TResult`> lub <xref:System.Activities.ActivityFunc%601><`DbDataReader``TResult`).</span><span class="sxs-lookup"><span data-stu-id="635b3-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="635b3-165">Ta funkcja mapowania pobiera rekord w `DbDataReader` i mapuje go do obiektu, który ma zostać zwrócony.</span><span class="sxs-lookup"><span data-stu-id="635b3-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

<span data-ttu-id="635b3-166">Informacje o połączeniu można skonfigurować przez ustawienie niezmiennej nazwy dostawcy (`ProviderName`) i parametrów połączenia (`ConnectionString`) lub po prostu użycie nazwy konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="635b3-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="635b3-167">Zapytanie, które ma zostać wykonane, jest skonfigurowane we właściwości `Sql`, a parametry są przesyłane przez kolekcję `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="635b3-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="635b3-168">Wyniki zapytania SQL są pobierane przy użyciu `DbDataReader`.</span><span class="sxs-lookup"><span data-stu-id="635b3-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="635b3-169">Działanie iteruje `DbDataReader` i mapuje wiersze w `DbDataReader` do wystąpienia `TResult`.</span><span class="sxs-lookup"><span data-stu-id="635b3-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="635b3-170">Użytkownik `DbQuery` musi dostarczyć kod mapowania i można to zrobić na dwa sposoby: używając <xref:System.Func%601><`DbDataReader`, `TResult`> lub <xref:System.Activities.ActivityFunc%601><`DbDataReader``TResult`.</span><span class="sxs-lookup"><span data-stu-id="635b3-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="635b3-171">W pierwszym przypadku mapa jest wykonywana w ramach jednego impulsu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="635b3-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="635b3-172">W związku z tym jest to szybsze, ale nie można go serializować do XAML.</span><span class="sxs-lookup"><span data-stu-id="635b3-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="635b3-173">W ostatnim przypadku mapa jest wykonywana w wielu pulsach.</span><span class="sxs-lookup"><span data-stu-id="635b3-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="635b3-174">W związku z tym może być wolniejszy, ale może być serializowany do XAML i w sposób deklaratywny (wszystkie istniejące działania mogą uczestniczyć w mapowaniu).</span><span class="sxs-lookup"><span data-stu-id="635b3-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

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

|<span data-ttu-id="635b3-175">Argument</span><span class="sxs-lookup"><span data-stu-id="635b3-175">Argument</span></span>|<span data-ttu-id="635b3-176">Opis</span><span class="sxs-lookup"><span data-stu-id="635b3-176">Description</span></span>|
|-|-|
|<span data-ttu-id="635b3-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="635b3-177">ProviderName</span></span>|<span data-ttu-id="635b3-178">Niezmienna nazwa dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="635b3-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="635b3-179">Jeśli ten argument jest ustawiony, należy również ustawić `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="635b3-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="635b3-180">Przekształcon</span><span class="sxs-lookup"><span data-stu-id="635b3-180">ConnectionString</span></span>|<span data-ttu-id="635b3-181">Parametry połączenia w celu nawiązania połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="635b3-181">Connection string to connect to the database.</span></span> <span data-ttu-id="635b3-182">Jeśli ten argument jest ustawiony, należy również ustawić `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="635b3-182">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="635b3-183">Konfiguracja pliku</span><span class="sxs-lookup"><span data-stu-id="635b3-183">ConfigName</span></span>|<span data-ttu-id="635b3-184">Nazwa sekcji pliku konfiguracji, w której są przechowywane informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="635b3-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="635b3-185">Gdy ten argument jest ustawiony `ProviderName` i `ConnectionString` nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="635b3-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="635b3-186">CommandType</span><span class="sxs-lookup"><span data-stu-id="635b3-186">CommandType</span></span>|<span data-ttu-id="635b3-187">Typ <xref:System.Data.Common.DbCommand>, który ma zostać wykonany.</span><span class="sxs-lookup"><span data-stu-id="635b3-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="635b3-188">Server</span><span class="sxs-lookup"><span data-stu-id="635b3-188">Sql</span></span>|<span data-ttu-id="635b3-189">Polecenie SQL, które ma zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="635b3-189">The SQL command to be executed.</span></span>|
|<span data-ttu-id="635b3-190">Parametry</span><span class="sxs-lookup"><span data-stu-id="635b3-190">Parameters</span></span>|<span data-ttu-id="635b3-191">Kolekcja parametrów zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="635b3-191">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="635b3-192">wzor</span><span class="sxs-lookup"><span data-stu-id="635b3-192">Mapper</span></span>|<span data-ttu-id="635b3-193">Funkcja mapowania (<xref:System.Func%601><`DbDataReader`, `TResult`>), która pobiera rekord w `DataReader` uzyskany w wyniku wykonania zapytania i zwraca wystąpienie obiektu typu `TResult`, który zostanie dodany do kolekcji `Result`.</span><span class="sxs-lookup"><span data-stu-id="635b3-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="635b3-194">W takim przypadku mapowanie jest wykonywane w ramach pojedynczego impulsu wykonywania, ale nie można go utworzyć deklaratywnie przy użyciu projektanta.</span><span class="sxs-lookup"><span data-stu-id="635b3-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="635b3-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="635b3-195">MapperFunc</span></span>|<span data-ttu-id="635b3-196">Funkcja mapowania (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>), która pobiera rekord w `DataReader` uzyskany w wyniku wykonania zapytania i zwraca wystąpienie obiektu typu `TResult`, który zostanie dodany do kolekcji `Result`.</span><span class="sxs-lookup"><span data-stu-id="635b3-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="635b3-197">W takim przypadku mapowanie jest wykonywane w wielu impulsach wykonania.</span><span class="sxs-lookup"><span data-stu-id="635b3-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="635b3-198">Tę funkcję można serializować do języka XAML i utworzyć deklaratywnie (wszystkie istniejące działania mogą uczestniczyć w mapowaniu).</span><span class="sxs-lookup"><span data-stu-id="635b3-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="635b3-199">Wynik</span><span class="sxs-lookup"><span data-stu-id="635b3-199">Result</span></span>|<span data-ttu-id="635b3-200">Lista obiektów uzyskanych jako wynik wykonywania zapytania i wykonująca funkcję mapowania dla każdego rekordu w `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="635b3-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="635b3-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="635b3-201">DbQueryDataSet</span></span>

<span data-ttu-id="635b3-202">Wykonuje zapytanie, które zwraca <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="635b3-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="635b3-203">Ta klasa wykonuje asynchroniczne działanie.</span><span class="sxs-lookup"><span data-stu-id="635b3-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="635b3-204">Pochodzi on z <xref:System.Activities.AsyncCodeActivity><`TResult`> i używa jego funkcji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="635b3-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

<span data-ttu-id="635b3-205">Informacje o połączeniu można skonfigurować przez ustawienie niezmiennej nazwy dostawcy (`ProviderName`) i parametrów połączenia (`ConnectionString`) lub po prostu użycie nazwy konfiguracji parametrów połączenia (`ConfigFileSectionName`) z pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="635b3-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="635b3-206">Zapytanie, które ma zostać wykonane, jest skonfigurowane we właściwości `Sql`, a parametry są przesyłane przez kolekcję `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="635b3-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="635b3-207">Po wykonaniu `DbQueryDataSet` `DataSet` jest zwracany w argumencie `Result out` (typu `TResult`, który jest zdefiniowany w klasie podstawowej <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="635b3-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

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

|<span data-ttu-id="635b3-208">Argument</span><span class="sxs-lookup"><span data-stu-id="635b3-208">Argument</span></span>|<span data-ttu-id="635b3-209">Opis</span><span class="sxs-lookup"><span data-stu-id="635b3-209">Description</span></span>|
|-|-|
|<span data-ttu-id="635b3-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="635b3-210">ProviderName</span></span>|<span data-ttu-id="635b3-211">Niezmienna nazwa dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="635b3-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="635b3-212">Jeśli ten argument jest ustawiony, należy również ustawić `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="635b3-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="635b3-213">Przekształcon</span><span class="sxs-lookup"><span data-stu-id="635b3-213">ConnectionString</span></span>|<span data-ttu-id="635b3-214">Parametry połączenia w celu nawiązania połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="635b3-214">Connection string to connect to the database.</span></span> <span data-ttu-id="635b3-215">Jeśli ten argument jest ustawiony, należy również ustawić `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="635b3-215">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="635b3-216">Konfiguracja pliku</span><span class="sxs-lookup"><span data-stu-id="635b3-216">ConfigName</span></span>|<span data-ttu-id="635b3-217">Nazwa sekcji pliku konfiguracji, w której są przechowywane informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="635b3-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="635b3-218">Gdy ten argument jest ustawiony `ProviderName` i `ConnectionString` nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="635b3-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="635b3-219">CommandType</span><span class="sxs-lookup"><span data-stu-id="635b3-219">CommandType</span></span>|<span data-ttu-id="635b3-220">Typ <xref:System.Data.Common.DbCommand>, który ma zostać wykonany.</span><span class="sxs-lookup"><span data-stu-id="635b3-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="635b3-221">Server</span><span class="sxs-lookup"><span data-stu-id="635b3-221">Sql</span></span>|<span data-ttu-id="635b3-222">Polecenie SQL, które ma zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="635b3-222">The SQL command to be executed.</span></span>|
|<span data-ttu-id="635b3-223">Parametry</span><span class="sxs-lookup"><span data-stu-id="635b3-223">Parameters</span></span>|<span data-ttu-id="635b3-224">Kolekcja parametrów zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="635b3-224">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="635b3-225">Wynik</span><span class="sxs-lookup"><span data-stu-id="635b3-225">Result</span></span>|<span data-ttu-id="635b3-226"><xref:System.Data.DataSet> uzyskiwany po wykonaniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="635b3-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="635b3-227">Konfigurowanie informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="635b3-227">Configuring Connection Information</span></span>

<span data-ttu-id="635b3-228">Wszystkie działania współużytkują te same parametry konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="635b3-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="635b3-229">Można je skonfigurować na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="635b3-229">They can be configured in two ways:</span></span>

- <span data-ttu-id="635b3-230">`ConnectionString + InvariantName`: Ustaw niezmienną nazwę i parametry połączenia dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="635b3-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

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

- <span data-ttu-id="635b3-231">`ConfigName`: Ustaw nazwę sekcji konfiguracji zawierającej informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="635b3-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

  ```xml
  <connectionStrings>
      <add name="DbActivitiesSample"
            providerName="System.Data.SqlClient"
            connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
    </connectionStrings>
  ```

- <span data-ttu-id="635b3-232">W działaniu:</span><span class="sxs-lookup"><span data-stu-id="635b3-232">In the activity:</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<int>()
  {
      ConfigName = "DbActivitiesSample",
      Sql = "SELECT COUNT(*) FROM Roles"
  };
  ```

## <a name="running-this-sample"></a><span data-ttu-id="635b3-233">Uruchamianie tego przykładu</span><span class="sxs-lookup"><span data-stu-id="635b3-233">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="635b3-234">Instrukcje dotyczące instalacji</span><span class="sxs-lookup"><span data-stu-id="635b3-234">Setup instructions</span></span>

<span data-ttu-id="635b3-235">Ten przykład używa bazy danych.</span><span class="sxs-lookup"><span data-stu-id="635b3-235">This sample uses a database.</span></span> <span data-ttu-id="635b3-236">Skrypt zestawu i ładowania (Setup. cmd) jest dostarczany z przykładem.</span><span class="sxs-lookup"><span data-stu-id="635b3-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="635b3-237">Należy wykonać ten plik przy użyciu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="635b3-237">You must execute that file using the command prompt.</span></span>

<span data-ttu-id="635b3-238">Skrypt Setup. cmd wywołuje plik skryptu CreateDb. SQL, który zawiera polecenia SQL, które wykonują następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="635b3-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

- <span data-ttu-id="635b3-239">Tworzy bazę danych o nazwie DbActivitiesSample.</span><span class="sxs-lookup"><span data-stu-id="635b3-239">Creates a database called DbActivitiesSample.</span></span>

- <span data-ttu-id="635b3-240">Tworzy tabelę role.</span><span class="sxs-lookup"><span data-stu-id="635b3-240">Creates the Roles table.</span></span>

- <span data-ttu-id="635b3-241">Tworzy tabelę Employees.</span><span class="sxs-lookup"><span data-stu-id="635b3-241">Creates Employees table.</span></span>

- <span data-ttu-id="635b3-242">Wstawia trzy rekordy do tabeli role.</span><span class="sxs-lookup"><span data-stu-id="635b3-242">Inserts three records into the Roles table.</span></span>

- <span data-ttu-id="635b3-243">Wstawia dwanaście rekordów do tabeli Employees.</span><span class="sxs-lookup"><span data-stu-id="635b3-243">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="635b3-244">Aby uruchomić program Setup. cmd</span><span class="sxs-lookup"><span data-stu-id="635b3-244">To run Setup.cmd</span></span>

1. <span data-ttu-id="635b3-245">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="635b3-245">Open a command prompt.</span></span>

2. <span data-ttu-id="635b3-246">Przejdź do przykładowego folderu DbActivities.</span><span class="sxs-lookup"><span data-stu-id="635b3-246">Go to the DbActivities sample folder.</span></span>

3. <span data-ttu-id="635b3-247">Wpisz "Setup. cmd" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="635b3-247">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    > <span data-ttu-id="635b3-248">Setup. cmd próbuje zainstalować przykład w wystąpieniu programu Local Machine SqlExpress.</span><span class="sxs-lookup"><span data-stu-id="635b3-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="635b3-249">Jeśli chcesz zainstalować ją w innym wystąpieniu programu SQL Server, edytuj plik Setup. cmd przy użyciu nowej nazwy wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="635b3-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="635b3-250">Aby odinstalować przykładową bazę danych</span><span class="sxs-lookup"><span data-stu-id="635b3-250">To uninstall the sample database</span></span>

1. <span data-ttu-id="635b3-251">Uruchom polecenie Oczyść. cmd z przykładowego folderu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="635b3-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="635b3-252">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="635b3-252">To run the sample</span></span>

1. <span data-ttu-id="635b3-253">Otwórz rozwiązanie w programie Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="635b3-253">Open the solution in Visual Studio 2010</span></span>

2. <span data-ttu-id="635b3-254">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="635b3-254">To compile the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="635b3-255">Aby uruchomić przykład bez debugowania, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="635b3-255">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="635b3-256">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="635b3-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="635b3-257">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="635b3-257">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="635b3-258">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="635b3-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="635b3-259">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="635b3-259">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
