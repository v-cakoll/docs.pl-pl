---
title: "Połączenie ze źródłem danych w ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 01a7342d6e081bec88aeef2c55461be2d936e4a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="90666-102">Połączenie ze źródłem danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="90666-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="90666-103">W ADO.NET użyjesz **połączenia** obiektu nawiązywania połączenia ze źródłem danych określonym przez dostarczenie informacji na potrzeby uwierzytelniania w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="90666-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="90666-104">**Połączenia** obiektu używasz zależy od typu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="90666-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="90666-105">Każdy dostawca danych programu .NET Framework uwzględnionych w programie .NET Framework ma <xref:System.Data.Common.DbConnection> obiektu: .NET Framework Data Provider for OLE DB zawiera <xref:System.Data.OleDb.OleDbConnection> obiekt dostawcy danych programu .NET Framework dla programu SQL Server zawiera <xref:System.Data.SqlClient.SqlConnection> obiektu,. Obejmuje dostawcy NET Framework Data Provider for ODBC <xref:System.Data.Odbc.OdbcConnection> obiektu i .NET Framework Data Provider for Oracle obejmuje <xref:System.Data.OracleClient.OracleConnection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="90666-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90666-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="90666-106">In This Section</span></span>  
 [<span data-ttu-id="90666-107">Nawiązywanie połączenia</span><span class="sxs-lookup"><span data-stu-id="90666-107">Establishing the Connection</span></span>](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 <span data-ttu-id="90666-108">Informacje dotyczące używania **połączenia** obiekt do nawiązania połączenia ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="90666-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="90666-109">Zdarzenia połączenia</span><span class="sxs-lookup"><span data-stu-id="90666-109">Connection Events</span></span>](../../../../docs/framework/data/adonet/connection-events.md)  
 <span data-ttu-id="90666-110">Informacje dotyczące używania **InfoMessage** zdarzenie, aby pobrać komunikaty informacyjne ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="90666-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90666-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90666-111">See Also</span></span>  
 [<span data-ttu-id="90666-112">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="90666-112">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="90666-113">Pula połączeń</span><span class="sxs-lookup"><span data-stu-id="90666-113">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [<span data-ttu-id="90666-114">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="90666-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="90666-115">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="90666-115">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="90666-116">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="90666-116">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="90666-117">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="90666-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
