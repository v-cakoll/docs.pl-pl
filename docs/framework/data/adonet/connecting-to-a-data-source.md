---
title: Nawiązywanie połączenia ze źródłem danych
deescription: Learn about Connection objects, used to connect to data sources in ADO.NET. The Connection object you choose depends on the type of data source.
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: a14fe179cf2fc8714a54e52252c53bd71346cad3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287080"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="1a9c8-102">Nawiązywanie połączenia ze źródłem danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1a9c8-102">Connecting to a Data Source in ADO.NET</span></span>

<span data-ttu-id="1a9c8-103">W programie ADO.NET do łączenia się z określonym źródłem danych jest używany obiekt **połączenia** , dostarczając wymagane informacje o uwierzytelnianiu w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="1a9c8-103">In ADO.NET, you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="1a9c8-104">Używany obiekt **połączenia** zależy od typu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="1a9c8-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="1a9c8-105">Każdy dostawca danych .NET Framework dołączony do .NET Framework ma <xref:System.Data.Common.DbConnection> obiekt: Dostawca danych .NET Framework dla OLE DB zawiera obiekt, .NET Framework dostawca danych dla <xref:System.Data.OleDb.OleDbConnection> SQL Server zawiera obiekt <xref:System.Data.SqlClient.SqlConnection> , .NET Framework dostawca danych dla ODBC zawiera obiekt, a .NET Framework dostawca danych <xref:System.Data.Odbc.OdbcConnection> dla programu Oracle zawiera <xref:System.Data.OracleClient.OracleConnection> obiekt.</span><span class="sxs-lookup"><span data-stu-id="1a9c8-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1a9c8-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1a9c8-106">In This Section</span></span>  
 <span data-ttu-id="1a9c8-107">[Nawiązywanie połączenia](establishing-the-connection.md)</span><span class="sxs-lookup"><span data-stu-id="1a9c8-107">[Establishing the Connection](establishing-the-connection.md)</span></span>\
 <span data-ttu-id="1a9c8-108">Opisuje sposób użycia obiektu **połączenia** w celu nawiązania połączenia ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="1a9c8-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 <span data-ttu-id="1a9c8-109">[Zdarzenia połączenia](connection-events.md)</span><span class="sxs-lookup"><span data-stu-id="1a9c8-109">[Connection Events](connection-events.md)</span></span>\
 <span data-ttu-id="1a9c8-110">Opisuje sposób użycia zdarzenia **InfoMessage** do pobierania komunikatów informacyjnych ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="1a9c8-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a9c8-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a9c8-111">See also</span></span>

- [<span data-ttu-id="1a9c8-112">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="1a9c8-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="1a9c8-113">Buforowanie połączeń</span><span class="sxs-lookup"><span data-stu-id="1a9c8-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="1a9c8-114">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="1a9c8-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="1a9c8-115">Elementy DataAdapter i DataReader</span><span class="sxs-lookup"><span data-stu-id="1a9c8-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="1a9c8-116">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="1a9c8-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="1a9c8-117">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1a9c8-117">ADO.NET Overview</span></span>](ado-net-overview.md)
