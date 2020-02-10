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
# <a name="connecting-to-a-data-source-in-adonet"></a>Nawiązywanie połączenia ze źródłem danych w ADO.NET

W programie ADO.NET do łączenia się z określonym źródłem danych jest używany obiekt **połączenia** , dostarczając wymagane informacje o uwierzytelnianiu w parametrach połączenia. Używany obiekt **połączenia** zależy od typu źródła danych.  
  
 Każdy dostawca danych .NET Framework dołączony do .NET Framework ma <xref:System.Data.Common.DbConnection> obiekt: .NET Framework Dostawca danych dla OLE DB zawiera obiekt <xref:System.Data.OleDb.OleDbConnection>, .NET Framework dostawca danych dla SQL Server zawiera obiekt <xref:System.Data.SqlClient.SqlConnection>, .NET Framework dostawca danych dla ODBC zawiera obiekt <xref:System.Data.Odbc.OdbcConnection>, a .NET Framework dostawca danych dla programu Oracle zawiera obiekt <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Ustanawianie\ połączenia](establishing-the-connection.md)
 Opisuje sposób użycia obiektu **połączenia** w celu nawiązania połączenia ze źródłem danych.  
  
 \ [zdarzeń połączenia](connection-events.md)
 Opisuje sposób użycia zdarzenia **InfoMessage** do pobierania komunikatów informacyjnych ze źródła danych.  
  
## <a name="see-also"></a>Zobacz też

- [Parametry połączeń](connection-strings.md)
- [Buforowanie połączeń](connection-pooling.md)
- [Polecenia i parametry](commands-and-parameters.md)
- [Elementy DataAdapter i DataReaders](dataadapters-and-datareaders.md)
- [Transakcje i współbieżność](transactions-and-concurrency.md)
- [Omówienie ADO.NET](ado-net-overview.md)
