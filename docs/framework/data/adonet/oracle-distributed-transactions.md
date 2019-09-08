---
title: Transakcje rozproszone Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 6f910f1dbbe448352c0edd5d1b80df659ac453d4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795149"
---
# <a name="oracle-distributed-transactions"></a>Transakcje rozproszone Oracle
<xref:System.Data.OracleClient.OracleConnection> Obiekt jest automatycznie zarejestrowany w istniejącej transakcji rozproszonej, jeśli określa, że transakcja jest aktywna. Automatyczne rejestracje transakcji odbywa się po otwarciu lub pobraniu połączenia z puli połączeń. Funkcję autorejestracji można wyłączyć w istniejących transakcjach, określając  
  
```  
Enlist=false  
```  
  
 jako parametr parametrów połączenia dla <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Zobacz także

- [Oracle i ADO.NET](oracle-and-adonet.md)
- [Omówienie ADO.NET](ado-net-overview.md)
