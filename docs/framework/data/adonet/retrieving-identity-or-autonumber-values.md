---
title: "Pobieranie tożsamości lub wartości automatyczny numer"
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
ms.assetid: d6b7f9cb-81be-44e1-bb94-56137954876d
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1a689bb22fc5bb553084b9d1b1dc60e74e47970c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-identity-or-autonumber-values"></a>Pobieranie tożsamości lub wartości automatyczny numer
Klucz podstawowy relacyjnej bazy danych jest kolumna lub połączenie kolumn, które zawsze zawiera unikatowe wartości. Wiedzy o wartości klucza podstawowego można zlokalizować wiersza, który go zawiera. Relacyjnych baz danych, takich jak SQL Server, Oracle i Microsoft Access/Jet obsługuje tworzenie automatycznie zwiększany kolumn, które mogą być oznaczone jako klucze podstawowe. Wartości te są generowane przez serwer jako wiersze są dodawane do tabeli. W programie SQL Server ustaw właściwość identity kolumny w oprogramowaniu Oracle tworzenia sekwencji i programu Microsoft Access tworzenia automatycznie numerowane kolumny.  
  
 A <xref:System.Data.DataColumn> mogą służyć do generowania wartości automatycznie zwiększającą przez ustawienie <xref:System.Data.DataColumn.AutoIncrement%2A> właściwości na wartość true. Jednak może być na końcu zduplikowanych wartości w osobnych wystąpień <xref:System.Data.DataTable>, jeśli wiele aplikacji klienckich niezależnie jest generowany automatycznie zwiększającą wartości. Serwer generowania wartości automatycznie zwiększającą eliminuje potencjalnych konfliktów przez każdego użytkownika do pobierania wartości wygenerowany dla każdego wstawionego wiersza.  
  
 Podczas wywoływania `Update` metody `DataAdapter`, bazy danych może wysyłać dane do aplikacji ADO.NET jako parametry wyjściowe lub pierwszy rekord zwróconego zestawu wyników w instrukcji SELECT wykonywane w tej samej partii jako instrukcji INSERT. ADO.NET można pobierać te wartości i zaktualizuj odpowiednie kolumny w <xref:System.Data.DataRow> aktualizowana.  
  
 Niektórych baz danych, takich jak aparat bazy danych programu Microsoft Jet dostępu nie obsługuje parametrów wyjściowych i nie może przetwarzać wiele instrukcji w jednym zadaniu wsadowym. Podczas pracy z aparatu bazy danych Jet, można pobrać wartość Automatyczny numer wygenerowany dla wstawionego wiersza, wykonując osobne polecenie SELECT w obsłudze zdarzeń dla `RowUpdated` zdarzenie `DataAdapter`.  
  
> [!NOTE]
>  Jest to alternatywa dla użycia automatyczne zwiększanie wartości do użycia <xref:System.Guid.NewGuid%2A> metody <xref:System.Guid> obiektu do generowania identyfikatora GUID lub Unikatowy identyfikator globalny, na komputerze klienckim, który można skopiować do serwera jako dodaje się każdego nowego wiersza. `NewGuid` Metoda generuje 16-bajtową wartość binarna, która jest tworzona przy użyciu algorytmu, który zapewnia w dużym prawdopodobieństwem zostaną zduplikowane wartości. W bazie danych programu SQL Server, identyfikator GUID jest przechowywany w `uniqueidentifier` kolumny, której program SQL Server może automatycznie generować przy użyciu języka Transact-SQL `NEWID()` funkcji. Przy użyciu identyfikatora GUID jako klucz podstawowy może niekorzystnie wpłynąć na wydajność. [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]zapewnia obsługę `NEWSEQUENTIALID()` funkcji, która generuje sekwencyjnych identyfikator GUID nie jest gwarantowana globalnie unikatowa, ale które mogą być indeksowane wydajniej.  
  
## <a name="retrieving-sql-server-identity-column-values"></a>Pobieranie wartości kolumny tożsamości serwera SQL  
 Podczas pracy z programem Microsoft SQL Server, można utworzyć procedury składowanej z parametrem wyjściowym, aby zwrócić wartości tożsamości dla wstawionego wiersza. W poniższej tabeli opisano trzy funkcje języka Transact-SQL w programie SQL Server, który może służyć do pobierania wartości w kolumnach tożsamości.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|SCOPE_IDENTITY|Zwraca ostatnią wartość tożsamości w bieżącym zakresie wykonywania. SCOPE_IDENTITY jest zalecane dla większości scenariuszy.|  
|@@IDENTITY|Zawiera wygenerowane w dowolnej tabeli w bieżącej sesji, ostatnią wartość tożsamości. @@IDENTITY mogą mieć wpływ wyzwalaczy i nie może zwracać wartości tożsamości, z oczekiwaniami.|  
|ATRYBUTU IDENT_CURRENT|Zwraca ostatnią wartość tożsamości wygenerowany dla określonej tabeli w dowolnej sesji oraz wszelkich zakresach.|  
  
 Poniższe procedury składowanej pokazano, jak wstawienia wiersza do **kategorii** tabeli i użyj parametru wyjściowego, aby zwrócić wartość tożsamości wygenerowane przez funkcję SCOPE_IDENTITY() języka Transact-SQL.  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
```  
  
 Następnie można określić procedurę składowaną jako źródło <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> z <xref:System.Data.SqlClient.SqlDataAdapter> obiektu. <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> Właściwość <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> musi mieć ustawioną <xref:System.Data.CommandType.StoredProcedure>. Tożsamość dane wyjściowe są pobierane przez utworzenie <xref:System.Data.SqlClient.SqlParameter> mający <xref:System.Data.ParameterDirection> z <xref:System.Data.ParameterDirection.Output>. Podczas `InsertCommand` jest przetwarzane, wartość automatycznie zwiększana tożsamości jest zwracana i umieszczane w **CategoryID** kolumny bieżącego wiersza. Jeśli ustawisz <xref:System.Data.SqlClient.SqlCommand.UpdatedRowSource%2A> właściwość polecenia insert do `UpdateRowSource.OutputParameters` lub `UpdateRowSource.Both`.  
  
 Jeśli polecenia insert wykonuje partii, który zawiera zarówno w instrukcji INSERT, jak i w instrukcji SELECT, która zwraca nową wartość tożsamości, a następnie można pobrać nowej wartości przez ustawienie `UpdatedRowSource` właściwość polecenia insert do `UpdateRowSource.FirstReturnedRecord`.  
  
 [!code-csharp[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/VB/source.vb#1)]  
  
## <a name="merging-new-identity-values"></a>Scalanie nowych wartości tożsamości  
 Typowy scenariusz polega na wywołaniu `GetChanges` metody `DataTable` do tworzenia kopii, która zawiera tylko zmienionych wierszy i użyj nowej kopii podczas wywoływania metody `Update` metody `DataAdapter`. Jest to szczególnie przydatne, jeśli musisz kierować zmienionych wierszy do oddzielnych składnika, który wykonuje aktualizację. Po aktualizacji kopii może zawierać nowe wartości tożsamości, które muszą zostać połączone następnie wrócić do oryginalnej `DataTable`. Nowe wartości tożsamości mogą się różnić od oryginalnej wartości w `DataTable`. Do wykonania scalenia oryginalnej wartości **AutoIncrement** kolumn w kopii muszą zostać zachowane, aby można było odnaleźć i zaktualizować istniejące wiersze w oryginalnym `DataTable`, zamiast dodanie nowych wierszy zawierających nowe wartości tożsamości. Jednak domyślnie tych oryginalnych wartości zostaną utracone po wywołaniu `Update` metody `DataAdapter`, ponieważ `AcceptChanges` jest wywoływany niejawnie dla każdej aktualizacji `DataRow`.  
  
 Istnieją dwa sposoby, aby zachować oryginalne wartości `DataColumn` w `DataRow` podczas `DataAdapter` aktualizacji:  
  
-   Pierwsza metoda zachowania oryginalnych wartości jest skonfigurowanie `AcceptChangesDuringUpdate` właściwość `DataAdapter` do `false`. Ma to wpływ na każdy `DataRow` w `DataTable` aktualizowana. Aby uzyskać więcej informacji i przykładowego kodu, zobacz <xref:System.Data.Common.DataAdapter.AcceptChangesDuringUpdate%2A>.  
  
-   Drugi sposób polega na pisania kodu `RowUpdated` obsługi zdarzeń `DataAdapter` można ustawić <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> do <xref:System.Data.UpdateStatus.SkipCurrentRow>. `DataRow` Jest aktualizowana, ale oryginalna wartość `DataColumn` są zachowywane. Ta metoda umożliwia zachować oryginalne wartości dla niektórych wierszy, a nie do innych użytkowników. Na przykład kodu można zachować oryginalne wartości dodanych wierszy, a nie do edycji lub usuniętych wierszy sprawdzając najpierw <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> , a następnie ustawienie <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> do <xref:System.Data.UpdateStatus.SkipCurrentRow> tylko dla wierszy z `StatementType` z `Insert`.  
  
 Każda z tych metod stosowania zachować oryginalne wartości w `DataRow` podczas `DataAdapter` aktualizacji ADO.NET wykonuje szereg akcji można ustawić bieżące wartości `DataRow` do nowych wartości zwracane przez parametry wyjściowe lub pierwszy zwrócony wiersza w zestawie wyników, zachowując nadal oryginalnej wartości w każdym `DataColumn`. Najpierw `AcceptChanges` metoda `DataRow` jest wywoływana, aby zachować bieżące wartości jako oryginalnych wartości, a następnie nowe wartości. Te akcje po `DataRows` które ich <xref:System.Data.DataRow.RowState%2A> ustawioną właściwość <xref:System.Data.DataRowState.Added> będzie mieć ich `RowState` ustawioną właściwość <xref:System.Data.DataRowState.Modified>, które mogą być nieoczekiwany.  
  
 Sposób wyniki poleceń są stosowane do każdego <xref:System.Data.DataRow> aktualizacji jest określany przez <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> właściwości każdego <xref:System.Data.Common.DbCommand>. Ta właściwość ma ustawioną wartość z zakresu od `UpdateRowSource` wyliczenia.  
  
 W poniższej tabeli opisano sposób `UpdateRowSource` wartości wyliczenia mają wpływ na <xref:System.Data.DataRow.RowState%2A> właściwości Zaktualizowano wierszy.  
  
|Nazwa elementu członkowskiego|Opis|  
|-----------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|`AcceptChanges`nazywa się i obie wartości parametrów w danych wyjściowych i/lub wartości w pierwszym wierszu każdy zestaw wyników zwrócony są umieszczane w `DataRow` aktualizowana. Jeśli nie znajdują się wartości do zastosowania, `RowState` będzie <xref:System.Data.DataRowState.Unchanged>.|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Jeśli wiersz został zwrócony, `AcceptChanges` nosi nazwę i wiersz jest zamapowana na wiersz zmienione w `DataTable`, ustawienie `RowState` do `Modified`. Jeśli nie wiersza jest zwracany, następnie `AcceptChanges` nie jest wywoływany i `RowState` pozostaje `Added`.|  
|<xref:System.Data.UpdateRowSource.None>|Parametry zwracane ani wierszy są ignorowane. Brak Brak wywołania `AcceptChanges` i `RowState` pozostaje `Added`.|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|`AcceptChanges`jest nazywana i wszelkie parametry wyjściowe są mapowane na zmienionych wierszy w `DataTable`, ustawienie `RowState` do `Modified`. Jeśli nie ma żadnych parametrów wyjściowych `RowState` będzie `Unchanged`.|  
  
### <a name="example"></a>Przykład  
 W tym przykładzie pokazano wyodrębniania zmienionych wierszy z `DataTable` i przy użyciu <xref:System.Data.SqlClient.SqlDataAdapter> do aktualizowania źródła danych i pobierania nowych wartości kolumny tożsamości. <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> Wykonuje dwie instrukcji języka Transact-SQL; pierwsza z nich jest instrukcji INSERT, a drugi jest instrukcji SELECT, która wykorzystuje funkcję SCOPE_IDENTITY można pobrać wartości tożsamości.  
  
```  
INSERT INTO dbo.Shippers (CompanyName)   
VALUES (@CompanyName);  
SELECT ShipperID, CompanyName FROM dbo.Shippers   
WHERE ShipperID = SCOPE_IDENTITY();  
```  
  
 `UpdatedRowSource` Ma ustawioną właściwość polecenia insert `UpdateRowSource.FirstReturnedRow` i <xref:System.Data.MissingSchemaAction> właściwość `DataAdapter` ma ustawioną wartość `MissingSchemaAction.AddWithKey`. `DataTable` Jest wypełniony i kod dodaje nowy wiersz do `DataTable`. Następnie wyodrębnieniu zmienionych wierszy do nowego `DataTable`, która jest przekazywana do `DataAdapter`, który następnie zaktualizowanie danych na serwerze.  
  
 [!code-csharp[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#1)]  
  
 `OnRowUpdated` Kontroli programu obsługi zdarzeń <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> z <xref:System.Data.SqlClient.SqlRowUpdatedEventArgs> do ustalenia, czy wiersz jest insert. Jeśli tak jest, a następnie <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> właściwość jest ustawiona na <xref:System.Data.UpdateStatus.SkipCurrentRow>. Zaktualizować wiersza, ale zostaną zachowane oryginalnych wartości w wierszu. W głównej części procedura <xref:System.Data.DataSet.Merge%2A> wywoływana jest metoda Scal nową wartość tożsamości w oryginalnym `DataTable`, a na końcu `AcceptChanges` jest wywoływana.  
  
 [!code-csharp[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#2)]
 [!code-vb[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#2)]  
  
## <a name="retrieving-microsoft-access-autonumber-values"></a>Pobieranie wartości automatycznie numerowane programu Microsoft Access  
 Ta sekcja zawiera przykład, który pokazuje, jak pobrać `Autonumber` wartości z bazy danych Jet 4.0. Aparat bazy danych Jet nie obsługuje wykonywania wielu instrukcji w partii lub użyj parametrów wyjściowych, dlatego nie jest możliwe, użyj jednej z następujących metod, aby zwrócić nowe `Autonumber` wartość przypisana do wstawionego wiersza. Można jednak dodać kod `RowUpdated` obsługi zdarzeń, która wykonuje oddzielne wybierz @@IDENTITY instrukcji, aby pobrać nowe `Autonumber` wartość.  
  
### <a name="example"></a>Przykład  
 Zamiast opcji dodawania informacji schematu za pomocą `MissingSchemaAction.AddWithKey`, ten przykład konfiguruje `DataTable` z prawidłowego schematu przed wywołaniem <xref:System.Data.OleDb.OleDbDataAdapter> do wypełnienia `DataTable`. W takim przypadku **CategoryID** kolumny jest skonfigurowany do zmniejszyć wartość przypisana do każdego wstawiony wiersz, rozpoczynając od zera, ustawiając <xref:System.Data.DataColumn.AutoIncrement%2A> do `true`, <xref:System.Data.DataColumn.AutoIncrementSeed%2A> 0 i <xref:System.Data.DataColumn.AutoIncrementStep%2A> -1. Kod następnie dodaje dwa nowe wiersze i używa `GetChanges` dodać zmienionych wierszy do nowego `DataTable` przekazywany do `Update` metody.  
  
 [!code-csharp[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#1)]
 [!code-vb[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#1)]  
  
 `RowUpdated` Obsługi zdarzeń używa tego samego Otwórz <xref:System.Data.OleDb.OleDbConnection> jako `Update` instrukcja `OleDbDataAdapter`. Sprawdza `StatementType` z <xref:System.Data.OleDb.OleDbRowUpdatedEventArgs> dla wstawić wierszy. Dla każdego wstawiony wiersz nowy <xref:System.Data.OleDb.OleDbCommand> utworzeniu można wykonać instrukcji "SELECT" @@IDENTITY instrukcji połączenia i zwraca nowy `Autonumber` wartość, która znajduje się w **CategoryID** kolumny `DataRow`. `Status` Następnie ustawioną właściwość `UpdateStatus.SkipCurrentRow` do pomijania ukryte wywołanie `AcceptChanges`. W głównej części procedura `Merge` metoda jest wywoływana w celu scalenia dwa `DataTable` obiektów, a na końcu `AcceptChanges` jest wywoływana.  
  
 [!code-csharp[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#2)]
 [!code-vb[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#2)]  
  
### <a name="retrieving-identity-values"></a>Pobieranie wartości tożsamości  
 Kolumna możemy często ustawiona jako tożsamości, gdy wartości w kolumnie muszą być unikatowe. I czasami potrzebujemy wartości tożsamości nowych danych. W tym przykładzie pokazano, jak można pobrać wartości tożsamości:  
  
-   Tworzy procedury składowanej wstawiania danych i zwracają wartość tożsamości.  
  
-   Wykonuje polecenie wstawiać nowe dane i wyświetlić wyniki.  
  
-   Używa <xref:System.Data.SqlClient.SqlDataAdapter> można wstawiać nowe dane i wyświetlić wyniki.  
  
 Aby skompilować i uruchomić przykładowy, należy utworzyć przykładowej bazy danych, za pomocą następującego skryptu:  
  
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
  
 Kod, listę w następujący sposób:  
  
> [!IMPORTANT]
>  Przykładowy kod odwołuje się do pliku bazy danych programu Access o nazwie MySchool.mdb. Można pobrać MySchool.mdb (jako część pełnej projektu próbki C# lub Visual Basic) albo [próbki programu Visual Studio 2012](http://code.msdn.microsoft.com/How-to-retrieve-the-95b4ee43) lub [próbki programu Visual Studio 2013](http://code.msdn.microsoft.com/How-to-Retrieve-the-511acece).  
  
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
 [Trwa pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Obiektów DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Stany wiersza i wersje wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [Metoda AcceptChanges i RejectChanges](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 [Scalanie zawartości zestawu danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 [Aktualizowanie źródła danych za pomocą obiektów DataAdapter](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
