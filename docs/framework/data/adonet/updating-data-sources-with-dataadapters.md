---
title: Aktualizowanie źródeł danych za pomocą elementów DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: 4a6e22352a309f9d624c6922abc531cb31a5baf1
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736687"
---
# <a name="updating-data-sources-with-dataadapters"></a><span data-ttu-id="a541a-102">Aktualizowanie źródeł danych za pomocą elementów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="a541a-102">Updating Data Sources with DataAdapters</span></span>

<span data-ttu-id="a541a-103">Metoda `Update` <xref:System.Data.Common.DataAdapter> jest wywoływana, aby rozwiązać zmiany z <xref:System.Data.DataSet> z powrotem do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a541a-103">The `Update` method of the <xref:System.Data.Common.DataAdapter> is called to resolve changes from a <xref:System.Data.DataSet> back to the data source.</span></span> <span data-ttu-id="a541a-104">Metoda `Update`, taka jak Metoda `Fill`, przyjmuje jako argumenty wystąpienie `DataSet`oraz opcjonalny obiekt <xref:System.Data.DataTable> lub `DataTable` nazwę.</span><span class="sxs-lookup"><span data-stu-id="a541a-104">The `Update` method, like the `Fill` method, takes as arguments an instance of a `DataSet`, and an optional <xref:System.Data.DataTable> object or `DataTable` name.</span></span> <span data-ttu-id="a541a-105">Wystąpienie `DataSet` jest `DataSet`, który zawiera wprowadzone zmiany, a `DataTable` określa tabelę, z której mają zostać pobrane zmiany.</span><span class="sxs-lookup"><span data-stu-id="a541a-105">The `DataSet` instance is the `DataSet` that contains the changes that have been made, and the `DataTable` identifies the table from which to retrieve the changes.</span></span> <span data-ttu-id="a541a-106">Jeśli `DataTable` nie zostanie określona, zostanie użyty pierwszy `DataTable` w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a541a-106">If no `DataTable` is specified, the first `DataTable` in the `DataSet` is used.</span></span>

<span data-ttu-id="a541a-107">Gdy wywołasz metodę `Update`, `DataAdapter` analizuje wprowadzone zmiany i wykonuje odpowiednie polecenie (INSERT, UPDATE lub DELETE).</span><span class="sxs-lookup"><span data-stu-id="a541a-107">When you call the `Update` method, the `DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE).</span></span> <span data-ttu-id="a541a-108">Gdy `DataAdapter` napotka zmianę <xref:System.Data.DataRow>, do przetworzenia zmiany używa <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>lub <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A>.</span><span class="sxs-lookup"><span data-stu-id="a541a-108">When the `DataAdapter` encounters a change to a <xref:System.Data.DataRow>, it uses the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, or <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> to process the change.</span></span> <span data-ttu-id="a541a-109">Pozwala to zmaksymalizować wydajność aplikacji ADO.NET przez określenie składni polecenia w czasie projektowania i, jeśli to możliwe, za pomocą procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="a541a-109">This allows you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, through the use of stored procedures.</span></span> <span data-ttu-id="a541a-110">Przed wywołaniem `Update`należy jawnie ustawić te polecenia.</span><span class="sxs-lookup"><span data-stu-id="a541a-110">You must explicitly set the commands before calling `Update`.</span></span> <span data-ttu-id="a541a-111">Jeśli `Update` jest wywoływana i nie istnieje odpowiednie polecenie dla określonej aktualizacji (na przykład brak `DeleteCommand` dla usuniętych wierszy), zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a541a-111">If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.</span></span>

> [!NOTE]
> <span data-ttu-id="a541a-112">Jeśli używasz SQL Server procedur składowanych do edytowania lub usuwania danych przy użyciu `DataAdapter`, upewnij się, że nie używasz opcji SET NOCOUNT ON w definicji procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="a541a-112">If you are using SQL Server stored procedures to edit or delete data using a `DataAdapter`, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="a541a-113">Powoduje to, że liczba zwracanych wierszy jest równa zero, która `DataAdapter` interpretuje jako konflikt współbieżności.</span><span class="sxs-lookup"><span data-stu-id="a541a-113">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="a541a-114">W tym zdarzeniu zostanie zgłoszony <xref:System.Data.DBConcurrencyException>.</span><span class="sxs-lookup"><span data-stu-id="a541a-114">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>

<span data-ttu-id="a541a-115">Parametry polecenia mogą służyć do określania wartości wejściowych i wyjściowych dla instrukcji SQL lub procedury składowanej dla każdego zmodyfikowanego wiersza w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a541a-115">Command parameters can be used to specify input and output values for an SQL statement or stored procedure for each modified row in a `DataSet`.</span></span> <span data-ttu-id="a541a-116">Aby uzyskać więcej informacji, zobacz [DataAdapter Parameters](dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a541a-116">For more information, see [DataAdapter Parameters](dataadapter-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a541a-117">Ważne jest, aby zrozumieć różnicę między usunięciem wiersza w <xref:System.Data.DataTable> i usunięciem wiersza.</span><span class="sxs-lookup"><span data-stu-id="a541a-117">It is important to understand the difference between deleting a row in a <xref:System.Data.DataTable> and removing the row.</span></span> <span data-ttu-id="a541a-118">Po wywołaniu metody `Remove` lub `RemoveAt` wiersz jest usuwany natychmiast.</span><span class="sxs-lookup"><span data-stu-id="a541a-118">When you call the `Remove` or `RemoveAt` method, the row is removed immediately.</span></span> <span data-ttu-id="a541a-119">Jeśli przekazanie `DataTable` lub `DataSet` do `DataAdapter` i wywołań `Update`nie wpłynie na odpowiednie wiersze w źródle danych zaplecza.</span><span class="sxs-lookup"><span data-stu-id="a541a-119">Any corresponding rows in the back end data source will not be affected if you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`.</span></span> <span data-ttu-id="a541a-120">Gdy używasz metody `Delete`, wiersz pozostanie w `DataTable` i zostanie oznaczony do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="a541a-120">When you use the `Delete` method, the row remains in the `DataTable` and is marked for deletion.</span></span> <span data-ttu-id="a541a-121">Po przejściu `DataTable` lub `DataSet` do `DataAdapter` i wywołań `Update`, odpowiedni wiersz w źródle danych zaplecza zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="a541a-121">If you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`, the corresponding row in the back end data source is deleted.</span></span>

<span data-ttu-id="a541a-122">Jeśli `DataTable` są mapowane na lub generowane na podstawie pojedynczej tabeli bazy danych, można skorzystać z obiektu <xref:System.Data.Common.DbCommandBuilder>, aby automatycznie generować obiekty `DeleteCommand`, `InsertCommand`i `UpdateCommand` dla `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="a541a-122">If your `DataTable` maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` objects for the `DataAdapter`.</span></span> <span data-ttu-id="a541a-123">Aby uzyskać więcej informacji, zobacz [Generowanie poleceń z CommandBuilders](generating-commands-with-commandbuilders.md).</span><span class="sxs-lookup"><span data-stu-id="a541a-123">For more information, see [Generating Commands with CommandBuilders](generating-commands-with-commandbuilders.md).</span></span>

## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a><span data-ttu-id="a541a-124">Mapowanie wartości do zestawu danych za pomocą UpdatedRowSource</span><span class="sxs-lookup"><span data-stu-id="a541a-124">Using UpdatedRowSource to Map Values to a DataSet</span></span>

<span data-ttu-id="a541a-125">Można kontrolować sposób, w jaki wartości zwracane ze źródła danych są mapowane z powrotem do `DataTable` następującego po wywołaniu metody Update `DataAdapter`, przy użyciu właściwości <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> obiektu <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="a541a-125">You can control how the values returned from the data source are mapped back to the `DataTable` following a call to the Update method of a `DataAdapter`, by using the <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> property of a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="a541a-126">Ustawiając właściwość `UpdatedRowSource` na jedną z wartości wyliczenia <xref:System.Data.UpdateRowSource>, można kontrolować, czy parametry wyjściowe zwracane przez polecenia `DataAdapter` są ignorowane lub stosowane do zmienionych wierszy w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a541a-126">By setting the `UpdatedRowSource` property to one of the <xref:System.Data.UpdateRowSource> enumeration values, you can control whether output parameters returned by the `DataAdapter` commands are ignored or applied to the changed row in the `DataSet`.</span></span> <span data-ttu-id="a541a-127">Można również określić, czy pierwszy zwracany wiersz (jeśli istnieje) jest stosowany do zmienionego wiersza w `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="a541a-127">You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataTable`.</span></span>

<span data-ttu-id="a541a-128">W poniższej tabeli opisano różne wartości `UpdateRowSource` Wyliczenie i ich wpływ na zachowanie polecenia użytego z `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="a541a-128">The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter`.</span></span>

|<span data-ttu-id="a541a-129">UpdatedRowSource, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a541a-129">UpdatedRowSource Enumeration</span></span>|<span data-ttu-id="a541a-130">Opis</span><span class="sxs-lookup"><span data-stu-id="a541a-130">Description</span></span>|
|----------------------------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|<span data-ttu-id="a541a-131">Zarówno parametry wyjściowe, jak i pierwszy wiersz zwracanego zestawu wyników mogą zostać zamapowane na zmieniony wiersz w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a541a-131">Both the output parameters and the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|<span data-ttu-id="a541a-132">Tylko dane z pierwszego wiersza zwróconego zestawu wyników mogą zostać zamapowane na zmieniony wiersz w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a541a-132">Only the data in the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.None>|<span data-ttu-id="a541a-133">Wszystkie parametry wyjściowe lub wiersze zwróconego zestawu wyników są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a541a-133">Any output parameters or rows of a returned result set are ignored.</span></span>|
|<xref:System.Data.UpdateRowSource.OutputParameters>|<span data-ttu-id="a541a-134">Tylko parametry wyjściowe mogą być mapowane do zmienionego wiersza w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a541a-134">Only output parameters may be mapped to the changed row in the `DataSet`.</span></span>|

<span data-ttu-id="a541a-135">Metoda `Update` rozwiązuje zmiany z powrotem do źródła danych; Jednak inni klienci mogą modyfikować dane w źródle danych od czasu ostatniego wypełnienia `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a541a-135">The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the `DataSet`.</span></span> <span data-ttu-id="a541a-136">Aby odświeżyć `DataSet` przy użyciu bieżących danych, użyj metody `DataAdapter` i `Fill`.</span><span class="sxs-lookup"><span data-stu-id="a541a-136">To refresh your `DataSet` with current data, use the `DataAdapter` and `Fill` method.</span></span> <span data-ttu-id="a541a-137">Nowe wiersze zostaną dodane do tabeli, a zaktualizowane informacje zostaną dołączone do istniejących wierszy.</span><span class="sxs-lookup"><span data-stu-id="a541a-137">New rows will be added to the table, and updated information will be incorporated into existing rows.</span></span> <span data-ttu-id="a541a-138">Metoda `Fill` określa, czy nowy wiersz zostanie dodany, czy istniejący wiersz zostanie zaktualizowany poprzez sprawdzenie wartości klucza podstawowego wierszy w `DataSet` i wierszy zwracanych przez `SelectCommand`.</span><span class="sxs-lookup"><span data-stu-id="a541a-138">The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the `DataSet` and the rows returned by the `SelectCommand`.</span></span> <span data-ttu-id="a541a-139">Jeśli `Fill` Metoda napotka wartość klucza podstawowego dla wiersza w `DataSet`, który dopasowuje wartość klucza podstawowego z wiersza w wynikach zwróconych przez `SelectCommand`, aktualizuje istniejący wiersz o informacje z wiersza zwrócone przez `SelectCommand` i ustawia <xref:System.Data.DataRow.RowState%2A> istniejącego wiersza do `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="a541a-139">If the `Fill` method encounters a primary key value for a row in the `DataSet` that matches a primary key value from a row in the results returned by the `SelectCommand`, it updates the existing row with the information from the row returned by the `SelectCommand` and sets the <xref:System.Data.DataRow.RowState%2A> of the existing row to `Unchanged`.</span></span> <span data-ttu-id="a541a-140">Jeśli wiersz zwrócony przez `SelectCommand` ma wartość klucza podstawowego, która nie pasuje do żadnej wartości klucza podstawowego wierszy w `DataSet`, Metoda `Fill` dodaje nowy wiersz z `RowState` `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="a541a-140">If a row returned by the `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the `DataSet`, the `Fill` method adds a new row with a `RowState` of `Unchanged`.</span></span>

> [!NOTE]
> <span data-ttu-id="a541a-141">Jeśli `SelectCommand` zwraca wyniki SPRZĘŻENIa zewnętrznego, `DataAdapter` nie ustawi `PrimaryKey` wartości dla wynikowego `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="a541a-141">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` will not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="a541a-142">Należy zdefiniować `PrimaryKey` samodzielnie, aby upewnić się, że zduplikowane wiersze są poprawnie rozpoznawane.</span><span class="sxs-lookup"><span data-stu-id="a541a-142">You must define the `PrimaryKey` yourself to ensure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="a541a-143">Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="a541a-143">For more information, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>

<span data-ttu-id="a541a-144">Aby obsłużyć wyjątki, które mogą wystąpić podczas wywoływania metody `Update`, można użyć zdarzenia `RowUpdated`, aby odpowiedzieć na błędy aktualizacji wierszy w miarę ich występowania (zobacz [Obsługa zdarzeń DataAdapter](handling-dataadapter-events.md)), lub ustawić `DataAdapter.ContinueUpdateOnError` na `true` przed wywołaniem `Update`, a następnie odpowiedzieć na informacje o błędzie przechowywane we właściwości `RowError` określonego wiersza po zakończeniu aktualizacji (zobacz [Informacje o błędzie wiersza](./dataset-datatable-dataview/row-error-information.md)).</span><span class="sxs-lookup"><span data-stu-id="a541a-144">To handle exceptions that may occur when calling the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur (see [Handling DataAdapter Events](handling-dataadapter-events.md)), or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete (see [Row Error Information](./dataset-datatable-dataview/row-error-information.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="a541a-145">Wywoływanie `AcceptChanges` na `DataSet`, `DataTable`lub `DataRow` spowoduje zastąpienie wszystkich wartości `Original` `DataRow`, które mają zostać zastąpione wartościami `Current` `DataRow`.</span><span class="sxs-lookup"><span data-stu-id="a541a-145">Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` will cause all `Original` values for a `DataRow` to be overwritten with the `Current` values for the `DataRow`.</span></span> <span data-ttu-id="a541a-146">Jeśli wartości pól, które identyfikują wiersz jako unikatowy, zostały zmodyfikowane, po wywołaniu `AcceptChanges` wartości `Original` nie będą już zgodne z wartościami w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="a541a-146">If the field values that identify the row as unique have been modified, after calling `AcceptChanges` the `Original` values will no longer match the values in the data source.</span></span> <span data-ttu-id="a541a-147">`AcceptChanges` jest automatycznie wywoływana dla każdego wiersza w trakcie wywołania metody Update `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="a541a-147">`AcceptChanges` is called automatically for each row during a call to the Update method of a `DataAdapter`.</span></span> <span data-ttu-id="a541a-148">Oryginalne wartości można zachować podczas wywołania metody Update, najpierw ustawiając właściwość `AcceptChangesDuringUpdate` `DataAdapter` na false lub przez utworzenie programu obsługi zdarzeń dla zdarzenia `RowUpdated` i ustawienie <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> na <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span><span class="sxs-lookup"><span data-stu-id="a541a-148">You can preserve the original values during a call to the Update method by first setting the `AcceptChangesDuringUpdate` property of the `DataAdapter` to false, or by creating an event handler for the `RowUpdated` event and setting the <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> to <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span></span> <span data-ttu-id="a541a-149">Aby uzyskać więcej informacji, zobacz [scalanie zawartości zestawu danych](./dataset-datatable-dataview/merging-dataset-contents.md) i [Obsługa zdarzeń DataAdapter](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="a541a-149">For more information, see [Merging DataSet Contents](./dataset-datatable-dataview/merging-dataset-contents.md) and [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>

## <a name="example"></a><span data-ttu-id="a541a-150">Przykład</span><span class="sxs-lookup"><span data-stu-id="a541a-150">Example</span></span>

<span data-ttu-id="a541a-151">W poniższych przykładach pokazano, jak wykonać aktualizacje zmodyfikowanych wierszy, jawnie ustawiając `UpdateCommand` `DataAdapter` i wywołując metodę `Update`.</span><span class="sxs-lookup"><span data-stu-id="a541a-151">The following examples demonstrate how to perform updates to modified rows by explicitly setting the `UpdateCommand` of a `DataAdapter` and calling its `Update` method.</span></span> <span data-ttu-id="a541a-152">Należy zauważyć, że parametr określony w klauzuli WHERE instrukcji UPDATE jest ustawiony tak, aby używał wartości `Original` `SourceColumn`.</span><span class="sxs-lookup"><span data-stu-id="a541a-152">Notice that the parameter specified in the WHERE clause of the UPDATE statement is set to use the `Original` value of the `SourceColumn`.</span></span> <span data-ttu-id="a541a-153">Jest to ważne, ponieważ wartość `Current` mogła zostać zmodyfikowana i może nie być zgodna z wartością w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="a541a-153">This is important, because the `Current` value may have been modified and may not match the value in the data source.</span></span> <span data-ttu-id="a541a-154">Wartość `Original` to wartość użyta do wypełnienia `DataTable` ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a541a-154">The `Original` value is the value that was used to populate the `DataTable` from the data source.</span></span>

[!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]

## <a name="autoincrement-columns"></a><span data-ttu-id="a541a-155">Kolumny AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="a541a-155">AutoIncrement Columns</span></span>

<span data-ttu-id="a541a-156">Jeśli tabele ze źródła danych mają funkcję autozwiększania wartości kolumn, kolumny w `DataSet` można wypełnić przez zwrócenie wartości autoprzyrostu jako parametru wyjściowego procedury składowanej i mapowania, które należy do kolumny w tabeli, zwracając wartość autoprzyrostu z pierwszego wiersza zestawu wyników zwróconego przez procedurę składowaną lub instrukcję SQL lub używając zdarzenia `RowUpdated` `DataAdapter` w celu wykonania dodatkowej instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="a541a-156">If the tables from your data source have auto-incrementing columns, you can fill the columns in your `DataSet` either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, by returning the auto-increment value in the first row of a result set returned by a stored procedure or SQL statement, or by using the `RowUpdated` event of the `DataAdapter` to execute an additional SELECT statement.</span></span> <span data-ttu-id="a541a-157">Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [pobieranie tożsamości lub wartości AutoNumber](retrieving-identity-or-autonumber-values.md).</span><span class="sxs-lookup"><span data-stu-id="a541a-157">For more information and an example, see [Retrieving Identity or Autonumber Values](retrieving-identity-or-autonumber-values.md).</span></span>

## <a name="ordering-of-inserts-updates-and-deletes"></a><span data-ttu-id="a541a-158">Porządkowanie operacji wstawiania, aktualizacji i usuwania</span><span class="sxs-lookup"><span data-stu-id="a541a-158">Ordering of Inserts, Updates, and Deletes</span></span>

<span data-ttu-id="a541a-159">W wielu przypadkach kolejność, w jakiej zmiany wprowadzane przez `DataSet` są wysyłane do źródła danych, jest ważna.</span><span class="sxs-lookup"><span data-stu-id="a541a-159">In many circumstances, the order in which changes made through the `DataSet` are sent to the data source is important.</span></span> <span data-ttu-id="a541a-160">Na przykład jeśli wartość klucza podstawowego dla istniejącego wiersza zostanie zaktualizowana, a nowy wiersz został dodany z nową wartością klucza podstawowego jako klucz obcy, ważne jest, aby przetworzyć aktualizację przed wstawieniem.</span><span class="sxs-lookup"><span data-stu-id="a541a-160">For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value as a foreign key, it is important to process the update before the insert.</span></span>

<span data-ttu-id="a541a-161">Można użyć metody `Select` `DataTable`, aby zwrócić tablicę `DataRow`, która odwołuje się tylko do wierszy z określoną `RowState`ą.</span><span class="sxs-lookup"><span data-stu-id="a541a-161">You can use the `Select` method of the `DataTable` to return a `DataRow` array that only references rows with a particular `RowState`.</span></span> <span data-ttu-id="a541a-162">Następnie można przekazać zwróconą tablicę `DataRow` do metody `Update` `DataAdapter` w celu przetworzenia zmodyfikowanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="a541a-162">You can then pass the returned `DataRow` array to the `Update` method of the `DataAdapter` to process the modified rows.</span></span> <span data-ttu-id="a541a-163">Określając podzestaw wierszy do zaktualizowania, można kontrolować kolejność, w której przetwarzane są operacje INSERT, Update i usunięć.</span><span class="sxs-lookup"><span data-stu-id="a541a-163">By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.</span></span>

## <a name="example"></a><span data-ttu-id="a541a-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="a541a-164">Example</span></span>

<span data-ttu-id="a541a-165">Na przykład poniższy kod gwarantuje, że usunięte wiersze tabeli są przetwarzane jako pierwsze, a następnie zaktualizowane wiersze, a następnie wstawione wiersze.</span><span class="sxs-lookup"><span data-stu-id="a541a-165">For example, the following code ensures that the deleted rows of the table are processed first, then the updated rows, and then the inserted rows.</span></span>

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

## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a><span data-ttu-id="a541a-166">Pobieranie i aktualizowanie danych przy użyciu elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="a541a-166">Use a DataAdapter to Retrieve and Update Data</span></span>

<span data-ttu-id="a541a-167">Możesz użyć elementu DataAdapter, aby pobrać i zaktualizować dane.</span><span class="sxs-lookup"><span data-stu-id="a541a-167">You can use a DataAdapter to retrieve and update the data.</span></span>

- <span data-ttu-id="a541a-168">Przykład używa DataAdapter. AcceptChangesDuringFill do klonowania danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a541a-168">The sample uses DataAdapter.AcceptChangesDuringFill to clone the data in the database.</span></span> <span data-ttu-id="a541a-169">Jeśli właściwość jest ustawiona na wartość false, Metoda AcceptChanges nie jest wywoływana podczas wypełniania tabeli, a nowo dodane wiersze są traktowane jako wstawione wiersze.</span><span class="sxs-lookup"><span data-stu-id="a541a-169">If the property is set as false, AcceptChanges is not called when filling the table, and the newly added rows are treated as inserted rows.</span></span> <span data-ttu-id="a541a-170">Dlatego przykład używa tych wierszy do wstawienia nowych wierszy do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a541a-170">So, the sample uses these rows to insert the new rows into the database.</span></span>

- <span data-ttu-id="a541a-171">Przykłady używają klasy DataAdapter. TableMappings do definiowania mapowania między tabelą źródłową i DataTable.</span><span class="sxs-lookup"><span data-stu-id="a541a-171">The samples uses DataAdapter.TableMappings to define the mapping between the source table and DataTable.</span></span>

- <span data-ttu-id="a541a-172">Przykład używa DataAdapter. FillLoadOption, aby określić, w jaki sposób karta wypełnia DataTable z elementu DbDataReader.</span><span class="sxs-lookup"><span data-stu-id="a541a-172">The sample uses DataAdapter.FillLoadOption to determine how the adapter fills the DataTable from the DbDataReader.</span></span> <span data-ttu-id="a541a-173">Podczas tworzenia elementu DataTable można zapisać tylko dane z bazy danych do bieżącej wersji lub oryginalnej wersji, ustawiając właściwość jako LoadOption. upsert lub LoadOption. PreserveChanges.</span><span class="sxs-lookup"><span data-stu-id="a541a-173">When you create a DataTable, you can only write the data from database to the current version or the original version by setting the property as the LoadOption.Upsert or the LoadOption.PreserveChanges.</span></span>

- <span data-ttu-id="a541a-174">Przykład spowoduje również zaktualizowanie tabeli przy użyciu DbDataAdapter. UpdateBatchSize do wykonywania operacji wsadowych.</span><span class="sxs-lookup"><span data-stu-id="a541a-174">The sample will also update the table by using DbDataAdapter.UpdateBatchSize to perform batch operations.</span></span>

<span data-ttu-id="a541a-175">Przed skompilowaniem i uruchomieniem przykładu należy utworzyć przykładową bazę danych:</span><span class="sxs-lookup"><span data-stu-id="a541a-175">Before you compile and run the sample, you need to create the sample database:</span></span>

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

<span data-ttu-id="a541a-176">C#Visual Basic projekty z tym przykładem kodu można znaleźć na przykładach [kodu dewelopera](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span><span class="sxs-lookup"><span data-stu-id="a541a-176">C# and Visual Basic projects with this code sample can be found on [Developer Code Samples](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a541a-177">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a541a-177">See also</span></span>

- [<span data-ttu-id="a541a-178">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="a541a-178">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="a541a-179">Stany wiersza i wersje wiersza</span><span class="sxs-lookup"><span data-stu-id="a541a-179">Row States and Row Versions</span></span>](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [<span data-ttu-id="a541a-180">Metody AcceptChanges i RejectChanges</span><span class="sxs-lookup"><span data-stu-id="a541a-180">AcceptChanges and RejectChanges</span></span>](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [<span data-ttu-id="a541a-181">Scalanie zawartości elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="a541a-181">Merging DataSet Contents</span></span>](./dataset-datatable-dataview/merging-dataset-contents.md)
- [<span data-ttu-id="a541a-182">Pobieranie tożsamości lub wartości automatycznych numerów</span><span class="sxs-lookup"><span data-stu-id="a541a-182">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)
- [<span data-ttu-id="a541a-183">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a541a-183">ADO.NET Overview</span></span>](ado-net-overview.md)
