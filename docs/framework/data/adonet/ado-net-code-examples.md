---
title: Przykłady kodu ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 93cc0cf34d2bba23ff0938c8c13d7343d665192d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43773610"
---
# <a name="adonet-code-examples"></a>Przykłady kodu ADO.NET
Zamieszczone w tym temacie pokazują, jak pobierać dane z bazy danych przy użyciu następujących technologii ADO.NET:

- Dostawcy danych ADO.NET:

  - [Klient SQL](#sqlclient) (`System.Data.SqlClient`)

  - [OleDb](#oledb) (`System.Data.OleDb`)

  - [ODBC](#odbc) (`System.Data.Odbc`)

  - [Programu OracleClient](#oracleclient) (`System.Data.OracleClient`)

- ADO.NET Entity Framework:

  - [LINQ to Entities](#linq-to-entities)

  - [Typizowany obiekt ObjectQuery](#typed-objectquery)

  - [Dostawca EntityClient](#entityclient) (`System.Data.EntityClient`)

- [LINQ to SQL](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a>Przykłady dostawcy danych ADO.NET
Następujące fragmentów kodu pokazują, jak pobierać dane z bazy danych przy użyciu dostawcy danych ADO.NET. Dane są zwracane w `DataReader`. Aby uzyskać więcej informacji, zobacz [podczas pobierania danych przy użyciu elementu DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).

### <a name="sqlclient"></a>SqlClient
W kodzie, w tym przykładzie założono, że można nawiązać `Northwind` przykładową bazę danych w programie Microsoft SQL Server. Ten kod tworzy <xref:System.Data.SqlClient.SqlCommand> celu wybrania wierszy z tabeli Produkty Dodawanie <xref:System.Data.SqlClient.SqlParameter> związane z ograniczaniem wyników do wierszy za pomocą UnitPrice większa niż określona wartość parametru, w tym przypadku 5. <xref:System.Data.SqlClient.SqlConnection> Jest otwarte wewnątrz `using` bloku, który gwarantuje, że zasoby są zamknięte i usuwane, gdy kończy działanie kodu. Kod wykonuje polecenie przy użyciu <xref:System.Data.SqlClient.SqlDataReader>i wyświetla wyniki w oknie konsoli.

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a>OLE DB
Kod w tym przykładzie przyjęto założenie, że można połączyć się z przykładową bazą danych Northwind dostępu firmy Microsoft. Ten kod tworzy <xref:System.Data.OleDb.OleDbCommand> celu wybrania wierszy z tabeli Produkty Dodawanie <xref:System.Data.OleDb.OleDbParameter> związane z ograniczaniem wyników do wierszy za pomocą UnitPrice większa niż określona wartość parametru, w tym przypadku 5. <xref:System.Data.OleDb.OleDbConnection> Jest otwarty w `using` bloku, który gwarantuje, że zasoby są zamknięte i usuwane, gdy kończy działanie kodu. Kod wykonuje polecenie przy użyciu <xref:System.Data.OleDb.OleDbDataReader>i wyświetla wyniki w oknie konsoli.

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a>Odbc
Kod w tym przykładzie przyjęto założenie, że można połączyć się z przykładową bazą danych Northwind dostępu firmy Microsoft. Ten kod tworzy <xref:System.Data.Odbc.OdbcCommand> celu wybrania wierszy z tabeli Produkty Dodawanie <xref:System.Data.Odbc.OdbcParameter> związane z ograniczaniem wyników do wierszy za pomocą UnitPrice większa niż określona wartość parametru, w tym przypadku 5. <xref:System.Data.Odbc.OdbcConnection> Jest otwarte wewnątrz `using` bloku, który gwarantuje, że zasoby są zamknięte i usuwane, gdy kończy działanie kodu. Kod wykonuje polecenie przy użyciu <xref:System.Data.Odbc.OdbcDataReader>i wyświetla wyniki w oknie konsoli.

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)] 
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)] 

### <a name="oracleclient"></a>OracleClient
Kod w tym przykładzie przyjęto założenie, połączenie pokaz. KLIENTÓW na serwerze bazy danych Oracle. Należy również dodać odwołanie do System.Data.OracleClient.dll. Kod zwraca dane w <xref:System.Data.OracleClient.OracleDataReader>.

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a>Entity Framework przykłady
Następujące fragmentów kodu pokazują, jak można pobrać danych ze źródła danych, badając jednostek w Entity Data Model (EDM). Użyj tych przykładach [modelu Northwind](https://msdn.microsoft.com/74521f8c-e974-48cb-8858-c08deff52638). Aby uzyskać więcej informacji, zobacz [Omówienie programu Entity Framework](../../../../docs/framework/data/adonet/ef/overview.md).

### <a name="linq-to-entities"></a>LINQ do Jednostek
Kod w tym przykładzie używa zapytania LINQ, aby zwrócić dane jako obiekty kategorie, które jest przekazywany jako typ anonimowy, który zawiera tylko właściwości CategoryID i CategoryName. Aby uzyskać więcej informacji, zobacz [LINQ to Entities — Przegląd](https://msdn.microsoft.com/86d87a27-c17a-45ac-b28d-72c8500333c6).

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

Imports System
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

### <a name="typed-objectquery"></a>Typizowany obiekt ObjectQuery
W kodzie, w tym przykładzie użyto <xref:System.Data.Objects.ObjectQuery%601> do zwrócenia danych jako obiektami kategorii. Aby uzyskać więcej informacji, zobacz [zapytań dotyczących obiektów](https://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276).

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

Imports System
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

### <a name="entityclient"></a>EntityClient
W kodzie, w tym przykładzie użyto <xref:System.Data.EntityClient.EntityCommand> można wykonać zapytania SQL jednostki. Ta kwerenda zwraca listę rekordów, które reprezentują wystąpień tego typu jednostki kategorii. <xref:System.Data.EntityClient.EntityDataReader> Służy do uzyskiwania dostępu do rekordów danych w zestawie wyników. Aby uzyskać więcej informacji, zobacz [dostawca EntityClient dla programu Entity Framework](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).

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

Imports System
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

## <a name="linq-to-sql"></a>LINQ do SQL
Kod w tym przykładzie używa zapytania LINQ, aby zwrócić dane jako obiekty kategorie, które jest przekazywany jako typ anonimowy, który zawiera tylko właściwości CategoryID i CategoryName. Ten przykład jest oparty na kontekście danych Northwind. Aby uzyskać więcej informacji, zobacz [wprowadzenie](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).

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

Imports System
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

## <a name="see-also"></a>Zobacz także
 [Omówienie ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Tworzenie aplikacji do danych](https://msdn.microsoft.com/library/ab334d5f-4f49-4346-bce0-3325d6130b3e)  
 [Wykonywanie zapytań z modelem EDM (Entity Framework zadania)](https://msdn.microsoft.com/187f1caa-e4d3-4e31-bd99-5d5c2b329c77)  
 [Porady: wykonywanie zapytania, które zwraca obiekty typu anonimowego](https://msdn.microsoft.com/3b264025-e911-4d73-90ce-992d2b9d189d)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)  
