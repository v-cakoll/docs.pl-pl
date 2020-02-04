---
title: Nawiązywanie połączenia ze źródłem danych
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 84dc15c0965b7ac8209bd9115d611162e57d6dda
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980252"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="752c1-102">Nawiązywanie połączenia ze źródłem danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="752c1-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="752c1-103">W ADO.NET używasz obiektu **połączenia** do łączenia się z określonym źródłem danych, dostarczając wymagane informacje uwierzytelniania w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="752c1-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="752c1-104">Używany obiekt **połączenia** zależy od typu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="752c1-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="752c1-105">Każdy dostawca danych .NET Framework dołączony do .NET Framework ma <xref:System.Data.Common.DbConnection> obiekt: .NET Framework Dostawca danych dla OLE DB zawiera obiekt <xref:System.Data.OleDb.OleDbConnection>, .NET Framework dostawca danych dla SQL Server zawiera obiekt <xref:System.Data.SqlClient.SqlConnection>, .NET Framework dostawca danych dla ODBC zawiera obiekt <xref:System.Data.Odbc.OdbcConnection>, a .NET Framework dostawca danych dla programu Oracle zawiera obiekt <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="752c1-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="752c1-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="752c1-106">In This Section</span></span>  
 [<span data-ttu-id="752c1-107">Nawiązywanie połączenia</span><span class="sxs-lookup"><span data-stu-id="752c1-107">Establishing the Connection</span></span>](establishing-the-connection.md)  
 <span data-ttu-id="752c1-108">Opisuje sposób użycia obiektu **połączenia** w celu nawiązania połączenia ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="752c1-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="752c1-109">Zdarzenia połączenia</span><span class="sxs-lookup"><span data-stu-id="752c1-109">Connection Events</span></span>](connection-events.md)  
 <span data-ttu-id="752c1-110">Opisuje sposób użycia zdarzenia **InfoMessage** do pobierania komunikatów informacyjnych ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="752c1-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="752c1-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="752c1-111">See also</span></span>

- [<span data-ttu-id="752c1-112">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="752c1-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="752c1-113">Pula połączeń</span><span class="sxs-lookup"><span data-stu-id="752c1-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="752c1-114">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="752c1-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="752c1-115">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="752c1-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="752c1-116">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="752c1-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="752c1-117">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="752c1-117">ADO.NET Overview</span></span>](ado-net-overview.md)
