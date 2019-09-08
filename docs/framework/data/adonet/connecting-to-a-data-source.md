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
# <a name="connecting-to-a-data-source-in-adonet"></a>Nawiązywanie połączenia ze źródłem danych w ADO.NET
W ADO.NET używasz obiektu **połączenia** do łączenia się z określonym źródłem danych, dostarczając wymagane informacje uwierzytelniania w parametrach połączenia. Używany obiekt **połączenia** zależy od typu źródła danych.  
  
 Każdy dostawca danych .NET Framework dołączony do .NET Framework ma <xref:System.Data.Common.DbConnection> obiekt: dostawca danych .NET Framework dla OLE DB <xref:System.Data.OleDb.OleDbConnection> zawiera obiekt, .NET Framework dostawca danych dla SQL Server zawiera <xref:System.Data.SqlClient.SqlConnection> obiekt,. Dostawca danych .NET Framework dla ODBC zawiera <xref:System.Data.Odbc.OdbcConnection> obiekt, a .NET Framework dostawca danych dla programu Oracle <xref:System.Data.OracleClient.OracleConnection> zawiera obiekt.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Nawiązywanie połączenia](establishing-the-connection.md)  
 Opisuje sposób użycia obiektu **połączenia** w celu nawiązania połączenia ze źródłem danych.  
  
 [Zdarzenia połączenia](connection-events.md)  
 Opisuje sposób użycia zdarzenia **InfoMessage** do pobierania komunikatów informacyjnych ze źródła danych.  
  
## <a name="see-also"></a>Zobacz także

- [Parametry połączeń](connection-strings.md)
- [Pula połączeń](connection-pooling.md)
- [Polecenia i parametry](commands-and-parameters.md)
- [Elementy DataAdapter i DataReaders](dataadapters-and-datareaders.md)
- [Transakcje i współbieżność](transactions-and-concurrency.md)
- [Omówienie ADO.NET](ado-net-overview.md)
