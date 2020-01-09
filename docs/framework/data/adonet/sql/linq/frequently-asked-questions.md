---
title: Często zadawane pytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 3cc879e97438138554f1d39cf588e01bfbba28a6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634706"
---
# <a name="frequently-asked-questions"></a><span data-ttu-id="37b8b-102">Często zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="37b8b-102">Frequently Asked Questions</span></span>

<span data-ttu-id="37b8b-103">W poniższych sekcjach przedstawiono kilka typowych problemów, które mogą wystąpić podczas implementowania LINQ.</span><span class="sxs-lookup"><span data-stu-id="37b8b-103">The following sections answer some common issues that you might encounter when you implement LINQ.</span></span>

<span data-ttu-id="37b8b-104">[Rozwiązywanie problemów](troubleshooting.md)z dodatkowymi problemami.</span><span class="sxs-lookup"><span data-stu-id="37b8b-104">Additional issues are addressed in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="cannot-connect"></a><span data-ttu-id="37b8b-105">Nie można nawiązać połączenia</span><span class="sxs-lookup"><span data-stu-id="37b8b-105">Cannot Connect</span></span>

<span data-ttu-id="37b8b-106">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-106">Q.</span></span> <span data-ttu-id="37b8b-107">Nie mogę nawiązać połączenia z moją bazą danych.</span><span class="sxs-lookup"><span data-stu-id="37b8b-107">I cannot connect to my database.</span></span>

<span data-ttu-id="37b8b-108">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-108">A.</span></span> <span data-ttu-id="37b8b-109">Upewnij się, że parametry połączenia są poprawne i że wystąpienie SQL Server jest uruchomione.</span><span class="sxs-lookup"><span data-stu-id="37b8b-109">Make sure your connection string is correct and that your SQL Server instance is running.</span></span> <span data-ttu-id="37b8b-110">Należy również pamiętać, że [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wymaga włączenia protokołu potoków nazwanych.</span><span class="sxs-lookup"><span data-stu-id="37b8b-110">Note also that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requires the Named Pipes protocol to be enabled.</span></span> <span data-ttu-id="37b8b-111">Aby uzyskać więcej informacji, zobacz [uczenie się według przewodników](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="37b8b-111">For more information, see [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

## <a name="changes-to-database-lost"></a><span data-ttu-id="37b8b-112">Utracone zmiany w bazie danych</span><span class="sxs-lookup"><span data-stu-id="37b8b-112">Changes to Database Lost</span></span>

<span data-ttu-id="37b8b-113">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-113">Q.</span></span> <span data-ttu-id="37b8b-114">Po zmianie danych w bazie danych, ale gdy reran moją aplikację, zmiana nie została już tam osiągnięta.</span><span class="sxs-lookup"><span data-stu-id="37b8b-114">I made a change to data in the database, but when I reran my application, the change was no longer there.</span></span>

<span data-ttu-id="37b8b-115">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-115">A.</span></span> <span data-ttu-id="37b8b-116">Upewnij się, że <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, aby zapisać wyniki w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="37b8b-116">Make sure that you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> to save results to the database.</span></span>

## <a name="database-connection-open-how-long"></a><span data-ttu-id="37b8b-117">Połączenie z bazą danych: Otwórz jak długo?</span><span class="sxs-lookup"><span data-stu-id="37b8b-117">Database Connection: Open How Long?</span></span>

<span data-ttu-id="37b8b-118">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-118">Q.</span></span> <span data-ttu-id="37b8b-119">Jak długo zostanie otwarte moje połączenie z bazą danych?</span><span class="sxs-lookup"><span data-stu-id="37b8b-119">How long does my database connection remain open?</span></span>

<span data-ttu-id="37b8b-120">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-120">A.</span></span> <span data-ttu-id="37b8b-121">Połączenie jest zazwyczaj otwarte, dopóki nie zostaną zużyte wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="37b8b-121">A connection typically remains open until you consume the query results.</span></span> <span data-ttu-id="37b8b-122">Jeśli spodziewasz się czasu na przetworzenie wszystkich wyników i nie będzie to odróżnienia od buforowania wyników, Zastosuj <xref:System.Linq.Enumerable.ToList%2A> do zapytania.</span><span class="sxs-lookup"><span data-stu-id="37b8b-122">If you expect to take time to process all the results and are not opposed to caching the results, apply <xref:System.Linq.Enumerable.ToList%2A> to the query.</span></span> <span data-ttu-id="37b8b-123">W typowych scenariuszach, w których każdy obiekt jest przetwarzany tylko jeden raz, model przesyłania strumieniowego jest wyższy zarówno do `DataReader`, jak i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="37b8b-123">In common scenarios where each object is processed only one time, the streaming model is superior in both `DataReader` and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

<span data-ttu-id="37b8b-124">Dokładne szczegóły użycia połączenia zależą od następujących:</span><span class="sxs-lookup"><span data-stu-id="37b8b-124">The exact details of connection usage depend on the following:</span></span>

- <span data-ttu-id="37b8b-125">Stan połączenia, jeśli <xref:System.Data.Linq.DataContext> jest konstruowany przy użyciu obiektu połączenia.</span><span class="sxs-lookup"><span data-stu-id="37b8b-125">Connection status if the <xref:System.Data.Linq.DataContext> is constructed with a connection object.</span></span>

- <span data-ttu-id="37b8b-126">Ustawienia parametrów połączenia (na przykład włączenie wielu aktywnych zestawów wyników (MARS).</span><span class="sxs-lookup"><span data-stu-id="37b8b-126">Connection string settings (for example, enabling Multiple Active Result Sets (MARS).</span></span> <span data-ttu-id="37b8b-127">Aby uzyskać więcej informacji, zobacz [wiele aktywnych zestawów wyników (MARS)](../multiple-active-result-sets-mars.md).</span><span class="sxs-lookup"><span data-stu-id="37b8b-127">For more information, see [Multiple Active Result Sets (MARS)](../multiple-active-result-sets-mars.md).</span></span>

## <a name="updating-without-querying"></a><span data-ttu-id="37b8b-128">Aktualizowanie bez wykonywania zapytań</span><span class="sxs-lookup"><span data-stu-id="37b8b-128">Updating Without Querying</span></span>

<span data-ttu-id="37b8b-129">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-129">Q.</span></span> <span data-ttu-id="37b8b-130">Czy mogę zaktualizować dane tabeli bez uprzedniego zapytania do bazy danych?</span><span class="sxs-lookup"><span data-stu-id="37b8b-130">Can I update table data without first querying the database?</span></span>

<span data-ttu-id="37b8b-131">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-131">A.</span></span> <span data-ttu-id="37b8b-132">Mimo że [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie ma poleceń aktualizacji opartych na zestawie, można użyć jednej z następujących technik do aktualizacji bez uprzedniego zapytania:</span><span class="sxs-lookup"><span data-stu-id="37b8b-132">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not have set-based update commands, you can use either of the following techniques to update without first querying:</span></span>

- <span data-ttu-id="37b8b-133">Użyj <xref:System.Data.Linq.DataContext.ExecuteCommand%2A>, aby wysłać kod SQL.</span><span class="sxs-lookup"><span data-stu-id="37b8b-133">Use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to send SQL code.</span></span>

- <span data-ttu-id="37b8b-134">Utwórz nowe wystąpienie obiektu i zainicjuj wszystkie bieżące wartości (pola), które mają wpływ na tę aktualizację.</span><span class="sxs-lookup"><span data-stu-id="37b8b-134">Create a new instance of the object and initialize all the current values (fields) that affect the update.</span></span> <span data-ttu-id="37b8b-135">Następnie Dołącz obiekt do <xref:System.Data.Linq.DataContext> przy użyciu <xref:System.Data.Linq.Table%601.Attach%2A> i zmodyfikuj pole, które chcesz zmienić.</span><span class="sxs-lookup"><span data-stu-id="37b8b-135">Then attach the object to the <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.Table%601.Attach%2A> and modify the field you want to change.</span></span>

## <a name="unexpected-query-results"></a><span data-ttu-id="37b8b-136">Nieoczekiwane wyniki zapytania</span><span class="sxs-lookup"><span data-stu-id="37b8b-136">Unexpected Query Results</span></span>

<span data-ttu-id="37b8b-137">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-137">Q.</span></span> <span data-ttu-id="37b8b-138">Moje zapytanie zwraca nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="37b8b-138">My query is returning unexpected results.</span></span> <span data-ttu-id="37b8b-139">Jak można sprawdzić, co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="37b8b-139">How can I inspect what is occurring?</span></span>

<span data-ttu-id="37b8b-140">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-140">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="37b8b-141">udostępnia kilka narzędzi do sprawdzania kodu SQL, który generuje.</span><span class="sxs-lookup"><span data-stu-id="37b8b-141">provides several tools for inspecting the SQL code it generates.</span></span> <span data-ttu-id="37b8b-142">Jednym z najważniejszych jest <xref:System.Data.Linq.DataContext.Log%2A>.</span><span class="sxs-lookup"><span data-stu-id="37b8b-142">One of the most important is <xref:System.Data.Linq.DataContext.Log%2A>.</span></span> <span data-ttu-id="37b8b-143">Aby uzyskać więcej informacji, zobacz [obsługa debugowania](debugging-support.md).</span><span class="sxs-lookup"><span data-stu-id="37b8b-143">For more information, see [Debugging Support](debugging-support.md).</span></span>

## <a name="unexpected-stored-procedure-results"></a><span data-ttu-id="37b8b-144">Nieoczekiwane wyniki procedury składowanej</span><span class="sxs-lookup"><span data-stu-id="37b8b-144">Unexpected Stored Procedure Results</span></span>

<span data-ttu-id="37b8b-145">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-145">Q.</span></span> <span data-ttu-id="37b8b-146">Mam procedurę składowaną, której wartość zwracana jest obliczana przez `MAX()`.</span><span class="sxs-lookup"><span data-stu-id="37b8b-146">I have a stored procedure whose return value is calculated by `MAX()`.</span></span> <span data-ttu-id="37b8b-147">Gdy przeciągniesz procedurę składowaną do powierzchni projektanta O/R, wartość zwracana jest niepoprawna.</span><span class="sxs-lookup"><span data-stu-id="37b8b-147">When I drag the stored procedure to the O/R Designer surface, the return value is not correct.</span></span>

<span data-ttu-id="37b8b-148">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-148">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="37b8b-149">zapewnia dwa sposoby zwracania wartości generowanych przez bazę danych zgodnie z procedurami składowanymi:</span><span class="sxs-lookup"><span data-stu-id="37b8b-149">provides two ways to return database-generated values by way of stored procedures:</span></span>

- <span data-ttu-id="37b8b-150">Poprzez nadanie nazwy wynikowi wyjściowemu.</span><span class="sxs-lookup"><span data-stu-id="37b8b-150">By naming the output result.</span></span>

- <span data-ttu-id="37b8b-151">Jawnie określając parametr wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="37b8b-151">By explicitly specifying an output parameter.</span></span>

<span data-ttu-id="37b8b-152">Poniżej przedstawiono przykład niepoprawnych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="37b8b-152">The following is an example of incorrect output.</span></span> <span data-ttu-id="37b8b-153">Ponieważ [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie może mapować wyników, zawsze zwraca 0:</span><span class="sxs-lookup"><span data-stu-id="37b8b-153">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot map the results, it always returns 0:</span></span>

```sql
create procedure proc2

as

begin

select max(i) from t where name like 'hello'

end
```

<span data-ttu-id="37b8b-154">Poniżej znajduje się przykład poprawnych danych wyjściowych przy użyciu parametru wyjściowego:</span><span class="sxs-lookup"><span data-stu-id="37b8b-154">The following is an example of correct output by using an output parameter:</span></span>

```sql
create procedure proc2

@result int OUTPUT

as

select @result = MAX(i) from t where name like 'hello'

go
```

<span data-ttu-id="37b8b-155">Poniżej znajduje się przykład poprawnych danych wyjściowych przez nadanie nazwy wynikowi wyjściowemu:</span><span class="sxs-lookup"><span data-stu-id="37b8b-155">The following is an example of correct output by naming the output result:</span></span>

```sql
create procedure proc2

as

begin

select nax(i) AS MaxResult from t where name like 'hello'

end
```

<span data-ttu-id="37b8b-156">Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji za pomocą procedur składowanych](customizing-operations-by-using-stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="37b8b-156">For more information, see [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md).</span></span>

## <a name="serialization-errors"></a><span data-ttu-id="37b8b-157">Błędy serializacji</span><span class="sxs-lookup"><span data-stu-id="37b8b-157">Serialization Errors</span></span>

<span data-ttu-id="37b8b-158">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-158">Q.</span></span> <span data-ttu-id="37b8b-159">Podczas próby serializacji pojawia się następujący błąd: "Type" System. Data. LINQ. ChangeTracker + StandardChangeTracker "... nie jest oznaczony jako możliwy do serializacji. "</span><span class="sxs-lookup"><span data-stu-id="37b8b-159">When I try to serialize, I get the following error: "Type 'System.Data.Linq.ChangeTracker+StandardChangeTracker' ... is not marked as serializable."</span></span>

<span data-ttu-id="37b8b-160">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-160">A.</span></span> <span data-ttu-id="37b8b-161">Generowanie kodu w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje serializacji <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="37b8b-161">Code generation in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports <xref:System.Runtime.Serialization.DataContractSerializer> serialization.</span></span> <span data-ttu-id="37b8b-162">Nie obsługuje <xref:System.Xml.Serialization.XmlSerializer> ani <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="37b8b-162">It does not support <xref:System.Xml.Serialization.XmlSerializer> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="37b8b-163">Aby uzyskać więcej informacji, zobacz [serializacji](serialization.md).</span><span class="sxs-lookup"><span data-stu-id="37b8b-163">For more information, see [Serialization](serialization.md).</span></span>

## <a name="multiple-dbml-files"></a><span data-ttu-id="37b8b-164">Wiele plików DBML</span><span class="sxs-lookup"><span data-stu-id="37b8b-164">Multiple DBML Files</span></span>

<span data-ttu-id="37b8b-165">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-165">Q.</span></span> <span data-ttu-id="37b8b-166">Gdy mam wiele plików DBML, które współdzielą niektóre tabele, otrzymuję błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="37b8b-166">When I have multiple DBML files that share some tables in common, I get a compiler error.</span></span>

<span data-ttu-id="37b8b-167">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-167">A.</span></span> <span data-ttu-id="37b8b-168">Ustaw **przestrzeń nazw kontekstu** i właściwości **przestrzeni nazw jednostki** z Object Relational Designer na wartość odrębną dla każdego pliku DBML.</span><span class="sxs-lookup"><span data-stu-id="37b8b-168">Set the **Context Namespace** and **Entity Namespace** properties from the Object Relational Designer to a distinct value for each DBML file.</span></span> <span data-ttu-id="37b8b-169">Takie podejście eliminuje kolizję nazw/przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="37b8b-169">This approach eliminates the name/namespace collision.</span></span>

## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a><span data-ttu-id="37b8b-170">Unikanie jawnego ustawienia wartości generowanych przez bazę danych przy wstawianiu lub aktualizacji</span><span class="sxs-lookup"><span data-stu-id="37b8b-170">Avoiding Explicit Setting of Database-Generated Values on Insert or Update</span></span>

<span data-ttu-id="37b8b-171">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-171">Q.</span></span> <span data-ttu-id="37b8b-172">Mam tabelę bazy danych z kolumną `DateCreated`, która domyślnie jest `Getdate()`SQL.</span><span class="sxs-lookup"><span data-stu-id="37b8b-172">I have a database table with a `DateCreated` column that defaults to SQL `Getdate()`.</span></span> <span data-ttu-id="37b8b-173">Przy próbie wstawienia nowego rekordu przy użyciu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]wartość jest ustawiana na `NULL`.</span><span class="sxs-lookup"><span data-stu-id="37b8b-173">When I try to insert a new record by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the value gets set to `NULL`.</span></span> <span data-ttu-id="37b8b-174">Oczekujemy, że zostanie ona ustawiona na wartość domyślną bazy danych.</span><span class="sxs-lookup"><span data-stu-id="37b8b-174">I would expect it to be set to the database default.</span></span>

<span data-ttu-id="37b8b-175">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-175">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="37b8b-176">automatycznie obsługuje tę sytuację dla tożsamości (Automatyczne zwiększenie) i ROWGUIDCOL (identyfikator GUID generowany przez bazę danych) i kolumny sygnatur czasowych.</span><span class="sxs-lookup"><span data-stu-id="37b8b-176">handles this situation automatically for identity (auto-increment) and rowguidcol (database-generated GUID) and timestamp columns.</span></span> <span data-ttu-id="37b8b-177">W innych przypadkach należy ręcznie ustawić <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> właściwości.</span><span class="sxs-lookup"><span data-stu-id="37b8b-177">In other cases, you should manually set <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` and <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> properties.</span></span>

## <a name="multiple-dataloadoptions"></a><span data-ttu-id="37b8b-178">Wiele DataLoadOptions</span><span class="sxs-lookup"><span data-stu-id="37b8b-178">Multiple DataLoadOptions</span></span>

<span data-ttu-id="37b8b-179">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-179">Q.</span></span> <span data-ttu-id="37b8b-180">Czy mogę określić dodatkowe opcje ładowania bez zastępowania pierwszej?</span><span class="sxs-lookup"><span data-stu-id="37b8b-180">Can I specify additional load options without overwriting the first?</span></span>

<span data-ttu-id="37b8b-181">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-181">A.</span></span> <span data-ttu-id="37b8b-182">Tak.</span><span class="sxs-lookup"><span data-stu-id="37b8b-182">Yes.</span></span> <span data-ttu-id="37b8b-183">Pierwsze nie jest zastępowane, tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="37b8b-183">The first is not overwritten, as in the following example:</span></span>

```vb
Dim dlo As New DataLoadOptions()
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)
```

```csharp
DataLoadOptions dlo = new DataLoadOptions();
dlo.LoadWith<Order>(o => o.Customer);
dlo.LoadWith<Order>(o => o.OrderDetails);
```

## <a name="errors-using-sql-compact-35"></a><span data-ttu-id="37b8b-184">Błędy przy użyciu programu SQL Compact 3,5</span><span class="sxs-lookup"><span data-stu-id="37b8b-184">Errors Using SQL Compact 3.5</span></span>

<span data-ttu-id="37b8b-185">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-185">Q.</span></span> <span data-ttu-id="37b8b-186">Otrzymuję komunikat o błędzie podczas przeciągania tabel z bazy danych SQL Server Compact 3,5.</span><span class="sxs-lookup"><span data-stu-id="37b8b-186">I get an error when I drag tables out of a SQL Server Compact 3.5 database.</span></span>

<span data-ttu-id="37b8b-187">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-187">A.</span></span> <span data-ttu-id="37b8b-188">Object Relational Designer nie obsługuje SQL Server Compact 3,5, chociaż środowisko uruchomieniowe [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] działa.</span><span class="sxs-lookup"><span data-stu-id="37b8b-188">The Object Relational Designer does not support SQL Server Compact 3.5, although the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime does.</span></span> <span data-ttu-id="37b8b-189">W takiej sytuacji należy utworzyć własne klasy jednostek i dodać odpowiednie atrybuty.</span><span class="sxs-lookup"><span data-stu-id="37b8b-189">In this situation, you must create your own entity classes and add the appropriate attributes.</span></span>

## <a name="errors-in-inheritance-relationships"></a><span data-ttu-id="37b8b-190">Błędy w relacjach dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="37b8b-190">Errors in Inheritance Relationships</span></span>

<span data-ttu-id="37b8b-191">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-191">Q.</span></span> <span data-ttu-id="37b8b-192">W Object Relational Designer użyto kształtu dziedziczenie przybornika, aby połączyć dwie jednostki, ale otrzymuję błędy.</span><span class="sxs-lookup"><span data-stu-id="37b8b-192">I used the toolbox inheritance shape in the Object Relational Designer to connect two entities, but I get errors.</span></span>

<span data-ttu-id="37b8b-193">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-193">A.</span></span> <span data-ttu-id="37b8b-194">Tworzenie relacji jest niewystarczające.</span><span class="sxs-lookup"><span data-stu-id="37b8b-194">Creating the relationship is not enough.</span></span> <span data-ttu-id="37b8b-195">Należy podać informacje takie jak kolumna rozróżniacza, wartość rozróżniacza klasy bazowej i wartość rozróżniacza klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="37b8b-195">You must provide information such as the discriminator column, base class discriminator value, and derived class discriminator value.</span></span>

## <a name="provider-model"></a><span data-ttu-id="37b8b-196">Model dostawcy</span><span class="sxs-lookup"><span data-stu-id="37b8b-196">Provider Model</span></span>

<span data-ttu-id="37b8b-197">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-197">Q.</span></span> <span data-ttu-id="37b8b-198">Czy jest dostępny publiczny model dostawcy?</span><span class="sxs-lookup"><span data-stu-id="37b8b-198">Is a public provider model available?</span></span>

<span data-ttu-id="37b8b-199">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-199">A.</span></span> <span data-ttu-id="37b8b-200">Nie jest dostępny żaden model dostawcy publicznego.</span><span class="sxs-lookup"><span data-stu-id="37b8b-200">No public provider model is available.</span></span> <span data-ttu-id="37b8b-201">W tej chwili [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje tylko SQL Server i SQL Server Compact 3,5.</span><span class="sxs-lookup"><span data-stu-id="37b8b-201">At this time, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports SQL Server and SQL Server Compact 3.5 only.</span></span>

## <a name="sql-injection-attacks"></a><span data-ttu-id="37b8b-202">Ataki z iniekcją SQL</span><span class="sxs-lookup"><span data-stu-id="37b8b-202">SQL-Injection Attacks</span></span>

<span data-ttu-id="37b8b-203">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-203">Q.</span></span> <span data-ttu-id="37b8b-204">Jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] chronić przed atakami polegającymi na iniekcji SQL?</span><span class="sxs-lookup"><span data-stu-id="37b8b-204">How is [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] protected from SQL-injection attacks?</span></span>

<span data-ttu-id="37b8b-205">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-205">A.</span></span> <span data-ttu-id="37b8b-206">Iniekcja kodu SQL stanowi znaczne ryzyko dla tradycyjnych zapytań SQL utworzonych przez połączenie danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="37b8b-206">SQL injection has been a significant risk for traditional SQL queries formed by concatenating user input.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="37b8b-207">pozwala uniknąć takiego wstrzyknięcia przy użyciu <xref:System.Data.SqlClient.SqlParameter> w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="37b8b-207">avoids such injection by using <xref:System.Data.SqlClient.SqlParameter> in queries.</span></span> <span data-ttu-id="37b8b-208">Dane wejściowe użytkownika są włączane do wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="37b8b-208">User input is turned into parameter values.</span></span> <span data-ttu-id="37b8b-209">Takie podejście uniemożliwia używanie złośliwych poleceń z poziomu danych wejściowych klienta.</span><span class="sxs-lookup"><span data-stu-id="37b8b-209">This approach prevents malicious commands from being used from customer input.</span></span>

## <a name="changing-read-only-flag-in-dbml-files"></a><span data-ttu-id="37b8b-210">Zmiana flagi tylko do odczytu w plikach DBML</span><span class="sxs-lookup"><span data-stu-id="37b8b-210">Changing Read-only Flag in DBML Files</span></span>

<span data-ttu-id="37b8b-211">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-211">Q.</span></span> <span data-ttu-id="37b8b-212">Jak mogę wyeliminować metody ustawiane z niektórych właściwości podczas tworzenia modelu obiektów z pliku DBML?</span><span class="sxs-lookup"><span data-stu-id="37b8b-212">How do I eliminate setters from some properties when I create an object model from a DBML file?</span></span>

<span data-ttu-id="37b8b-213">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-213">A.</span></span> <span data-ttu-id="37b8b-214">Wykonaj następujące czynności w tym zaawansowanym scenariuszu:</span><span class="sxs-lookup"><span data-stu-id="37b8b-214">Take the following steps for this advanced scenario:</span></span>

1. <span data-ttu-id="37b8b-215">W pliku. dbml Zmodyfikuj właściwość, zmieniając flagę <xref:System.Data.Linq.ITable.IsReadOnly%2A>, aby `True`.</span><span class="sxs-lookup"><span data-stu-id="37b8b-215">In the .dbml file, modify the property by changing the <xref:System.Data.Linq.ITable.IsReadOnly%2A> flag to `True`.</span></span>

2. <span data-ttu-id="37b8b-216">Dodaj klasę częściową.</span><span class="sxs-lookup"><span data-stu-id="37b8b-216">Add a partial class.</span></span> <span data-ttu-id="37b8b-217">Utwórz konstruktora z parametrami dla elementów członkowskich tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="37b8b-217">Create a constructor with parameters for the read-only members.</span></span>

3. <span data-ttu-id="37b8b-218">Sprawdź domyślną wartość <xref:System.Data.Linq.Mapping.UpdateCheck> (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>), aby określić, czy jest to poprawna wartość dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="37b8b-218">Review the default <xref:System.Data.Linq.Mapping.UpdateCheck> value (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) to determine whether that is the correct value for your application.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="37b8b-219">Jeśli używasz Object Relational Designer w programie Visual Studio, zmiany mogą zostać nadpisywane.</span><span class="sxs-lookup"><span data-stu-id="37b8b-219">If you are using the Object Relational Designer in Visual Studio, your changes might be overwritten.</span></span>

## <a name="aptca"></a><span data-ttu-id="37b8b-220">APTCA</span><span class="sxs-lookup"><span data-stu-id="37b8b-220">APTCA</span></span>

<span data-ttu-id="37b8b-221">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-221">Q.</span></span> <span data-ttu-id="37b8b-222">Czy system. Data. LINQ oznaczono do użycia przez częściowo zaufany kod?</span><span class="sxs-lookup"><span data-stu-id="37b8b-222">Is System.Data.Linq marked for use by partially trusted code?</span></span>

<span data-ttu-id="37b8b-223">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-223">A.</span></span> <span data-ttu-id="37b8b-224">Tak, zestaw system. Data. LINQ. dll znajduje się wśród zestawów .NET Framework oznaczonych atrybutem <xref:System.Security.AllowPartiallyTrustedCallersAttribute>.</span><span class="sxs-lookup"><span data-stu-id="37b8b-224">Yes, the System.Data.Linq.dll assembly is among those .NET Framework assemblies marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="37b8b-225">Bez oznaczania, zestawy w .NET Framework są przeznaczone do użycia tylko przez w pełni zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="37b8b-225">Without this marking, assemblies in the .NET Framework are intended for use only by fully trusted code.</span></span>

<span data-ttu-id="37b8b-226">Głównym scenariuszem w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], aby zezwolić częściowo zaufanym obiektom wywołującym na dostęp do zestawu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] z aplikacji sieci Web, gdzie konfiguracja *zaufania* jest średnia.</span><span class="sxs-lookup"><span data-stu-id="37b8b-226">The principal scenario in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] for allowing partially trusted callers is to enable the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly to be accessed from Web applications, where the *trust* configuration is Medium.</span></span>

## <a name="mapping-data-from-multiple-tables"></a><span data-ttu-id="37b8b-227">Mapowanie danych z wielu tabel</span><span class="sxs-lookup"><span data-stu-id="37b8b-227">Mapping Data from Multiple Tables</span></span>

<span data-ttu-id="37b8b-228">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-228">Q.</span></span> <span data-ttu-id="37b8b-229">Dane w mojej jednostce pochodzą z wielu tabel.</span><span class="sxs-lookup"><span data-stu-id="37b8b-229">The data in my entity comes from multiple tables.</span></span> <span data-ttu-id="37b8b-230">Jak mogę ją zmapować?</span><span class="sxs-lookup"><span data-stu-id="37b8b-230">How do I map it?</span></span>

<span data-ttu-id="37b8b-231">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-231">A.</span></span> <span data-ttu-id="37b8b-232">Możesz utworzyć widok w bazie danych i zmapować jednostkę do widoku.</span><span class="sxs-lookup"><span data-stu-id="37b8b-232">You can create a view in a database and map the entity to the view.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="37b8b-233">generuje ten sam kod SQL dla widoków, tak jak w przypadku tabel.</span><span class="sxs-lookup"><span data-stu-id="37b8b-233">generates the same SQL for views as it does for tables.</span></span>

> [!NOTE]
> <span data-ttu-id="37b8b-234">Korzystanie z widoków w tym scenariuszu ma pewne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="37b8b-234">The use of views in this scenario has limitations.</span></span> <span data-ttu-id="37b8b-235">To podejście jest najbardziej bezpieczne, gdy operacje wykonywane na <xref:System.Data.Linq.Table%601> są obsługiwane przez widok podstawowy.</span><span class="sxs-lookup"><span data-stu-id="37b8b-235">This approach works most safely when the operations performed on <xref:System.Data.Linq.Table%601> are supported by the underlying view.</span></span> <span data-ttu-id="37b8b-236">Tylko ty wiesz, które operacje są zamierzone.</span><span class="sxs-lookup"><span data-stu-id="37b8b-236">Only you know which operations are intended.</span></span> <span data-ttu-id="37b8b-237">Na przykład większość aplikacji jest tylko do odczytu, a inny numer pokaźną wykonuje `Create`/`Update`/operacje `Delete` przy użyciu procedur składowanych w widokach.</span><span class="sxs-lookup"><span data-stu-id="37b8b-237">For example, most applications are read-only, and another sizeable number perform `Create`/`Update`/`Delete` operations only by using stored procedures against views.</span></span>

## <a name="connection-pooling"></a><span data-ttu-id="37b8b-238">Pula połączeń</span><span class="sxs-lookup"><span data-stu-id="37b8b-238">Connection Pooling</span></span>

<span data-ttu-id="37b8b-239">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-239">Q.</span></span> <span data-ttu-id="37b8b-240">Czy istnieje konstrukcja, która może pomóc w <xref:System.Data.Linq.DataContext> pule?</span><span class="sxs-lookup"><span data-stu-id="37b8b-240">Is there a construct that can help with <xref:System.Data.Linq.DataContext> pooling?</span></span>

<span data-ttu-id="37b8b-241">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-241">A.</span></span> <span data-ttu-id="37b8b-242">Nie próbuj ponownie używać wystąpień <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="37b8b-242">Do not try to reuse instances of <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="37b8b-243">Każda <xref:System.Data.Linq.DataContext> utrzymuje stan (łącznie z pamięcią podręczną tożsamości) dla jednej konkretnej sesji edytowania/zapytań.</span><span class="sxs-lookup"><span data-stu-id="37b8b-243">Each <xref:System.Data.Linq.DataContext> maintains state (including an identity cache) for one particular edit/query session.</span></span> <span data-ttu-id="37b8b-244">Aby uzyskać nowe wystąpienia na podstawie bieżącego stanu bazy danych, Użyj nowego <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="37b8b-244">To obtain new instances based on the current state of the database, use a new <xref:System.Data.Linq.DataContext>.</span></span>

<span data-ttu-id="37b8b-245">Nadal można używać podstawowej puli połączeń ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="37b8b-245">You can still use underlying ADO.NET connection pooling.</span></span> <span data-ttu-id="37b8b-246">Aby uzyskać więcej informacji, zobacz [SQL Servering pooling (ADO.NET)](../../sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="37b8b-246">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../sql-server-connection-pooling.md).</span></span>

## <a name="second-datacontext-is-not-updated"></a><span data-ttu-id="37b8b-247">Drugi element DataContext nie został zaktualizowany</span><span class="sxs-lookup"><span data-stu-id="37b8b-247">Second DataContext Is Not Updated</span></span>

<span data-ttu-id="37b8b-248">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-248">Q.</span></span> <span data-ttu-id="37b8b-249">Użyto jednego wystąpienia <xref:System.Data.Linq.DataContext> do przechowywania wartości w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="37b8b-249">I used one instance of <xref:System.Data.Linq.DataContext> to store values in the database.</span></span> <span data-ttu-id="37b8b-250">Jednak druga <xref:System.Data.Linq.DataContext> w tej samej bazie danych nie odzwierciedla zaktualizowanych wartości.</span><span class="sxs-lookup"><span data-stu-id="37b8b-250">However, a second <xref:System.Data.Linq.DataContext> on the same database does not reflect the updated values.</span></span> <span data-ttu-id="37b8b-251">Drugie wystąpienie <xref:System.Data.Linq.DataContext> prawdopodobnie zwraca zbuforowane wartości.</span><span class="sxs-lookup"><span data-stu-id="37b8b-251">The second <xref:System.Data.Linq.DataContext> instance seems to return cached values.</span></span>

<span data-ttu-id="37b8b-252">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-252">A.</span></span> <span data-ttu-id="37b8b-253">To zachowanie jest zgodne z założeniami.</span><span class="sxs-lookup"><span data-stu-id="37b8b-253">This behavior is by design.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="37b8b-254">nadal zwracają te same wystąpienia/wartości, które zostały wydane w pierwszym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="37b8b-254">continues to return the same instances/values that you saw in the first instance.</span></span> <span data-ttu-id="37b8b-255">Podczas wprowadzania aktualizacji należy użyć optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="37b8b-255">When you make updates, you use optimistic concurrency.</span></span> <span data-ttu-id="37b8b-256">Oryginalne dane są używane do sprawdzania stanu bieżącego bazy danych w celu potwierdzenia, że nadal nie są zmieniane.</span><span class="sxs-lookup"><span data-stu-id="37b8b-256">The original data is used to check against the current database state to assert that it is in fact still unchanged.</span></span> <span data-ttu-id="37b8b-257">Jeśli uległy zmianie, wystąpi konflikt i aplikacja musi je rozwiązać.</span><span class="sxs-lookup"><span data-stu-id="37b8b-257">If it has changed, a conflict occurs and your application must resolve it.</span></span> <span data-ttu-id="37b8b-258">Jedną z opcji aplikacji jest zresetowanie oryginalnego stanu do bieżącego stanu bazy danych i ponowne wypróbowanie aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="37b8b-258">One option of your application is to reset the original state to the current database state and to try the update again.</span></span> <span data-ttu-id="37b8b-259">Aby uzyskać więcej informacji, zobacz [How to: Manage konflikts Change](how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="37b8b-259">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>

<span data-ttu-id="37b8b-260">Możesz również ustawić <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> na false, co spowoduje wyłączenie buforowania i śledzenie zmian.</span><span class="sxs-lookup"><span data-stu-id="37b8b-260">You can also set <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to false, which turns off caching and change tracking.</span></span> <span data-ttu-id="37b8b-261">Następnie można pobrać najnowsze wartości przy każdym zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="37b8b-261">You can then retrieve the latest values every time that you query.</span></span>

## <a name="cannot-call-submitchanges-in-read-only-mode"></a><span data-ttu-id="37b8b-262">Nie można wywołać SubmitChanges w trybie tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="37b8b-262">Cannot Call SubmitChanges in Read-only Mode</span></span>

<span data-ttu-id="37b8b-263">PYTANIE:</span><span class="sxs-lookup"><span data-stu-id="37b8b-263">Q.</span></span> <span data-ttu-id="37b8b-264">Gdy próbuję wywołać <xref:System.Data.Linq.DataContext.SubmitChanges%2A> w trybie tylko do odczytu, pojawia się błąd.</span><span class="sxs-lookup"><span data-stu-id="37b8b-264">When I try to call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> in read-only mode, I get an error.</span></span>

<span data-ttu-id="37b8b-265">A.</span><span class="sxs-lookup"><span data-stu-id="37b8b-265">A.</span></span> <span data-ttu-id="37b8b-266">Tryb tylko do odczytu wyłącza możliwość śledzenia zmian w kontekście.</span><span class="sxs-lookup"><span data-stu-id="37b8b-266">Read-only mode turns off the ability of the context to track changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="37b8b-267">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37b8b-267">See also</span></span>

- [<span data-ttu-id="37b8b-268">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="37b8b-268">Reference</span></span>](reference.md)
- [<span data-ttu-id="37b8b-269">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="37b8b-269">Troubleshooting</span></span>](troubleshooting.md)
- [<span data-ttu-id="37b8b-270">Zabezpieczenia w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="37b8b-270">Security in LINQ to SQL</span></span>](security-in-linq-to-sql.md)
