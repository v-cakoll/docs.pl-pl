---
title: Działania dostępu do bazy danych
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: e9c7627738d3c5313a4f3e6e4451daf78b87839a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520412"
---
# <a name="database-access-activities"></a><span data-ttu-id="e037d-102">Działania dostępu do bazy danych</span><span class="sxs-lookup"><span data-stu-id="e037d-102">Database Access Activities</span></span>
<span data-ttu-id="e037d-103">Działania dostępu do bazy danych pozwalają na dostęp do bazy danych w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="e037d-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="e037d-104">Te działania Zezwalaj na dostęp do bazy danych do pobierania lub modyfikowanie informacji i użycia [ADO.NET](http://go.microsoft.com/fwlink/?LinkId=166081) dostęp do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e037d-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](http://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e037d-105">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e037d-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e037d-106">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e037d-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e037d-107">Jeśli ten katalog nie istnieje, przejdź do (stronę pobierania) można pobrać wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="e037d-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e037d-108">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e037d-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`  
  
## <a name="database-activities"></a><span data-ttu-id="e037d-109">Działania bazy danych</span><span class="sxs-lookup"><span data-stu-id="e037d-109">Database Activities</span></span>  
 <span data-ttu-id="e037d-110">W poniższych sekcjach opisano na liście działań zawarty w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e037d-110">The following sections detail the list of activities included in this sample.</span></span>  
  
## <a name="dbupdate"></a><span data-ttu-id="e037d-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="e037d-111">DbUpdate</span></span>  
 <span data-ttu-id="e037d-112">Wykonuje zapytanie SQL, które powoduje zmianę w bazie danych (insert, update, delete i innych modyfikacji).</span><span class="sxs-lookup"><span data-stu-id="e037d-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>  
  
 <span data-ttu-id="e037d-113">Ta klasa wykonuje pracę asynchronicznie (dziedziczy <xref:System.Activities.AsyncCodeActivity> i używa jej możliwości asynchroniczne).</span><span class="sxs-lookup"><span data-stu-id="e037d-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>  
  
 <span data-ttu-id="e037d-114">Informacje o połączeniu można skonfigurować przez ustawienie niezmienną nazwę dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub tylko przy użyciu nazwy konfiguracji ciągu połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e037d-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="e037d-115">Kwerenda ma być wykonywana jest skonfigurowana w jego `Sql` właściwości i parametry są przekazywane za pośrednictwem `Parameters` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e037d-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="e037d-116">Po `DbUpdate` jest wykonywane, liczbę uwzględnionych rekordów jest zwracany w `AffectedRecords` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e037d-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>  
  
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
  
|<span data-ttu-id="e037d-117">Argument</span><span class="sxs-lookup"><span data-stu-id="e037d-117">Argument</span></span>|<span data-ttu-id="e037d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="e037d-118">Description</span></span>|  
|-|-|  
|<span data-ttu-id="e037d-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="e037d-119">ProviderName</span></span>|<span data-ttu-id="e037d-120">Niezmienna Nazwa dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="e037d-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="e037d-121">Jeśli ten argument jest ustawiona, a następnie `ConnectionString` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="e037d-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="e037d-122">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="e037d-122">ConnectionString</span></span>|<span data-ttu-id="e037d-123">Parametry połączenia do połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="e037d-123">Connection string to connect to the database.</span></span> <span data-ttu-id="e037d-124">Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="e037d-124">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="e037d-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="e037d-125">ConfigName</span></span>|<span data-ttu-id="e037d-126">Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="e037d-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="e037d-127">Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="e037d-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="e037d-128">Obiekt CommandType</span><span class="sxs-lookup"><span data-stu-id="e037d-128">CommandType</span></span>|<span data-ttu-id="e037d-129">Typ <xref:System.Data.Common.DbCommand> do wykonania.</span><span class="sxs-lookup"><span data-stu-id="e037d-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="e037d-130">SQL</span><span class="sxs-lookup"><span data-stu-id="e037d-130">Sql</span></span>|<span data-ttu-id="e037d-131">Polecenie SQL do wykonania.</span><span class="sxs-lookup"><span data-stu-id="e037d-131">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="e037d-132">Parametry</span><span class="sxs-lookup"><span data-stu-id="e037d-132">Parameters</span></span>|<span data-ttu-id="e037d-133">Kolekcja parametrów zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="e037d-133">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="e037d-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="e037d-134">AffectedRecords</span></span>|<span data-ttu-id="e037d-135">Liczba rekordów wpływ ostatniej operacji.</span><span class="sxs-lookup"><span data-stu-id="e037d-135">Number of records affected by the last operation.</span></span>|  
  
## <a name="dbqueryscalar"></a><span data-ttu-id="e037d-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="e037d-136">DbQueryScalar</span></span>  
 <span data-ttu-id="e037d-137">Wykonuje zapytanie, które pobiera pojedynczą wartość z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e037d-137">Executes a query that retrieves a single value from the database.</span></span>  
  
 <span data-ttu-id="e037d-138">Ta klasa wykonuje pracę asynchronicznie (dziedziczy <xref:System.Activities.AsyncCodeActivity%601> i używa jej możliwości asynchroniczne).</span><span class="sxs-lookup"><span data-stu-id="e037d-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>  
  
 <span data-ttu-id="e037d-139">Informacje o połączeniu można skonfigurować przez ustawienie niezmienną nazwę dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub tylko przy użyciu nazwy konfiguracji ciągu połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e037d-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="e037d-140">Kwerenda ma być wykonywana jest skonfigurowana w jego `Sql` właściwości i parametry są przekazywane za pośrednictwem `Parameters` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e037d-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="e037d-141">Po `DbQueryScalar` jest wykonywane, skalarnych jest zwracany w `Result``out` argumentu (typu `TResult`, która jest zdefiniowana w klasie podstawowej <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="e037d-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result``out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>  
  
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
  
|<span data-ttu-id="e037d-142">Argument</span><span class="sxs-lookup"><span data-stu-id="e037d-142">Argument</span></span>|<span data-ttu-id="e037d-143">Opis</span><span class="sxs-lookup"><span data-stu-id="e037d-143">Description</span></span>|  
|-|-|  
|<span data-ttu-id="e037d-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="e037d-144">ProviderName</span></span>|<span data-ttu-id="e037d-145">Niezmienna Nazwa dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="e037d-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="e037d-146">Jeśli ten argument jest ustawiona, a następnie `ConnectionString` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="e037d-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="e037d-147">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="e037d-147">ConnectionString</span></span>|<span data-ttu-id="e037d-148">Parametry połączenia do połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="e037d-148">Connection string to connect to the database.</span></span> <span data-ttu-id="e037d-149">Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="e037d-149">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="e037d-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="e037d-150">ConfigName</span></span>|<span data-ttu-id="e037d-151">Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="e037d-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="e037d-152">Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="e037d-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="e037d-153">Obiekt CommandType</span><span class="sxs-lookup"><span data-stu-id="e037d-153">CommandType</span></span>|<span data-ttu-id="e037d-154">Typ <xref:System.Data.Common.DbCommand> do wykonania.</span><span class="sxs-lookup"><span data-stu-id="e037d-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="e037d-155">SQL</span><span class="sxs-lookup"><span data-stu-id="e037d-155">Sql</span></span>|<span data-ttu-id="e037d-156">Polecenie SQL do wykonania.</span><span class="sxs-lookup"><span data-stu-id="e037d-156">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="e037d-157">Parametry</span><span class="sxs-lookup"><span data-stu-id="e037d-157">Parameters</span></span>|<span data-ttu-id="e037d-158">Kolekcja parametrów zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="e037d-158">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="e037d-159">Wynik</span><span class="sxs-lookup"><span data-stu-id="e037d-159">Result</span></span>|<span data-ttu-id="e037d-160">Skalarną uzyskany po wykonaniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="e037d-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="e037d-161">Ten argument jest typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="e037d-161">This argument is of type `TResult`.</span></span>|  
  
## <a name="dbquery"></a><span data-ttu-id="e037d-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="e037d-162">DbQuery</span></span>  
 <span data-ttu-id="e037d-163">Wykonuje zapytanie pobiera listę obiektów.</span><span class="sxs-lookup"><span data-stu-id="e037d-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="e037d-164">Po wykonaniu zapytania wykonaniu funkcji mapowania (można go <xref:System.Func%601> < `DbDataReader`, `TResult`> lub <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>).</span><span class="sxs-lookup"><span data-stu-id="e037d-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="e037d-165">Ta funkcja mapowania pobiera rekord w `DbDataReader` oraz opisano, jak obiekt ma zostać zwrócona.</span><span class="sxs-lookup"><span data-stu-id="e037d-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>  
  
 <span data-ttu-id="e037d-166">Informacje o połączeniu można skonfigurować przez ustawienie niezmienną nazwę dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub tylko przy użyciu nazwy konfiguracji ciągu połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e037d-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="e037d-167">Kwerenda ma być wykonywana jest skonfigurowana w jego `Sql` właściwości i parametry są przekazywane za pośrednictwem `Parameters` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e037d-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="e037d-168">Pobierane są wyniki zapytania SQL, używając `DbDataReader`.</span><span class="sxs-lookup"><span data-stu-id="e037d-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="e037d-169">Działania wykonuje iterację `DbDataReader` i mapy wierszy w `DbDataReader` na wystąpienie `TResult`.</span><span class="sxs-lookup"><span data-stu-id="e037d-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="e037d-170">Użytkownik `DbQuery` musi podać kod mapowania i to zrobić na dwa sposoby: za pomocą <xref:System.Func%601> < `DbDataReader`, `TResult`> lub <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>.</span><span class="sxs-lookup"><span data-stu-id="e037d-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="e037d-171">W pierwszym przypadku mapy odbywa się w jednym pulse wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e037d-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="e037d-172">W związku z tym szybciej, ale to nie może być serializowany w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="e037d-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="e037d-173">W ostatnim przypadku mapy odbywa się w wielu impulsów.</span><span class="sxs-lookup"><span data-stu-id="e037d-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="e037d-174">W związku z tym może przebiegać wolniej, ale można go serializować w języku XAML i deklaratywnie utworzone (wszystkie istniejące działania mogą uczestniczyć w mapowaniu).</span><span class="sxs-lookup"><span data-stu-id="e037d-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>  
  
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
  
|<span data-ttu-id="e037d-175">Argument</span><span class="sxs-lookup"><span data-stu-id="e037d-175">Argument</span></span>|<span data-ttu-id="e037d-176">Opis</span><span class="sxs-lookup"><span data-stu-id="e037d-176">Description</span></span>|  
|-|-|  
|<span data-ttu-id="e037d-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="e037d-177">ProviderName</span></span>|<span data-ttu-id="e037d-178">Niezmienna Nazwa dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="e037d-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="e037d-179">Jeśli ten argument jest ustawiona, a następnie `ConnectionString` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="e037d-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="e037d-180">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="e037d-180">ConnectionString</span></span>|<span data-ttu-id="e037d-181">Parametry połączenia do połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="e037d-181">Connection string to connect to the database.</span></span> <span data-ttu-id="e037d-182">Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="e037d-182">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="e037d-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="e037d-183">ConfigName</span></span>|<span data-ttu-id="e037d-184">Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="e037d-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="e037d-185">Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="e037d-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="e037d-186">Obiekt CommandType</span><span class="sxs-lookup"><span data-stu-id="e037d-186">CommandType</span></span>|<span data-ttu-id="e037d-187">Typ <xref:System.Data.Common.DbCommand> do wykonania.</span><span class="sxs-lookup"><span data-stu-id="e037d-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="e037d-188">SQL</span><span class="sxs-lookup"><span data-stu-id="e037d-188">Sql</span></span>|<span data-ttu-id="e037d-189">Polecenie SQL do wykonania.</span><span class="sxs-lookup"><span data-stu-id="e037d-189">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="e037d-190">Parametry</span><span class="sxs-lookup"><span data-stu-id="e037d-190">Parameters</span></span>|<span data-ttu-id="e037d-191">Kolekcja parametrów zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="e037d-191">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="e037d-192">mapowania</span><span class="sxs-lookup"><span data-stu-id="e037d-192">Mapper</span></span>|<span data-ttu-id="e037d-193">Mapowanie funkcji (<xref:System.Func%601><`DbDataReader`, `TResult`>) pobierającej rekord `DataReader` uzyskane w rezultacie wykonywania zapytania i zwraca wystąpienie obiektu typu `TResult` mają zostać dodane do `Result` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e037d-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="e037d-194">W takim przypadku mapowania odbywa się w jednym pulse wykonywania, ale nie może być utworzone, deklaratywnego przy użyciu narzędzia Projektant.</span><span class="sxs-lookup"><span data-stu-id="e037d-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|  
|<span data-ttu-id="e037d-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="e037d-195">MapperFunc</span></span>|<span data-ttu-id="e037d-196">Mapowanie funkcji (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) pobierającej rekord `DataReader` uzyskane w rezultacie wykonywania zapytania i zwraca wystąpienie obiektu typu `TResult` mają zostać dodane do `Result` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e037d-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="e037d-197">W takim przypadku mapowanie odbywa się w wielu impulsów wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e037d-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="e037d-198">Ta funkcja może być serializacji w języku XAML i deklaratywnie utworzone (wszystkie istniejące działania mogą uczestniczyć w mapowaniu).</span><span class="sxs-lookup"><span data-stu-id="e037d-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|  
|<span data-ttu-id="e037d-199">Wynik</span><span class="sxs-lookup"><span data-stu-id="e037d-199">Result</span></span>|<span data-ttu-id="e037d-200">Lista obiektów uzyskane w rezultacie wykonywania zapytania i wykonywania funkcji mapowania dla każdego rekordu w `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="e037d-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|  
  
## <a name="dbquerydataset"></a><span data-ttu-id="e037d-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="e037d-201">DbQueryDataSet</span></span>  
 <span data-ttu-id="e037d-202">Wykonuje zapytanie zwracające <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e037d-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e037d-203">Ta klasa wykonuje pracę asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="e037d-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="e037d-204">Dziedziczy <xref:System.Activities.AsyncCodeActivity> < `TResult`> i używa jej możliwości asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="e037d-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>  
  
 <span data-ttu-id="e037d-205">Informacje o połączeniu można skonfigurować przez ustawienie niezmienną nazwę dostawcy (`ProviderName`) i parametry połączenia (`ConnectionString`) lub tylko przy użyciu nazwy konfiguracji ciągu połączenia (`ConfigFileSectionName`) z pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e037d-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="e037d-206">Kwerenda ma być wykonywana jest skonfigurowana w jego `Sql` właściwości i parametry są przekazywane za pośrednictwem `Parameters` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e037d-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="e037d-207">Po `DbQueryDataSet` jest wykonywany `DataSet` jest zwracany w `Result``out` argumentu (typu `TResult`, która jest zdefiniowana w klasie podstawowej <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="e037d-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result``out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>  
  
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
  
|<span data-ttu-id="e037d-208">Argument</span><span class="sxs-lookup"><span data-stu-id="e037d-208">Argument</span></span>|<span data-ttu-id="e037d-209">Opis</span><span class="sxs-lookup"><span data-stu-id="e037d-209">Description</span></span>|  
|-|-|  
|<span data-ttu-id="e037d-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="e037d-210">ProviderName</span></span>|<span data-ttu-id="e037d-211">Niezmienna Nazwa dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="e037d-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="e037d-212">Jeśli ten argument jest ustawiona, a następnie `ConnectionString` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="e037d-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="e037d-213">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="e037d-213">ConnectionString</span></span>|<span data-ttu-id="e037d-214">Parametry połączenia do połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="e037d-214">Connection string to connect to the database.</span></span> <span data-ttu-id="e037d-215">Jeśli ten argument jest ustawiona, następnie `ProviderName` również musi być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="e037d-215">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="e037d-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="e037d-216">ConfigName</span></span>|<span data-ttu-id="e037d-217">Nazwa sekcji pliku konfiguracji, na którym są przechowywane informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="e037d-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="e037d-218">Jeśli ten argument ma wartość `ProviderName` i `ConnectionString` nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="e037d-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="e037d-219">Obiekt CommandType</span><span class="sxs-lookup"><span data-stu-id="e037d-219">CommandType</span></span>|<span data-ttu-id="e037d-220">Typ <xref:System.Data.Common.DbCommand> do wykonania.</span><span class="sxs-lookup"><span data-stu-id="e037d-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="e037d-221">SQL</span><span class="sxs-lookup"><span data-stu-id="e037d-221">Sql</span></span>|<span data-ttu-id="e037d-222">Polecenie SQL do wykonania.</span><span class="sxs-lookup"><span data-stu-id="e037d-222">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="e037d-223">Parametry</span><span class="sxs-lookup"><span data-stu-id="e037d-223">Parameters</span></span>|<span data-ttu-id="e037d-224">Kolekcja parametrów zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="e037d-224">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="e037d-225">Wynik</span><span class="sxs-lookup"><span data-stu-id="e037d-225">Result</span></span>|<span data-ttu-id="e037d-226"><xref:System.Data.DataSet> które są uzyskiwane po wykonaniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="e037d-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|  
  
## <a name="configuring-connection-information"></a><span data-ttu-id="e037d-227">Konfigurowanie informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="e037d-227">Configuring Connection Information</span></span>  
 <span data-ttu-id="e037d-228">Wszystkie DbActivities mają te same parametry konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e037d-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="e037d-229">Można je skonfigurować na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="e037d-229">They can be configured in two ways:</span></span>  
  
-   <span data-ttu-id="e037d-230">`ConnectionString + InvariantName`: Ustawienie dostawcy ADO.NET niezmienny ciąg połączenia i nazwę.</span><span class="sxs-lookup"><span data-stu-id="e037d-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>  
  
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
  
-   <span data-ttu-id="e037d-231">`ConfigName`: Ustaw nazwę sekcji konfiguracyjnej, który zawiera informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="e037d-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>  
  
    ```xml  
    <connectionStrings>      
        <add name="DbActivitiesSample"  
             providerName="System.Data.SqlClient"  
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>  
      </connectionStrings>  
    ```  
  
-   <span data-ttu-id="e037d-232">W działaniu:</span><span class="sxs-lookup"><span data-stu-id="e037d-232">In the activity:</span></span>  
  
    ```  
    Activity dbSelectCount = new DbQueryScalar<int>()  
    {                  
        ConfigName = "DbActivitiesSample",  
        Sql = "SELECT COUNT(*) FROM Roles"  
    };  
    ```  
  
## <a name="running-this-sample"></a><span data-ttu-id="e037d-233">Uruchomione w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="e037d-233">Running this sample</span></span>  
  
### <a name="setup-instructions"></a><span data-ttu-id="e037d-234">Instrukcje instalacji</span><span class="sxs-lookup"><span data-stu-id="e037d-234">Setup instructions</span></span>  
 <span data-ttu-id="e037d-235">W tym przykładzie korzysta z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e037d-235">This sample uses a database.</span></span> <span data-ttu-id="e037d-236">Konfiguracja i obciążenia skryptu (Setup.cmd) jest dostarczany z próbki.</span><span class="sxs-lookup"><span data-stu-id="e037d-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="e037d-237">Należy wykonać tego pliku przy użyciu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e037d-237">You must execute that file using the command prompt.</span></span>  
  
 <span data-ttu-id="e037d-238">Skrypt Setup.cmd wywołuje CreateDb.sql pliku skryptu, który zawiera poleceń SQL, które należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e037d-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>  
  
-   <span data-ttu-id="e037d-239">Tworzy bazę danych o nazwie DbActivitiesSample.</span><span class="sxs-lookup"><span data-stu-id="e037d-239">Creates a database called DbActivitiesSample.</span></span>  
  
-   <span data-ttu-id="e037d-240">Tworzy tabelę ról.</span><span class="sxs-lookup"><span data-stu-id="e037d-240">Creates the Roles table.</span></span>  
  
-   <span data-ttu-id="e037d-241">Tworzy tabelę pracowników.</span><span class="sxs-lookup"><span data-stu-id="e037d-241">Creates Employees table.</span></span>  
  
-   <span data-ttu-id="e037d-242">Wstawia trzy rekordy do tabeli ról.</span><span class="sxs-lookup"><span data-stu-id="e037d-242">Inserts three records into the Roles table.</span></span>  
  
-   <span data-ttu-id="e037d-243">Wstawia dwanaście rekordów do tabeli pracowników.</span><span class="sxs-lookup"><span data-stu-id="e037d-243">Inserts twelve records into the Employees table.</span></span>  
  
##### <a name="to-run-setupcmd"></a><span data-ttu-id="e037d-244">Aby uruchomić Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="e037d-244">To run Setup.cmd</span></span>  
  
1.  <span data-ttu-id="e037d-245">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="e037d-245">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="e037d-246">Przejdź do folderu DbActivities próbki.</span><span class="sxs-lookup"><span data-stu-id="e037d-246">Go to the DbActivities sample folder.</span></span>  
  
3.  <span data-ttu-id="e037d-247">Wpisz "setup.cmd" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="e037d-247">Type "setup.cmd" and press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e037d-248">Setup.cmd próbuje zainstalować przykład wystąpienia SqlExpress komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="e037d-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="e037d-249">Jeśli użytkownik chce go zainstalować w inne wystąpienie programu SQL server, należy edytować Setup.cmd z nową nazwą wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e037d-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>  
  
##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="e037d-250">Aby odinstalować przykładowej bazy danych</span><span class="sxs-lookup"><span data-stu-id="e037d-250">To uninstall the sample database</span></span>  
  
1.  <span data-ttu-id="e037d-251">Uruchom Cleanup.cmd z tym samym folderze, w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e037d-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>  
  
##### <a name="to-run-the-sample"></a><span data-ttu-id="e037d-252">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="e037d-252">To run the sample</span></span>  
  
1.  <span data-ttu-id="e037d-253">Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e037d-253">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]</span></span>  
  
2.  <span data-ttu-id="e037d-254">Aby skompilować rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="e037d-254">To compile the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e037d-255">Aby uruchomić przykładowy bez debugowania, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="e037d-255">To run the sample without debugging, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e037d-256">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e037d-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e037d-257">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e037d-257">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e037d-258">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="e037d-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e037d-259">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e037d-259">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
