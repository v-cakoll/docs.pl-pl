---
title: Aktualizowanie źródła danych za pomocą obiektów DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: 9d9eeb93cf0360f321c124bb6bce6ed02a9ea253
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365504"
---
# <a name="updating-data-sources-with-dataadapters"></a>Aktualizowanie źródła danych za pomocą obiektów DataAdapter
`Update` Metody <xref:System.Data.Common.DataAdapter> jest wywoływana, aby rozwiązać zmian z <xref:System.Data.DataSet> do źródła danych. `Update` Metody, takiej jak `Fill` metoda, przyjmuje jako argumenty wystąpienia `DataSet`i opcjonalny <xref:System.Data.DataTable> obiektu lub `DataTable` nazwy. `DataSet` Wystąpienie jest `DataSet` zawiera zmiany, które zostały wprowadzone, i `DataTable` identyfikuje tabeli, z której można pobrać zmiany. Jeśli nie `DataTable` jest określony, pierwszy `DataTable` w `DataSet` jest używany.  
  
 Podczas wywoływania `Update` metody `DataAdapter` analizuje zmiany, które zostały wprowadzone i wykonuje odpowiednie polecenie (INSERT, UPDATE lub DELETE). Gdy `DataAdapter` wykryje zmianę <xref:System.Data.DataRow>, używa <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, lub <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> przetwarzania zmian. Dzięki temu można zmaksymalizować wydajność aplikacji ADO.NET, określając składni polecenia w czasie projektowania i, jeśli to możliwe, przy użyciu procedur składowanych. Musisz jawnie ustawić przed wywołaniem polecenia `Update`. Jeśli `Update` nazywa się i odpowiednie polecenie nie istnieje dla określonej aktualizacji (na przykład nie `DeleteCommand` dla usuniętych wierszy), jest zgłaszany wyjątek.  
  
> [!NOTE]
>  Jeśli używasz procedur składowanych serwera SQL, aby edytować lub usunąć danych przy użyciu `DataAdapter`, upewnij się, że nie używasz SET NOCOUNT ON w definicji procedury składowanej. Powoduje to, że liczba zmodyfikowanych wierszy zwrócił zero, który `DataAdapter` jako konflikt współbieżności. W takim przypadku <xref:System.Data.DBConcurrencyException> zostanie wygenerowany.  
  
 Parametry polecenia mogą być używane do określenia wartości wejściowe i wyjściowe dla instrukcji SQL lub procedurę składowaną dla każdego wiersza zmodyfikowane w `DataSet`. Aby uzyskać więcej informacji, zobacz [parametry element DataAdapter](../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
> [!NOTE]
>  Ważne jest, aby zrozumieć różnicę między usuwanie wiersza w <xref:System.Data.DataTable> i usuwanie wiersza. Podczas wywoływania `Remove` lub `RemoveAt` metody, wiersz jest usuwany natychmiast. Wszystkie odpowiednie wiersze w źródle danych zaplecza nie zostaną zmienione, jeśli następnie przekazać `DataTable` lub `DataSet` do `DataAdapter` i Wywołaj `Update`. Jeśli używasz `Delete` metody wiersz pozostaje w `DataTable` i jest oznaczony do usunięcia. Jeśli następnie przekazać `DataTable` lub `DataSet` do `DataAdapter` i Wywołaj `Update`, odpowiedni wiersz w źródle danych zaplecza zostanie usunięty.  
  
 Jeśli Twoje `DataTable` mapuje lub jest generowany z jednej bazy danych, możesz korzystać z <xref:System.Data.Common.DbCommandBuilder> obiektu w celu automatycznego generowania `DeleteCommand`, `InsertCommand`, i `UpdateCommand` obiektów na `DataAdapter`. Aby uzyskać więcej informacji, zobacz [generowania poleceń CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>Mapuj wartości do zestawu danych za pomocą przetwarzania wsadowego  
 Można kontrolować sposób wartości zwracane ze źródła danych są mapowane z powrotem na `DataTable` po wywołaniu metody aktualizacji `DataAdapter`, za pomocą <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> właściwość <xref:System.Data.Common.DbCommand> obiektu. Przez ustawienie `UpdatedRowSource` jedną z właściwości <xref:System.Data.UpdateRowSource> wartości wyliczenia można kontrolować, czy parametry wyjściowe zwracane przez `DataAdapter` polecenia są ignorowane lub zastosowany do wiersza zmienione w `DataSet`. Można również określić, czy pierwszy zwrócony wiersza (jeśli istnieje) jest stosowana do zmienionych wierszy w `DataTable`.  
  
 W poniższej tabeli opisano różne wartości `UpdateRowSource` wyliczenie i ich wpływu na zachowanie polecenia używane z `DataAdapter`.  
  
|Wyliczenie przetwarzania wsadowego|Opis|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|Parametry wyjściowe jak pierwszy wiersz zestaw wyników zwrócony mogą być mapowane na zmienionych wierszy w `DataSet`.|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Tylko dane w pierwszym wierszu zestaw wyników zwrócony mogą być mapowane na zmienionych wierszy w `DataSet`.|  
|<xref:System.Data.UpdateRowSource.None>|Wszystkie dane wyjściowe są parametry lub wierszy zestawu wyników zwróconego są ignorowane.|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|Tylko parametry wyjściowe można mapować zmienionych wierszy w `DataSet`.|  
  
 `Update` Metoda usuwa zmiany z powrotem do źródła danych; jednak innych klientów zmienił danych w źródle danych od czasu ostatniego wypełniony `DataSet`. Aby odświeżyć Twojej `DataSet` bieżące dane za pomocą `DataAdapter` i `Fill` — metoda. Nowe wiersze zostaną dodane do tabeli, a zaktualizowane informacje zostaną uwzględnione w istniejących wierszy. `Fill` Metoda określa, czy zostanie dodany nowy wiersz lub istniejącego wiersza zostaną zaktualizowane, sprawdzając wartości kluczy podstawowych wierszy w `DataSet` i wierszy zwracanych przez `SelectCommand`. Jeśli `Fill` metody napotka wartość klucza podstawowego dla wiersza w `DataSet` odpowiadającego wartość klucza podstawowego z wiersza wyników zwróconych przez `SelectCommand`, aktualizuje istniejący wiersz z informacjami z wierszy zwracanych przez `SelectCommand`i ustawia <xref:System.Data.DataRow.RowState%2A> istniejącego wiersza do `Unchanged`. Jeśli wiersz zwrócony przez `SelectCommand` ma wartość klucza podstawowego, który nie pasuje do żadnej wartości kluczy podstawowych wierszy w `DataSet`, `Fill` metody dodaje nowy wiersz z `RowState` z `Unchanged`.  
  
> [!NOTE]
>  Jeśli `SelectCommand` zwraca wyniki OUTER JOIN `DataAdapter` nie ustawi `PrimaryKey` wartość powstałe w ten sposób `DataTable`. Należy zdefiniować `PrimaryKey` samodzielnie, aby upewnić się, że zduplikowane wiersze są rozpoznawane poprawnie. Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Do obsługi wyjątków, które mogą wystąpić podczas wywoływania metody `Update` metody, można użyć `RowUpdated` zdarzenia występujące odpowiedzieć na błędy aktualizacji wiersza (zobacz [obsługi zdarzeń element DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), lub możesz ustawić `DataAdapter.ContinueUpdateOnError` do `true` przed wywołaniem `Update`i reagowanie na informacje o błędzie, przechowywane w `RowError` właściwości określonego wiersza po ukończeniu aktualizacji (zobacz [informacje o błędzie wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).  
  
 **Uwaga** wywoływania `AcceptChanges` na `DataSet`, `DataTable`, lub `DataRow` spowoduje, że wszystkie `Original` wartości `DataRow` zostaną zastąpione z `Current` wartości `DataRow`. Jeśli wartości pól, które identyfikują wiersze jako unikatowy zostały zmodyfikowane po wywołaniu `AcceptChanges` `Original` wartości będzie już nie pasują do wartości w źródle danych. `AcceptChanges` jest wywoływana automatycznie dla każdego wiersza podczas wywoływania metody aktualizacji `DataAdapter`. Można zachować oryginalne wartości podczas wywoływania metody aktualizacji przez pierwsze ustawienie `AcceptChangesDuringUpdate` właściwość `DataAdapter` false lub przez tworzenie obsługi zdarzeń dla `RowUpdated` zdarzeń i ustawienie <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> do <xref:System.Data.UpdateStatus.SkipCurrentRow>. Aby uzyskać więcej informacji, zobacz [Scalanie zawartości zestawu danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) i [obsługi zdarzeń element DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="example"></a>Przykład  
 Poniższe przykłady przedstawiają sposób przeprowadzania aktualizacji do zmodyfikowanych wierszy, jawnie ustawiając `UpdateCommand` z `DataAdapter` i wywoływanie jej `Update` metody. Powiadomienie, że parametr określony w klauzuli WHERE aktualizacji instrukcji jest skonfigurowany do używania `Original` wartość `SourceColumn`. Jest to ważne, ponieważ `Current` wartość mogły zostać zmodyfikowane i może nie pasuje do wartości w źródle danych. `Original` Wartość jest wartością, którego użyto do wypełnienia `DataTable` ze źródła danych.  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a>Kolumny typu AutoIncrement  
 Jeśli zwiększanie automatycznie kolumn tabel w źródle danych, można wypełnić kolumn z `DataSet` albo przez zwrócenie wartości automatycznego przyrostu jako parametr wyjściowy procedury składowanej i mapowanie do kolumny w tabeli, zwracanie przez automatycznego przyrostu wartości w pierwszym wierszu zestaw zwrócony przez instrukcję SQL lub procedury składowanej lub przy użyciu wyników `RowUpdated` zdarzenie `DataAdapter` do wykonania dodatkowych instrukcji SELECT. Aby uzyskać więcej informacji i przykład zobacz [pobierania tożsamości lub wartości automatycznie numerowane](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a>Kolejność wstawienia, aktualizacje i usunięcia  
 W wielu sytuacjach, w kolejności, w których zmiany wprowadzane za pośrednictwem `DataSet` są wysyłane źródło danych jest ważne. Na przykład jeśli wartość klucza podstawowego dla istniejącego wiersza jest aktualizowana, a nowy wiersz została dodana do nowej wartości klucza podstawowego jako klucz obcy, należy przetworzyć aktualizacji przed insert.  
  
 Można użyć `Select` metody `DataTable` do zwrócenia `DataRow` tablicy, która odwołuje się tylko wiersze z określonego `RowState`. Można następnie przekazać zwróconego `DataRow` tablicy do `Update` metody `DataAdapter` przetworzyć zmodyfikowanych wierszy. Określając podzbiór wierszy, które zostaną zaktualizowane, można kontrolować kolejności przetwarzania wstawienia, aktualizacje i usunięcia.  
  
## <a name="example"></a>Przykład  
 Na przykład poniższy kod zapewnia, że usuniętych wierszy w tabeli są przetworzonych pierwszy, a następnie zaktualizowano wierszy, a następnie wstawionych wierszy.  
  
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
  
## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a>Element DataAdapter umożliwia pobieranie i aktualizowanie danych  
 Element DataAdapter służy do pobierania i aktualizowania danych.  
  
-   W przykładzie użyto DataAdapter.AcceptChangesDuringFill sklonować w bazie danych. Jeśli właściwość jest ustawiona jako wartość false, metoda AcceptChanges nie jest wywoływana podczas wypełniania tabeli i nowo dodanych wierszy są traktowane jako wstawionych wierszy. Tak próbki używa tych wierszy, aby wstawić nowe wiersze do bazy danych.  
  
-   Przykłady używa DataAdapter.TableMappings w celu zdefiniowania mapowanie między tabeli źródłowej i elementu DataTable.  
  
-   Próbki używa DataAdapter.FillLoadOption, aby określić sposób wypełniania elementu DataTable z DbDataReader. Podczas tworzenia elementu DataTable, możesz tylko zapisywać dane z bazy danych do bieżącej wersji lub wersji oryginalnej przez ustawienie właściwości LoadOption.Upsert lub LoadOption.PreserveChanges.  
  
-   Próbka będzie również zaktualizować tabeli za pomocą DbDataAdapter.UpdateBatchSize do wykonywania operacji wsadowych.  
  
 Aby skompilować i uruchomić przykład, musisz utworzyć przykładowa baza danych:  
  
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
  
 C# i Visual Basic projektów z tym przykładowym kodzie można znaleźć w [przykłady kodu dewelopera](http://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Stany wiersza i wersje wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [Metody AcceptChanges i RejectChanges](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 [Scalanie zawartości elementu DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 [Pobieranie tożsamości lub wartości automatycznych numerów](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
