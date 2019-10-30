---
title: Transakcje rozproszone Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: edd06b94ce4157e90d334ee7feac2a449f7ee74b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040481"
---
# <a name="oracle-distributed-transactions"></a>Transakcje rozproszone Oracle
Obiekt <xref:System.Data.OracleClient.OracleConnection> jest automatycznie zarejestrowany w istniejącej transakcji rozproszonej, jeśli określa, że transakcja jest aktywna. Automatyczne rejestracje transakcji odbywa się po otwarciu lub pobraniu połączenia z puli połączeń. Funkcję autorejestracji można wyłączyć w istniejących transakcjach, określając  
  
```csharp  
Enlist=false  
```  
  
 jako parametr parametrów połączenia dla <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Zobacz także

- [Oracle i ADO.NET](oracle-and-adonet.md)
- [Omówienie ADO.NET](ado-net-overview.md)
