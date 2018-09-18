---
title: Pobieranie tożsamości lub wartości automatycznych numerów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6b7f9cb-81be-44e1-bb94-56137954876d
ms.openlocfilehash: ca739f703267f27932ec7450a59d7f4afaffd64b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45972601"
---
# <a name="retrieving-identity-or-autonumber-values"></a>Pobieranie tożsamości lub wartości automatycznych numerów
Klucz podstawowy w relacyjnej bazie danych jest kolumna lub połączenie kolumn, które zawsze zawierać unikatowe wartości. Wartość klucza podstawowego, wiedząc, umożliwia Znajdź wiersz, który go zawiera. Tworzenie automatycznego przyrostu o wartości kolumn, które mogą być oznaczone jako klucze podstawowe obsługują aparatów relacyjnych baz danych, takich jak SQL Server, Oracle i Microsoft Access/Jet. Te wartości są generowane przez serwer w miarę dodawania wierszy do tabeli. W programie SQL Server Ustaw właściwości tożsamości kolumny, Oracle, należy utworzyć sekwencję, a w programie Microsoft Access utworzyć automatycznie numerowane kolumny.  
  
 A <xref:System.Data.DataColumn> może również służyć do generowania wartości automatycznie zwiększającej się wartości, ustawiając <xref:System.Data.DataColumn.AutoIncrement%2A> właściwości na wartość true. Jednak może się to zakończyć ze zduplikowanymi wartościami w osobnych wystąpień <xref:System.Data.DataTable>, jeśli wiele aplikacji klienckich niezależnie generują wartości automatycznie zwiększającej się wartości. Serwer generowania wartości automatycznie zwiększającą eliminuje konflikty, dzięki czemu każdy użytkownik pobrać wygenerowaną wartość dla każdego wiersza wstawiono.  
  
 Podczas wywoływania `Update` metody `DataAdapter`, baza danych może wysyłać dane do aplikacji ADO.NET jako parametry wyjściowe lub jako pierwszy rekord zwróconego zestawu wyników instrukcji SELECT, wykonywane w tej samej partii jako instrukcji INSERT. ADO.NET może pobrać te wartości i zaktualizuj odpowiednie kolumny w <xref:System.Data.DataRow> aktualizowana.  
  
 Niektóre aparaty bazy danych, takich jak aparat bazy danych Microsoft Jet dostępu nie obsługują parametrów wyjściowych i nie może przetworzyć wielu instrukcji w jednej partii. Podczas pracy z aparatu bazy danych Jet, można pobrać wartość automatycznie numerowane generowane dla wstawionego wiersza, wykonując osobne polecenie SELECT w obsłudze zdarzeń dla `RowUpdated` zdarzenia `DataAdapter`.  
  
> [!NOTE]
>  Alternatywa dla użycia automatyczne zwiększanie wartości jest użycie <xref:System.Guid.NewGuid%2A> metody <xref:System.Guid> obiektu umożliwiającą wygenerowanie identyfikatora GUID lub Unikatowy identyfikator globalny, na komputerze klienckim, który można skopiować do serwera jako wstawieniu każdego nowego wiersza. `NewGuid` Metoda generuje 16-bajtową wartość binarna, która jest tworzona przy użyciu algorytmu, który zapewnia wysokie prawdopodobieństwo wartość nie będzie można zduplikować. W bazie danych programu SQL Server, identyfikator GUID jest przechowywany w `uniqueidentifier` kolumnę, która programu SQL Server może automatycznie generować za pomocą instrukcji języka Transact-SQL `NEWID()` funkcji. Przy użyciu identyfikatora GUID jako klucz podstawowy może niekorzystnie wpłynąć na wydajność. Program SQL Server zapewnia obsługę `NEWSEQUENTIALID()` funkcji, która generuje sekwencyjny identyfikatora GUID, nie musi być globalnie unikatowa, ale które mogą być indeksowane wydajniej.  
  
## <a name="retrieving-sql-server-identity-column-values"></a>Pobieranie wartości kolumny tożsamości serwera SQL  
 Podczas pracy z programem Microsoft SQL Server, można utworzyć procedurę przechowywaną z parametru wyjściowego do zwrócenia wartości tożsamości dla wstawionego wiersza. W poniższej tabeli opisano trzy funkcje języka Transact-SQL w programie SQL Server, który może służyć do pobierania wartości w kolumnach tożsamości.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|SCOPE_IDENTITY|Zwraca ostatnią wartość tożsamości w bieżącym zakresie wykonywania. SCOPE_IDENTITY jest zalecane w przypadku większości scenariuszy.|  
|@@IDENTITY|Zawiera ostatnią wartość tożsamości wygenerowanego w dowolnej tabeli w bieżącej sesji. @@IDENTITY mogą mieć wpływ wyzwalaczy i mogą nie zwracać wartości tożsamości, których oczekujesz.|  
|IDENT_CURRENT|Zwraca ostatnią wartość tożsamości wygenerowanego dla określonej tabeli w dowolnej sesji i dowolnego zakresu.|  
  
 Następujące procedury składowanej pokazano, jak wstawić nowy wiersz do **kategorie** tabeli i użyj parametru wyjściowego, aby zwrócić wartość tożsamości wygenerowane przez funkcję SCOPE_IDENTITY() języka Transact-SQL.  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
```  
  
 Następnie można określić procedurę składowaną jako źródło <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> z <xref:System.Data.SqlClient.SqlDataAdapter> obiektu. <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> Właściwość <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> musi być równa <xref:System.Data.CommandType.StoredProcedure>. Dane wyjściowe tożsamości jest pobierana, tworząc <xref:System.Data.SqlClient.SqlParameter> zawierający <xref:System.Data.ParameterDirection> z <xref:System.Data.ParameterDirection.Output>. Podczas `InsertCommand` jest przetwarzany, wartość tożsamości automatycznie zwiększana został zwrócony, a umieszczone w **CategoryID** kolumnę bieżącego wiersza. Jeśli ustawisz <xref:System.Data.SqlClient.SqlCommand.UpdatedRowSource%2A> właściwości polecenia insert do `UpdateRowSource.OutputParameters` lub `UpdateRowSource.Both`.  
  
 Jeśli polecenia insert wykonuje plik wsadowy, który zawiera zarówno w instrukcji INSERT, jak i w instrukcji SELECT, która zwraca nową wartość tożsamości, a następnie można pobrać nową wartość przez ustawienie `UpdatedRowSource` właściwości polecenia insert do `UpdateRowSource.FirstReturnedRecord`.  
  
 [!code-csharp[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/VB/source.vb#1)]  
  
## <a name="merging-new-identity-values"></a>Scalanie nowych wartości tożsamości  
 Typowy scenariusz polega na wywołaniu `GetChanges` metody `DataTable` do utworzenia kopii, który zawiera tylko zmienione wiersze, a nowa kopia podczas wywoływania `Update` metody `DataAdapter`. Jest to szczególnie przydatne w przypadku, gdy trzeba zorganizować zmienionych wierszy do oddzielnych składnika, który wykonuje aktualizację. Po aktualizacji kopii może zawierać nowe wartości tożsamości, które następnie muszą zostać połączone z powrotem do oryginalnego `DataTable`. Nowe wartości tożsamości prawdopodobnie może różnić się od oryginalnej wartości w `DataTable`. Aby wykonać scalanie, oryginalne wartości parametru **AutoIncrement** kolumn w kopii muszą zostać zachowane, aby można było znaleźć i zaktualizować istniejące wiersze w oryginalnym `DataTable`, zamiast dołączać nowych wierszy zawierających nowe wartości tożsamości. Jednak domyślnie tych oryginalnych wartości zostaną utracone po wywołaniu `Update` metody `DataAdapter`, ponieważ `AcceptChanges` jest wywoływany niejawnie dla każdej aktualizacji `DataRow`.  
  
 Istnieją dwa sposoby, aby zachować oryginalne wartości parametru `DataColumn` w `DataRow` podczas `DataAdapter` aktualizacji:  
  
-   Pierwsza metoda zachować oryginalne wartości, jest ustalenie `AcceptChangesDuringUpdate` właściwość `DataAdapter` do `false`. Ma to wpływ na co `DataRow` w `DataTable` aktualizowana. Aby uzyskać więcej informacji i przykładowy kod, zobacz <xref:System.Data.Common.DataAdapter.AcceptChangesDuringUpdate%2A>.  
  
-   Druga metoda jest pisanie kodu w `RowUpdated` program obsługi zdarzeń `DataAdapter` można ustawić <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> do <xref:System.Data.UpdateStatus.SkipCurrentRow>. `DataRow` Jest aktualizowana, ale oryginalna wartość `DataColumn` są zachowywane. Ta metoda pozwala zachować oryginalne wartości dla niektórych wierszy, a nie dla innych użytkowników. Na przykład, kod można zachować oryginalne wartości dodanymi wierszami, a nie edytowane lub usuniętych wierszy sprawdzając najpierw <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> , a następnie ustawiając <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> do <xref:System.Data.UpdateStatus.SkipCurrentRow> tylko dla wierszy z `StatementType` z `Insert`.  
  
 Gdy każda z tych metod służy do zachowania oryginalnych wartości w `DataRow` podczas `DataAdapter` aktualizacji ADO.NET wykonuje szereg działań, aby ustawić bieżące wartości `DataRow` do nowych wartości zwracane przez parametry wyjściowe lub pierwszy zwracany wiersz z zestawu wyników, zachowując przy tym nadal oryginalnej wartości w każdym `DataColumn`. Najpierw `AcceptChanges` metody `DataRow` jest wywoływana, aby zachować bieżące wartości jako oryginalne wartości, a następnie nowe wartości są przypisane. Zgodnie z tych akcji `DataRows` którym wykorzystano ich <xref:System.Data.DataRow.RowState%2A> właściwością <xref:System.Data.DataRowState.Added> będzie mieć ich `RowState` właściwością <xref:System.Data.DataRowState.Modified>, może być nieoczekiwany.  
  
 Jak wyniki polecenia są stosowane do każdego <xref:System.Data.DataRow> aktualizowana jest określana przez <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> właściwości każdego <xref:System.Data.Common.DbCommand>. Ta właściwość jest ustawiona na wartość z zakresu od `UpdateRowSource` wyliczenia.  
  
 W poniższej tabeli opisano sposób, w jaki `UpdateRowSource` wartości wyliczenia mają wpływ na <xref:System.Data.DataRow.RowState%2A> właściwość zaktualizowanych wierszy.  
  
|Nazwa elementu członkowskiego|Opis|  
|-----------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|`AcceptChanges` nazywa się i obie wartości parametrów w danych wyjściowych i/lub wartości w pierwszym wierszu dowolnego zestawu wyników zwracanego są umieszczane w `DataRow` aktualizowana. Jeśli nie znajdują się wartości do zastosowania, `RowState` będzie <xref:System.Data.DataRowState.Unchanged>.|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Jeśli wiersz został zwrócony, `AcceptChanges` nosi nazwę i wiersz jest mapowany do zmienionego wiersza w `DataTable`, ustawiając `RowState` do `Modified`. Jeśli nie jest zwracany wiersz, następnie `AcceptChanges` nie jest wywoływany i `RowState` pozostaje `Added`.|  
|<xref:System.Data.UpdateRowSource.None>|Wiersze lub parametrów zwracane są ignorowane. Brak Brak wywołania `AcceptChanges` i `RowState` pozostaje `Added`.|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|`AcceptChanges` nosi nazwę oraz wszelkie parametry wyjściowe są mapowane do zmienionego wiersza w `DataTable`, ustawiając `RowState` do `Modified`. Jeśli nie ma żadnych parametrów danych wyjściowych `RowState` będzie `Unchanged`.|  
  
### <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono wyodrębniania zmienionych wierszy z `DataTable` i przy użyciu <xref:System.Data.SqlClient.SqlDataAdapter> zaktualizować źródło danych do pobrania nowej wartości kolumny tożsamości. <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> Wykonuje dwie instrukcje języka Transact-SQL; pierwsza z nich jest instrukcji INSERT, a drugi jest instrukcji SELECT, która używa funkcji SCOPE_IDENTITY do pobierania wartości tożsamości.  
  
```  
INSERT INTO dbo.Shippers (CompanyName)   
VALUES (@CompanyName);  
SELECT ShipperID, CompanyName FROM dbo.Shippers   
WHERE ShipperID = SCOPE_IDENTITY();  
```  
  
 `UpdatedRowSource` Polecenia insert zostaje ustalona `UpdateRowSource.FirstReturnedRow` i <xref:System.Data.MissingSchemaAction> właściwość `DataAdapter` ustawiono `MissingSchemaAction.AddWithKey`. `DataTable` Jest wypełniony i kod dodaje nowy wiersz do `DataTable`. Zmienione wiersze następnie są wyodrębniane do nowego `DataTable`, która jest przekazywana do `DataAdapter`, który następnie zaktualizowanie danych na serwerze.  
  
 [!code-csharp[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#1)]  
  
 `OnRowUpdated` Kontroli programu obsługi zdarzeń <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> z <xref:System.Data.SqlClient.SqlRowUpdatedEventArgs> do ustalenia, czy wiersz jest wstawieniem. Jeśli tak jest, a następnie <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> właściwość jest ustawiona na <xref:System.Data.UpdateStatus.SkipCurrentRow>. Wiersz jest aktualizowany, ale są zachowywane, oryginalnym wartości w wierszu. W głównej części procedura <xref:System.Data.DataSet.Merge%2A> metoda jest wywoływana, aby scalić nową wartość tożsamości w oryginalnym `DataTable`, a na koniec `AcceptChanges` jest wywoływana.  
  
 [!code-csharp[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#2)]
 [!code-vb[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#2)]  
  
## <a name="retrieving-microsoft-access-autonumber-values"></a>Pobieranie wartości automatycznych numerów programu Microsoft Access  
 Ta sekcja zawiera przykład przedstawiający sposób pobierania `Autonumber` wartości z bazy danych Jet 4.0. Aparat bazy danych Jet nie obsługuje wykonanie wielu instrukcji w zadaniu wsadowym lub użyj parametrów wyjściowych, więc nie jest możliwe, użyj jednej z następujących metod, aby zwrócić nowe `Autonumber` wartość przypisana do wstawionego wiersza. Można jednak dodać kod `RowUpdated` programu obsługi zdarzeń, który wykonuje oddzielne wybierz @@IDENTITY instrukcję, aby pobrać nowy `Autonumber` wartość.  
  
### <a name="example"></a>Przykład  
 Zamiast opcji dodawania informacji przy użyciu schematu `MissingSchemaAction.AddWithKey`, ten przykład umożliwia skonfigurowanie `DataTable` przy użyciu poprawnego schematu przed wywołaniem <xref:System.Data.OleDb.OleDbDataAdapter> do wypełnienia `DataTable`. W tym przypadku **CategoryID** kolumny jest skonfigurowany do wartość przypisaną każdy wiersz wstawiony, zaczynając od zera, ustawiając zmniejszenia <xref:System.Data.DataColumn.AutoIncrement%2A> do `true`, <xref:System.Data.DataColumn.AutoIncrementSeed%2A> 0, i <xref:System.Data.DataColumn.AutoIncrementStep%2A> na -1. Kodzie następnie dodaje dwa nowe wiersze i używa `GetChanges` dodać zmienionych wierszy na nową `DataTable` przekazana do `Update` metody.  
  
 [!code-csharp[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#1)]
 [!code-vb[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#1)]  
  
 `RowUpdated` Obsługa zdarzeń używa tego samego open <xref:System.Data.OleDb.OleDbConnection> jako `Update` instrukcja `OleDbDataAdapter`. Sprawdza `StatementType` z <xref:System.Data.OleDb.OleDbRowUpdatedEventArgs> dla wstawione wiersze. Dla każdego wstawiony wiersz nową <xref:System.Data.OleDb.OleDbCommand> służy do wykonywania wybierz @@IDENTITY instrukcji na połączenie, zwracając nowy `Autonumber` wartość, która jest umieszczany w **CategoryID** kolumny `DataRow`. `Status` Zostanie następnie ustawiona właściwość `UpdateStatus.SkipCurrentRow` pominąć wywołanie ukryte `AcceptChanges`. W głównej części procedura `Merge` metoda jest wywoływana, aby scalić dwa `DataTable` obiektów, a na koniec `AcceptChanges` jest wywoływana.  
  
 [!code-csharp[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#2)]
 [!code-vb[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#2)]  
  
### <a name="retrieving-identity-values"></a>Podczas pobierania wartości tożsamości  
 Firma Microsoft często należy ustawić kolumny jako tożsamość, gdy wartości w kolumnie muszą być unikatowe. I czasami potrzebujemy wartości tożsamości nowych danych. Ten przykład przedstawia sposób pobierania wartości tożsamości:  
  
-   Tworzy procedurę przechowywaną, aby wstawić dane i zwracają wartość tożsamości.  
  
-   Wykonuje polecenie, aby wstawić nowe dane i wyświetlić wyniki.  
  
-   Używa <xref:System.Data.SqlClient.SqlDataAdapter> Wstaw nowe dane do wyświetlenia wyniku.  
  
 Aby skompilować i uruchomić przykład, należy utworzyć przykładowej bazy danych, za pomocą następującego skryptu:  
  
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
CREATE procedure [dbo].[CourseExtInfo] @CourseId int  
as  
select c.CourseID,c.Title,c.Credits,d.Name as DepartmentName  
from Course as c left outer join Department as d on c.DepartmentID=d.DepartmentID  
where c.CourseID=@CourseId  
  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
create procedure [dbo].[DepartmentInfo] @DepartmentId int,@CourseCount int output  
as  
select @CourseCount=Count(c.CourseID)  
from course as c  
where c.DepartmentID=@DepartmentId  
  
select d.DepartmentID,d.Name,d.Budget,d.StartDate,d.Administrator  
from Department as d  
where d.DepartmentID=@DepartmentId  
  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
Create PROCEDURE [dbo].[GetDepartmentsOfSpecifiedYear]   
@Year int,@BudgetSum money output  
AS  
BEGIN  
        SELECT @BudgetSum=SUM([Budget])  
  FROM [MySchool].[dbo].[Department]  
  Where YEAR([StartDate])=@Year   
  
SELECT [DepartmentID]  
      ,[Name]  
      ,[Budget]  
      ,[StartDate]  
      ,[Administrator]  
  FROM [MySchool].[dbo].[Department]  
  Where YEAR([StartDate])=@Year  
  
END  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE PROCEDURE [dbo].[GradeOfStudent]   
-- Add the parameters for the stored procedure here  
@CourseTitle nvarchar(100),@FirstName nvarchar(50),  
@LastName nvarchar(50),@Grade decimal(3,2) output  
AS  
BEGIN  
select @Grade=Max(Grade)  
from [dbo].[StudentGrade] as s join [dbo].[Course] as c on   
s.CourseID=c.CourseID join [dbo].[Person] as p on s.StudentID=p.PersonID  
where c.Title=@CourseTitle and p.FirstName=@FirstName   
and p.LastName= @LastName  
END  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE PROCEDURE [dbo].[InsertPerson]   
-- Add the parameters for the stored procedure here  
@FirstName nvarchar(50),@LastName nvarchar(50),  
@PersonID int output  
AS  
BEGIN  
    insert [dbo].[Person](LastName,FirstName) Values(@LastName,@FirstName)  
  
    set @PersonID=SCOPE_IDENTITY()  
END  
Go  
  
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
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
SET ANSI_PADDING ON  
GO  
CREATE TABLE [dbo].[Person]([PersonID] [int] IDENTITY(1,1) NOT NULL,  
[LastName] [nvarchar](50) NOT NULL,  
[FirstName] [nvarchar](50) NOT NULL,  
[HireDate] [datetime] NULL,  
[EnrollmentDate] [datetime] NULL,  
[Picture] [varbinary](max) NULL,  
 CONSTRAINT [PK_School.Student] PRIMARY KEY CLUSTERED  
(  
[PersonID] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]  
  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE TABLE [dbo].[StudentGrade]([EnrollmentID] [int] IDENTITY(1,1) NOT NULL,  
[CourseID] [nvarchar](10) NOT NULL,  
[StudentID] [int] NOT NULL,  
[Grade] [decimal](3, 2) NOT NULL,  
 CONSTRAINT [PK_StudentGrade] PRIMARY KEY CLUSTERED  
(  
[EnrollmentID] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
create view [dbo].[EnglishCourse]  
as  
select c.CourseID,c.Title,c.Credits,c.DepartmentID  
from Course as c join Department as d on c.DepartmentID=d.DepartmentID  
where d.Name=N'English'  
  
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
SET IDENTITY_INSERT [dbo].[Person] ON   
  
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (1, N'Hu', N'Nan', NULL, CAST(0x0000A0BF00000000 AS DateTime))  
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (2, N'Norman', N'Laura', NULL, CAST(0x0000A0BF00000000 AS DateTime))  
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (3, N'Olivotto', N'Nino', NULL, CAST(0x0000A0BF00000000 AS DateTime))  
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (4, N'Anand', N'Arturo', NULL, CAST(0x0000A0BF00000000 AS DateTime))  
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (5, N'Jai', N'Damien', NULL, CAST(0x0000A0BF00000000 AS DateTime))  
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (6, N'Holt', N'Roger', CAST(0x000097F100000000 AS DateTime), NULL)  
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (7, N'Martin', N'Randall', CAST(0x00008B1A00000000 AS DateTime), NULL)  
SET IDENTITY_INSERT [dbo].[Person] OFF  
SET IDENTITY_INSERT [dbo].[StudentGrade] ON   
  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (1, N'C1045', 1, CAST(3.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (2, N'C1045', 2, CAST(3.00 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (3, N'C1045', 3, CAST(2.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (4, N'C1045', 4, CAST(4.00 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (5, N'C1045', 5, CAST(3.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (6, N'C1061', 1, CAST(4.00 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (7, N'C1061', 3, CAST(3.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (8, N'C1061', 4, CAST(2.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (9, N'C1061', 5, CAST(1.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (10, N'C2021', 1, CAST(2.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (11, N'C2021', 2, CAST(3.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (12, N'C2021', 4, CAST(3.00 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (13, N'C2021', 5, CAST(3.00 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (14, N'C2042', 1, CAST(2.00 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (15, N'C2042', 2, CAST(3.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (16, N'C2042', 3, CAST(4.00 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (17, N'C2042', 5, CAST(3.00 AS Decimal(3, 2)))  
SET IDENTITY_INSERT [dbo].[StudentGrade] OFF  
ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])  
REFERENCES [dbo].[Department] ([DepartmentID])  
GO  
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]  
GO  
ALTER TABLE [dbo].[StudentGrade]  WITH CHECK ADD  CONSTRAINT [FK_StudentGrade_Student] FOREIGN KEY([StudentID])  
REFERENCES [dbo].[Person] ([PersonID])  
GO  
ALTER TABLE [dbo].[StudentGrade] CHECK CONSTRAINT [FK_StudentGrade_Student]  
GO  
```  
  
 Listing kodu poniżej:  
  
> [!IMPORTANT]
>  Przykładowy kod odwołuje się do pliku bazy danych programu Access, o nazwie MySchool.mdb. Możesz pobrać MySchool.mdb (jako część pełnej języka C# lub Visual Basic przykładowy projekt), albo [przykładowy program Visual Studio 2012](https://code.msdn.microsoft.com/How-to-retrieve-the-95b4ee43) lub [przykład Visual Studio 2013](https://code.msdn.microsoft.com/How-to-Retrieve-the-511acece).  
  
```  
using System;  
using System.Data;  
using System.Data.OleDb;  
using System.Data.SqlClient;  
  
class Program {  
   static void Main(string[] args) {  
      String SqlDbConnectionString = "Data Source=(local);Initial Catalog=MySchool;Integrated Security=True;Asynchronous Processing=true;";  
  
      InsertPerson(SqlDbConnectionString, "Janice", "Galvin");  
      Console.WriteLine();  
  
      InsertPersonInAdapter(SqlDbConnectionString, "Peter", "Krebs");  
      Console.WriteLine();  
  
      String oledbConnectionString = "Provider=Microsoft.Jet.OLEDB.4.0; Data Source=Database\\MySchool.mdb";  
      InsertPersonInJet4Database(oledbConnectionString, "Janice", "Galvin");  
      Console.WriteLine();  
  
      Console.WriteLine("Please press any key to exit.....");  
      Console.ReadKey();  
   }  
  
   // Using stored procedure to insert a new row and retrieve the identity value  
   static void InsertPerson(String connectionString, String firstName, String lastName) {  
      String commandText = "dbo.InsertPerson";  
  
      using (SqlConnection conn = new SqlConnection(connectionString)) {  
         using (SqlCommand cmd = new SqlCommand(commandText, conn)) {  
            cmd.CommandType = CommandType.StoredProcedure;  
  
            cmd.Parameters.Add(new SqlParameter("@FirstName", firstName));  
            cmd.Parameters.Add(new SqlParameter("@LastName", lastName));  
            SqlParameter personId = new SqlParameter("@PersonID", SqlDbType.Int);  
            personId.Direction = ParameterDirection.Output;  
            cmd.Parameters.Add(personId);  
  
            conn.Open();  
            cmd.ExecuteNonQuery();  
  
            Console.WriteLine("Person Id of new person:{0}", personId.Value);  
         }  
      }  
   }  
  
   // Using stored procedure in adapter to insert new rows and update the identity value.  
   static void InsertPersonInAdapter(String connectionString, String firstName, String lastName) {  
      String commandText = "dbo.InsertPerson";  
      using (SqlConnection conn = new SqlConnection(connectionString)) {  
         SqlDataAdapter mySchool = new SqlDataAdapter("Select PersonID,FirstName,LastName from [dbo].[Person]", conn);  
  
         mySchool.InsertCommand = new SqlCommand(commandText, conn);  
         mySchool.InsertCommand.CommandType = CommandType.StoredProcedure;  
  
         mySchool.InsertCommand.Parameters.Add(  
             new SqlParameter("@FirstName", SqlDbType.NVarChar, 50, "FirstName"));  
         mySchool.InsertCommand.Parameters.Add(  
             new SqlParameter("@LastName", SqlDbType.NVarChar, 50, "LastName"));  
  
         SqlParameter personId = mySchool.InsertCommand.Parameters.Add(new SqlParameter("@PersonID", SqlDbType.Int, 0, "PersonID"));  
         personId.Direction = ParameterDirection.Output;  
  
         DataTable persons = new DataTable();  
         mySchool.Fill(persons);  
  
         DataRow newPerson = persons.NewRow();  
         newPerson["FirstName"] = firstName;  
         newPerson["LastName"] = lastName;  
         persons.Rows.Add(newPerson);  
  
         mySchool.Update(persons);  
         Console.WriteLine("Show all persons:");  
         ShowDataTable(persons, 14);  
      }  
   }  
  
   /// For a Jet 4.0 database, we need use the sigle statement and event handler to insert new rows and retrieve the identity value.  
   static void InsertPersonInJet4Database(String connectionString, String firstName, String lastName) {  
      String commandText = "Insert into Person(FirstName,LastName) Values(?,?)";  
      using (OleDbConnection conn = new OleDbConnection(connectionString)) {  
         OleDbDataAdapter mySchool = new OleDbDataAdapter("Select PersonID,FirstName,LastName from Person", conn);  
  
         // Create Insert Command  
         mySchool.InsertCommand = new OleDbCommand(commandText, conn);  
         mySchool.InsertCommand.CommandType = CommandType.Text;  
  
         mySchool.InsertCommand.Parameters.Add(new OleDbParameter("@FirstName", OleDbType.VarChar, 50, "FirstName"));  
         mySchool.InsertCommand.Parameters.Add(new OleDbParameter("@LastName", OleDbType.VarChar, 50, "LastName"));  
         mySchool.InsertCommand.UpdatedRowSource = UpdateRowSource.Both;  
  
         DataTable persons = CreatePersonsTable();  
  
         mySchool.Fill(persons);  
  
         DataRow newPerson = persons.NewRow();  
         newPerson["FirstName"] = firstName;  
         newPerson["LastName"] = lastName;  
         persons.Rows.Add(newPerson);  
  
         DataTable dataChanges = persons.GetChanges();  
  
         mySchool.RowUpdated += OnRowUpdated;  
  
         mySchool.Update(dataChanges);  
  
         Console.WriteLine("Data before merging:");  
         ShowDataTable(persons, 14);  
         Console.WriteLine();  
  
         persons.Merge(dataChanges);  
         persons.AcceptChanges();  
  
         Console.WriteLine("Data after merging");  
         ShowDataTable(persons, 14);  
      }  
   }  
  
   static void OnRowUpdated(object sender, OleDbRowUpdatedEventArgs e) {  
      if (e.StatementType == StatementType.Insert) {  
         // Retrieve the identity value  
         OleDbCommand cmdNewId = new OleDbCommand("Select @@IDENTITY", e.Command.Connection);  
         e.Row["PersonID"] = (Int32)cmdNewId.ExecuteScalar();  
  
         // After the status is changed, the original values in the row are preserved. And the   
         // Merge method will be called to merge the new identity value into the original DataTable.  
         e.Status = UpdateStatus.SkipCurrentRow;  
      }  
   }  
  
   // Create the Persons table before filling.  
   private static DataTable CreatePersonsTable() {  
      DataTable persons = new DataTable();  
  
      DataColumn personId = new DataColumn();  
      personId.DataType = Type.GetType("System.Int32");  
      personId.ColumnName = "PersonID";  
      personId.AutoIncrement = true;  
      personId.AutoIncrementSeed = 0;  
      personId.AutoIncrementStep = -1;  
      persons.Columns.Add(personId);  
  
      DataColumn firstName = new DataColumn();  
      firstName.DataType = Type.GetType("System.String");  
      firstName.ColumnName = "FirstName";  
      persons.Columns.Add(firstName);  
  
      DataColumn lastName = new DataColumn();  
      lastName.DataType = Type.GetType("System.String");  
      lastName.ColumnName = "LastName";  
      persons.Columns.Add(lastName);  
  
      DataColumn[] pkey = { personId };  
      persons.PrimaryKey = pkey;  
  
      return persons;  
   }  
  
   private static void ShowDataTable(DataTable table, Int32 length) {  
      foreach (DataColumn col in table.Columns) {  
         Console.Write("{0,-" + length + "}", col.ColumnName);  
      }  
      Console.WriteLine();  
  
      foreach (DataRow row in table.Rows) {  
         foreach (DataColumn col in table.Columns) {  
            if (col.DataType.Equals(typeof(DateTime)))  
               Console.Write("{0,-" + length + ":d}", row[col]);  
            else if (col.DataType.Equals(typeof(Decimal)))   
               Console.Write("{0,-" + length + ":C}", row[col]);  
            else  
               Console.Write("{0,-" + length + "}", row[col]);  
         }  
  
         Console.WriteLine();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Stany wiersza i wersje wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [Metody AcceptChanges i RejectChanges](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 [Scalanie zawartości elementu DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
