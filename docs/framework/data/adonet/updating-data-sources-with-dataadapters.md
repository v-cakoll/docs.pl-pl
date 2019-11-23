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
# <a name="updating-data-sources-with-dataadapters"></a>Aktualizowanie źródeł danych za pomocą elementów DataAdapter

Metoda `Update` <xref:System.Data.Common.DataAdapter> jest wywoływana, aby rozwiązać zmiany z <xref:System.Data.DataSet> z powrotem do źródła danych. Metoda `Update`, taka jak Metoda `Fill`, przyjmuje jako argumenty wystąpienie `DataSet`oraz opcjonalny obiekt <xref:System.Data.DataTable> lub `DataTable` nazwę. Wystąpienie `DataSet` jest `DataSet`, który zawiera wprowadzone zmiany, a `DataTable` określa tabelę, z której mają zostać pobrane zmiany. Jeśli `DataTable` nie zostanie określona, zostanie użyty pierwszy `DataTable` w `DataSet`.

Gdy wywołasz metodę `Update`, `DataAdapter` analizuje wprowadzone zmiany i wykonuje odpowiednie polecenie (INSERT, UPDATE lub DELETE). Gdy `DataAdapter` napotka zmianę <xref:System.Data.DataRow>, do przetworzenia zmiany używa <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>lub <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A>. Pozwala to zmaksymalizować wydajność aplikacji ADO.NET przez określenie składni polecenia w czasie projektowania i, jeśli to możliwe, za pomocą procedur składowanych. Przed wywołaniem `Update`należy jawnie ustawić te polecenia. Jeśli `Update` jest wywoływana i nie istnieje odpowiednie polecenie dla określonej aktualizacji (na przykład brak `DeleteCommand` dla usuniętych wierszy), zgłaszany jest wyjątek.

> [!NOTE]
> Jeśli używasz SQL Server procedur składowanych do edytowania lub usuwania danych przy użyciu `DataAdapter`, upewnij się, że nie używasz opcji SET NOCOUNT ON w definicji procedury składowanej. Powoduje to, że liczba zwracanych wierszy jest równa zero, która `DataAdapter` interpretuje jako konflikt współbieżności. W tym zdarzeniu zostanie zgłoszony <xref:System.Data.DBConcurrencyException>.

Parametry polecenia mogą służyć do określania wartości wejściowych i wyjściowych dla instrukcji SQL lub procedury składowanej dla każdego zmodyfikowanego wiersza w `DataSet`. Aby uzyskać więcej informacji, zobacz [DataAdapter Parameters](dataadapter-parameters.md).

> [!NOTE]
> Ważne jest, aby zrozumieć różnicę między usunięciem wiersza w <xref:System.Data.DataTable> i usunięciem wiersza. Po wywołaniu metody `Remove` lub `RemoveAt` wiersz jest usuwany natychmiast. Jeśli przekazanie `DataTable` lub `DataSet` do `DataAdapter` i wywołań `Update`nie wpłynie na odpowiednie wiersze w źródle danych zaplecza. Gdy używasz metody `Delete`, wiersz pozostanie w `DataTable` i zostanie oznaczony do usunięcia. Po przejściu `DataTable` lub `DataSet` do `DataAdapter` i wywołań `Update`, odpowiedni wiersz w źródle danych zaplecza zostanie usunięty.

Jeśli `DataTable` są mapowane na lub generowane na podstawie pojedynczej tabeli bazy danych, można skorzystać z obiektu <xref:System.Data.Common.DbCommandBuilder>, aby automatycznie generować obiekty `DeleteCommand`, `InsertCommand`i `UpdateCommand` dla `DataAdapter`. Aby uzyskać więcej informacji, zobacz [Generowanie poleceń z CommandBuilders](generating-commands-with-commandbuilders.md).

## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>Mapowanie wartości do zestawu danych za pomocą UpdatedRowSource

Można kontrolować sposób, w jaki wartości zwracane ze źródła danych są mapowane z powrotem do `DataTable` następującego po wywołaniu metody Update `DataAdapter`, przy użyciu właściwości <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> obiektu <xref:System.Data.Common.DbCommand>. Ustawiając właściwość `UpdatedRowSource` na jedną z wartości wyliczenia <xref:System.Data.UpdateRowSource>, można kontrolować, czy parametry wyjściowe zwracane przez polecenia `DataAdapter` są ignorowane lub stosowane do zmienionych wierszy w `DataSet`. Można również określić, czy pierwszy zwracany wiersz (jeśli istnieje) jest stosowany do zmienionego wiersza w `DataTable`.

W poniższej tabeli opisano różne wartości `UpdateRowSource` Wyliczenie i ich wpływ na zachowanie polecenia użytego z `DataAdapter`.

|UpdatedRowSource, Wyliczenie|Opis|
|----------------------------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|Zarówno parametry wyjściowe, jak i pierwszy wiersz zwracanego zestawu wyników mogą zostać zamapowane na zmieniony wiersz w `DataSet`.|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Tylko dane z pierwszego wiersza zwróconego zestawu wyników mogą zostać zamapowane na zmieniony wiersz w `DataSet`.|
|<xref:System.Data.UpdateRowSource.None>|Wszystkie parametry wyjściowe lub wiersze zwróconego zestawu wyników są ignorowane.|
|<xref:System.Data.UpdateRowSource.OutputParameters>|Tylko parametry wyjściowe mogą być mapowane do zmienionego wiersza w `DataSet`.|

Metoda `Update` rozwiązuje zmiany z powrotem do źródła danych; Jednak inni klienci mogą modyfikować dane w źródle danych od czasu ostatniego wypełnienia `DataSet`. Aby odświeżyć `DataSet` przy użyciu bieżących danych, użyj metody `DataAdapter` i `Fill`. Nowe wiersze zostaną dodane do tabeli, a zaktualizowane informacje zostaną dołączone do istniejących wierszy. Metoda `Fill` określa, czy nowy wiersz zostanie dodany, czy istniejący wiersz zostanie zaktualizowany poprzez sprawdzenie wartości klucza podstawowego wierszy w `DataSet` i wierszy zwracanych przez `SelectCommand`. Jeśli `Fill` Metoda napotka wartość klucza podstawowego dla wiersza w `DataSet`, który dopasowuje wartość klucza podstawowego z wiersza w wynikach zwróconych przez `SelectCommand`, aktualizuje istniejący wiersz o informacje z wiersza zwrócone przez `SelectCommand` i ustawia <xref:System.Data.DataRow.RowState%2A> istniejącego wiersza do `Unchanged`. Jeśli wiersz zwrócony przez `SelectCommand` ma wartość klucza podstawowego, która nie pasuje do żadnej wartości klucza podstawowego wierszy w `DataSet`, Metoda `Fill` dodaje nowy wiersz z `RowState` `Unchanged`.

> [!NOTE]
> Jeśli `SelectCommand` zwraca wyniki SPRZĘŻENIa zewnętrznego, `DataAdapter` nie ustawi `PrimaryKey` wartości dla wynikowego `DataTable`. Należy zdefiniować `PrimaryKey` samodzielnie, aby upewnić się, że zduplikowane wiersze są poprawnie rozpoznawane. Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](./dataset-datatable-dataview/defining-primary-keys.md).

Aby obsłużyć wyjątki, które mogą wystąpić podczas wywoływania metody `Update`, można użyć zdarzenia `RowUpdated`, aby odpowiedzieć na błędy aktualizacji wierszy w miarę ich występowania (zobacz [Obsługa zdarzeń DataAdapter](handling-dataadapter-events.md)), lub ustawić `DataAdapter.ContinueUpdateOnError` na `true` przed wywołaniem `Update`, a następnie odpowiedzieć na informacje o błędzie przechowywane we właściwości `RowError` określonego wiersza po zakończeniu aktualizacji (zobacz [Informacje o błędzie wiersza](./dataset-datatable-dataview/row-error-information.md)).

> [!NOTE]
> Wywoływanie `AcceptChanges` na `DataSet`, `DataTable`lub `DataRow` spowoduje zastąpienie wszystkich wartości `Original` `DataRow`, które mają zostać zastąpione wartościami `Current` `DataRow`. Jeśli wartości pól, które identyfikują wiersz jako unikatowy, zostały zmodyfikowane, po wywołaniu `AcceptChanges` wartości `Original` nie będą już zgodne z wartościami w źródle danych. `AcceptChanges` jest automatycznie wywoływana dla każdego wiersza w trakcie wywołania metody Update `DataAdapter`. Oryginalne wartości można zachować podczas wywołania metody Update, najpierw ustawiając właściwość `AcceptChangesDuringUpdate` `DataAdapter` na false lub przez utworzenie programu obsługi zdarzeń dla zdarzenia `RowUpdated` i ustawienie <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> na <xref:System.Data.UpdateStatus.SkipCurrentRow>. Aby uzyskać więcej informacji, zobacz [scalanie zawartości zestawu danych](./dataset-datatable-dataview/merging-dataset-contents.md) i [Obsługa zdarzeń DataAdapter](handling-dataadapter-events.md).

## <a name="example"></a>Przykład

W poniższych przykładach pokazano, jak wykonać aktualizacje zmodyfikowanych wierszy, jawnie ustawiając `UpdateCommand` `DataAdapter` i wywołując metodę `Update`. Należy zauważyć, że parametr określony w klauzuli WHERE instrukcji UPDATE jest ustawiony tak, aby używał wartości `Original` `SourceColumn`. Jest to ważne, ponieważ wartość `Current` mogła zostać zmodyfikowana i może nie być zgodna z wartością w źródle danych. Wartość `Original` to wartość użyta do wypełnienia `DataTable` ze źródła danych.

[!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]

## <a name="autoincrement-columns"></a>Kolumny AutoIncrement

Jeśli tabele ze źródła danych mają funkcję autozwiększania wartości kolumn, kolumny w `DataSet` można wypełnić przez zwrócenie wartości autoprzyrostu jako parametru wyjściowego procedury składowanej i mapowania, które należy do kolumny w tabeli, zwracając wartość autoprzyrostu z pierwszego wiersza zestawu wyników zwróconego przez procedurę składowaną lub instrukcję SQL lub używając zdarzenia `RowUpdated` `DataAdapter` w celu wykonania dodatkowej instrukcji SELECT. Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [pobieranie tożsamości lub wartości AutoNumber](retrieving-identity-or-autonumber-values.md).

## <a name="ordering-of-inserts-updates-and-deletes"></a>Porządkowanie operacji wstawiania, aktualizacji i usuwania

W wielu przypadkach kolejność, w jakiej zmiany wprowadzane przez `DataSet` są wysyłane do źródła danych, jest ważna. Na przykład jeśli wartość klucza podstawowego dla istniejącego wiersza zostanie zaktualizowana, a nowy wiersz został dodany z nową wartością klucza podstawowego jako klucz obcy, ważne jest, aby przetworzyć aktualizację przed wstawieniem.

Można użyć metody `Select` `DataTable`, aby zwrócić tablicę `DataRow`, która odwołuje się tylko do wierszy z określoną `RowState`ą. Następnie można przekazać zwróconą tablicę `DataRow` do metody `Update` `DataAdapter` w celu przetworzenia zmodyfikowanych wierszy. Określając podzestaw wierszy do zaktualizowania, można kontrolować kolejność, w której przetwarzane są operacje INSERT, Update i usunięć.

## <a name="example"></a>Przykład

Na przykład poniższy kod gwarantuje, że usunięte wiersze tabeli są przetwarzane jako pierwsze, a następnie zaktualizowane wiersze, a następnie wstawione wiersze.

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

## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a>Pobieranie i aktualizowanie danych przy użyciu elementu DataAdapter

Możesz użyć elementu DataAdapter, aby pobrać i zaktualizować dane.

- Przykład używa DataAdapter. AcceptChangesDuringFill do klonowania danych w bazie danych. Jeśli właściwość jest ustawiona na wartość false, Metoda AcceptChanges nie jest wywoływana podczas wypełniania tabeli, a nowo dodane wiersze są traktowane jako wstawione wiersze. Dlatego przykład używa tych wierszy do wstawienia nowych wierszy do bazy danych.

- Przykłady używają klasy DataAdapter. TableMappings do definiowania mapowania między tabelą źródłową i DataTable.

- Przykład używa DataAdapter. FillLoadOption, aby określić, w jaki sposób karta wypełnia DataTable z elementu DbDataReader. Podczas tworzenia elementu DataTable można zapisać tylko dane z bazy danych do bieżącej wersji lub oryginalnej wersji, ustawiając właściwość jako LoadOption. upsert lub LoadOption. PreserveChanges.

- Przykład spowoduje również zaktualizowanie tabeli przy użyciu DbDataAdapter. UpdateBatchSize do wykonywania operacji wsadowych.

Przed skompilowaniem i uruchomieniem przykładu należy utworzyć przykładową bazę danych:

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

C#Visual Basic projekty z tym przykładem kodu można znaleźć na przykładach [kodu dewelopera](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).

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

## <a name="see-also"></a>Zobacz także

- [Elementy DataAdapter i DataReaders](dataadapters-and-datareaders.md)
- [Stany wiersza i wersje wiersza](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [Metody AcceptChanges i RejectChanges](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [Scalanie zawartości elementu DataSet](./dataset-datatable-dataview/merging-dataset-contents.md)
- [Pobieranie tożsamości lub wartości automatycznych numerów](retrieving-identity-or-autonumber-values.md)
- [Omówienie ADO.NET](ado-net-overview.md)
