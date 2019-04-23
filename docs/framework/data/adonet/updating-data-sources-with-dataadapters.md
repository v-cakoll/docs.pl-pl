---
title: Aktualizowanie źródeł danych za pomocą elementów DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: 548e374fbabee57e756d06e5cb56a59f8e97a47c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153598"
---
# <a name="updating-data-sources-with-dataadapters"></a>Aktualizowanie źródeł danych za pomocą elementów DataAdapter
`Update` Metody <xref:System.Data.Common.DataAdapter> jest wywoływana, aby rozwiązać zmian z <xref:System.Data.DataSet> wstecz do źródła danych. `Update` Metody, takiej jak `Fill` metoda, przyjmuje jako argumenty wystąpienie `DataSet`oraz opcjonalny <xref:System.Data.DataTable> obiektu lub `DataTable` nazwy. `DataSet` Wystąpienie jest `DataSet` zawiera zmiany, które zostały wprowadzone, a `DataTable` Określa tabelę, z którego można pobrać zmiany. Jeśli nie `DataTable` jest określony, pierwszy `DataTable` w `DataSet` jest używany.  
  
 Gdy wywołujesz `Update` metody `DataAdapter` analizuje zmiany, które zostały wprowadzone i uruchamia odpowiednie polecenie (INSERT, UPDATE lub DELETE). Gdy `DataAdapter` wykryje zmianę <xref:System.Data.DataRow>, używa ona <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, lub <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> przetworzyć zmiany. Dzięki temu można zmaksymalizować wydajność aplikacji ADO.NET, określając składni polecenia w czasie projektowania i, jeśli jest to możliwe przy użyciu procedur składowanych. Musisz jawnie ustawić polecenia przed wywołaniem `Update`. Jeśli `Update` nosi nazwę i odpowiednie polecenie nie istnieje dla określonej aktualizacji (na przykład nie `DeleteCommand` dla usuniętych wierszy), zgłaszany jest wyjątek.  
  
> [!NOTE]
>  Jeśli używasz procedur składowanych serwera SQL Server, aby edytować lub usunąć dane za pomocą `DataAdapter`, upewnij się, że nie używasz SET NOCOUNT ON w definicji procedury składowanej. Powoduje to, że liczba zmodyfikowanych wierszy zwracane jako zera, które `DataAdapter` interpretuje jako konflikt współbieżności. W takim przypadku <xref:System.Data.DBConcurrencyException> zostanie zgłoszony.  
  
 Parametry polecenia może służyć do określenia wartości wejściowe i wyjściowe dla instrukcji SQL lub procedurę składowaną dla każdego wiersza zmodyfikowane w `DataSet`. Aby uzyskać więcej informacji, zobacz [parametry elementu DataAdapter](../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
> [!NOTE]
>  Należy zrozumieć różnicę między usuwanie wierszy w <xref:System.Data.DataTable> i usuwania wiersza. Gdy wywołujesz `Remove` lub `RemoveAt` metody wiersza jest usuwany natychmiast. Wszystkie odpowiednie wiersze ze źródła danych zaplecza nie zostaną zmienione, jeśli następnie przekażesz `DataTable` lub `DataSet` do `DataAdapter` i wywołać `Update`. Kiedy używasz `Delete` metody wiersz pozostaje w `DataTable` i jest oznaczony do usunięcia. Jeśli następnie przekażesz `DataTable` lub `DataSet` do `DataAdapter` i wywołać `Update`, odpowiedni wiersz w źródle danych zaplecza zostanie usunięty.  
  
 Jeśli Twoje `DataTable` mapuje lub jest generowana z tabeli pojedynczej bazy danych, możesz korzystać z zalet <xref:System.Data.Common.DbCommandBuilder> obiektu w celu automatycznego generowania `DeleteCommand`, `InsertCommand`, i `UpdateCommand` obiektów dla `DataAdapter`. Aby uzyskać więcej informacji, zobacz [Generowanie poleceń za pomocą CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>Mapuj wartości do zestawu danych przy użyciu przetwarzania wsadowego  
 Można kontrolować, jak wartości zwrócone ze źródła danych są mapowane z powrotem na `DataTable` następujące wywołanie do metody aktualizacji `DataAdapter`, za pomocą <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> właściwość <xref:System.Data.Common.DbCommand> obiektu. Ustawiając `UpdatedRowSource` jedną z właściwości <xref:System.Data.UpdateRowSource> wartości wyliczenia można kontrolować, czy parametry wyjściowe zwracane przez `DataAdapter` polecenia są ignorowane lub zastosowane do zmienionych wierszy w `DataSet`. Można również określić, czy pierwszy zwracane wiersza (jeśli istnieje) jest stosowany do zmienionego wiersza w `DataTable`.  
  
 W poniższej tabeli opisano różne wartości `UpdateRowSource` wyliczenie i ich wpływ na zachowanie polecenia używane z `DataAdapter`.  
  
|Wyliczenie przetwarzania wsadowego|Opis|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|Pierwszy wiersz z zestawu wyników zwracanego i parametry wyjściowe można mapować do zmienionego wiersza w `DataSet`.|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Tylko dane w pierwszym wierszu zestaw wyników zwrócony można mapować do zmienionego wiersza w `DataSet`.|  
|<xref:System.Data.UpdateRowSource.None>|Wszystkie dane wyjściowe są parametry lub wiersze zestaw wyników zwrócony są ignorowane.|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|Tylko parametry wyjściowe można mapować do zmienionego wiersza w `DataSet`.|  
  
 `Update` Metoda rozpoznaje zmiany z powrotem do źródła danych; jednak inni klienci mogą zmodyfikowano dane w źródle danych od czasu ostatniego wypełniony `DataSet`. Aby odświeżyć swoje `DataSet` z bieżącymi danymi, użyj `DataAdapter` i `Fill` metody. Nowe wiersze, które zostaną dodane do tabeli, a następnie zaktualizowane informacje zostaną uwzględnione w istniejących wierszy. `Fill` Metoda określa, czy zostanie dodany nowy wiersz, czy istniejący wiersz zostaną zaktualizowane, sprawdzając wartości klucza podstawowego wierszy w `DataSet` i wierszy zwracanych przez `SelectCommand`. Jeśli `Fill` metoda napotka wartość klucza podstawowego dla wiersza w `DataSet` , które odpowiadają wartości klucza podstawowego z wiersza w wynikach zwróconych przez `SelectCommand`, aktualizuje istniejący wiersz z informacjami z wierszy zwróconych przez `SelectCommand`i ustawia <xref:System.Data.DataRow.RowState%2A> istniejącego wiersza, aby `Unchanged`. Jeśli wiersz zwrócony przez `SelectCommand` ma wartość klucza podstawowego, który nie pasuje do żadnej wartości klucza podstawowego wierszy w `DataSet`, `Fill` metoda dodaje nowy wiersz z `RowState` z `Unchanged`.  
  
> [!NOTE]
>  Jeśli `SelectCommand` zwraca wyniki OUTER JOIN `DataAdapter` nie ustawi `PrimaryKey` wartości wynikowe `DataTable`. Należy zdefiniować `PrimaryKey` sobie, aby upewnić się, że zduplikowane wiersze są rozpoznawane prawidłowo. Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Aby obsłużyć wyjątki, które mogą wystąpić podczas wywoływania `Update` metody, można użyć `RowUpdated` zdarzenie, aby reagować na błędy aktualizacji wiersza w miarę ich występowania (zobacz [Obsługa zdarzeń elementu DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), lub możesz ustawić `DataAdapter.ContinueUpdateOnError` do `true` przed wywołaniem `Update`i reagować na informacje o błędzie, przechowywane w `RowError` właściwości określonego wiersza po zakończeniu aktualizacji (zobacz [informacje o błędzie wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).  
  
 **Uwaga** wywoływania `AcceptChanges` na `DataSet`, `DataTable`, lub `DataRow` spowoduje, że wszystkie `Original` wartości `DataRow` zostaną zastąpione przy użyciu `Current` wartości `DataRow`. Jeśli wartości pól, które identyfikują wiersze jako unikatowy zostały zmodyfikowane po wywołaniu `AcceptChanges` `Original` wartości nie będzie już zgodny wartości w źródle danych. `AcceptChanges` jest wywoływana automatycznie dla każdego wiersza podczas wywoływania metody aktualizacji `DataAdapter`. Można zachować oryginalne wartości podczas wywoływania metody aktualizacji przez pierwsze ustawienie `AcceptChangesDuringUpdate` właściwość `DataAdapter` na wartość false lub przez tworzenie programu obsługi zdarzeń dla `RowUpdated` zdarzeń i ustawienie <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> do <xref:System.Data.UpdateStatus.SkipCurrentRow>. Aby uzyskać więcej informacji, zobacz [Scalanie zawartości elementu DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) i [Obsługa zdarzeń elementu DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano, jak przeprowadzić aktualizacje zmodyfikowanych wierszy poprzez jawne ustawienie `UpdateCommand` z `DataAdapter` i wywoływania jego `Update` metody. Zwróć uwagę, że parametr określony w klauzuli WHERE aktualizacji instrukcji jest skonfigurowany do używania `Original` wartość `SourceColumn`. Jest to ważne, ponieważ `Current` wartości mogły zostać zmodyfikowane i może nie być zgodna wartość w źródle danych. `Original` Wartość jest wartością, który został użyty do wypełniania `DataTable` ze źródła danych.  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a>Kolumn typu AutoIncrement  
 Tabele ze źródła danych ma kolumn o wartości auto, możesz wpisać kolumny w swojej `DataSet` albo przez zwrócenie wartości automatycznego przyrostu jako parametru wyjściowego procedury składowanej i mapowanie do kolumny w tabeli, zwracanie przez automatycznego przyrostu wartości w pierwszym wierszu zestawu zwrócone przez procedurę składowaną lub instrukcji SQL lub za pomocą wyników `RowUpdated` zdarzenia `DataAdapter` wykonywanie dodatkowych instrukcji SELECT. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [pobieranie tożsamości lub wartości automatycznych numerów](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a>Kolejność wstawiania, aktualizacji i usuwania  
 W wielu sytuacjach, kolejność, w którym zmiany wprowadzone za pomocą `DataSet` są wysyłane do danych źródła jest ważne. Na przykład jeśli wartość klucza podstawowego dla istniejącego wiersza jest aktualizowana, a nowy wiersz został dodany z kluczem obcym nowe wartości klucza podstawowego, jest ważne, aby przetworzyć aktualizacji przed insert.  
  
 Możesz użyć `Select` metody `DataTable` do zwrócenia `DataRow` tablica, która odwołuje się tylko do wierszy z określonym `RowState`. Możesz następnie przekazać zwracanego `DataRow` tablicy do `Update` metody `DataAdapter` do przetworzenia zmodyfikowanych wierszy. Określając podzestawu wierszy, które mają być aktualizowane, można kontrolować kolejności przetwarzania wstawiania, aktualizacji i usuwania.  
  
## <a name="example"></a>Przykład  
 Na przykład poniższy kod zapewnia, że usunięte wiersze w tabeli są przetwarzania pierwszego, a następnie zaktualizowane wiersze i wstawione wiersze.  
  
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
  
## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a>Użyj elementu DataAdapter pobierania i aktualizowania danych  
 Element DataAdapter służy do pobierania i aktualizowania danych.  
  
-   W przykładzie użyto DataAdapter.AcceptChangesDuringFill się klonowanie danych w bazie danych. Jeśli właściwość została ustawiona jako wartość false, metoda AcceptChanges nie jest wywoływana, gdy wypełnianie tabeli, a nowo dodane wiersze są traktowane jako wstawione wiersze. Tak w przykładzie użyto tych wierszy, aby wstawić nowe wiersze do bazy danych.  
  
-   Przykłady używa DataAdapter.TableMappings do definiowania mapowanie między tabelą źródłową i DataTable.  
  
-   W przykładzie użyto DataAdapter.FillLoadOption, aby określić sposobu wypełniania elementu DataTable z obiekt DbDataReader. Podczas tworzenia elementu DataTable możesz tylko zapisywać dane z bazy danych bieżącej wersji lub wersji oryginalnej, ustawiając właściwość jako LoadOption.Upsert lub LoadOption.PreserveChanges.  
  
-   Próbka będzie również zaktualizować tabeli przy użyciu DbDataAdapter.UpdateBatchSize do wykonywania operacji wsadowych.  
  
 Aby skompilować i uruchomić przykład, musisz utworzyć przykładowej bazy danych:  
  
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
  
 Projekty języka C# i Visual Basic z tego przykładu kodu można znaleźć na [Developer Code Samples](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).  
  
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
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
