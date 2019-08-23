---
title: Aktualizowanie źródeł danych za pomocą elementów DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: 2b7d6ac6022da793b90b5447062ceac82cc7290c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965201"
---
# <a name="updating-data-sources-with-dataadapters"></a>Aktualizowanie źródeł danych za pomocą elementów DataAdapter
Metoda jest wywoływana ,<xref:System.Data.DataSet> aby rozwiązać zmiany z powrotem do źródła danych. `Update` <xref:System.Data.Common.DataAdapter> Metoda `Update` , taka `Fill` jak metoda, przyjmuje jako argumenty wystąpienia a `DataSet`i opcjonalnego <xref:System.Data.DataTable> obiektu lub `DataTable` nazwy. Wystąpienie to zawiera wprowadzone zmiany i `DataTable` identyfikuje tabelę, z której mają zostać pobrane zmiany. `DataSet` `DataSet` Jeśli nie `DataTable` jest określony, zostanie użyta pierwsza `DataSet` `DataTable` z.  
  
 Po wywołaniu `Update` metody `DataAdapter` , analizuje wprowadzone zmiany i wykonuje odpowiednie polecenie (INSERT, Update lub Delete). <xref:System.Data.DataRow> <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>Gdy napotka zmiany, używa ,<xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> lub<xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A>doprzetwarzaniazmiany. `DataAdapter` Pozwala to zmaksymalizować wydajność aplikacji ADO.NET przez określenie składni polecenia w czasie projektowania i, jeśli to możliwe, za pomocą procedur składowanych. Należy jawnie ustawić polecenia przed wywołaniem `Update`. Jeśli `Update` jest wywoływana i odpowiednie polecenie nie istnieje dla określonej aktualizacji (na przykład nie `DeleteCommand` dla usuniętych wierszy), zgłaszany jest wyjątek.  
  
> [!NOTE]
> Jeśli używasz SQL Server procedur składowanych do edytowania lub usuwania danych przy użyciu programu `DataAdapter`, upewnij się, że w definicji procedury składowanej nie używasz opcji SET NOCOUNT on. Powoduje to, że liczba zwracanych wierszy jest równa zero, `DataAdapter` która interpretuje jako konflikt współbieżności. W takim przypadku <xref:System.Data.DBConcurrencyException> zostanie zgłoszone zdarzenie.  
  
 Parametry polecenia mogą służyć do określania wartości wejściowych i wyjściowych dla instrukcji SQL lub procedury składowanej dla każdego zmodyfikowanego wiersza w `DataSet`. Aby uzyskać więcej informacji, zobacz [DataAdapter Parameters](../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
> [!NOTE]
> Ważne jest, aby zrozumieć różnicę między usunięciem wiersza w <xref:System.Data.DataTable> a i usunięciem wiersza. Gdy wywołasz `Remove` metodę lub `RemoveAt` , wiersz zostanie natychmiast usunięty. Nie wpłynie to na wszystkie odpowiadające im wiersze w `DataTable` źródle danych zaplecza, `DataAdapter` a następnie `DataSet` do wywołania `Update`i. Gdy używasz `Delete` metody, wiersz pozostaje `DataTable` w i jest oznaczony do usunięcia. Jeśli następnie przekażesz `DataTable` wywołanie `DataSet` lub`Update`do `DataAdapter` i, odpowiadający mu wiersz w źródle danych zaplecza zostanie usunięty.  
  
 `UpdateCommand` `DeleteCommand` <xref:System.Data.Common.DbCommandBuilder> `DataAdapter` `InsertCommand`Jeśli mapowania do lub są generowane na podstawie pojedynczej tabeli bazy danych, można skorzystać z obiektu, aby automatycznie generować obiekty, i. `DataTable` Aby uzyskać więcej informacji, zobacz [Generowanie poleceń z CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>Mapowanie wartości do zestawu danych za pomocą UpdatedRowSource  
 Można kontrolować sposób `DataAdapter`, w jaki wartości zwracane ze źródła danych są mapowane z powrotem do `DataTable` następującego wywołania metody Update w, <xref:System.Data.Common.DbCommand> przy użyciu <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> właściwości obiektu. Ustawiając `UpdatedRowSource` właściwość na jedną <xref:System.Data.UpdateRowSource> z wartości wyliczenia, można kontrolować, czy parametry `DataAdapter` wyjściowe zwracane przez polecenia są ignorowane `DataSet`czy stosowane do zmienionych wierszy w. Można również określić, czy pierwszy zwracany wiersz (jeśli istnieje) jest stosowany do zmienionego wiersza w `DataTable`.  
  
 W poniższej tabeli opisano różne wartości `UpdateRowSource` wyliczania i ich wpływ na zachowanie polecenia użytego `DataAdapter`z.  
  
|UpdatedRowSource, Wyliczenie|Opis|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|Zarówno parametry wyjściowe, jak i pierwszy wiersz zwracanego zestawu wyników mogą być zamapowane do zmienionego wiersza w `DataSet`.|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Tylko dane z pierwszego wiersza zwróconego zestawu wyników mogą być mapowane do zmienionego wiersza w `DataSet`.|  
|<xref:System.Data.UpdateRowSource.None>|Wszystkie parametry wyjściowe lub wiersze zwróconego zestawu wyników są ignorowane.|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|Tylko parametry wyjściowe mogą być mapowane do zmienionego wiersza w `DataSet`.|  
  
 Metoda rozwiązuje zmiany z powrotem do źródła danych, ale inni klienci mogą modyfikować dane w źródle danych od czasu ostatniego `DataSet`wypełnienia. `Update` Aby odświeżyć `DataSet` dane przy użyciu bieżących danych, `DataAdapter` Użyj `Fill` metody i. Nowe wiersze zostaną dodane do tabeli, a zaktualizowane informacje zostaną dołączone do istniejących wierszy. Metoda określa, czy nowy wiersz zostanie dodany, czy istniejący wiersz zostanie zaktualizowany poprzez sprawdzenie wartości klucza podstawowego wierszy `DataSet` w i wierszy zwracanych przez `SelectCommand`. `Fill` Jeśli metoda napotka wartość klucza podstawowego dla wiersza `DataSet` w, który dopasowuje wartość klucza podstawowego z wiersza w wynikach zwróconych przez `SelectCommand`, aktualizuje istniejący wiersz o informacje z wiersza zwróconego przez `Fill` `SelectCommand`i ustawia <xref:System.Data.DataRow.RowState%2A> istniejący wiersz na `Unchanged`. `SelectCommand` Jeśli wiersz zwrócony przez ma wartość klucza podstawowego, która nie pasuje do żadnej wartości klucza podstawowego wierszy `DataSet`w, `Fill` `Unchanged`Metoda dodaje nowy wiersz z `RowState` .  
  
> [!NOTE]
> Jeśli zwraca wyniki sprzężenia zewnętrznego `DataAdapter` , nie ustawi `PrimaryKey` wartości wynikowej `DataTable`. `SelectCommand` Należy zdefiniować siebie, `PrimaryKey` aby upewnić się, że zduplikowane wiersze są poprawnie rozpoznawane. Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Aby obsłużyć wyjątki, które mogą wystąpić `Update` podczas wywoływania metody, można `RowUpdated` użyć zdarzenia w celu reagowania na błędy aktualizacji wierszy w miarę ich występowania (zobacz [Obsługa zdarzeń DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)) lub `DataAdapter.ContinueUpdateOnError` można `true` ustawić na przed Wywoływanie `Update`i reagowanie na informacje o błędzie przechowywane `RowError` we właściwości określonego wiersza po zakończeniu aktualizacji (zobacz [Informacje o błędzie wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).  
  
 **Uwaga** `AcceptChanges` Wywołanieelementu`DataRow` `Current` `DataRow`,, lub spowoduje zastąpienie wszystkich`Original` wartości w celu zastąpienia wartościami dla. `DataTable` `DataSet` `DataRow` Jeśli wartości pól, które identyfikują wiersz jako unikatowy, zostały zmodyfikowane, po wywołaniu `AcceptChanges` `Original` wartości nie będą już zgodne z wartościami w źródle danych. `AcceptChanges`jest wywoływana automatycznie dla każdego wiersza w trakcie wywołania metody `DataAdapter`Update. Oryginalne wartości można zachować podczas wywołania metody Update, najpierw ustawiając `AcceptChangesDuringUpdate` Właściwość `DataAdapter` na false lub tworząc procedurę obsługi zdarzeń dla `RowUpdated` zdarzenia i ustawiając wartość <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> na <xref:System.Data.UpdateStatus.SkipCurrentRow>. Aby uzyskać więcej informacji, zobacz [scalanie zawartości zestawu danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) i [Obsługa zdarzeń DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano, jak wykonać aktualizacje modyfikowanych wierszy, jawnie ustawiając `UpdateCommand` wartość `DataAdapter` a i wywołując jej `Update` metodę. Należy zauważyć, że parametr określony w klauzuli WHERE instrukcji Update jest ustawiony tak, aby używał `Original` wartości. `SourceColumn` Jest to ważne, ponieważ `Current` wartość mogła zostać zmodyfikowana i może nie być zgodna z wartością w źródle danych. Wartość jest wartością użytą do `DataTable` wypełnienia ze źródła danych. `Original`  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a>Kolumny AutoIncrement  
 Jeśli tabele ze źródła danych zawierają autoprzyrostowe kolumny, można wypełnić kolumny w `DataSet` elemencie przez zwrócenie wartości autoprzyrostu jako parametru wyjściowego procedury składowanej i mapowania do kolumny w tabeli, zwracając element wartość AutoIncrement w pierwszym wierszu zestawu wyników zwrócone przez procedurę składowaną lub instrukcję SQL albo za pomocą `RowUpdated` zdarzenia `DataAdapter` do wykonania dodatkowej instrukcji SELECT. Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [pobieranie tożsamości lub wartości AutoNumber](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a>Porządkowanie operacji wstawiania, aktualizacji i usuwania  
 W wielu przypadkach kolejność, w jakiej zmiany wprowadzane przez `DataSet` program są wysyłane do źródła danych, jest ważna. Na przykład jeśli wartość klucza podstawowego dla istniejącego wiersza zostanie zaktualizowana, a nowy wiersz został dodany z nową wartością klucza podstawowego jako klucz obcy, ważne jest, aby przetworzyć aktualizację przed wstawieniem.  
  
 Można użyć `Select` metody, `DataTable` aby zwrócić `DataRow` tablicę, która odwołuje się tylko do wierszy z konkretną `RowState`. Następnie można przekazać zwróconą `DataRow` tablicę `Update` do metody `DataAdapter` w celu przetworzenia zmodyfikowanych wierszy. Określając podzestaw wierszy do zaktualizowania, można kontrolować kolejność, w której przetwarzane są operacje INSERT, Update i usunięć.  
  
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

- [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Stany wiersza i wersje wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)
- [Metody AcceptChanges i RejectChanges](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [Scalanie zawartości elementu DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)
- [Pobieranie tożsamości lub wartości automatycznych numerów](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
