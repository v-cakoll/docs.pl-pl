---
title: Transakcje rozproszone Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 8e7530621254881402570b59b47a22052b40f2b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713251"
---
# <a name="oracle-distributed-transactions"></a>Transakcje rozproszone Oracle
<xref:System.Data.OracleClient.OracleConnection> Obiektu pozyskuje automatycznie w ramach istniejącej transakcji rozproszonej, gdy ustali, że jest aktywna transakcja. Rejestracja automatyczna transakcja występuje, gdy połączenie jest otwarte lub pobierane z puli połączeń. Funkcja automatycznego rejestracji w istniejących transakcji można wyłączyć, określając  
  
```  
Enlist=false  
```  
  
 jako parametr ciągu połączenia dla <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Zobacz także
- [Oracle i ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
