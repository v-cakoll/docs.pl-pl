---
title: Transakcje rozproszone Oracle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7c48232bb204b71c662a99bf210ad54fc3ee9eb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="oracle-distributed-transactions"></a>Transakcje rozproszone Oracle
<xref:System.Data.OracleClient.OracleConnection> Obiektu automatycznie rejestruje w istniejącej transakcji rozproszonej, gdy ustali, że transakcja jest aktywna. Automatyczne transakcji rejestracji występuje, gdy połączenie jest otwarte lub pobrać z puli połączeń. Auto rejestracji w istniejącej transakcji można wyłączyć, określając  
  
```  
Enlist=false  
```  
  
 jako parametr ciągu połączenia dla <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Zobacz też  
 [Oracle i ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
