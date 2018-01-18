---
title: "Aktualizowanie źródła danych za pomocą obiektów DataAdapter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e99ff801894149a2324638bfacbc1d32ee937e0a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="updating-data-sources-with-dataadapters"></a><span data-ttu-id="cf853-102">Aktualizowanie źródła danych za pomocą obiektów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="cf853-102">Updating Data Sources with DataAdapters</span></span>
<span data-ttu-id="cf853-103">`Update` Metody <xref:System.Data.Common.DataAdapter> jest wywoływana, aby rozwiązać zmian z <xref:System.Data.DataSet> do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="cf853-103">The `Update` method of the <xref:System.Data.Common.DataAdapter> is called to resolve changes from a <xref:System.Data.DataSet> back to the data source.</span></span> <span data-ttu-id="cf853-104">`Update` Metody, takiej jak `Fill` metoda, przyjmuje jako argumenty wystąpienia `DataSet`i opcjonalny <xref:System.Data.DataTable> obiektu lub `DataTable` nazwy.</span><span class="sxs-lookup"><span data-stu-id="cf853-104">The `Update` method, like the `Fill` method, takes as arguments an instance of a `DataSet`, and an optional <xref:System.Data.DataTable> object or `DataTable` name.</span></span> <span data-ttu-id="cf853-105">`DataSet` Wystąpienie jest `DataSet` zawiera zmiany, które zostały wprowadzone, i `DataTable` identyfikuje tabeli, z której można pobrać zmiany.</span><span class="sxs-lookup"><span data-stu-id="cf853-105">The `DataSet` instance is the `DataSet` that contains the changes that have been made, and the `DataTable` identifies the table from which to retrieve the changes.</span></span> <span data-ttu-id="cf853-106">Jeśli nie `DataTable` jest określony, pierwszy `DataTable` w `DataSet` jest używany.</span><span class="sxs-lookup"><span data-stu-id="cf853-106">If no `DataTable` is specified, the first `DataTable` in the `DataSet` is used.</span></span>  
  
 <span data-ttu-id="cf853-107">Podczas wywoływania `Update` metody `DataAdapter` analizuje zmiany, które zostały wprowadzone i wykonuje odpowiednie polecenie (INSERT, UPDATE lub DELETE).</span><span class="sxs-lookup"><span data-stu-id="cf853-107">When you call the `Update` method, the `DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE).</span></span> <span data-ttu-id="cf853-108">Gdy `DataAdapter` wykryje zmianę <xref:System.Data.DataRow>, używa <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, lub <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> przetwarzania zmian.</span><span class="sxs-lookup"><span data-stu-id="cf853-108">When the `DataAdapter` encounters a change to a <xref:System.Data.DataRow>, it uses the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, or <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> to process the change.</span></span> <span data-ttu-id="cf853-109">Dzięki temu można zmaksymalizować wydajność aplikacji ADO.NET, określając składni polecenia w czasie projektowania i, jeśli to możliwe, przy użyciu procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="cf853-109">This allows you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, through the use of stored procedures.</span></span> <span data-ttu-id="cf853-110">Musisz jawnie ustawić przed wywołaniem polecenia `Update`.</span><span class="sxs-lookup"><span data-stu-id="cf853-110">You must explicitly set the commands before calling `Update`.</span></span> <span data-ttu-id="cf853-111">Jeśli `Update` nazywa się i odpowiednie polecenie nie istnieje dla określonej aktualizacji (na przykład nie `DeleteCommand` dla usuniętych wierszy), jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="cf853-111">If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf853-112">Jeśli używasz procedur składowanych serwera SQL, aby edytować lub usunąć danych przy użyciu `DataAdapter`, upewnij się, że nie używasz SET NOCOUNT ON w definicji procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="cf853-112">If you are using SQL Server stored procedures to edit or delete data using a `DataAdapter`, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="cf853-113">Powoduje to, że liczba zmodyfikowanych wierszy zwrócił zero, który `DataAdapter` jako konflikt współbieżności.</span><span class="sxs-lookup"><span data-stu-id="cf853-113">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="cf853-114">W takim przypadku <xref:System.Data.DBConcurrencyException> zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="cf853-114">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
 <span data-ttu-id="cf853-115">Parametry polecenia mogą być używane do określenia wartości wejściowe i wyjściowe dla instrukcji SQL lub procedurę składowaną dla każdego wiersza zmodyfikowane w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cf853-115">Command parameters can be used to specify input and output values for an SQL statement or stored procedure for each modified row in a `DataSet`.</span></span> <span data-ttu-id="cf853-116">Aby uzyskać więcej informacji, zobacz [parametry element DataAdapter](../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="cf853-116">For more information, see [DataAdapter Parameters](../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf853-117">Ważne jest, aby zrozumieć różnicę między usuwanie wiersza w <xref:System.Data.DataTable> i usuwanie wiersza.</span><span class="sxs-lookup"><span data-stu-id="cf853-117">It is important to understand the difference between deleting a row in a <xref:System.Data.DataTable> and removing the row.</span></span> <span data-ttu-id="cf853-118">Podczas wywoływania `Remove` lub `RemoveAt` metody, wiersz jest usuwany natychmiast.</span><span class="sxs-lookup"><span data-stu-id="cf853-118">When you call the `Remove` or `RemoveAt` method, the row is removed immediately.</span></span> <span data-ttu-id="cf853-119">Wszystkie odpowiednie wiersze w źródle danych zaplecza nie zostaną zmienione, jeśli następnie przekazać `DataTable` lub `DataSet` do `DataAdapter` i Wywołaj `Update`.</span><span class="sxs-lookup"><span data-stu-id="cf853-119">Any corresponding rows in the back end data source will not be affected if you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`.</span></span> <span data-ttu-id="cf853-120">Jeśli używasz `Delete` metody wiersz pozostaje w `DataTable` i jest oznaczony do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="cf853-120">When you use the `Delete` method, the row remains in the `DataTable` and is marked for deletion.</span></span> <span data-ttu-id="cf853-121">Jeśli następnie przekazać `DataTable` lub `DataSet` do `DataAdapter` i Wywołaj `Update`, odpowiedni wiersz w źródle danych zaplecza zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="cf853-121">If you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`, the corresponding row in the back end data source is deleted.</span></span>  
  
 <span data-ttu-id="cf853-122">Jeśli Twoje `DataTable` mapuje lub jest generowany z jednej bazy danych, możesz korzystać z <xref:System.Data.Common.DbCommandBuilder> obiektu w celu automatycznego generowania `DeleteCommand`, `InsertCommand`, i `UpdateCommand` obiektów na `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="cf853-122">If your `DataTable` maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` objects for the `DataAdapter`.</span></span> <span data-ttu-id="cf853-123">Aby uzyskać więcej informacji, zobacz [generowania poleceń CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).</span><span class="sxs-lookup"><span data-stu-id="cf853-123">For more information, see [Generating Commands with CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).</span></span>  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a><span data-ttu-id="cf853-124">Mapuj wartości do zestawu danych za pomocą przetwarzania wsadowego</span><span class="sxs-lookup"><span data-stu-id="cf853-124">Using UpdatedRowSource to Map Values to a DataSet</span></span>  
 <span data-ttu-id="cf853-125">Można kontrolować sposób wartości zwracane ze źródła danych są mapowane z powrotem na `DataTable` po wywołaniu metody aktualizacji `DataAdapter`, za pomocą <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> właściwość <xref:System.Data.Common.DbCommand> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cf853-125">You can control how the values returned from the data source are mapped back to the `DataTable` following a call to the Update method of a `DataAdapter`, by using the <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> property of a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="cf853-126">Przez ustawienie `UpdatedRowSource` jedną z właściwości <xref:System.Data.UpdateRowSource> wartości wyliczenia można kontrolować, czy parametry wyjściowe zwracane przez `DataAdapter` polecenia są ignorowane lub zastosowany do wiersza zmienione w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cf853-126">By setting the `UpdatedRowSource` property to one of the <xref:System.Data.UpdateRowSource> enumeration values, you can control whether output parameters returned by the `DataAdapter` commands are ignored or applied to the changed row in the `DataSet`.</span></span> <span data-ttu-id="cf853-127">Można również określić, czy pierwszy zwrócony wiersza (jeśli istnieje) jest stosowana do zmienionych wierszy w `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="cf853-127">You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataTable`.</span></span>  
  
 <span data-ttu-id="cf853-128">W poniższej tabeli opisano różne wartości `UpdateRowSource` wyliczenie i ich wpływu na zachowanie polecenia używane z `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="cf853-128">The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter`.</span></span>  
  
|<span data-ttu-id="cf853-129">Wyliczenie przetwarzania wsadowego</span><span class="sxs-lookup"><span data-stu-id="cf853-129">UpdatedRowSource Enumeration</span></span>|<span data-ttu-id="cf853-130">Opis</span><span class="sxs-lookup"><span data-stu-id="cf853-130">Description</span></span>|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|<span data-ttu-id="cf853-131">Parametry wyjściowe jak pierwszy wiersz zestaw wyników zwrócony mogą być mapowane na zmienionych wierszy w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cf853-131">Both the output parameters and the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|<span data-ttu-id="cf853-132">Tylko dane w pierwszym wierszu zestaw wyników zwrócony mogą być mapowane na zmienionych wierszy w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cf853-132">Only the data in the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|  
|<xref:System.Data.UpdateRowSource.None>|<span data-ttu-id="cf853-133">Wszystkie dane wyjściowe są parametry lub wierszy zestawu wyników zwróconego są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="cf853-133">Any output parameters or rows of a returned result set are ignored.</span></span>|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|<span data-ttu-id="cf853-134">Tylko parametry wyjściowe można mapować zmienionych wierszy w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cf853-134">Only output parameters may be mapped to the changed row in the `DataSet`.</span></span>|  
  
 <span data-ttu-id="cf853-135">`Update` Metoda usuwa zmiany z powrotem do źródła danych; jednak innych klientów zmienił danych w źródle danych od czasu ostatniego wypełniony `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cf853-135">The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the `DataSet`.</span></span> <span data-ttu-id="cf853-136">Aby odświeżyć Twojej `DataSet` bieżące dane za pomocą `DataAdapter` i `Fill` — metoda.</span><span class="sxs-lookup"><span data-stu-id="cf853-136">To refresh your `DataSet` with current data, use the `DataAdapter` and `Fill` method.</span></span> <span data-ttu-id="cf853-137">Nowe wiersze zostaną dodane do tabeli, a zaktualizowane informacje zostaną uwzględnione w istniejących wierszy.</span><span class="sxs-lookup"><span data-stu-id="cf853-137">New rows will be added to the table, and updated information will be incorporated into existing rows.</span></span> <span data-ttu-id="cf853-138">`Fill` Metoda określa, czy zostanie dodany nowy wiersz lub istniejącego wiersza zostaną zaktualizowane, sprawdzając wartości kluczy podstawowych wierszy w `DataSet` i wierszy zwracanych przez `SelectCommand`.</span><span class="sxs-lookup"><span data-stu-id="cf853-138">The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the `DataSet` and the rows returned by the `SelectCommand`.</span></span> <span data-ttu-id="cf853-139">Jeśli `Fill` metody napotka wartość klucza podstawowego dla wiersza w `DataSet` odpowiadającego wartość klucza podstawowego z wiersza wyników zwróconych przez `SelectCommand`, aktualizuje istniejący wiersz z informacjami z wierszy zwracanych przez `SelectCommand`i ustawia <xref:System.Data.DataRow.RowState%2A> istniejącego wiersza do `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="cf853-139">If the `Fill` method encounters a primary key value for a row in the `DataSet` that matches a primary key value from a row in the results returned by the `SelectCommand`, it updates the existing row with the information from the row returned by the `SelectCommand` and sets the <xref:System.Data.DataRow.RowState%2A> of the existing row to `Unchanged`.</span></span> <span data-ttu-id="cf853-140">Jeśli wiersz zwrócony przez `SelectCommand` ma wartość klucza podstawowego, który nie pasuje do żadnej wartości kluczy podstawowych wierszy w `DataSet`, `Fill` metody dodaje nowy wiersz z `RowState` z `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="cf853-140">If a row returned by the `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the `DataSet`, the `Fill` method adds a new row with a `RowState` of `Unchanged`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf853-141">Jeśli `SelectCommand` zwraca wyniki OUTER JOIN `DataAdapter` nie ustawi `PrimaryKey` wartość powstałe w ten sposób `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="cf853-141">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` will not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="cf853-142">Należy zdefiniować `PrimaryKey` samodzielnie, aby upewnić się, że zduplikowane wiersze są rozpoznawane poprawnie.</span><span class="sxs-lookup"><span data-stu-id="cf853-142">You must define the `PrimaryKey` yourself to ensure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="cf853-143">Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="cf853-143">For more information, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="cf853-144">Do obsługi wyjątków, które mogą wystąpić podczas wywoływania metody `Update` metody, można użyć `RowUpdated` zdarzenia występujące odpowiedzieć na błędy aktualizacji wiersza (zobacz [obsługi zdarzeń element DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), lub możesz ustawić `DataAdapter.ContinueUpdateOnError` do `true` przed wywołaniem `Update`i reagowanie na informacje o błędzie, przechowywane w `RowError` właściwości określonego wiersza po ukończeniu aktualizacji (zobacz [informacje o błędzie wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).</span><span class="sxs-lookup"><span data-stu-id="cf853-144">To handle exceptions that may occur when calling the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur (see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete (see [Row Error Information](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).</span></span>  
  
 <span data-ttu-id="cf853-145">**Uwaga** wywoływania `AcceptChanges` na `DataSet`, `DataTable`, lub `DataRow` spowoduje, że wszystkie `Original` wartości `DataRow` zostaną zastąpione z `Current` wartości `DataRow`.</span><span class="sxs-lookup"><span data-stu-id="cf853-145">**Note** Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` will cause all `Original` values for a `DataRow` to be overwritten with the `Current` values for the `DataRow`.</span></span> <span data-ttu-id="cf853-146">Jeśli wartości pól, które identyfikują wiersze jako unikatowy zostały zmodyfikowane po wywołaniu `AcceptChanges` `Original` wartości będzie już nie pasują do wartości w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="cf853-146">If the field values that identify the row as unique have been modified, after calling `AcceptChanges` the `Original` values will no longer match the values in the data source.</span></span> <span data-ttu-id="cf853-147">`AcceptChanges`jest wywoływana automatycznie dla każdego wiersza podczas wywoływania metody aktualizacji `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="cf853-147">`AcceptChanges` is called automatically for each row during a call to the Update method of a `DataAdapter`.</span></span> <span data-ttu-id="cf853-148">Można zachować oryginalne wartości podczas wywoływania metody aktualizacji przez pierwsze ustawienie `AcceptChangesDuringUpdate` właściwość `DataAdapter` false lub przez tworzenie obsługi zdarzeń dla `RowUpdated` zdarzeń i ustawienie <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> do <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span><span class="sxs-lookup"><span data-stu-id="cf853-148">You can preserve the original values during a call to the Update method by first setting the `AcceptChangesDuringUpdate` property of the `DataAdapter` to false, or by creating an event handler for the `RowUpdated` event and setting the <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> to <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span></span> <span data-ttu-id="cf853-149">Aby uzyskać więcej informacji, zobacz [Scalanie zawartości zestawu danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) i [obsługi zdarzeń element DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="cf853-149">For more information, see [Merging DataSet Contents](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) and [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf853-150">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf853-150">Example</span></span>  
 <span data-ttu-id="cf853-151">Poniższe przykłady przedstawiają sposób przeprowadzania aktualizacji do zmodyfikowanych wierszy, jawnie ustawiając `UpdateCommand` z `DataAdapter` i wywoływanie jej `Update` metody.</span><span class="sxs-lookup"><span data-stu-id="cf853-151">The following examples demonstrate how to perform updates to modified rows by explicitly setting the `UpdateCommand` of a `DataAdapter` and calling its `Update` method.</span></span> <span data-ttu-id="cf853-152">Powiadomienie, że parametr określony w klauzuli WHERE aktualizacji instrukcji jest skonfigurowany do używania `Original` wartość `SourceColumn`.</span><span class="sxs-lookup"><span data-stu-id="cf853-152">Notice that the parameter specified in the WHERE clause of the UPDATE statement is set to use the `Original` value of the `SourceColumn`.</span></span> <span data-ttu-id="cf853-153">Jest to ważne, ponieważ `Current` wartość mogły zostać zmodyfikowane i może nie pasuje do wartości w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="cf853-153">This is important, because the `Current` value may have been modified and may not match the value in the data source.</span></span> <span data-ttu-id="cf853-154">`Original` Wartość jest wartością, którego użyto do wypełnienia `DataTable` ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="cf853-154">The `Original` value is the value that was used to populate the `DataTable` from the data source.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a><span data-ttu-id="cf853-155">Kolumny typu AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="cf853-155">AutoIncrement Columns</span></span>  
 <span data-ttu-id="cf853-156">Jeśli zwiększanie automatycznie kolumn tabel w źródle danych, można wypełnić kolumn z `DataSet` albo przez zwrócenie wartości automatycznego przyrostu jako parametr wyjściowy procedury składowanej i mapowanie do kolumny w tabeli, zwracanie przez automatycznego przyrostu wartości w pierwszym wierszu zestaw zwrócony przez instrukcję SQL lub procedury składowanej lub przy użyciu wyników `RowUpdated` zdarzenie `DataAdapter` do wykonania dodatkowych instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="cf853-156">If the tables from your data source have auto-incrementing columns, you can fill the columns in your `DataSet` either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, by returning the auto-increment value in the first row of a result set returned by a stored procedure or SQL statement, or by using the `RowUpdated` event of the `DataAdapter` to execute an additional SELECT statement.</span></span> <span data-ttu-id="cf853-157">Aby uzyskać więcej informacji i przykład zobacz [pobierania tożsamości lub wartości automatycznie numerowane](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).</span><span class="sxs-lookup"><span data-stu-id="cf853-157">For more information and an example, see [Retrieving Identity or Autonumber Values](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).</span></span>  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a><span data-ttu-id="cf853-158">Kolejność wstawienia, aktualizacje i usunięcia</span><span class="sxs-lookup"><span data-stu-id="cf853-158">Ordering of Inserts, Updates, and Deletes</span></span>  
 <span data-ttu-id="cf853-159">W wielu sytuacjach, w kolejności, w których zmiany wprowadzane za pośrednictwem `DataSet` są wysyłane źródło danych jest ważne.</span><span class="sxs-lookup"><span data-stu-id="cf853-159">In many circumstances, the order in which changes made through the `DataSet` are sent to the data source is important.</span></span> <span data-ttu-id="cf853-160">Na przykład jeśli wartość klucza podstawowego dla istniejącego wiersza jest aktualizowana, a nowy wiersz została dodana do nowej wartości klucza podstawowego jako klucz obcy, należy przetworzyć aktualizacji przed insert.</span><span class="sxs-lookup"><span data-stu-id="cf853-160">For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value as a foreign key, it is important to process the update before the insert.</span></span>  
  
 <span data-ttu-id="cf853-161">Można użyć `Select` metody `DataTable` do zwrócenia `DataRow` tablicy, która odwołuje się tylko wiersze z określonego `RowState`.</span><span class="sxs-lookup"><span data-stu-id="cf853-161">You can use the `Select` method of the `DataTable` to return a `DataRow` array that only references rows with a particular `RowState`.</span></span> <span data-ttu-id="cf853-162">Można następnie przekazać zwróconego `DataRow` tablicy do `Update` metody `DataAdapter` przetworzyć zmodyfikowanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="cf853-162">You can then pass the returned `DataRow` array to the `Update` method of the `DataAdapter` to process the modified rows.</span></span> <span data-ttu-id="cf853-163">Określając podzbiór wierszy, które zostaną zaktualizowane, można kontrolować kolejności przetwarzania wstawienia, aktualizacje i usunięcia.</span><span class="sxs-lookup"><span data-stu-id="cf853-163">By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf853-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf853-164">Example</span></span>  
 <span data-ttu-id="cf853-165">Na przykład poniższy kod zapewnia, że usuniętych wierszy w tabeli są przetworzonych pierwszy, a następnie zaktualizowano wierszy, a następnie wstawionych wierszy.</span><span class="sxs-lookup"><span data-stu-id="cf853-165">For example, the following code ensures that the deleted rows of the table are processed first, then the updated rows, and then the inserted rows.</span></span>  
  
```vb  
Dim table As DataTable = dataSet.Tables("Customers")  
  
' First process deletes.  
dataSet.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.Deleted))  
  
' Next process updates.  
adapter.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.ModifiedCurrent))  
  
' Finally, process inserts.  
dataAdapater.Update(table.Select(Nothing, Nothing, _  
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
  
## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a><span data-ttu-id="cf853-166">Element DataAdapter umożliwia pobieranie i aktualizowanie danych</span><span class="sxs-lookup"><span data-stu-id="cf853-166">Use a DataAdapter to Retrieve and Update Data</span></span>  
 <span data-ttu-id="cf853-167">Element DataAdapter służy do pobierania i aktualizowania danych.</span><span class="sxs-lookup"><span data-stu-id="cf853-167">You can use a DataAdapter to retrieve and update the data.</span></span>  
  
-   <span data-ttu-id="cf853-168">W przykładzie użyto DataAdapter.AcceptChangesDuringFill sklonować w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="cf853-168">The sample uses DataAdapter.AcceptChangesDuringFill to clone the data in the database.</span></span> <span data-ttu-id="cf853-169">Jeśli właściwość jest ustawiona jako wartość false, metoda AcceptChanges nie jest wywoływana podczas wypełniania tabeli i nowo dodanych wierszy są traktowane jako wstawionych wierszy.</span><span class="sxs-lookup"><span data-stu-id="cf853-169">If the property is set as false, AcceptChanges is not called when filling the table, and the newly added rows are treated as inserted rows.</span></span> <span data-ttu-id="cf853-170">Tak próbki używa tych wierszy, aby wstawić nowe wiersze do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cf853-170">So, the sample uses these rows to insert the new rows into the database.</span></span>  
  
-   <span data-ttu-id="cf853-171">Przykłady używa DataAdapter.TableMappings w celu zdefiniowania mapowanie między tabeli źródłowej i elementu DataTable.</span><span class="sxs-lookup"><span data-stu-id="cf853-171">The samples uses DataAdapter.TableMappings to define the mapping between the source table and DataTable.</span></span>  
  
-   <span data-ttu-id="cf853-172">Próbki używa DataAdapter.FillLoadOption, aby określić sposób wypełniania elementu DataTable z DbDataReader.</span><span class="sxs-lookup"><span data-stu-id="cf853-172">The sample uses DataAdapter.FillLoadOption to determine how the adapter fills the DataTable from the DbDataReader.</span></span> <span data-ttu-id="cf853-173">Podczas tworzenia elementu DataTable, możesz tylko zapisywać dane z bazy danych do bieżącej wersji lub wersji oryginalnej przez ustawienie właściwości LoadOption.Upsert lub LoadOption.PreserveChanges.</span><span class="sxs-lookup"><span data-stu-id="cf853-173">When you create a DataTable, you can only write the data from database to the current version or the original version by setting the property as the LoadOption.Upsert or the LoadOption.PreserveChanges.</span></span>  
  
-   <span data-ttu-id="cf853-174">Próbka będzie również zaktualizować tabeli za pomocą DbDataAdapter.UpdateBatchSize do wykonywania operacji wsadowych.</span><span class="sxs-lookup"><span data-stu-id="cf853-174">The sample will also update the table by using DbDataAdapter.UpdateBatchSize to perform batch operations.</span></span>  
  
 <span data-ttu-id="cf853-175">Aby skompilować i uruchomić przykład, musisz utworzyć przykładowa baza danych:</span><span class="sxs-lookup"><span data-stu-id="cf853-175">Before you compile and run the sample, you need to create the sample database:</span></span>  
  
```  
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
  
 <span data-ttu-id="cf853-176">C# i Visual Basic projektów z tym przykładowym kodzie można znaleźć w [przykłady kodu dewelopera](http://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span><span class="sxs-lookup"><span data-stu-id="cf853-176">C# and Visual Basic projects with this code sample can be found on [Developer Code Samples](http://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span></span>  
  
```  
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
      String resetCols = String.Join(",", resetColumns.Select(col => "Max(" + col.ColumnName + ") as " + col.ColumnName));  
  
      String selectString = String.Format("Select {0},{1} from Course Group by {0}", primaryCols, resetCols);  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf853-177">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf853-177">See Also</span></span>  
 [<span data-ttu-id="cf853-178">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="cf853-178">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="cf853-179">Stany wiersza i wersje wiersza</span><span class="sxs-lookup"><span data-stu-id="cf853-179">Row States and Row Versions</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [<span data-ttu-id="cf853-180">Metody AcceptChanges i RejectChanges</span><span class="sxs-lookup"><span data-stu-id="cf853-180">AcceptChanges and RejectChanges</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 [<span data-ttu-id="cf853-181">Scalanie zawartości elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="cf853-181">Merging DataSet Contents</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 [<span data-ttu-id="cf853-182">Pobieranie tożsamości lub wartości automatycznych numerów</span><span class="sxs-lookup"><span data-stu-id="cf853-182">Retrieving Identity or Autonumber Values</span></span>](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 [<span data-ttu-id="cf853-183">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="cf853-183">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
