---
title: Łączenie ze źródłem danych w ADO.NET
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: f5788b9b0b19f32d03c917575db7b3f40324c0a2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189267"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="a8ca1-102">Łączenie ze źródłem danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8ca1-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="a8ca1-103">W ADO.NET **połączenia** obiekt, aby połączyć się z określonym źródłem danych, podając niezbędne informacje dotyczące uwierzytelniania w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="a8ca1-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="a8ca1-104">**Połączenia** obiektu użyjesz zależy od typu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a8ca1-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="a8ca1-105">Każdego dostawcy danych .NET Framework, dołączone do programu .NET Framework ma <xref:System.Data.Common.DbConnection> obiektu: .NET Framework Data Provider for OLE DB zawiera <xref:System.Data.OleDb.OleDbConnection> obiektu .NET Framework Data Provider for SQL Server zawiera <xref:System.Data.SqlClient.SqlConnection> obiektu. NET Framework Data Provider for ODBC obejmuje <xref:System.Data.Odbc.OdbcConnection> obiektu i .NET Framework Data Provider for Oracle obejmuje <xref:System.Data.OracleClient.OracleConnection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a8ca1-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8ca1-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a8ca1-106">In This Section</span></span>  
 [<span data-ttu-id="a8ca1-107">Nawiązywanie połączenia</span><span class="sxs-lookup"><span data-stu-id="a8ca1-107">Establishing the Connection</span></span>](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 <span data-ttu-id="a8ca1-108">Opisuje sposób używania **połączenia** obiektów do nawiązania połączenia ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="a8ca1-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="a8ca1-109">Zdarzenia połączenia</span><span class="sxs-lookup"><span data-stu-id="a8ca1-109">Connection Events</span></span>](../../../../docs/framework/data/adonet/connection-events.md)  
 <span data-ttu-id="a8ca1-110">Opisuje sposób używania **InfoMessage** zdarzenie, aby pobrać komunikaty informacyjne ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a8ca1-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8ca1-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8ca1-111">See Also</span></span>  
 [<span data-ttu-id="a8ca1-112">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="a8ca1-112">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="a8ca1-113">Pula połączeń</span><span class="sxs-lookup"><span data-stu-id="a8ca1-113">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [<span data-ttu-id="a8ca1-114">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="a8ca1-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="a8ca1-115">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="a8ca1-115">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="a8ca1-116">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="a8ca1-116">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="a8ca1-117">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="a8ca1-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
