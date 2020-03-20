---
title: Przykłady kodu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 8a0a7c6166bb4cfc8064faa20056fda16b593e81
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151770"
---
# <a name="adonet-code-examples"></a>ADO.NET przykłady kodu
Lista kodów w tym temacie pokazuje, jak pobierać dane z bazy danych przy użyciu następujących technologii ADO.NET:

- ADO.NET dostawców danych:

  - [SqlClient](#sqlclient) `System.Data.SqlClient`( )

  - [OleDb](#oledb) `System.Data.OleDb`( )

  - [Odbc](#odbc) `System.Data.Odbc`( )

  - [OracleClient](#oracleclient) `System.Data.OracleClient`( )

- ADO.NET Entity Framework:

  - [LINQ to Entities](#linq-to-entities)

  - [Typizowane zapytanie obiektów](#typed-objectquery)

  - [EntityClient](#entityclient) `System.Data.EntityClient`( )

- [LINQ to SQL](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a>ADO.NET przykłady dostawców danych
Poniższe listy kodów pokazują, jak pobierać dane z bazy danych przy użyciu ADO.NET dostawców danych. Dane są zwracane `DataReader`w pliku . Aby uzyskać więcej informacji, zobacz [Pobieranie danych przy użyciu czytnika danych](retrieving-data-using-a-datareader.md).

### <a name="sqlclient"></a>Sqlclient
Kod w tym przykładzie zakłada, że `Northwind` można połączyć się z przykładowej bazy danych na microsoft SQL Server. Kod tworzy <xref:System.Data.SqlClient.SqlCommand> do wyboru wiersze z Products <xref:System.Data.SqlClient.SqlParameter> tabeli, dodając a, aby ograniczyć wyniki do wierszy z UnitPrice większa niż określona wartość parametru, w tym przypadku 5. Jest <xref:System.Data.SqlClient.SqlConnection> otwarty wewnątrz `using` bloku, co zapewnia, że zasoby są zamknięte i usuwane po zamknięciu kodu. Kod wykonuje polecenie za pomocą <xref:System.Data.SqlClient.SqlDataReader>programu , i wyświetla wyniki w oknie konsoli.

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a>OleDb
Kod w tym przykładzie zakłada, że można połączyć się z przykładową bazą danych programu Microsoft Access Northwind. Kod tworzy <xref:System.Data.OleDb.OleDbCommand> do wyboru wiersze z Products <xref:System.Data.OleDb.OleDbParameter> tabeli, dodając a, aby ograniczyć wyniki do wierszy z UnitPrice większa niż określona wartość parametru, w tym przypadku 5. Jest <xref:System.Data.OleDb.OleDbConnection> otwarty wewnątrz `using` bloku, co zapewnia, że zasoby są zamknięte i usuwane po zamknięciu kodu. Kod wykonuje polecenie za pomocą <xref:System.Data.OleDb.OleDbDataReader>programu , i wyświetla wyniki w oknie konsoli.

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a>Odbc
Kod w tym przykładzie zakłada, że można połączyć się z przykładową bazą danych programu Microsoft Access Northwind. Kod tworzy <xref:System.Data.Odbc.OdbcCommand> do wyboru wiersze z Products <xref:System.Data.Odbc.OdbcParameter> tabeli, dodając a, aby ograniczyć wyniki do wierszy z UnitPrice większa niż określona wartość parametru, w tym przypadku 5. Jest <xref:System.Data.Odbc.OdbcConnection> otwarty wewnątrz `using` bloku, co zapewnia, że zasoby są zamknięte i usuwane po zamknięciu kodu. Kod wykonuje polecenie za pomocą <xref:System.Data.Odbc.OdbcDataReader>programu , i wyświetla wyniki w oknie konsoli.

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)]
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)]

### <a name="oracleclient"></a>OracleClient (OracleClient)
Kod w tym przykładzie zakłada połączenie z DEMO. klienta na serwerze Oracle. Należy również dodać odwołanie do pliku System.Data.OracleClient.dll. Kod zwraca dane w <xref:System.Data.OracleClient.OracleDataReader>pliku .

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a>Przykłady struktury encji
Poniższe listy kodu pokazują, jak pobierać dane ze źródła danych, wykonując kwerendy jednostek w modelu danych jednostki (EDM). W tych przykładach użyto modelu opartego na przykładowej bazie danych Northwind. Aby uzyskać więcej informacji na temat struktury encji, zobacz [Omówienie struktury encji](./ef/overview.md).

### <a name="linq-to-entities"></a>LINQ do Jednostek
Kod w tym przykładzie używa kwerendy LINQ do zwracania danych jako obiekty kategorie, które są rzutowane jako typ anonimowy, który zawiera tylko CategoryID i CategoryName właściwości. Aby uzyskać więcej informacji, zobacz [OMÓWIENIE LINQ to Entities](./ef/language-reference/linq-to-entities.md).

```csharp
using System;
using System.Linq;
using System.Data.Objects;
using NorthwindModel;

class LinqSample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            try
            {
                var query = from category in context.Categories
                            select new
                            {
                                categoryID = category.CategoryID,
                                categoryName = category.CategoryName
                            };

                foreach (var categoryInfo in query)
                {
                    Console.WriteLine("\t{0}\t{1}",
                        categoryInfo.categoryID, categoryInfo.categoryName);
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Linq
Imports System.Data.Objects
Imports NorthwindModel

Class LinqSample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Try
                Dim query = From category In context.Categories _
                            Select New With _
                            { _
                                .categoryID = category.CategoryID, _
                                .categoryName = category.CategoryName _
                            }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                        categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using
    End Sub
End Class
```

### <a name="typed-objectquery"></a>Typizowane zapytanie obiektów
Kod w tym przykładzie <xref:System.Data.Objects.ObjectQuery%601> używa do zwrócenia danych jako kategorie obiektów. Aby uzyskać więcej informacji, zobacz [Kwerendy obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).

```csharp
using System;
using System.Data.Objects;
using NorthwindModel;

class ObjectQuerySample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            ObjectQuery<Categories> categoryQuery = context.Categories;

            foreach (Categories category in
                categoryQuery.Execute(MergeOption.AppendOnly))
            {
                Console.WriteLine("\t{0}\t{1}",
                    category.CategoryID, category.CategoryName);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Data.Objects
Imports NorthwindModel

Class ObjectQuerySample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Dim categoryQuery As ObjectQuery(Of Categories) = context.Categories

            For Each category As Categories In _
                categoryQuery.Execute(MergeOption.AppendOnly)
                Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                    category.CategoryID, category.CategoryName)
            Next
        End Using
    End Sub
End Class
```

### <a name="entityclient"></a>Entityclient
Kod w tym przykładzie <xref:System.Data.EntityClient.EntityCommand> używa do wykonania kwerendy SQL jednostki. Ta kwerenda zwraca listę rekordów, które reprezentują wystąpienia typu jednostki Kategorie. An <xref:System.Data.EntityClient.EntityDataReader> jest używany do uzyskiwania dostępu do rekordów danych w zestawie wyników. Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.EntityClient;
using NorthwindModel;

class EntityClientSample
{
    public static void ExecuteQuery()
    {
        string queryString =
            @"SELECT c.CategoryID, c.CategoryName
                FROM NorthwindEntities.Categories AS c";

        using (EntityConnection conn =
            new EntityConnection("name=NorthwindEntities"))
        {
            try
            {
                conn.Open();
                using (EntityCommand query = new EntityCommand(queryString, conn))
                {
                    using (DbDataReader rdr =
                        query.ExecuteReader(CommandBehavior.SequentialAccess))
                    {
                        while (rdr.Read())
                        {
                            Console.WriteLine("\t{0}\t{1}", rdr[0], rdr[1]);
                        }
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Data
Imports System.Data.Common
Imports System.Data.EntityClient
Imports NorthwindModel

Class EntityClientSample
    Public Shared Sub ExecuteQuery()
        Dim queryString As String = _
            "SELECT c.CategoryID, c.CategoryName " & _
                "FROM NorthwindEntities.Categories AS c"

        Using conn As EntityConnection = _
            New EntityConnection("name=NorthwindEntities")

            Try
                conn.Open()
                Using query As EntityCommand = _
                New EntityCommand(queryString, conn)
                    Using rdr As DbDataReader = _
                        query.ExecuteReader(CommandBehavior.SequentialAccess)
                        While rdr.Read()
                            Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                                              rdr(0), rdr(1))
                        End While
                    End Using
                End Using
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using
    End Sub
End Class
```

## <a name="linq-to-sql"></a>LINQ to SQL
Kod w tym przykładzie używa kwerendy LINQ do zwracania danych jako obiekty kategorie, które są rzutowane jako typ anonimowy, który zawiera tylko CategoryID i CategoryName właściwości. W tym przykładzie jest oparty na kontekście danych Northwind. Aby uzyskać więcej informacji, zobacz [Wprowadzenie](./sql/linq/getting-started.md).

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Northwind;

    class LinqSqlSample
    {
        public static void ExecuteQuery()
        {
            using (NorthwindDataContext db = new NorthwindDataContext())
            {
                try
                {
                    var query = from category in db.Categories
                                select new
                                {
                                    categoryID = category.CategoryID,
                                    categoryName = category.CategoryName
                                };

                    foreach (var categoryInfo in query)
                    {
                        Console.WriteLine("vbTab {0} vbTab {1}",
                            categoryInfo.categoryID, categoryInfo.categoryName);
                    }
                }
                catch (Exception ex)
                {
                    Console.WriteLine(ex.Message);
                }
            }
        }
    }
```

```vb
Option Explicit On
Option Strict On

Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports Northwind

Class LinqSqlSample
    Public Shared Sub ExecuteQuery()
        Using db As NorthwindDataContext = New NorthwindDataContext()
            Try
                Dim query = From category In db.Categories _
                                Select New With _
                                { _
                                    .categoryID = category.CategoryID, _
                                    .categoryName = category.CategoryName _
                                }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                            categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
            End Using
    End Sub
End Class
```

## <a name="see-also"></a>Zobacz też

- [Omówienie ADO.NET](ado-net-overview.md)
- [Pobieranie i modyfikowanie danych ADO.NET](retrieving-and-modifying-data.md)
- [Tworzenie aplikacji danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))
- [Wykonywanie zapytań o model danych jednostki (zadania struktury encji)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))
- [Jak: Wykonanie kwerendy, która zwraca obiekty typu anonimowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))
