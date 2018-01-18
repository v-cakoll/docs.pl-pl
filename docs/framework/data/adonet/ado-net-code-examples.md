---
title: "Przykłady kodu dla ADO.NET"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-ado
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ea26b4297f587a449b8484947257081e0d11906c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="adonet-code-examples"></a>Przykłady kodu dla ADO.NET
Zamieszczone w tym temacie przedstawiają sposób pobierania danych z bazy danych przy użyciu następujących technologii ADO.NET:

- Dostawcy danych ADO.NET:

  - [SqlClient](#sqlclient) (`System.Data.SqlClient`)

  - [OleDb](#oledb) (`System.Data.OleDb`)

  - [ODBC](#odbc) (`System.Data.Odbc`)

  - [OracleClient](#oracleclient) (`System.Data.OracleClient`)

- ADO.NET Entity Framework:

  - [LINQ to Entities](#linq-to-entities)

  - [Typizowany ObjectQuery](#typed-objectquery)

  - [Dostawca EntityClient](#entityclient) (`System.Data.EntityClient`)

- [LINQ to SQL](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a>Przykłady dostawcy danych ADO.NET
Następujące listy kodu przedstawiają sposób pobierać dane z bazy danych przy użyciu dostawcy danych ADO.NET. Dane są zwracane w `DataReader`. Aby uzyskać więcej informacji, zobacz [pobierania danych przy użyciu elementu DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).

### <a name="sqlclient"></a>SqlClient
Kod w tym przykładzie przyjęto założenie, że można nawiązać `Northwind` przykładowej bazy danych w systemie Microsoft [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]. Kod tworzy <xref:System.Data.SqlClient.SqlCommand> do wybrania wierszy z tabeli Produkty Dodawanie <xref:System.Data.SqlClient.SqlParameter> Aby ograniczyć wyniki do wiersze z UnitPrice większa niż podana wartość parametru, w tym przypadku 5. <xref:System.Data.SqlClient.SqlConnection> Jest otwarty w `using` bloku, który zapewnia, że zasoby są zamknięty i usunięty, gdy kod jest kończona. Kod wykonywany polecenia przy użyciu <xref:System.Data.SqlClient.SqlDataReader>i wyświetla wyniki w oknie konsoli.

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a>OLE DB
Kod w tym przykładzie przyjęto założenie, czy możesz nawiązać przykładowej bazy danych Northwind dostępu firmy Microsoft. Kod tworzy <xref:System.Data.OleDb.OleDbCommand> do wybrania wierszy z tabeli Produkty Dodawanie <xref:System.Data.OleDb.OleDbParameter> Aby ograniczyć wyniki do wiersze z UnitPrice większa niż podana wartość parametru, w tym przypadku 5. <xref:System.Data.OleDb.OleDbConnection> Jest otwarty wewnątrz `using` bloku, który zapewnia, że zasoby są zamknięty i usunięty, gdy kod jest kończona. Kod wykonywany polecenia przy użyciu <xref:System.Data.OleDb.OleDbDataReader>i wyświetla wyniki w oknie konsoli.

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a>Odbc
Kod w tym przykładzie przyjęto założenie, czy możesz nawiązać przykładowej bazy danych Northwind dostępu firmy Microsoft. Kod tworzy <xref:System.Data.Odbc.OdbcCommand> do wybrania wierszy z tabeli Produkty Dodawanie <xref:System.Data.Odbc.OdbcParameter> Aby ograniczyć wyniki do wiersze z UnitPrice większa niż podana wartość parametru, w tym przypadku 5. <xref:System.Data.Odbc.OdbcConnection> Jest otwarty w `using` bloku, który zapewnia, że zasoby są zamknięty i usunięty, gdy kod jest kończona. Kod wykonywany polecenia przy użyciu <xref:System.Data.Odbc.OdbcDataReader>i wyświetla wyniki w oknie konsoli.

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)] 
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)] 

### <a name="oracleclient"></a>OracleClient
Kod w tym przykładzie przyjęto założenie, połączenie DEMONSTRACYJNEJ. KLIENTA na serwerze programu Oracle. Należy również dodać odwołanie do System.Data.OracleClient.dll. Kod zwraca dane w <xref:System.Data.OracleClient.OracleDataReader>.

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a>Entity Framework przykłady
Poniższe listy kodu pokazują, jak można pobrać danych ze źródła danych, badając jednostek w modelu danych jednostki (EDM). Użyj tych przykładów [modelu Northwind](http://msdn.microsoft.com/74521f8c-e974-48cb-8858-c08deff52638). Aby uzyskać więcej informacji, zobacz [Omówienie struktury jednostek](../../../../docs/framework/data/adonet/ef/overview.md).

### <a name="linq-to-entities"></a>LINQ do Jednostek
Kod w tym przykładzie użyto zapytań LINQ, aby zwrócić danych jako obiekty kategorie, które jest przekazywany jako typu anonimowego, który zawiera tylko właściwości CategoryID i CategoryName. Aby uzyskać więcej informacji, zobacz [składnika LINQ to Entities omówienie](http://msdn.microsoft.com/86d87a27-c17a-45ac-b28d-72c8500333c6).

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

### <a name="typed-objectquery"></a>Typizowany ObjectQuery
W kodzie w tym przykładzie użyto <xref:System.Data.Objects.ObjectQuery%601> aby zwrócić dane jako obiekty kategorii. Aby uzyskać więcej informacji, zobacz [zapytań obiektu](http://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276).

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
W kodzie w tym przykładzie użyto <xref:System.Data.EntityClient.EntityCommand> można wykonać zapytania SQL jednostki. To zapytanie zwraca listę rekordów, które reprezentują wystąpień typu jednostki kategorii. <xref:System.Data.EntityClient.EntityDataReader> Służy do uzyskiwania dostępu do danych rekordów w zestawie wyników. Aby uzyskać więcej informacji, zobacz [dostawcy EntityClient Entity Framework](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).

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
Kod w tym przykładzie użyto zapytań LINQ, aby zwrócić danych jako obiekty kategorie, które jest przekazywany jako typu anonimowego, który zawiera tylko właściwości CategoryID i CategoryName. Ten przykład jest oparty na kontekst danych Northwind. Aby uzyskać więcej informacji, zobacz [wprowadzenie](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).

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
 [Tworzenie aplikacji danych](http://msdn.microsoft.com/library/ab334d5f-4f49-4346-bce0-3325d6130b3e)  
 [Wykonywanie zapytania modelu danych jednostki (Entity Framework zadania)](http://msdn.microsoft.com/187f1caa-e4d3-4e31-bd99-5d5c2b329c77)  
 [Porady: kwerenda zwraca obiekty typu anonimowego](http://msdn.microsoft.com/3b264025-e911-4d73-90ce-992d2b9d189d)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)  
