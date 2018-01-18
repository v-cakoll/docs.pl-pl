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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1df18730d3a4428f245fe4222dafec0eaf6c08a5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="connecting-to-a-data-source-in-adonet"></a>Połączenie ze źródłem danych w ADO.NET
W ADO.NET użyjesz **połączenia** obiektu nawiązywania połączenia ze źródłem danych określonym przez dostarczenie informacji na potrzeby uwierzytelniania w parametrach połączenia. **Połączenia** obiektu używasz zależy od typu źródła danych.  
  
 Każdy dostawca danych programu .NET Framework uwzględnionych w programie .NET Framework ma <xref:System.Data.Common.DbConnection> obiektu: .NET Framework Data Provider for OLE DB zawiera <xref:System.Data.OleDb.OleDbConnection> obiekt dostawcy danych programu .NET Framework dla programu SQL Server zawiera <xref:System.Data.SqlClient.SqlConnection> obiektu,. Obejmuje dostawcy NET Framework Data Provider for ODBC <xref:System.Data.Odbc.OdbcConnection> obiektu i .NET Framework Data Provider for Oracle obejmuje <xref:System.Data.OracleClient.OracleConnection> obiektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Nawiązywanie połączenia](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 Informacje dotyczące używania **połączenia** obiekt do nawiązania połączenia ze źródłem danych.  
  
 [Zdarzenia połączenia](../../../../docs/framework/data/adonet/connection-events.md)  
 Informacje dotyczące używania **InfoMessage** zdarzenie, aby pobrać komunikaty informacyjne ze źródła danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Parametry połączeń](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Pula połączeń](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
