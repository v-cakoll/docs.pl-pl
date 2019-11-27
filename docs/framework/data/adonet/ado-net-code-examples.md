---
title: Przykłady kodu ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: a66ae2b2b8bed95fd38b71a39682a2a7f42be218
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430804"
---
# <a name="adonet-code-examples"></a><span data-ttu-id="81981-102">Przykłady kodu ADO.NET</span><span class="sxs-lookup"><span data-stu-id="81981-102">ADO.NET code examples</span></span>
<span data-ttu-id="81981-103">Na listach w tym temacie przedstawiono sposób pobierania danych z bazy danych przy użyciu następujących technologii ADO.NET:</span><span class="sxs-lookup"><span data-stu-id="81981-103">The code listings in this topic demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="81981-104">ADO.NET dostawcy danych:</span><span class="sxs-lookup"><span data-stu-id="81981-104">ADO.NET data providers:</span></span>

  - <span data-ttu-id="81981-105">[Klient SqlClient](#sqlclient) (`System.Data.SqlClient`)</span><span class="sxs-lookup"><span data-stu-id="81981-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="81981-106">[OLEDB](#oledb) (`System.Data.OleDb`)</span><span class="sxs-lookup"><span data-stu-id="81981-106">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="81981-107">[ODBC](#odbc) (`System.Data.Odbc`)</span><span class="sxs-lookup"><span data-stu-id="81981-107">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="81981-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span><span class="sxs-lookup"><span data-stu-id="81981-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="81981-109">ADO.NET Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="81981-109">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="81981-110">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="81981-110">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="81981-111">Wpisane ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="81981-111">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="81981-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span><span class="sxs-lookup"><span data-stu-id="81981-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="81981-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="81981-113">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="81981-114">Przykłady dostawcy danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="81981-114">ADO.NET data provider examples</span></span>
<span data-ttu-id="81981-115">Poniższe listy kodu przedstawiają sposób pobierania danych z bazy danych przy użyciu dostawców danych ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="81981-115">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="81981-116">Dane są zwracane w `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="81981-116">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="81981-117">Aby uzyskać więcej informacji, zobacz [pobieranie danych za pomocą elementu DataReader](retrieving-data-using-a-datareader.md).</span><span class="sxs-lookup"><span data-stu-id="81981-117">For more information, see [Retrieving Data Using a DataReader](retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="81981-118">SqlClient</span><span class="sxs-lookup"><span data-stu-id="81981-118">SqlClient</span></span>
<span data-ttu-id="81981-119">W kodzie w tym przykładzie przyjęto założenie, że można nawiązać połączenie z przykładową bazą danych `Northwind` w Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="81981-119">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft SQL Server.</span></span> <span data-ttu-id="81981-120">Kod tworzy <xref:System.Data.SqlClient.SqlCommand> do wybierania wierszy z tabeli Products, dodając <xref:System.Data.SqlClient.SqlParameter>, aby ograniczyć wyniki do wierszy o wartości CenaJednostkowa większej niż określona wartość parametru, w tym przypadku 5.</span><span class="sxs-lookup"><span data-stu-id="81981-120">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="81981-121"><xref:System.Data.SqlClient.SqlConnection> jest otwarty wewnątrz bloku `using`, co zapewnia, że zasoby są zamykane i usuwane po zakończeniu działania kodu.</span><span class="sxs-lookup"><span data-stu-id="81981-121">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="81981-122">Kod wykonuje polecenie przy użyciu <xref:System.Data.SqlClient.SqlDataReader>i wyświetla wyniki w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="81981-122">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="81981-123">OleDb</span><span class="sxs-lookup"><span data-stu-id="81981-123">OleDb</span></span>
<span data-ttu-id="81981-124">W kodzie w tym przykładzie przyjęto założenie, że można nawiązać połączenie z przykładową bazą danych Northwind programu Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="81981-124">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="81981-125">Kod tworzy <xref:System.Data.OleDb.OleDbCommand> do wybierania wierszy z tabeli Products, dodając <xref:System.Data.OleDb.OleDbParameter>, aby ograniczyć wyniki do wierszy o wartości CenaJednostkowa większej niż określona wartość parametru, w tym przypadku 5.</span><span class="sxs-lookup"><span data-stu-id="81981-125">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="81981-126"><xref:System.Data.OleDb.OleDbConnection> jest otwarty wewnątrz bloku `using`, co zapewnia, że zasoby są zamykane i usuwane po zakończeniu działania kodu.</span><span class="sxs-lookup"><span data-stu-id="81981-126">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="81981-127">Kod wykonuje polecenie przy użyciu <xref:System.Data.OleDb.OleDbDataReader>i wyświetla wyniki w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="81981-127">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="81981-128">Odbc</span><span class="sxs-lookup"><span data-stu-id="81981-128">Odbc</span></span>
<span data-ttu-id="81981-129">W kodzie w tym przykładzie przyjęto założenie, że można nawiązać połączenie z przykładową bazą danych Northwind programu Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="81981-129">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="81981-130">Kod tworzy <xref:System.Data.Odbc.OdbcCommand> do wybierania wierszy z tabeli Products, dodając <xref:System.Data.Odbc.OdbcParameter>, aby ograniczyć wyniki do wierszy o wartości CenaJednostkowa większej niż określona wartość parametru, w tym przypadku 5.</span><span class="sxs-lookup"><span data-stu-id="81981-130">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="81981-131"><xref:System.Data.Odbc.OdbcConnection> jest otwarty wewnątrz bloku `using`, co zapewnia, że zasoby są zamykane i usuwane po zakończeniu działania kodu.</span><span class="sxs-lookup"><span data-stu-id="81981-131">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="81981-132">Kod wykonuje polecenie przy użyciu <xref:System.Data.Odbc.OdbcDataReader>i wyświetla wyniki w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="81981-132">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)] 
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)] 

### <a name="oracleclient"></a><span data-ttu-id="81981-133">OracleClient</span><span class="sxs-lookup"><span data-stu-id="81981-133">OracleClient</span></span>
<span data-ttu-id="81981-134">Kod w tym przykładzie założono połączenie z DEMONSTRACJą. Klient na serwerze Oracle.</span><span class="sxs-lookup"><span data-stu-id="81981-134">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="81981-135">Należy również dodać odwołanie do pliku System. Data. OracleClient. dll.</span><span class="sxs-lookup"><span data-stu-id="81981-135">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="81981-136">Kod zwraca dane w <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="81981-136">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="81981-137">Przykłady Entity Framework</span><span class="sxs-lookup"><span data-stu-id="81981-137">Entity Framework examples</span></span>
<span data-ttu-id="81981-138">Poniższe listy kodu pokazują, jak pobrać dane ze źródła danych, badając jednostki w Entity Data Model (EDM).</span><span class="sxs-lookup"><span data-stu-id="81981-138">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="81981-139">Te przykłady używają modelu opartego na przykładowej bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="81981-139">These examples use a model based on the Northwind sample database.</span></span> <span data-ttu-id="81981-140">Aby uzyskać więcej informacji na temat Entity Framework, zobacz [Entity Framework Omówienie](./ef/overview.md).</span><span class="sxs-lookup"><span data-stu-id="81981-140">For more information about Entity Framework, see [Entity Framework Overview](./ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="81981-141">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="81981-141">LINQ to Entities</span></span>
<span data-ttu-id="81981-142">Kod w tym przykładzie używa zapytania LINQ do zwracania danych jako obiektów kategorii, które są rzutowane jako typ anonimowy, który zawiera tylko właściwości IDKategorii i CategoryName.</span><span class="sxs-lookup"><span data-stu-id="81981-142">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="81981-143">Aby uzyskać więcej informacji, zobacz [LINQ to Entities przegląd](./ef/language-reference/linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="81981-143">For more information, see [LINQ to Entities Overview](./ef/language-reference/linq-to-entities.md).</span></span>

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

### <a name="typed-objectquery"></a><span data-ttu-id="81981-144">Wpisane ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="81981-144">Typed ObjectQuery</span></span>
<span data-ttu-id="81981-145">Kod w tym przykładzie używa <xref:System.Data.Objects.ObjectQuery%601> do zwracania danych jako obiektów kategorii.</span><span class="sxs-lookup"><span data-stu-id="81981-145">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="81981-146">Aby uzyskać więcej informacji, zobacz [zapytania dotyczące obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="81981-146">For more information, see [Object Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span></span>

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

### <a name="entityclient"></a><span data-ttu-id="81981-147">EntityClient</span><span class="sxs-lookup"><span data-stu-id="81981-147">EntityClient</span></span>
<span data-ttu-id="81981-148">Kod w tym przykładzie używa <xref:System.Data.EntityClient.EntityCommand> do wykonania kwerendy Entity SQLowej.</span><span class="sxs-lookup"><span data-stu-id="81981-148">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="81981-149">To zapytanie zwraca listę rekordów reprezentujących wystąpienia typu jednostki kategorii.</span><span class="sxs-lookup"><span data-stu-id="81981-149">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="81981-150"><xref:System.Data.EntityClient.EntityDataReader> jest używany do uzyskiwania dostępu do rekordów danych w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="81981-150">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="81981-151">Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="81981-151">For more information, see [EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).</span></span>

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

## <a name="linq-to-sql"></a><span data-ttu-id="81981-152">LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="81981-152">LINQ to SQL</span></span>
<span data-ttu-id="81981-153">Kod w tym przykładzie używa zapytania LINQ do zwracania danych jako obiektów kategorii, które są rzutowane jako typ anonimowy, który zawiera tylko właściwości IDKategorii i CategoryName.</span><span class="sxs-lookup"><span data-stu-id="81981-153">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="81981-154">Ten przykład jest oparty na kontekście danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="81981-154">This example is based on the Northwind data context.</span></span> <span data-ttu-id="81981-155">Aby uzyskać więcej informacji, zobacz [wprowadzenie](./sql/linq/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="81981-155">For more information, see [Getting Started](./sql/linq/getting-started.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="81981-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81981-156">See also</span></span>

- [<span data-ttu-id="81981-157">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="81981-157">ADO.NET Overview</span></span>](ado-net-overview.md)
- [<span data-ttu-id="81981-158">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="81981-158">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- <span data-ttu-id="81981-159">[Tworzenie aplikacji danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="81981-159">[Creating Data Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span></span>
- <span data-ttu-id="81981-160">[Wykonywanie zapytania dotyczącego Entity Data Model (zadania Entity Framework)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="81981-160">[Querying an Entity Data Model (Entity Framework Tasks)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span></span>
- <span data-ttu-id="81981-161">[Instrukcje: wykonywanie zapytania, które zwraca obiekty typu anonimowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="81981-161">[How to: Execute a Query that Returns Anonymous Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>
