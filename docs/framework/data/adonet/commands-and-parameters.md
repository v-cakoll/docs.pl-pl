---
title: "Poleceń i parametrów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1086a8775c2bc478c91d74656cfbebc5408727ce
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="commands-and-parameters"></a><span data-ttu-id="9b478-102">Poleceń i parametrów</span><span class="sxs-lookup"><span data-stu-id="9b478-102">Commands and Parameters</span></span>
<span data-ttu-id="9b478-103">Po ustanowieniu połączenia ze źródłem danych, można wykonać polecenia i zwracają wyniki z źródła danych przy użyciu <xref:System.Data.Common.DbCommand> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9b478-103">After establishing a connection to a data source, you can execute commands and return results from the data source using a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="9b478-104">Można utworzyć przy użyciu jednego z konstruktorów polecenia dla dostawcy danych .NET Framework, które użytkownik pracuje z polecenia.</span><span class="sxs-lookup"><span data-stu-id="9b478-104">You can create a command using one of the command constructors for the .NET Framework data provider you are working with.</span></span> <span data-ttu-id="9b478-105">Konstruktory może zająć Argumenty opcjonalne, takie jak instrukcja SQL do wykonania w źródle danych <xref:System.Data.Common.DbConnection> obiekt, lub <xref:System.Data.Common.DbTransaction> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9b478-105">Constructors can take optional arguments, such as an SQL statement to execute at the data source, a <xref:System.Data.Common.DbConnection> object, or a <xref:System.Data.Common.DbTransaction> object.</span></span> <span data-ttu-id="9b478-106">Można również skonfigurować te obiekty jako właściwości polecenia.</span><span class="sxs-lookup"><span data-stu-id="9b478-106">You can also configure those objects as properties of the command.</span></span> <span data-ttu-id="9b478-107">Można również utworzyć polecenia dla konkretnego połączenia za pomocą <xref:System.Data.Common.DbConnection.CreateCommand%2A> metody `DbConnection` obiektu.</span><span class="sxs-lookup"><span data-stu-id="9b478-107">You can also create a command for a particular connection using the <xref:System.Data.Common.DbConnection.CreateCommand%2A> method of a `DbConnection` object.</span></span> <span data-ttu-id="9b478-108">Instrukcja SQL jest wykonywany przez polecenie można skonfigurować za pomocą <xref:System.Data.Common.DbCommand.CommandText%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9b478-108">The SQL statement being executed by the command can be configured using the <xref:System.Data.Common.DbCommand.CommandText%2A> property.</span></span>  
  
 <span data-ttu-id="9b478-109">Każdy dostawca danych programu .NET Framework uwzględnionych w programie .NET Framework ma `Command` obiektu.</span><span class="sxs-lookup"><span data-stu-id="9b478-109">Each .NET Framework data provider included with the .NET Framework has a `Command` object.</span></span> <span data-ttu-id="9b478-110">.NET Framework Data Provider for OLE DB zawiera <xref:System.Data.OleDb.OleDbCommand> obiekt dostawcy danych programu .NET Framework dla programu SQL Server zawiera <xref:System.Data.SqlClient.SqlCommand> obiekt dostawcy danych programu .NET Framework dla ODBC obejmuje <xref:System.Data.Odbc.OdbcCommand> obiektu i .NET Framework Dostawca danych dla Oracle zawiera <xref:System.Data.OracleClient.OracleCommand> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9b478-110">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b478-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9b478-111">In This Section</span></span>  
 [<span data-ttu-id="9b478-112">Wykonywanie polecenia</span><span class="sxs-lookup"><span data-stu-id="9b478-112">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 <span data-ttu-id="9b478-113">W tym artykule opisano ADO.NET `Command` obiekt i jak z niego korzystać do wykonywania zapytań i poleceń względem źródła danych.</span><span class="sxs-lookup"><span data-stu-id="9b478-113">Describes the ADO.NET `Command` object and how to use it to execute queries and commands against a data source.</span></span>  
  
 [<span data-ttu-id="9b478-114">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="9b478-114">Configuring Parameters and Parameter Data Types</span></span>](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 <span data-ttu-id="9b478-115">Zawiera opis pracy z `Command` parametrów, w tym kierunku, typy danych i składnia parametru.</span><span class="sxs-lookup"><span data-stu-id="9b478-115">Describes working with `Command` parameters, including direction, data types, and parameter syntax.</span></span>  
  
 [<span data-ttu-id="9b478-116">Generowanie poleceń za pomocą CommandBuilders</span><span class="sxs-lookup"><span data-stu-id="9b478-116">Generating Commands with CommandBuilders</span></span>](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md)  
 <span data-ttu-id="9b478-117">Informacje dotyczące używania polecenia konstruktorów mają być automatycznie generowane polecenia INSERT, UPDATE i DELETE dla `DataAdapter` mający pojedynczej tabeli polecenia wyboru.</span><span class="sxs-lookup"><span data-stu-id="9b478-117">Describes how to use command builders to automatically generate INSERT, UPDATE, and DELETE commands for a `DataAdapter` that has a single-table SELECT command.</span></span>  
  
 [<span data-ttu-id="9b478-118">Uzyskiwanie pojedynczej wartości z bazy danych</span><span class="sxs-lookup"><span data-stu-id="9b478-118">Obtaining a Single Value from a Database</span></span>](../../../../docs/framework/data/adonet/obtaining-a-single-value-from-a-database.md)  
 <span data-ttu-id="9b478-119">Informacje dotyczące używania `ExecuteScalar` metody `Command` obiektu do zwrócenia pojedynczej wartości z zapytania do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9b478-119">Describes how to use the `ExecuteScalar` method of a `Command` object to return a single value from a database query.</span></span>  
  
 [<span data-ttu-id="9b478-120">Używanie poleceń do modyfikacji danych</span><span class="sxs-lookup"><span data-stu-id="9b478-120">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 <span data-ttu-id="9b478-121">Informacje dotyczące używania dostawcy danych można wykonać przechowywanych danych lub procedury instrukcje języka definicji (DDL).</span><span class="sxs-lookup"><span data-stu-id="9b478-121">Describes how to use a data provider to execute stored procedures or data definition language (DDL) statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b478-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b478-122">See Also</span></span>  
 [<span data-ttu-id="9b478-123">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="9b478-123">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="9b478-124">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="9b478-124">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="9b478-125">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="9b478-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="9b478-126">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="9b478-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
