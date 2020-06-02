---
title: Aktualizowanie źródeł danych za pomocą elementów DataAdapter
description: Dowiedz się, w jaki sposób metoda Update klasy DataAdapter rozwiązuje zmiany z zestawu danych z powrotem do źródła danych w aplikacjach ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: e2348a3a89aa1c28856bfc21aaa25f2c8327aac7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286187"
---
# <a name="updating-data-sources-with-dataadapters"></a><span data-ttu-id="20df6-103">Aktualizowanie źródeł danych za pomocą elementów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="20df6-103">Updating Data Sources with DataAdapters</span></span>

<span data-ttu-id="20df6-104">`Update`Metoda <xref:System.Data.Common.DataAdapter> jest wywoływana, aby rozwiązać zmiany z <xref:System.Data.DataSet> powrotem do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="20df6-104">The `Update` method of the <xref:System.Data.Common.DataAdapter> is called to resolve changes from a <xref:System.Data.DataSet> back to the data source.</span></span> <span data-ttu-id="20df6-105">`Update`Metoda, taka jak `Fill` Metoda, przyjmuje jako argumenty wystąpienia a `DataSet` i opcjonalnego <xref:System.Data.DataTable> obiektu lub `DataTable` nazwy.</span><span class="sxs-lookup"><span data-stu-id="20df6-105">The `Update` method, like the `Fill` method, takes as arguments an instance of a `DataSet`, and an optional <xref:System.Data.DataTable> object or `DataTable` name.</span></span> <span data-ttu-id="20df6-106">`DataSet`Wystąpienie to `DataSet` zawiera wprowadzone zmiany i `DataTable` identyfikuje tabelę, z której mają zostać pobrane zmiany.</span><span class="sxs-lookup"><span data-stu-id="20df6-106">The `DataSet` instance is the `DataSet` that contains the changes that have been made, and the `DataTable` identifies the table from which to retrieve the changes.</span></span> <span data-ttu-id="20df6-107">Jeśli nie `DataTable` jest określony, zostanie `DataTable` `DataSet` użyta pierwsza z.</span><span class="sxs-lookup"><span data-stu-id="20df6-107">If no `DataTable` is specified, the first `DataTable` in the `DataSet` is used.</span></span>

<span data-ttu-id="20df6-108">Po wywołaniu `Update` metody, `DataAdapter` analizuje wprowadzone zmiany i wykonuje odpowiednie polecenie (INSERT, Update lub Delete).</span><span class="sxs-lookup"><span data-stu-id="20df6-108">When you call the `Update` method, the `DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE).</span></span> <span data-ttu-id="20df6-109">Gdy `DataAdapter` napotka zmiany <xref:System.Data.DataRow> , używa <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> lub <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> do przetwarzania zmiany.</span><span class="sxs-lookup"><span data-stu-id="20df6-109">When the `DataAdapter` encounters a change to a <xref:System.Data.DataRow>, it uses the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, or <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> to process the change.</span></span> <span data-ttu-id="20df6-110">Pozwala to zmaksymalizować wydajność aplikacji ADO.NET przez określenie składni polecenia w czasie projektowania i, jeśli to możliwe, za pomocą procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="20df6-110">This allows you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, through the use of stored procedures.</span></span> <span data-ttu-id="20df6-111">Należy jawnie ustawić polecenia przed wywołaniem `Update` .</span><span class="sxs-lookup"><span data-stu-id="20df6-111">You must explicitly set the commands before calling `Update`.</span></span> <span data-ttu-id="20df6-112">Jeśli `Update` jest wywoływana i odpowiednie polecenie nie istnieje dla określonej aktualizacji (na przykład nie `DeleteCommand` dla usuniętych wierszy), zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="20df6-112">If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.</span></span>

> [!NOTE]
> <span data-ttu-id="20df6-113">Jeśli używasz SQL Server procedur składowanych do edytowania lub usuwania danych przy użyciu programu `DataAdapter` , upewnij się, że w definicji procedury składowanej nie używasz opcji SET NOCOUNT on.</span><span class="sxs-lookup"><span data-stu-id="20df6-113">If you are using SQL Server stored procedures to edit or delete data using a `DataAdapter`, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="20df6-114">Powoduje to, że liczba zwracanych wierszy jest równa zero, która `DataAdapter` interpretuje jako konflikt współbieżności.</span><span class="sxs-lookup"><span data-stu-id="20df6-114">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="20df6-115">W takim przypadku <xref:System.Data.DBConcurrencyException> zostanie zgłoszone zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="20df6-115">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>

<span data-ttu-id="20df6-116">Parametry polecenia mogą służyć do określania wartości wejściowych i wyjściowych dla instrukcji SQL lub procedury składowanej dla każdego zmodyfikowanego wiersza w `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="20df6-116">Command parameters can be used to specify input and output values for an SQL statement or stored procedure for each modified row in a `DataSet`.</span></span> <span data-ttu-id="20df6-117">Aby uzyskać więcej informacji, zobacz [DataAdapter Parameters](dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="20df6-117">For more information, see [DataAdapter Parameters](dataadapter-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="20df6-118">Ważne jest, aby zrozumieć różnicę między usunięciem wiersza w <xref:System.Data.DataTable> a i usunięciem wiersza.</span><span class="sxs-lookup"><span data-stu-id="20df6-118">It is important to understand the difference between deleting a row in a <xref:System.Data.DataTable> and removing the row.</span></span> <span data-ttu-id="20df6-119">Gdy wywołasz `Remove` metodę lub `RemoveAt` , wiersz zostanie natychmiast usunięty.</span><span class="sxs-lookup"><span data-stu-id="20df6-119">When you call the `Remove` or `RemoveAt` method, the row is removed immediately.</span></span> <span data-ttu-id="20df6-120">Nie wpłynie to na wszystkie odpowiadające im wiersze w źródle danych zaplecza, `DataTable` `DataSet` a następnie do `DataAdapter` wywołania i `Update` .</span><span class="sxs-lookup"><span data-stu-id="20df6-120">Any corresponding rows in the back end data source will not be affected if you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`.</span></span> <span data-ttu-id="20df6-121">Gdy używasz `Delete` metody, wiersz pozostaje w `DataTable` i jest oznaczony do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="20df6-121">When you use the `Delete` method, the row remains in the `DataTable` and is marked for deletion.</span></span> <span data-ttu-id="20df6-122">Jeśli następnie przekażesz `DataTable` wywołanie lub `DataSet` do `DataAdapter` i `Update` , odpowiadający mu wiersz w źródle danych zaplecza zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="20df6-122">If you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`, the corresponding row in the back end data source is deleted.</span></span>

<span data-ttu-id="20df6-123">Jeśli `DataTable` mapowania do lub są generowane na podstawie pojedynczej tabeli bazy danych, można skorzystać z <xref:System.Data.Common.DbCommandBuilder> obiektu, aby automatycznie generować `DeleteCommand` `InsertCommand` obiekty, i `UpdateCommand` `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="20df6-123">If your `DataTable` maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` objects for the `DataAdapter`.</span></span> <span data-ttu-id="20df6-124">Aby uzyskać więcej informacji, zobacz [Generowanie poleceń z CommandBuilders](generating-commands-with-commandbuilders.md).</span><span class="sxs-lookup"><span data-stu-id="20df6-124">For more information, see [Generating Commands with CommandBuilders](generating-commands-with-commandbuilders.md).</span></span>

## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a><span data-ttu-id="20df6-125">Mapowanie wartości do zestawu danych za pomocą UpdatedRowSource</span><span class="sxs-lookup"><span data-stu-id="20df6-125">Using UpdatedRowSource to Map Values to a DataSet</span></span>

<span data-ttu-id="20df6-126">Można kontrolować sposób, w jaki wartości zwracane ze źródła danych są mapowane z powrotem do `DataTable` następującego wywołania metody Update w `DataAdapter` , przy użyciu <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> właściwości <xref:System.Data.Common.DbCommand> obiektu.</span><span class="sxs-lookup"><span data-stu-id="20df6-126">You can control how the values returned from the data source are mapped back to the `DataTable` following a call to the Update method of a `DataAdapter`, by using the <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> property of a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="20df6-127">Ustawiając `UpdatedRowSource` Właściwość na jedną z <xref:System.Data.UpdateRowSource> wartości wyliczenia, można kontrolować, czy parametry wyjściowe zwracane przez `DataAdapter` polecenia są ignorowane czy stosowane do zmienionych wierszy w `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="20df6-127">By setting the `UpdatedRowSource` property to one of the <xref:System.Data.UpdateRowSource> enumeration values, you can control whether output parameters returned by the `DataAdapter` commands are ignored or applied to the changed row in the `DataSet`.</span></span> <span data-ttu-id="20df6-128">Można również określić, czy pierwszy zwracany wiersz (jeśli istnieje) jest stosowany do zmienionego wiersza w `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="20df6-128">You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataTable`.</span></span>

<span data-ttu-id="20df6-129">W poniższej tabeli opisano różne wartości `UpdateRowSource` wyliczania i ich wpływ na zachowanie polecenia użytego z `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="20df6-129">The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter`.</span></span>

|<span data-ttu-id="20df6-130">UpdatedRowSource, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="20df6-130">UpdatedRowSource Enumeration</span></span>|<span data-ttu-id="20df6-131">Opis</span><span class="sxs-lookup"><span data-stu-id="20df6-131">Description</span></span>|
|----------------------------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|<span data-ttu-id="20df6-132">Zarówno parametry wyjściowe, jak i pierwszy wiersz zwracanego zestawu wyników mogą być zamapowane do zmienionego wiersza w `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="20df6-132">Both the output parameters and the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|<span data-ttu-id="20df6-133">Tylko dane z pierwszego wiersza zwróconego zestawu wyników mogą być mapowane do zmienionego wiersza w `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="20df6-133">Only the data in the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.None>|<span data-ttu-id="20df6-134">Wszystkie parametry wyjściowe lub wiersze zwróconego zestawu wyników są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="20df6-134">Any output parameters or rows of a returned result set are ignored.</span></span>|
|<xref:System.Data.UpdateRowSource.OutputParameters>|<span data-ttu-id="20df6-135">Tylko parametry wyjściowe mogą być mapowane do zmienionego wiersza w `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="20df6-135">Only output parameters may be mapped to the changed row in the `DataSet`.</span></span>|

<span data-ttu-id="20df6-136">`Update`Metoda rozwiązuje zmiany z powrotem do źródła danych, ale inni klienci mogą modyfikować dane w źródle danych od czasu ostatniego wypełnienia `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="20df6-136">The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the `DataSet`.</span></span> <span data-ttu-id="20df6-137">Aby odświeżyć `DataSet` dane przy użyciu bieżących danych, `DataAdapter` Użyj `Fill` metody i.</span><span class="sxs-lookup"><span data-stu-id="20df6-137">To refresh your `DataSet` with current data, use the `DataAdapter` and `Fill` method.</span></span> <span data-ttu-id="20df6-138">Nowe wiersze zostaną dodane do tabeli, a zaktualizowane informacje zostaną dołączone do istniejących wierszy.</span><span class="sxs-lookup"><span data-stu-id="20df6-138">New rows will be added to the table, and updated information will be incorporated into existing rows.</span></span> <span data-ttu-id="20df6-139">`Fill`Metoda określa, czy nowy wiersz zostanie dodany, czy istniejący wiersz zostanie zaktualizowany poprzez sprawdzenie wartości klucza podstawowego wierszy w `DataSet` i wierszy zwracanych przez `SelectCommand` .</span><span class="sxs-lookup"><span data-stu-id="20df6-139">The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the `DataSet` and the rows returned by the `SelectCommand`.</span></span> <span data-ttu-id="20df6-140">Jeśli `Fill` Metoda napotka wartość klucza podstawowego dla wiersza w, `DataSet` który dopasowuje wartość klucza podstawowego z wiersza w wynikach zwróconych przez `SelectCommand` , aktualizuje istniejący wiersz o informacje z wiersza zwrócone przez `SelectCommand` i ustawia <xref:System.Data.DataRow.RowState%2A> istniejący wiersz na `Unchanged` .</span><span class="sxs-lookup"><span data-stu-id="20df6-140">If the `Fill` method encounters a primary key value for a row in the `DataSet` that matches a primary key value from a row in the results returned by the `SelectCommand`, it updates the existing row with the information from the row returned by the `SelectCommand` and sets the <xref:System.Data.DataRow.RowState%2A> of the existing row to `Unchanged`.</span></span> <span data-ttu-id="20df6-141">Jeśli wiersz zwrócony przez `SelectCommand` ma wartość klucza podstawowego, która nie pasuje do żadnej wartości klucza podstawowego wierszy w `DataSet` , `Fill` Metoda dodaje nowy wiersz z `RowState` `Unchanged` .</span><span class="sxs-lookup"><span data-stu-id="20df6-141">If a row returned by the `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the `DataSet`, the `Fill` method adds a new row with a `RowState` of `Unchanged`.</span></span>

> [!NOTE]
> <span data-ttu-id="20df6-142">Jeśli `SelectCommand` zwraca wyniki sprzężenia zewnętrznego, `DataAdapter` nie ustawi `PrimaryKey` wartości wynikowej `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="20df6-142">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` will not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="20df6-143">Należy zdefiniować siebie, `PrimaryKey` Aby upewnić się, że zduplikowane wiersze są poprawnie rozpoznawane.</span><span class="sxs-lookup"><span data-stu-id="20df6-143">You must define the `PrimaryKey` yourself to ensure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="20df6-144">Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="20df6-144">For more information, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>

<span data-ttu-id="20df6-145">Aby obsłużyć wyjątki, które mogą wystąpić podczas wywoływania `Update` metody, można użyć `RowUpdated` zdarzenia w celu reagowania na błędy aktualizacji wierszy w miarę ich występowania (zobacz [Obsługa zdarzeń klasy DataAdapter](handling-dataadapter-events.md)) lub ustawić `DataAdapter.ContinueUpdateOnError` opcję `true` przed wywołaniem `Update` , a następnie odpowiedzieć na informacje o błędzie przechowywane we `RowError` właściwości określonego wiersza po zakończeniu aktualizacji (zobacz [Informacje o błędzie wiersza](./dataset-datatable-dataview/row-error-information.md)).</span><span class="sxs-lookup"><span data-stu-id="20df6-145">To handle exceptions that may occur when calling the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur (see [Handling DataAdapter Events](handling-dataadapter-events.md)), or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete (see [Row Error Information](./dataset-datatable-dataview/row-error-information.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="20df6-146">Wywołanie `AcceptChanges` `DataSet` `DataTable` elementu,, lub `DataRow` spowoduje zastąpienie wszystkich wartości w `Original` `DataRow` celu zastąpienia `Current` wartościami dla `DataRow` .</span><span class="sxs-lookup"><span data-stu-id="20df6-146">Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` will cause all `Original` values for a `DataRow` to be overwritten with the `Current` values for the `DataRow`.</span></span> <span data-ttu-id="20df6-147">Jeśli wartości pól, które identyfikują wiersz jako unikatowy, zostały zmodyfikowane, po wywołaniu `AcceptChanges` `Original` wartości nie będą już zgodne z wartościami w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="20df6-147">If the field values that identify the row as unique have been modified, after calling `AcceptChanges` the `Original` values will no longer match the values in the data source.</span></span> <span data-ttu-id="20df6-148">`AcceptChanges`jest wywoływana automatycznie dla każdego wiersza w trakcie wywołania metody Update `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="20df6-148">`AcceptChanges` is called automatically for each row during a call to the Update method of a `DataAdapter`.</span></span> <span data-ttu-id="20df6-149">Oryginalne wartości można zachować podczas wywołania metody Update, najpierw ustawiając `AcceptChangesDuringUpdate` Właściwość `DataAdapter` na false lub tworząc procedurę obsługi zdarzeń dla `RowUpdated` zdarzenia i ustawiając wartość <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> na <xref:System.Data.UpdateStatus.SkipCurrentRow> .</span><span class="sxs-lookup"><span data-stu-id="20df6-149">You can preserve the original values during a call to the Update method by first setting the `AcceptChangesDuringUpdate` property of the `DataAdapter` to false, or by creating an event handler for the `RowUpdated` event and setting the <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> to <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span></span> <span data-ttu-id="20df6-150">Aby uzyskać więcej informacji, zobacz [scalanie zawartości zestawu danych](./dataset-datatable-dataview/merging-dataset-contents.md) i [Obsługa zdarzeń DataAdapter](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="20df6-150">For more information, see [Merging DataSet Contents](./dataset-datatable-dataview/merging-dataset-contents.md) and [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>

## <a name="example"></a><span data-ttu-id="20df6-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="20df6-151">Example</span></span>

<span data-ttu-id="20df6-152">W poniższych przykładach pokazano, jak wykonać aktualizacje modyfikowanych wierszy, jawnie ustawiając wartość a `UpdateCommand` `DataAdapter` i wywołując jej `Update` metodę.</span><span class="sxs-lookup"><span data-stu-id="20df6-152">The following examples demonstrate how to perform updates to modified rows by explicitly setting the `UpdateCommand` of a `DataAdapter` and calling its `Update` method.</span></span> <span data-ttu-id="20df6-153">Należy zauważyć, że parametr określony w klauzuli WHERE instrukcji UPDATE jest ustawiony tak, aby używał `Original` wartości `SourceColumn` .</span><span class="sxs-lookup"><span data-stu-id="20df6-153">Notice that the parameter specified in the WHERE clause of the UPDATE statement is set to use the `Original` value of the `SourceColumn`.</span></span> <span data-ttu-id="20df6-154">Jest to ważne, ponieważ `Current` wartość mogła zostać zmodyfikowana i może nie być zgodna z wartością w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="20df6-154">This is important, because the `Current` value may have been modified and may not match the value in the data source.</span></span> <span data-ttu-id="20df6-155">`Original`Wartość jest wartością użytą do wypełnienia `DataTable` ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="20df6-155">The `Original` value is the value that was used to populate the `DataTable` from the data source.</span></span>

[!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]

## <a name="autoincrement-columns"></a><span data-ttu-id="20df6-156">Kolumny AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="20df6-156">AutoIncrement Columns</span></span>

<span data-ttu-id="20df6-157">Jeśli tabele ze źródła danych mają funkcję autozwiększania wartości kolumn, kolumny można wypełniać `DataSet` przez zwrócenie wartości autoprzyrostu jako parametru wyjściowego procedury składowanej i mapowania, które należy do kolumny w tabeli, zwracając wartość AutoIncrement z pierwszego wiersza zestawu wyników zwróconego przez procedurę składowaną lub instrukcję SQL lub używając `RowUpdated` zdarzenia `DataAdapter` do wykonania dodatkowej instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="20df6-157">If the tables from your data source have auto-incrementing columns, you can fill the columns in your `DataSet` either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, by returning the auto-increment value in the first row of a result set returned by a stored procedure or SQL statement, or by using the `RowUpdated` event of the `DataAdapter` to execute an additional SELECT statement.</span></span> <span data-ttu-id="20df6-158">Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [pobieranie tożsamości lub wartości AutoNumber](retrieving-identity-or-autonumber-values.md).</span><span class="sxs-lookup"><span data-stu-id="20df6-158">For more information and an example, see [Retrieving Identity or Autonumber Values](retrieving-identity-or-autonumber-values.md).</span></span>

## <a name="ordering-of-inserts-updates-and-deletes"></a><span data-ttu-id="20df6-159">Porządkowanie operacji wstawiania, aktualizacji i usuwania</span><span class="sxs-lookup"><span data-stu-id="20df6-159">Ordering of Inserts, Updates, and Deletes</span></span>

<span data-ttu-id="20df6-160">W wielu przypadkach kolejność, w jakiej zmiany wprowadzane przez program `DataSet` są wysyłane do źródła danych, jest ważna.</span><span class="sxs-lookup"><span data-stu-id="20df6-160">In many circumstances, the order in which changes made through the `DataSet` are sent to the data source is important.</span></span> <span data-ttu-id="20df6-161">Na przykład jeśli wartość klucza podstawowego dla istniejącego wiersza zostanie zaktualizowana, a nowy wiersz został dodany z nową wartością klucza podstawowego jako klucz obcy, ważne jest, aby przetworzyć aktualizację przed wstawieniem.</span><span class="sxs-lookup"><span data-stu-id="20df6-161">For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value as a foreign key, it is important to process the update before the insert.</span></span>

<span data-ttu-id="20df6-162">Można użyć `Select` metody, `DataTable` Aby zwrócić `DataRow` tablicę, która odwołuje się tylko do wierszy z konkretną `RowState` .</span><span class="sxs-lookup"><span data-stu-id="20df6-162">You can use the `Select` method of the `DataTable` to return a `DataRow` array that only references rows with a particular `RowState`.</span></span> <span data-ttu-id="20df6-163">Następnie można przekazać zwróconą `DataRow` tablicę do `Update` metody w `DataAdapter` celu przetworzenia zmodyfikowanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="20df6-163">You can then pass the returned `DataRow` array to the `Update` method of the `DataAdapter` to process the modified rows.</span></span> <span data-ttu-id="20df6-164">Określając podzestaw wierszy do zaktualizowania, można kontrolować kolejność, w której przetwarzane są operacje INSERT, Update i usunięć.</span><span class="sxs-lookup"><span data-stu-id="20df6-164">By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.</span></span>

## <a name="example"></a><span data-ttu-id="20df6-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="20df6-165">Example</span></span>

<span data-ttu-id="20df6-166">Na przykład poniższy kod gwarantuje, że usunięte wiersze tabeli są przetwarzane jako pierwsze, a następnie zaktualizowane wiersze, a następnie wstawione wiersze.</span><span class="sxs-lookup"><span data-stu-id="20df6-166">For example, the following code ensures that the deleted rows of the table are processed first, then the updated rows, and then the inserted rows.</span></span>

```vb
Dim table As DataTable = dataSet.Tables("Customers")

' First process deletes.
dataSet.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Deleted))

' Next process updates.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.ModifiedCurrent))

' Finally, process inserts.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Added))
```

```csharp
DataTable table = dataSet.Tables["Customers"];

// First process deletes.
adapter.Update(table.Select(null, null, DataViewRowState.Deleted));

// Next process updates.
adapter.Update(table.Select(null, null,
  DataViewRowState.ModifiedCurrent));

// Finally, process inserts.
adapter.Update(table.Select(null, null, DataViewRowState.Added));
```

## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a><span data-ttu-id="20df6-167">Pobieranie i aktualizowanie danych przy użyciu elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="20df6-167">Use a DataAdapter to Retrieve and Update Data</span></span>

<span data-ttu-id="20df6-168">Możesz użyć elementu DataAdapter, aby pobrać i zaktualizować dane.</span><span class="sxs-lookup"><span data-stu-id="20df6-168">You can use a DataAdapter to retrieve and update the data.</span></span>

- <span data-ttu-id="20df6-169">Przykład używa DataAdapter. AcceptChangesDuringFill do klonowania danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="20df6-169">The sample uses DataAdapter.AcceptChangesDuringFill to clone the data in the database.</span></span> <span data-ttu-id="20df6-170">Jeśli właściwość jest ustawiona na wartość false, Metoda AcceptChanges nie jest wywoływana podczas wypełniania tabeli, a nowo dodane wiersze są traktowane jako wstawione wiersze.</span><span class="sxs-lookup"><span data-stu-id="20df6-170">If the property is set as false, AcceptChanges is not called when filling the table, and the newly added rows are treated as inserted rows.</span></span> <span data-ttu-id="20df6-171">Dlatego przykład używa tych wierszy do wstawienia nowych wierszy do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="20df6-171">So, the sample uses these rows to insert the new rows into the database.</span></span>

- <span data-ttu-id="20df6-172">Przykłady używają klasy DataAdapter. TableMappings do definiowania mapowania między tabelą źródłową i DataTable.</span><span class="sxs-lookup"><span data-stu-id="20df6-172">The samples uses DataAdapter.TableMappings to define the mapping between the source table and DataTable.</span></span>

- <span data-ttu-id="20df6-173">Przykład używa DataAdapter. FillLoadOption, aby określić, w jaki sposób karta wypełnia DataTable z elementu DbDataReader.</span><span class="sxs-lookup"><span data-stu-id="20df6-173">The sample uses DataAdapter.FillLoadOption to determine how the adapter fills the DataTable from the DbDataReader.</span></span> <span data-ttu-id="20df6-174">Podczas tworzenia elementu DataTable można zapisać tylko dane z bazy danych do bieżącej wersji lub oryginalnej wersji, ustawiając właściwość jako LoadOption. upsert lub LoadOption. PreserveChanges.</span><span class="sxs-lookup"><span data-stu-id="20df6-174">When you create a DataTable, you can only write the data from database to the current version or the original version by setting the property as the LoadOption.Upsert or the LoadOption.PreserveChanges.</span></span>

- <span data-ttu-id="20df6-175">Przykład spowoduje również zaktualizowanie tabeli przy użyciu DbDataAdapter. UpdateBatchSize do wykonywania operacji wsadowych.</span><span class="sxs-lookup"><span data-stu-id="20df6-175">The sample will also update the table by using DbDataAdapter.UpdateBatchSize to perform batch operations.</span></span>

<span data-ttu-id="20df6-176">Przed skompilowaniem i uruchomieniem przykładu należy utworzyć przykładową bazę danych:</span><span class="sxs-lookup"><span data-stu-id="20df6-176">Before you compile and run the sample, you need to create the sample database:</span></span>

```sql
USE [master]
GO

CREATE DATABASE [MySchool]

GO

USE [MySchool]
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Course]([CourseID] [nvarchar](10) NOT NULL,
[Year] [smallint] NOT NULL,
[Title] [nvarchar](100) NOT NULL,
[Credits] [int] NOT NULL,
[DepartmentID] [int] NOT NULL,
 CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED
(
[CourseID] ASC,
[Year] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Department]([DepartmentID] [int] IDENTITY(1,1) NOT NULL,
[Name] [nvarchar](50) NOT NULL,
[Budget] [money] NOT NULL,
[StartDate] [datetime] NOT NULL,
[Administrator] [int] NULL,
 CONSTRAINT [PK_Department] PRIMARY KEY CLUSTERED
(
[DepartmentID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1045', 2012, N'Calculus', 4, 7)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1061', 2012, N'Physics', 4, 1)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2021', 2012, N'Composition', 3, 2)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2042', 2012, N'Literature', 4, 2)

SET IDENTITY_INSERT [dbo].[Department] ON

INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (1, N'Engineering', 350000.0000, CAST(0x0000999C00000000 AS DateTime), 2)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (2, N'English', 120000.0000, CAST(0x0000999C00000000 AS DateTime), 6)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (4, N'Economics', 200000.0000, CAST(0x0000999C00000000 AS DateTime), 4)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (7, N'Mathematics', 250024.0000, CAST(0x0000999C00000000 AS DateTime), 3)
SET IDENTITY_INSERT [dbo].[Department] OFF

ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])
REFERENCES [dbo].[Department] ([DepartmentID])
GO
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]
GO
```

<span data-ttu-id="20df6-177">Projekty C# i Visual Basic z tym przykładem kodu można znaleźć na przykładach [kodu dewelopera](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span><span class="sxs-lookup"><span data-stu-id="20df6-177">C# and Visual Basic projects with this code sample can be found on [Developer Code Samples](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span></span>

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.SqlClient;
using System.Linq;
using CSDataAdapterOperations.Properties;

namespace CSDataAdapterOperations.Properties {
   internal sealed partial class Settings : global::System.Configuration.ApplicationSettingsBase {

      private static Settings defaultInstance = ((Settings)(global::System.Configuration.ApplicationSettingsBase.Synchronized(new Settings())));

      public static Settings Default {
         get {
            return defaultInstance;
         }
      }

      [global::System.Configuration.ApplicationScopedSettingAttribute()]
      [global::System.Configuration.DefaultSettingValueAttribute("Data Source=(local);Initial Catalog=MySchool;Integrated Security=True")]
      public string MySchoolConnectionString {
         get {
            return ((string)(this["MySchoolConnectionString"]));
         }
      }
   }
}

class Program {
   static void Main(string[] args) {
      Settings settings = new Settings();

      // Copy the data from the database.  Get the table Department and Course from the database.
      String selectString = @"SELECT [DepartmentID],[Name],[Budget],[StartDate],[Administrator]
                                     FROM [MySchool].[dbo].[Department];

                                   SELECT [CourseID],@Year as [Year],Max([Title]) as [Title],
                                   Max([Credits]) as [Credits],Max([DepartmentID]) as [DepartmentID]
                                   FROM [MySchool].[dbo].[Course]
                                   Group by [CourseID]";

      DataSet mySchool = new DataSet();

      SqlCommand selectCommand = new SqlCommand(selectString);
      SqlParameter parameter = selectCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2);
      parameter.Value = new Random(DateTime.Now.Millisecond).Next(9999);

      // Use DataTableMapping to map the source tables and the destination tables.
      DataTableMapping[] tableMappings = {new DataTableMapping("Table", "Department"), new DataTableMapping("Table1", "Course")};
      CopyData(mySchool, settings.MySchoolConnectionString, selectCommand, tableMappings);

      Console.WriteLine("The following tables are from the database.");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      // Roll back the changes
      DataTable department = mySchool.Tables["Department"];
      DataTable course = mySchool.Tables["Course"];

      department.Rows[0]["Name"] = "New" + department.Rows[0][1];
      course.Rows[0]["Title"] = "New" + course.Rows[0]["Title"];
      course.Rows[0]["Credits"] = 10;

      Console.WriteLine("After we changed the tables:");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      department.RejectChanges();
      Console.WriteLine("After use the RejectChanges method in Department table to roll back the changes:");
      ShowDataTable(department);

      DataColumn[] primaryColumns = { course.Columns["CourseID"] };
      DataColumn[] resetColumns = { course.Columns["Title"] };
      ResetCourse(course, settings.MySchoolConnectionString, primaryColumns, resetColumns);
      Console.WriteLine("After use the ResetCourse method in Course table to roll back the changes:");
      ShowDataTable(course);

      // Batch update the table.
      String insertString = @"Insert into [MySchool].[dbo].[Course]([CourseID],[Year],[Title],
                                   [Credits],[DepartmentID])
             values (@CourseID,@Year,@Title,@Credits,@DepartmentID)";
      SqlCommand insertCommand = new SqlCommand(insertString);
      insertCommand.Parameters.Add("@CourseID", SqlDbType.NVarChar, 10, "CourseID");
      insertCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2, "Year");
      insertCommand.Parameters.Add("@Title", SqlDbType.NVarChar, 100, "Title");
      insertCommand.Parameters.Add("@Credits", SqlDbType.Int, 4, "Credits");
      insertCommand.Parameters.Add("@DepartmentID", SqlDbType.Int, 4, "DepartmentID");

      const Int32 batchSize = 10;
      BatchInsertUpdate(course, settings.MySchoolConnectionString, insertCommand, batchSize);
   }

   private static void CopyData(DataSet dataSet, String connectionString, SqlCommand selectCommand, DataTableMapping[] tableMappings) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {adapter.TableMappings.AddRange(tableMappings);
            // If set the AcceptChangesDuringFill as the false, AcceptChanges will not be called on a
            // DataRow after it is added to the DataTable during any of the Fill operations.
            adapter.AcceptChangesDuringFill = false;

            adapter.Fill(dataSet);
         }
      }
   }

   // Roll back only one column or several columns data of the Course table by call ResetDataTable method.
   private static void ResetCourse(DataTable table, String connectionString,
       DataColumn[] primaryColumns, DataColumn[] resetColumns) {
      table.PrimaryKey = primaryColumns;

      // Build the query string
      String primaryCols = String.Join(",", primaryColumns.Select(col => col.ColumnName));
      String resetCols = String.Join(",", resetColumns.Select(col => $"Max({col.ColumnName}) as {col.ColumnName}"));

      String selectString = $"Select {primaryCols},{resetCols} from Course Group by {primaryCols}");

      SqlCommand selectCommand = new SqlCommand(selectString);

      ResetDataTable(table, connectionString, selectCommand);
   }

   // RejectChanges will roll back all changes made to the table since it was loaded, or the last time AcceptChanges
   // was called. When you copy from the database, you can lose all the data after calling RejectChanges
   // The ResetDataTable method rolls back one or more columns of data.
   private static void ResetDataTable(DataTable table, String connectionString,
       SqlCommand selectCommand) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {
            // The incoming values for this row will be written to the current version of each
            // column. The original version of each column's data will not be changed.
            adapter.FillLoadOption = LoadOption.Upsert;

            adapter.Fill(table);
         }
      }
   }

   private static void BatchInsertUpdate(DataTable table, String connectionString,
       SqlCommand insertCommand, Int32 batchSize) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         insertCommand.Connection = connection;
         // When setting UpdateBatchSize to a value other than 1, all the commands
         // associated with the SqlDataAdapter have to have their UpdatedRowSource
         // property set to None or OutputParameters. An exception is thrown otherwise.
         insertCommand.UpdatedRowSource = UpdateRowSource.None;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter()) {
            adapter.InsertCommand = insertCommand;
            // Gets or sets the number of rows that are processed in each round-trip to the server.
            // Setting it to 1 disables batch updates, as rows are sent one at a time.
            adapter.UpdateBatchSize = batchSize;

            adapter.Update(table);

            Console.WriteLine("Successfully to update the table.");
         }
      }
   }

   private static void ShowDataTable(DataTable table) {
      foreach (DataColumn col in table.Columns) {
         Console.Write("{0,-14}", col.ColumnName);
      }
      Console.WriteLine("{0,-14}", "RowState");

      foreach (DataRow row in table.Rows) {
         foreach (DataColumn col in table.Columns) {
            if (col.DataType.Equals(typeof(DateTime)))
               Console.Write("{0,-14:d}", row[col]);
            else if (col.DataType.Equals(typeof(Decimal)))
               Console.Write("{0,-14:C}", row[col]);
            else
               Console.Write("{0,-14}", row[col]);
         }
         Console.WriteLine("{0,-14}", row.RowState);
      }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="20df6-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20df6-178">See also</span></span>

- [<span data-ttu-id="20df6-179">Elementy DataAdapter i DataReader</span><span class="sxs-lookup"><span data-stu-id="20df6-179">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="20df6-180">Stany wiersza i wersje wiersza</span><span class="sxs-lookup"><span data-stu-id="20df6-180">Row States and Row Versions</span></span>](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [<span data-ttu-id="20df6-181">Metody AcceptChanges i RejectChanges</span><span class="sxs-lookup"><span data-stu-id="20df6-181">AcceptChanges and RejectChanges</span></span>](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [<span data-ttu-id="20df6-182">Scalanie zawartości elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="20df6-182">Merging DataSet Contents</span></span>](./dataset-datatable-dataview/merging-dataset-contents.md)
- [<span data-ttu-id="20df6-183">Pobieranie tożsamości lub wartości automatycznych numerów</span><span class="sxs-lookup"><span data-stu-id="20df6-183">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)
- [<span data-ttu-id="20df6-184">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="20df6-184">ADO.NET Overview</span></span>](ado-net-overview.md)
