---
title: Nawiązywanie połączenia ze źródłem danych
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 206a4f741b6bf711b51da794e23f779c2bea6fa0
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094452"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="62129-102">Nawiązywanie połączenia ze źródłem danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="62129-102">Connecting to a Data Source in ADO.NET</span></span>

<span data-ttu-id="62129-103">W programie ADO.NET do łączenia się z określonym źródłem danych jest używany obiekt **połączenia** , dostarczając wymagane informacje o uwierzytelnianiu w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="62129-103">In ADO.NET, you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="62129-104">Używany obiekt **połączenia** zależy od typu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="62129-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="62129-105">Każdy dostawca danych .NET Framework dołączony do .NET Framework ma <xref:System.Data.Common.DbConnection> obiekt: .NET Framework Dostawca danych dla OLE DB zawiera obiekt <xref:System.Data.OleDb.OleDbConnection>, .NET Framework dostawca danych dla SQL Server zawiera obiekt <xref:System.Data.SqlClient.SqlConnection>, .NET Framework dostawca danych dla ODBC zawiera obiekt <xref:System.Data.Odbc.OdbcConnection>, a .NET Framework dostawca danych dla programu Oracle zawiera obiekt <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="62129-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="62129-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="62129-106">In This Section</span></span>  
 <span data-ttu-id="62129-107">[Ustanawianie\ połączenia](establishing-the-connection.md)</span><span class="sxs-lookup"><span data-stu-id="62129-107">[Establishing the Connection](establishing-the-connection.md)\</span></span>
 <span data-ttu-id="62129-108">Opisuje sposób użycia obiektu **połączenia** w celu nawiązania połączenia ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="62129-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 <span data-ttu-id="62129-109">\ [zdarzeń połączenia](connection-events.md)</span><span class="sxs-lookup"><span data-stu-id="62129-109">[Connection Events](connection-events.md)\</span></span>
 <span data-ttu-id="62129-110">Opisuje sposób użycia zdarzenia **InfoMessage** do pobierania komunikatów informacyjnych ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="62129-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62129-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62129-111">See also</span></span>

- [<span data-ttu-id="62129-112">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="62129-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="62129-113">Buforowanie połączeń</span><span class="sxs-lookup"><span data-stu-id="62129-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="62129-114">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="62129-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="62129-115">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="62129-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="62129-116">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="62129-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="62129-117">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="62129-117">ADO.NET Overview</span></span>](ado-net-overview.md)
