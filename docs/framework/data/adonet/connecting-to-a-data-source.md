---
title: Nawiązywanie połączenia ze źródłem danych w ADO.NET
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 01e4048fb9c7b53b1b1907d1965f822b9a4644a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786766"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="026f5-102">Nawiązywanie połączenia ze źródłem danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="026f5-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="026f5-103">W ADO.NET używasz obiektu **połączenia** do łączenia się z określonym źródłem danych, dostarczając wymagane informacje uwierzytelniania w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="026f5-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="026f5-104">Używany obiekt **połączenia** zależy od typu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="026f5-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="026f5-105">Każdy dostawca danych .NET Framework dołączony do .NET Framework ma <xref:System.Data.Common.DbConnection> obiekt: dostawca danych .NET Framework dla OLE DB <xref:System.Data.OleDb.OleDbConnection> zawiera obiekt, .NET Framework dostawca danych dla SQL Server zawiera <xref:System.Data.SqlClient.SqlConnection> obiekt,. Dostawca danych .NET Framework dla ODBC zawiera <xref:System.Data.Odbc.OdbcConnection> obiekt, a .NET Framework dostawca danych dla programu Oracle <xref:System.Data.OracleClient.OracleConnection> zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="026f5-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="026f5-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="026f5-106">In This Section</span></span>  
 [<span data-ttu-id="026f5-107">Nawiązywanie połączenia</span><span class="sxs-lookup"><span data-stu-id="026f5-107">Establishing the Connection</span></span>](establishing-the-connection.md)  
 <span data-ttu-id="026f5-108">Opisuje sposób użycia obiektu **połączenia** w celu nawiązania połączenia ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="026f5-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="026f5-109">Zdarzenia połączenia</span><span class="sxs-lookup"><span data-stu-id="026f5-109">Connection Events</span></span>](connection-events.md)  
 <span data-ttu-id="026f5-110">Opisuje sposób użycia zdarzenia **InfoMessage** do pobierania komunikatów informacyjnych ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="026f5-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="026f5-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="026f5-111">See also</span></span>

- [<span data-ttu-id="026f5-112">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="026f5-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="026f5-113">Pula połączeń</span><span class="sxs-lookup"><span data-stu-id="026f5-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="026f5-114">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="026f5-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="026f5-115">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="026f5-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="026f5-116">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="026f5-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="026f5-117">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="026f5-117">ADO.NET Overview</span></span>](ado-net-overview.md)
