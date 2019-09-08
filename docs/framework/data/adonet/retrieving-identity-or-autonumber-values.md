---
title: Pobieranie tożsamości lub wartości automatycznych numerów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6b7f9cb-81be-44e1-bb94-56137954876d
ms.openlocfilehash: 1387dad1f588770384422bf579ed547271b30c0a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794547"
---
# <a name="retrieving-identity-or-autonumber-values"></a>Pobieranie tożsamości lub wartości automatycznych numerów

Klucz podstawowy w relacyjnej bazie danych to kolumna lub kombinacja kolumn, które zawsze zawierają unikatowe wartości. Znajomość wartości klucza podstawowego pozwala zlokalizować wiersz, który go zawiera. Aparaty relacyjnych baz danych, takie jak SQL Server, Oracle i Microsoft Access/Jet, obsługują tworzenie automatycznie zwiększających się kolumn, które można wyznaczyć jako klucze podstawowe. Te wartości są generowane przez serwer, ponieważ wiersze są dodawane do tabeli. W SQL Server ustawiasz właściwość Identity kolumny, w programie Oracle utworzysz sekwencję, a w programie Microsoft Access utworzysz kolumnę AutoNumber.

Można również użyć do wygenerowania automatycznego zwiększania wartości przez <xref:System.Data.DataColumn.AutoIncrement%2A> ustawienie właściwości na wartość true. <xref:System.Data.DataColumn> Można jednak zakończyć z użyciem zduplikowanych wartości w osobnych wystąpieniach <xref:System.Data.DataTable>, jeśli wiele aplikacji klienckich jest generowanych niezależnie do automatycznego zwiększania wartości. Gdy serwer generuje automatyczne zwiększanie wartości, eliminuje potencjalne konflikty przez umożliwienie każdemu użytkownikowi pobrania wygenerowanej wartości dla każdego wstawionego wiersza.

W trakcie wywołania `Update` metody `DataAdapter`klasy, baza danych może wysyłać dane z powrotem do aplikacji ADO.NET jako parametry wyjściowe lub jako pierwszy zwrócony rekord zestawu wyników instrukcji SELECT wykonanej w tej samej partii co instrukcja INSERT. ADO.NET może pobrać te wartości i zaktualizować odpowiednie kolumny w <xref:System.Data.DataRow> aktualizowanej.

Niektóre aparaty bazy danych, takie jak aparat bazy danych Microsoft Access Jet, nie obsługują parametrów wyjściowych i nie mogą przetwarzać wielu instrukcji w pojedynczej partii. Podczas pracy z aparatem bazy danych Jet można pobrać nową wartość Autonumer wygenerowany dla wstawionego wiersza, wykonując oddzielne polecenie SELECT w procedurze obsługi zdarzeń dla `RowUpdated` zdarzenia. `DataAdapter`

> [!NOTE]
> Alternatywą dla korzystania z funkcji autozwiększania wartości jest użycie <xref:System.Guid.NewGuid%2A> metody <xref:System.Guid> obiektu do wygenerowania identyfikatora GUID lub unikatowego identyfikatora globalnego na komputerze klienckim, który można skopiować na serwer po wstawieniu każdego nowego wiersza. `NewGuid` Metoda generuje 16-bajtową wartość binarną, która jest tworzona przy użyciu algorytmu, który zapewnia wysokie prawdopodobieństwo, że żadna wartość nie zostanie zduplikowana. W bazie danych SQL Server Identyfikator GUID jest przechowywany w `uniqueidentifier` kolumnie, która SQL Server może być generowana automatycznie przy użyciu funkcji Transact-SQL. `NEWID()` Użycie identyfikatora GUID jako klucza podstawowego może niekorzystnie wpłynąć na wydajność. SQL Server zapewnia obsługę `NEWSEQUENTIALID()` funkcji, która generuje sekwencyjny identyfikator GUID, który nie jest gwarantowany globalnie unikatowy, ale może być bardziej wydajny.

## <a name="retrieving-sql-server-identity-column-values"></a>Pobieranie wartości kolumn tożsamości SQL Server

Podczas pracy z Microsoft SQL Server można utworzyć procedurę składowaną z parametrem Output w celu zwrócenia wartości tożsamości dla wstawionego wiersza. W poniższej tabeli opisano trzy funkcje języka Transact-SQL w SQL Server, które mogą być używane do pobierania wartości kolumn tożsamości.

|Funkcja|Opis|
|--------------|-----------------|
|SCOPE_IDENTITY|Zwraca ostatnią wartość tożsamości w bieżącym zakresie wykonywania. SCOPE_IDENTITY jest zalecane w przypadku większości scenariuszy.|
|@@IDENTITY|Zawiera ostatnią wartość tożsamości wygenerowaną w dowolnej tabeli w bieżącej sesji. na@IDENTITY wartość @ mogą mieć wpływ wyzwalacze i może nie zwracać oczekiwanej wartości tożsamości.|
|IDENT_CURRENT|Zwraca ostatnią wartość tożsamości wygenerowaną dla określonej tabeli w dowolnej sesji i dowolnym zakresie.|

 Poniższa procedura składowana pokazuje, jak wstawić wiersz do tabeli **Categories** i użyć parametru wyjściowego w celu zwrócenia nowej wartości tożsamości wygenerowanej przez funkcję Transact-SQL SCOPE_IDENTITY ().

```sql
CREATE PROCEDURE dbo.InsertCategory
  @CategoryName nvarchar(15),
  @Identity int OUT
AS
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)
SET @Identity = SCOPE_IDENTITY()
```

Procedurę składowaną można następnie określić jako źródło <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter> obiektu. Właściwość musi być ustawiona na <xref:System.Data.CommandType.StoredProcedure>wartość. <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> Dane wyjściowe tożsamości są pobierane przez utworzenie <xref:System.Data.SqlClient.SqlParameter> , która <xref:System.Data.ParameterDirection> ma <xref:System.Data.ParameterDirection.Output>. `UpdateRowSource.Both` <xref:System.Data.SqlClient.SqlCommand.UpdatedRowSource%2A> `UpdateRowSource.OutputParameters` Gdy jest przetwarzana, funkcja autozwiększania tożsamości jest zwracana i umieszczana w kolumnie IDKategorii bieżącego wiersza w przypadku ustawienia właściwości polecenia INSERT na lub. `InsertCommand`

Jeśli polecenie INSERT wykonuje partię, która zawiera instrukcję INSERT i instrukcję SELECT zwracającą nową wartość tożsamości, można pobrać nową wartość, ustawiając `UpdatedRowSource` właściwość polecenia INSERT na. `UpdateRowSource.FirstReturnedRecord`

[!code-csharp[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/VB/source.vb#1)]

## <a name="merging-new-identity-values"></a>Scalanie nowych wartości tożsamości

Typowym `GetChanges` scenariuszem jest wywołanie metody `DataTable` klasy, aby utworzyć kopię zawierającą tylko zmienione wiersze i użyć `Update` nowej kopii podczas `DataAdapter`wywoływania metody. Jest to szczególnie przydatne, gdy trzeba zorganizować zmienione wiersze w oddzielnym składniku, który wykonuje aktualizację. Po aktualizacji kopia może zawierać nowe wartości tożsamości, które następnie muszą zostać scalone z powrotem do oryginału `DataTable`. Nowe wartości tożsamości mogą się różnić od oryginalnych wartości w `DataTable`. Aby wykonać scalanie, należy zachować oryginalne wartości kolumn typu **AutoIncrement** w kopii, aby można było lokalizować i aktualizować istniejące wiersze w oryginalnym `DataTable`, zamiast dołączać nowe wiersze zawierające nowe wartości tożsamości. . Jednak domyślnie te oryginalne wartości `Update` są tracone po wywołaniu metody `DataAdapter`, ponieważ `AcceptChanges` jest wywoływana niejawnie dla każdej zaktualizowanej `DataRow`.

Istnieją dwa sposoby zachowywania oryginalnych wartości `DataColumn` `DataRow` w trakcie `DataAdapter` aktualizacji:

- Pierwszą metodą zachowywania oryginalnych wartości jest ustawienie `AcceptChangesDuringUpdate` właściwości `DataAdapter` na `false`. Ma to wpływ `DataRow` na wszystkie `DataTable` w aktualizowanych. Aby uzyskać więcej informacji i przykład kodu, zobacz <xref:System.Data.Common.DataAdapter.AcceptChangesDuringUpdate%2A>.

- Druga metoda polega na pisaniu kodu `RowUpdated` w procedurze obsługi zdarzeń w `DataAdapter` celu ustawienia <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> do <xref:System.Data.UpdateStatus.SkipCurrentRow>. Aktualizacja `DataRow` jest aktualizowana, ale oryginalna wartość każdego `DataColumn` z nich jest zachowywana. Ta metoda umożliwia zachowanie oryginalnych wartości niektórych wierszy, a nie dla innych. Na przykład kod może zachować oryginalne wartości dla dodanych wierszy, a nie dla edytowanych lub usuniętych wierszy, sprawdzając najpierw <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> , a następnie <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> <xref:System.Data.UpdateStatus.SkipCurrentRow> ustawienie tylko dla wierszy z `StatementType` `Insert`.

Gdy każda z tych metod jest używana do zachowywania oryginalnych wartości w `DataRow` `DataAdapter` trakcie aktualizacji, ADO.NET wykonuje serię akcji, aby ustawić bieżące wartości `DataRow` do nowych wartości zwracanych przez parametry wyjściowe lub według pierwszego Zwraca wiersz zestawu wyników, zachowując jednocześnie pierwotną wartość w każdym z nich `DataColumn`. `AcceptChanges` Najpierw Metoda `DataRow` jest wywoływana, aby zachować bieżące wartości jako pierwotne wartości, a następnie są przypisywane nowe wartości. Następujące `DataRows` akcje, <xref:System.Data.DataRowState.Modified>które <xref:System.Data.DataRow.RowState%2A> miały <xref:System.Data.DataRowState.Added> ustawionąwłaściwość,będąmiećustawionąwłaściwośćna,któramożebyćnieoczekiwana.`RowState`

Sposób, w jaki wyniki poleceń są stosowane <xref:System.Data.DataRow> do każdej aktualizacji, są określane <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> przez właściwość każdej <xref:System.Data.Common.DbCommand>z nich. Ta właściwość jest ustawiona na wartość z `UpdateRowSource` wyliczenia.

W poniższej tabeli opisano, jak `UpdateRowSource` wartości wyliczenia <xref:System.Data.DataRow.RowState%2A> wpływają na Właściwość zaktualizowanych wierszy.

|Nazwa elementu członkowskiego|Opis|
|-----------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|`AcceptChanges`jest wywoływana i obie wartości parametrów wyjściowych i/lub wartości w pierwszym wierszu dowolnego zwróconego zestawu wyników są umieszczane w `DataRow` aktualizowanym. Jeśli nie ma żadnych wartości do zastosowania, to `RowState` <xref:System.Data.DataRowState.Unchanged>będzie.|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Jeśli `AcceptChanges` wiersz został zwrócony, jest wywoływana i wiersz jest mapowany na zmieniony wiersz `DataTable`w, ustawienie `RowState` `Modified`na. Jeśli żaden wiersz nie jest zwracany, `AcceptChanges` wówczas nie jest wywoływana `RowState` i pozostaje `Added`.|
|<xref:System.Data.UpdateRowSource.None>|Wszystkie zwrócone parametry lub wiersze są ignorowane. Brak wywołania do `AcceptChanges` `RowState` i pozostają `Added`.|
|<xref:System.Data.UpdateRowSource.OutputParameters>|`AcceptChanges`jest wywoływana, a wszystkie parametry wyjściowe są mapowane na zmieniony wiersz w `DataTable`, `RowState` ustawienie `Modified`na. Jeśli nie ma parametrów wyjściowych, to `RowState` `Unchanged`będzie.|

### <a name="example"></a>Przykład

W tym przykładzie pokazano wyodrębnianie zmienionych wierszy `DataTable` z i <xref:System.Data.SqlClient.SqlDataAdapter> przy użyciu narzędzia, aby zaktualizować źródło danych i pobrać nową wartość kolumny tożsamości. <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> Wykonuje dwie instrukcje języka Transact-SQL; pierwszy z nich jest instrukcją INSERT, a drugi jest instrukcją SELECT, która używa funkcji SCOPE_IDENTITY do pobrania wartości tożsamości.

```sql
INSERT INTO dbo.Shippers (CompanyName)
VALUES (@CompanyName);
SELECT ShipperID, CompanyName FROM dbo.Shippers
WHERE ShipperID = SCOPE_IDENTITY();
```

`UpdateRowSource.FirstReturnedRow` <xref:System.Data.MissingSchemaAction> `MissingSchemaAction.AddWithKey` `DataAdapter` Właściwość polecenia INSERT jest ustawiona na, a właściwość jest ustawiona na. `UpdatedRowSource` Jest wypełnione i kod dodaje nowy wiersz `DataTable`do. `DataTable` Zmienione wiersze są następnie wyodrębniane do nowego `DataTable`, który jest przesyłany `DataAdapter`do, który następnie aktualizuje serwer.

[!code-csharp[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#1)]

Procedura obsługi <xref:System.Data.SqlClient.SqlRowUpdatedEventArgs> zdarzeń sprawdza, <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> czy w celu ustalenia, czy wiersz jest wstawiony. `OnRowUpdated` Jeśli tak jest, <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> właściwość jest ustawiona na. <xref:System.Data.UpdateStatus.SkipCurrentRow> Wiersz został zaktualizowany, ale oryginalne wartości w wierszu są zachowywane. W głównej treści procedury <xref:System.Data.DataSet.Merge%2A> Metoda jest wywoływana w celu scalenia nowej wartości tożsamości w oryginalną `DataTable`, a wreszcie `AcceptChanges` jest wywoływana.

[!code-csharp[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#2)]
[!code-vb[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#2)]

## <a name="retrieving-microsoft-access-autonumber-values"></a>Pobieranie wartości autonumerowania programu Microsoft Access

Ta sekcja zawiera przykład pokazujący sposób pobierania `Autonumber` wartości z bazy danych Jet 4,0. Aparat bazy danych Jet nie obsługuje wykonywania wielu instrukcji w partii ani używania parametrów wyjściowych, więc nie można użyć żadnej z tych technik do zwrócenia nowej `Autonumber` wartości przypisanej do wstawionego wiersza. Można jednak dodać kod do `RowUpdated` programu obsługi zdarzeń, który wykonuje oddzielną instrukcję SELECT @@IDENTITY , aby pobrać nową `Autonumber` wartość.

### <a name="example"></a>Przykład

Zamiast dodawać informacje o schemacie `MissingSchemaAction.AddWithKey`przy użyciu programu, w `DataTable` tym przykładzie skonfigurowano program z odpowiednim schematem przed `DataTable`wywołaniem programu <xref:System.Data.OleDb.OleDbDataAdapter> w celu wypełnienia. W takim przypadku kolumna **IDkategorii** jest skonfigurowana tak, aby zmniejszyć wartość przypisaną każdemu wstawionemu wierszowi Zaczynając od zera <xref:System.Data.DataColumn.AutoIncrement%2A> , `true`przez <xref:System.Data.DataColumn.AutoIncrementSeed%2A> ustawienie na wartość, <xref:System.Data.DataColumn.AutoIncrementStep%2A> 0 i do-1. Następnie kod dodaje dwa nowe wiersze i używa `GetChanges` do dodawania zmienionych wierszy do nowego `DataTable` `Update` , który jest przesyłany do metody.

[!code-csharp[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#1)]
[!code-vb[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#1)]

Procedura obsługi <xref:System.Data.OleDb.OleDbConnection> `Update` `OleDbDataAdapter`zdarzeń używa tego samego elementu Open jako instrukcji. `RowUpdated` `StatementType` Sprawdza<xref:System.Data.OleDb.OleDbRowUpdatedEventArgs> dla wstawionych wierszy. Dla każdego wstawionego wiersza tworzony <xref:System.Data.OleDb.OleDbCommand> jest nowy w celu wykonania instrukcji SELECT@IDENTITY @ w połączeniu, zwracając nową `Autonumber` wartość umieszczoną w kolumnie **IDkategorii** kolumny `DataRow`. Właściwość jest następnie ustawiona na `UpdateStatus.SkipCurrentRow` , aby `AcceptChanges`pominąć ukryte wywołanie. `Status` W głównej treści procedury `Merge` Metoda jest wywoływana w celu scalenia dwóch `DataTable` obiektów, a wreszcie `AcceptChanges` jest wywoływana.

[!code-csharp[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#2)]
[!code-vb[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#2)]

### <a name="retrieving-identity-values"></a>Pobieranie wartości tożsamości

Często ustawiamy kolumnę jako tożsamość, gdy wartości w kolumnie muszą być unikatowe. I czasami potrzebujemy wartości tożsamości nowych danych. Ten przykład pokazuje, jak pobrać wartości tożsamości:

- Tworzy procedurę przechowywaną służącą do wstawiania danych i zwracania wartości tożsamości.

- Wykonuje polecenie, aby wstawić nowe dane i wyświetlić wynik.

- Używa <xref:System.Data.SqlClient.SqlDataAdapter> do wstawiania nowych danych i wyświetlania wyniku.

Przed skompilowaniem i uruchomieniem przykładu należy utworzyć przykładową bazę danych przy użyciu następującego skryptu:

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

Następująca lista kodu:

> [!TIP]
> Lista kod odnosi się do pliku bazy danych programu Access o nazwie plik *. mdb. Możesz pobrać szkołę. mdb (jako część pełnego C# lub Visual Basic przykładowego projektu) z [Code.MSDN.Microsoft.com](https://code.msdn.microsoft.com/How-to-Retrieve-the-511acece).

```csharp
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

   /// For a Jet 4.0 database, we need use the single statement and event handler to insert new rows and retrieve the identity value.
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

## <a name="see-also"></a>Zobacz także

- [Pobieranie i modyfikowanie danych ADO.NET](retrieving-and-modifying-data.md)
- [Elementy DataAdapter i DataReaders](dataadapters-and-datareaders.md)
- [Stany wiersza i wersje wiersza](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [Metody AcceptChanges i RejectChanges](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [Scalanie zawartości elementu DataSet](./dataset-datatable-dataview/merging-dataset-contents.md)
- [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](updating-data-sources-with-dataadapters.md)
- [Omówienie ADO.NET](ado-net-overview.md)
