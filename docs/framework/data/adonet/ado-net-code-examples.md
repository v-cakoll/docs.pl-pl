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
# <a name="adonet-code-examples"></a><span data-ttu-id="46f7b-102">Przykłady kodu dla ADO.NET</span><span class="sxs-lookup"><span data-stu-id="46f7b-102">ADO.NET code examples</span></span>
<span data-ttu-id="46f7b-103">Zamieszczone w tym temacie przedstawiają sposób pobierania danych z bazy danych przy użyciu następujących technologii ADO.NET:</span><span class="sxs-lookup"><span data-stu-id="46f7b-103">The code listings in this topic demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="46f7b-104">Dostawcy danych ADO.NET:</span><span class="sxs-lookup"><span data-stu-id="46f7b-104">ADO.NET data providers:</span></span>

  - <span data-ttu-id="46f7b-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span><span class="sxs-lookup"><span data-stu-id="46f7b-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="46f7b-106">[OleDb](#oledb) (`System.Data.OleDb`)</span><span class="sxs-lookup"><span data-stu-id="46f7b-106">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="46f7b-107">[ODBC](#odbc) (`System.Data.Odbc`)</span><span class="sxs-lookup"><span data-stu-id="46f7b-107">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="46f7b-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span><span class="sxs-lookup"><span data-stu-id="46f7b-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="46f7b-109">ADO.NET Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="46f7b-109">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="46f7b-110">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="46f7b-110">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="46f7b-111">Typizowany ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="46f7b-111">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="46f7b-112">[Dostawca EntityClient](#entityclient) (`System.Data.EntityClient`)</span><span class="sxs-lookup"><span data-stu-id="46f7b-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="46f7b-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="46f7b-113">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="46f7b-114">Przykłady dostawcy danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="46f7b-114">ADO.NET data provider examples</span></span>
<span data-ttu-id="46f7b-115">Następujące listy kodu przedstawiają sposób pobierać dane z bazy danych przy użyciu dostawcy danych ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="46f7b-115">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="46f7b-116">Dane są zwracane w `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="46f7b-116">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="46f7b-117">Aby uzyskać więcej informacji, zobacz [pobierania danych przy użyciu elementu DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).</span><span class="sxs-lookup"><span data-stu-id="46f7b-117">For more information, see [Retrieving Data Using a DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="46f7b-118">SqlClient</span><span class="sxs-lookup"><span data-stu-id="46f7b-118">SqlClient</span></span>
<span data-ttu-id="46f7b-119">Kod w tym przykładzie przyjęto założenie, że można nawiązać `Northwind` przykładowej bazy danych w systemie Microsoft [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46f7b-119">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="46f7b-120">Kod tworzy <xref:System.Data.SqlClient.SqlCommand> do wybrania wierszy z tabeli Produkty Dodawanie <xref:System.Data.SqlClient.SqlParameter> Aby ograniczyć wyniki do wiersze z UnitPrice większa niż podana wartość parametru, w tym przypadku 5.</span><span class="sxs-lookup"><span data-stu-id="46f7b-120">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="46f7b-121"><xref:System.Data.SqlClient.SqlConnection> Jest otwarty w `using` bloku, który zapewnia, że zasoby są zamknięty i usunięty, gdy kod jest kończona.</span><span class="sxs-lookup"><span data-stu-id="46f7b-121">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="46f7b-122">Kod wykonywany polecenia przy użyciu <xref:System.Data.SqlClient.SqlDataReader>i wyświetla wyniki w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="46f7b-122">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="46f7b-123">OLE DB</span><span class="sxs-lookup"><span data-stu-id="46f7b-123">OleDb</span></span>
<span data-ttu-id="46f7b-124">Kod w tym przykładzie przyjęto założenie, czy możesz nawiązać przykładowej bazy danych Northwind dostępu firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="46f7b-124">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="46f7b-125">Kod tworzy <xref:System.Data.OleDb.OleDbCommand> do wybrania wierszy z tabeli Produkty Dodawanie <xref:System.Data.OleDb.OleDbParameter> Aby ograniczyć wyniki do wiersze z UnitPrice większa niż podana wartość parametru, w tym przypadku 5.</span><span class="sxs-lookup"><span data-stu-id="46f7b-125">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="46f7b-126"><xref:System.Data.OleDb.OleDbConnection> Jest otwarty wewnątrz `using` bloku, który zapewnia, że zasoby są zamknięty i usunięty, gdy kod jest kończona.</span><span class="sxs-lookup"><span data-stu-id="46f7b-126">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="46f7b-127">Kod wykonywany polecenia przy użyciu <xref:System.Data.OleDb.OleDbDataReader>i wyświetla wyniki w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="46f7b-127">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="46f7b-128">Odbc</span><span class="sxs-lookup"><span data-stu-id="46f7b-128">Odbc</span></span>
<span data-ttu-id="46f7b-129">Kod w tym przykładzie przyjęto założenie, czy możesz nawiązać przykładowej bazy danych Northwind dostępu firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="46f7b-129">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="46f7b-130">Kod tworzy <xref:System.Data.Odbc.OdbcCommand> do wybrania wierszy z tabeli Produkty Dodawanie <xref:System.Data.Odbc.OdbcParameter> Aby ograniczyć wyniki do wiersze z UnitPrice większa niż podana wartość parametru, w tym przypadku 5.</span><span class="sxs-lookup"><span data-stu-id="46f7b-130">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="46f7b-131"><xref:System.Data.Odbc.OdbcConnection> Jest otwarty w `using` bloku, który zapewnia, że zasoby są zamknięty i usunięty, gdy kod jest kończona.</span><span class="sxs-lookup"><span data-stu-id="46f7b-131">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="46f7b-132">Kod wykonywany polecenia przy użyciu <xref:System.Data.Odbc.OdbcDataReader>i wyświetla wyniki w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="46f7b-132">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)] 
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)] 

### <a name="oracleclient"></a><span data-ttu-id="46f7b-133">OracleClient</span><span class="sxs-lookup"><span data-stu-id="46f7b-133">OracleClient</span></span>
<span data-ttu-id="46f7b-134">Kod w tym przykładzie przyjęto założenie, połączenie DEMONSTRACYJNEJ. KLIENTA na serwerze programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="46f7b-134">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="46f7b-135">Należy również dodać odwołanie do System.Data.OracleClient.dll.</span><span class="sxs-lookup"><span data-stu-id="46f7b-135">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="46f7b-136">Kod zwraca dane w <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="46f7b-136">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="46f7b-137">Entity Framework przykłady</span><span class="sxs-lookup"><span data-stu-id="46f7b-137">Entity Framework examples</span></span>
<span data-ttu-id="46f7b-138">Poniższe listy kodu pokazują, jak można pobrać danych ze źródła danych, badając jednostek w modelu danych jednostki (EDM).</span><span class="sxs-lookup"><span data-stu-id="46f7b-138">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="46f7b-139">Użyj tych przykładów [modelu Northwind](http://msdn.microsoft.com/74521f8c-e974-48cb-8858-c08deff52638).</span><span class="sxs-lookup"><span data-stu-id="46f7b-139">These examples use the [Northwind model](http://msdn.microsoft.com/74521f8c-e974-48cb-8858-c08deff52638).</span></span> <span data-ttu-id="46f7b-140">Aby uzyskać więcej informacji, zobacz [Omówienie struktury jednostek](../../../../docs/framework/data/adonet/ef/overview.md).</span><span class="sxs-lookup"><span data-stu-id="46f7b-140">For more information, see [Entity Framework Overview](../../../../docs/framework/data/adonet/ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="46f7b-141">LINQ do Jednostek</span><span class="sxs-lookup"><span data-stu-id="46f7b-141">LINQ to Entities</span></span>
<span data-ttu-id="46f7b-142">Kod w tym przykładzie użyto zapytań LINQ, aby zwrócić danych jako obiekty kategorie, które jest przekazywany jako typu anonimowego, który zawiera tylko właściwości CategoryID i CategoryName.</span><span class="sxs-lookup"><span data-stu-id="46f7b-142">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="46f7b-143">Aby uzyskać więcej informacji, zobacz [składnika LINQ to Entities omówienie](http://msdn.microsoft.com/86d87a27-c17a-45ac-b28d-72c8500333c6).</span><span class="sxs-lookup"><span data-stu-id="46f7b-143">For more information, see [LINQ to Entities Overview](http://msdn.microsoft.com/86d87a27-c17a-45ac-b28d-72c8500333c6).</span></span>

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

### <a name="typed-objectquery"></a><span data-ttu-id="46f7b-144">Typizowany ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="46f7b-144">Typed ObjectQuery</span></span>
<span data-ttu-id="46f7b-145">W kodzie w tym przykładzie użyto <xref:System.Data.Objects.ObjectQuery%601> aby zwrócić dane jako obiekty kategorii.</span><span class="sxs-lookup"><span data-stu-id="46f7b-145">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="46f7b-146">Aby uzyskać więcej informacji, zobacz [zapytań obiektu](http://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276).</span><span class="sxs-lookup"><span data-stu-id="46f7b-146">For more information, see [Object Queries](http://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276).</span></span>

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

### <a name="entityclient"></a><span data-ttu-id="46f7b-147">EntityClient</span><span class="sxs-lookup"><span data-stu-id="46f7b-147">EntityClient</span></span>
<span data-ttu-id="46f7b-148">W kodzie w tym przykładzie użyto <xref:System.Data.EntityClient.EntityCommand> można wykonać zapytania SQL jednostki.</span><span class="sxs-lookup"><span data-stu-id="46f7b-148">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="46f7b-149">To zapytanie zwraca listę rekordów, które reprezentują wystąpień typu jednostki kategorii.</span><span class="sxs-lookup"><span data-stu-id="46f7b-149">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="46f7b-150"><xref:System.Data.EntityClient.EntityDataReader> Służy do uzyskiwania dostępu do danych rekordów w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="46f7b-150">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="46f7b-151">Aby uzyskać więcej informacji, zobacz [dostawcy EntityClient Entity Framework](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="46f7b-151">For more information, see [EntityClient Provider for the Entity Framework](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>

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

## <a name="linq-to-sql"></a><span data-ttu-id="46f7b-152">LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="46f7b-152">LINQ to SQL</span></span>
<span data-ttu-id="46f7b-153">Kod w tym przykładzie użyto zapytań LINQ, aby zwrócić danych jako obiekty kategorie, które jest przekazywany jako typu anonimowego, który zawiera tylko właściwości CategoryID i CategoryName.</span><span class="sxs-lookup"><span data-stu-id="46f7b-153">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="46f7b-154">Ten przykład jest oparty na kontekst danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="46f7b-154">This example is based on the Northwind data context.</span></span> <span data-ttu-id="46f7b-155">Aby uzyskać więcej informacji, zobacz [wprowadzenie](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="46f7b-155">For more information, see [Getting Started](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="46f7b-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46f7b-156">See also</span></span>
 [<span data-ttu-id="46f7b-157">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="46f7b-157">ADO.NET Overview</span></span>](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [<span data-ttu-id="46f7b-158">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="46f7b-158">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="46f7b-159">Tworzenie aplikacji danych</span><span class="sxs-lookup"><span data-stu-id="46f7b-159">Creating Data Applications</span></span>](http://msdn.microsoft.com/library/ab334d5f-4f49-4346-bce0-3325d6130b3e)  
 [<span data-ttu-id="46f7b-160">Wykonywanie zapytania modelu danych jednostki (Entity Framework zadania)</span><span class="sxs-lookup"><span data-stu-id="46f7b-160">Querying an Entity Data Model (Entity Framework Tasks)</span></span>](http://msdn.microsoft.com/187f1caa-e4d3-4e31-bd99-5d5c2b329c77)  
 [<span data-ttu-id="46f7b-161">Porady: kwerenda zwraca obiekty typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="46f7b-161">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](http://msdn.microsoft.com/3b264025-e911-4d73-90ce-992d2b9d189d)  
 [<span data-ttu-id="46f7b-162">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="46f7b-162">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)  
